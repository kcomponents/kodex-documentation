![Kruger Corp](https://img.shields.io/badge/Kruger_Corp_®-Copyright_2022-blue)


# kng-components-v3

## k-search

El Componente k-search proporciona elementos para implementar filtros de búsqueda avanzados en aplicaciones web con `angular 17`. Incluye diversos tipos de entrada con validaciones y opciones de comparación, perfectos para filtrar datos en tablas y listados.

```typescript
import { Component, OnInit } from '@angular/core';
import { KSearchModule } from '@ec.com.kgr/kng-components-v3/k-search';
import { FilterVO } from '@ec.com.kgr/kng-components-v3/k-search';
import { CommonModule } from '@angular/common';
import { FormsModule } from '@angular/forms';
import { KFieldsetComponent } from '@ec.com.kgr/kng-components-v3/k-fieldset';
import { PopoverModule } from 'ngx-bootstrap/popover';

@Component({
  selector: 'app-parameter-filters',
  standalone: true,
  templateUrl: './parameter-filters.component.html',
  imports: [
    CommonModule,
    FormsModule,
    KSearchModule,
    KFieldsetComponent,
    PopoverModule
  ]
})
export class ParameterFiltersComponent implements OnInit {
  optionSettings: any[];
  rangeOptionSettings: any[];
  itemList: any[];
  
  constructor(public filtersService: ParameterFilterService) { }

  ngOnInit() {
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

  clickSearch() {
    this.filtersService.searchEvent.emit();
  }

  cleanFilters() {
    this.filtersService.cleanFilters();
  }
}
```

### Componentes de Búsqueda

#### Búsqueda de Texto con Caracteres

```html
<k-search-input-text class="k-search-space-top" id="name" name="name"
    [label]="'Nombre:'" [placeholder]="'Ingrese el nombre'" [(ngModel)]="filtersService.searchModel"
    [optionSettings]="optionSettings" [showComparatorType]="true" [disabledCommaList]="true"
    [upperInputValue]="true" [maxlength]="50" [regularExpression]="'[a-zñA-ZÑ ]'"
    [required]="false">
</k-search-input-text>
```

#### Búsqueda de Texto Alfanumérico

```html
<k-search-input-text class="k-search-space-top" id="code" name="code"
    [label]="'Código:'" [placeholder]="'Ingrese el código'" [(ngModel)]="filtersService.searchModel"
    [optionSettings]="optionSettings" [showComparatorType]="true" [disabledCommaList]="true"
    [upperInputValue]="true" [maxlength]="50" [regularExpression]="'[a-zñA-ZÑ 0-9]'"
    [required]="false">
</k-search-input-text>
```

#### Búsqueda Numérica

```html
<k-search-input-numeric class="k-search-space-top" id="age" name="age"
    [label]="'Edad:'" [placeholder]="'Ingrese la edad'" [(ngModel)]="filtersService.searchModel"
    [optionSettings]="rangeOptionSettings" [showComparatorType]="true"
    [disabledCommaList]="true" [maxlength]="50" [required]="false">
</k-search-input-numeric>
```

#### Búsqueda por Fecha

```html
<k-search-input-date class="k-search-space-top" id="date" name="date"
    [label]="'Fecha:'" [(ngModel)]="filtersService.searchModel"
    [optionSettings]="rangeOptionSettings" [showComparatorType]="true" [showTime]="false"
    [showIcon]="true" [yearRange]="1" [maxDate]="maxDate" [minDate]="minDate" [required]="true">
</k-search-input-date>
```

#### Selección con Búsqueda

```html
<k-search-select class="k-search-space-top" id="type" name="type" [label]="'Tipo:'"
    [placeholder]="'Seleccione'" [(ngModel)]="filtersService.searchModel"
    [optionSettings]="optionSettings" [itemList]="itemList" [optionValue]="'id'"
    [descriptionValue]="['name']" [notFoundText]="'No se encontraron resultados.'">
</k-search-select>
```

### Componente de Filtro Completo

```html
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
                        <k-search-input-text class="k-search-space-top" id="name" name="name"
                            [label]="'Nombre:'" [placeholder]="'Ingrese el nombre'" [(ngModel)]="filtersService.searchModel.name"
                            [optionSettings]="optionSettings" [showComparatorType]="true" [disabledCommaList]="true"
                            [upperInputValue]="true" [maxlength]="50" [regularExpression]="'[a-zñA-ZÑ ]'"
                            [required]="false">
                        </k-search-input-text>
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

### Propiedades Comunes

* **id**: Identificador único del elemento.
* **name**: Nombre del elemento para el formulario.
* **label**: Etiqueta que se muestra junto al componente.
* **placeholder**: Texto de ayuda dentro del campo de entrada.
* **ngModel**: Enlace bidireccional con la propiedad del modelo.
* **optionSettings**: Arreglo de opciones para el comparador.
* **showComparatorType**: Especifica true o false para mostrar el selector de tipo de comparación.
* **disabledCommaList**: Especifica true o false para deshabilitar la lista separada por comas.
* **required**: Especifica true o false si el campo es obligatorio.

### Propiedades Específicas

#### k-search-input-text / k-search-input-alphanumeric
* **upperInputValue**: Especifica true o false para convertir el texto a mayúsculas.
* **maxlength**: Establece la longitud máxima del texto.
* **regularExpression**: Expresión regular para validar la entrada.

#### k-search-input-date
* **showTime**: Especifica true o false para mostrar selectores de hora y minuto.
* **showIcon**: Especifica true o false para mostrar un ícono de calendario.
* **yearRange**: Establece el rango de años a mostrar.
* **maxDate**: Establece la fecha máxima seleccionable.
* **minDate**: Establece la fecha mínima seleccionable.

#### k-search-select
* **itemList**: Arreglo de elementos para seleccionar.
* **optionValue**: Propiedad de los elementos a usar como valor.
* **descriptionValue**: Propiedades de los elementos a mostrar como descripción.
* **notFoundText**: Texto a mostrar cuando no se encuentran resultados.

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

  getFilters() {
    const filters = [];
    if (this.searchModel.name && this.searchModel.name.value) {
      filters.push({ field: 'name', value: this.searchModel.name.value, operation: this.searchModel.name.operation });
    }
    return filters;
  }

  cleanFilters() {
    this.searchModel = {
      name: { value: null, operation: 'CONTAINS' }
    };
  }
}
``` 