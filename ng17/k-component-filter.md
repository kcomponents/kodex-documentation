![Kruger Corp](https://img.shields.io/badge/Kruger_Corp_®-Copyright_2022-blue)


# kng-components-v3

## k-component-filter

El Componente k-component-filter proporciona una estructura completa para implementar filtros de búsqueda en aplicaciones web con `angular 17`. Integra los componentes de búsqueda de k-search con un diseño estándar y lógica de gestión de filtros.

```typescript
import { Component, OnInit } from '@angular/core';
import { CommonModule } from '@angular/common';
import { FormsModule } from '@angular/forms';
import { KSearchModule } from '@ec.com.kgr/kng-components-v3/k-search';
import { KFieldsetComponent } from '@ec.com.kgr/kng-components-v3/k-fieldset';
import { PopoverModule } from 'ngx-bootstrap/popover';
import { KDirectivesModule } from '@ec.com.kgr/kng-components-v3/k-common/k-directives';

@Component({
  selector: 'app-parameter-filters',
  standalone: true,
  templateUrl: './parameter-filters.component.html',
  styleUrls: ['./parameter-filters.component.scss'],
  imports: [
    CommonModule,
    FormsModule,
    KSearchModule,
    KFieldsetComponent,
    PopoverModule,
    KDirectivesModule
  ]
})
export class ParameterFiltersComponent implements OnInit {
  optionSettings: any[];
  rangeOptionSettings: any[];
  itemList: any[];

  constructor(public filtersService: ParameterFilterService) { }

  ngOnInit() {
    this.initializeOptions();
    this.loadCatalogs();
  }

  /**
   * Initialize comparison options for filters
   */
  initializeOptions() {
    this.optionSettings = [
      { label: 'Contiene', value: 'CONTAINS' },
      { label: 'Igual', value: 'EQUALS' },
      { label: 'Inicia con', value: 'STARTS_WITH' },
      { label: 'Termina con', value: 'ENDS_WITH' }
    ];
    
    this.rangeOptionSettings = [
      { label: 'Mayor o igual que', value: 'GREATER_THAN_EQUAL' },
      { label: 'Menor o igual que', value: 'LESS_THAN_EQUAL' },
      { label: 'Entre', value: 'BETWEEN' }
    ];
  }

  /**
   * Load catalogs for select filters
   */
  loadCatalogs() {
    // Implementation to load data for dropdown selects
  }

  /**
   * Trigger search event
   */
  clickSearch() {
    this.filtersService.searchEvent.emit();
  }

  /**
   * Clean all filters
   */
  cleanFilters() {
    this.filtersService.cleanFilters();
  }
}
```

### Estructura Completa del Componente

```html
<!--k-content-filters-->
<div class="card">
    <div class="card-header">
        <h5>Filtros de búsqueda</h5>
        <div class="kl-sidebar-filter-buttons">
            <button type="button" class="btn btn-default" (click)="cleanFilters()">
                <span class="k-search-options text-center" [popover]="'Borrar todos los filtros'">
                    <em class="fa fa-eraser text-primary"></em>
                </span>
            </button>
        </div>
    </div>
    <div class="card-body">
        <form class="form" #resultForm="ngForm" (submitValidForm)="clickSearch()">
            <div class="scroll-sidebar">
                <div class="form-group">
                    <k-fieldset kFieldsetLegend='Parámetros' class='d-block mt-2'>
                        <!-- Filtro de texto para nombre -->
                        <k-search-input-text class="k-search-space-top" id="name" name="name"
                            [label]="'Nombre:'" [placeholder]="'Ingrese el nombre'" [(ngModel)]="filtersService.searchModel.name"
                            [optionSettings]="optionSettings" [showComparatorType]="true" [disabledCommaList]="true"
                            [upperInputValue]="true" [maxlength]="50" [regularExpression]="'[a-zñA-ZÑ ]'"
                            [required]="false">
                        </k-search-input-text>
                        
                        <!-- Filtro de texto para código -->
                        <k-search-input-text class="k-search-space-top" id="code" name="code"
                            [label]="'Código:'" [placeholder]="'Ingrese el código'" [(ngModel)]="filtersService.searchModel.code"
                            [optionSettings]="optionSettings" [showComparatorType]="true" [disabledCommaList]="true"
                            [upperInputValue]="true" [maxlength]="20" [regularExpression]="'[a-zñA-ZÑ 0-9]'"
                            [required]="false">
                        </k-search-input-text>
                        
                        <!-- Filtro de selección para tipo -->
                        <k-search-select class="k-search-space-top" id="type" name="type" [label]="'Tipo:'"
                            [placeholder]="'Seleccione'" [(ngModel)]="filtersService.searchModel.type"
                            [optionSettings]="optionSettings" [itemList]="itemList" [optionValue]="'id'"
                            [descriptionValue]="['name']" [notFoundText]="'No se encontraron resultados.'">
                        </k-search-select>
                    </k-fieldset>
                </div>
            </div>
            <div class="row k-search-button float-right">
                <button class="btn btn-primary"><em class="fa fa-search"></em> Buscar</button>
            </div>
        </form>
    </div>
</div>
```

### Servicio de Filtros

```typescript
import { EventEmitter, Injectable } from '@angular/core';

@Injectable({
  providedIn: 'root'
})
export class ParameterFilterService {
  searchModel: any = {};
  searchEvent = new EventEmitter<void>();

  constructor() {
    this.cleanFilters();
  }

  /**
   * Get filters for API request
   */
  getFilters() {
    const filters = [];
    if (this.searchModel.name && this.searchModel.name.value) {
      filters.push({ field: 'name', value: this.searchModel.name.value, operation: this.searchModel.name.operation });
    }
    if (this.searchModel.code && this.searchModel.code.value) {
      filters.push({ field: 'code', value: this.searchModel.code.value, operation: this.searchModel.code.operation });
    }
    if (this.searchModel.type && this.searchModel.type.value) {
      filters.push({ field: 'typeId', value: this.searchModel.type.value, operation: 'EQUALS' });
    }
    return filters;
  }

  /**
   * Reset all filters to default state
   */
  cleanFilters() {
    this.searchModel = {
      name: { value: null, operation: 'CONTAINS' },
      code: { value: null, operation: 'CONTAINS' },
      type: { value: null, operation: 'EQUALS' }
    };
  }
}
```

### Integración con Componente Principal

```typescript
import { Component, ViewChild } from '@angular/core';
import { Table } from 'primeng/table';
import { FilterVO } from '@ec.com.kgr/kng-components-v3/k-search';

@Component({
  // configuración del componente
})
export class MainComponent {
  @ViewChild('dataTable', { static: false }) private dataTable: Table;
  values: any[];
  totalRecords: number;
  request: FilterVO;

  constructor(
    private parameterService: ParameterService,
    public filterService: ParameterFilterService
  ) {
    this.request = new FilterVO();
    this.listenForFilterEvents();
  }

  listenForFilterEvents() {
    this.filterService.searchEvent.subscribe(() => {
      this.onSearchEvent();
    });
  }

  onSearchEvent() {
    this.dataTable.clear();
  }

  paginationEvent(event) {
    this.loadData((event.first / this.rows));
  }

  loadData(page) {
    this.request.filters = this.filterService.getFilters();
    this.request.page = page;
    this.request.size = this.rows;
    
    this.parameterService.findByFilter(this.request).subscribe(response => {
      const data = response.data;
      if (data.content) {
        this.values = data.content;
      } else {
        this.values = [];
      }
      this.totalRecords = data.total;
    });
  }
}
```

### Características Principales

* **Diseño Estructurado**: Proporciona una estructura visual coherente para los filtros de búsqueda.
* **Integración con k-search**: Utiliza los componentes de filtro avanzados de k-search.
* **Gestión de Eventos**: Incluye sistema de eventos para comunicación entre componentes.
* **Limpieza de Filtros**: Botón para restablecer todos los filtros a sus valores predeterminados.
* **Formulario Validado**: Implementa validación de formularios mediante directivas personalizadas.
* **Espaciado Consistente**: Usa clases como k-search-space-top para mantener el espaciado visual.

### Elementos Visuales

* **Card Header**: Encabezado que muestra el título "Filtros de búsqueda" y el botón para limpiar filtros.
* **Card Body**: Área principal que contiene el formulario con los filtros.
* **Botón de Búsqueda**: Botón para desencadenar la búsqueda con los filtros seleccionados.
* **Scroll-sidebar**: Área con desplazamiento para contener todos los filtros.
* **Fieldset**: Agrupación de filtros relacionados bajo un título descriptivo.

### Propiedades del Servicio

* **searchModel**: Objeto que mantiene el estado actual de todos los filtros.
* **searchEvent**: Evento que se dispara cuando el usuario hace clic en el botón de búsqueda.
* **getFilters()**: Método que convierte el estado de searchModel en un formato adecuado para la API.
* **cleanFilters()**: Método para restablecer todos los filtros a sus valores predeterminados. 