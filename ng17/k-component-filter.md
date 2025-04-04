![Kruger Corp](https://img.shields.io/badge/Kruger_Corp_®-Copyright_2022-blue)


# kng-components-v3

## k-component-filter

El Componente k-component-filter proporciona una estructura completa para implementar filtros de búsqueda en aplicaciones web con `angular 17`. Integra los componentes de búsqueda de k-search con un diseño estándar y lógica de gestión de filtros. El componente depende de librerías de terceros tales como `bootstrap4`, `primeng` y `ngx-bootstrap/popover`, los cuales deben ser incluidos.

```typescript
import { Component, EventEmitter, Output, ViewChild } from '@angular/core';
import {
  KSearchInputDateComponent, KSearchInputNumberComponent, KSearchInputNumericComponent,
  KSearchInputTextComponent, KSearchSelectComponent, KSearchTableComponent, OptionConfigModel, PrimeNgEs
} from '@ec.com.kgr/kng-components-v3/k-search';
import { CommonModule } from '@angular/common';
import { FormsModule } from '@angular/forms';
import { KFieldsetComponent } from '@ec.com.kgr/kng-components-v3/k-fieldset';
import { NumbersDirective, UpperCaseDirective, ToUpperCaseDirective } from '@ec.com.kgr/kng-components-v3/k-common/k-directives';
import { PersonsFilterService } from '@persons/services/persons-filter.service';
import { PopoverModule } from 'ngx-bootstrap/popover';
import { KValidationsModule } from '@ec.com.kgr/kng-components-v3/k-common/k-validations';

/**
 * Persons filters module
 *
 * @author components on 2024/06/18.
 * @version 1.0
 * @since 1.0.0
 */

@Component({
  selector: 'app-persons-filters',
  standalone: true,
  imports: [
    CommonModule,
    FormsModule,
    KFieldsetComponent,
    KSearchInputTextComponent,
    KSearchInputDateComponent,
    KSearchSelectComponent,
    PopoverModule,
    KValidationsModule
  ],
  templateUrl: './persons-filters.component.html',
  styleUrls: ['./persons-filters.component.scss']
})
export class PersonsFiltersComponent {

  /** Output event */
  @Output() onSearchEvent: EventEmitter<any> = new EventEmitter();
  @Output() change = new EventEmitter<any>();

  statusList: Array<any>;

  optionSettings: OptionConfigModel = new OptionConfigModel(true, true, true);
  rangeOptionSettings: OptionConfigModel = new OptionConfigModel(true, true, true);

  constructor(public personsFilterService: PersonsFilterService) {
    this.findStatus();
    this.personsFilterService.status.parameterValue = 'TODOS';
  }

  /**
   * Clean filters before to leave view.
   */
  ngOnDestroy() {
    this.cleanFilters();
    this.personsFilterService.cleanFilters();
  }

  /**
   * Clean filters action dispatch event.
   */
  cleanFilters() {
    this.personsFilterService.cleanFilters();
    this.personsFilterService.status.parameterValue = 'TODOS';
    this.findStatus();
  }

  /**
   * Search action to call search event.
   */
  clickSearch() {
    this.onSearchEvent.emit();
  }

  /**
   * Find status.
   */
  findStatus() {
    this.statusList = [
      { 'status': 'Todos', 'value': 'TODOS' },
      { 'status': 'Activo', 'value': 'true' },
      { 'status': 'Inactivo', 'value': 'false' }
    ];
  }
}
```

### Estructura Completa del Componente

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
        <!--SEARCH BY NAME - FILTER: ONLY CHARACTERS-->
        <div class="form-group">
            <k-fieldset kFieldsetLegend='Personas' class='d-block mt-2'>
                <div class="k-search-space-top">
                    <k-search-input-text class="k-search-space-top" id="firstName" name="Nombre" [required]="true"
                        [(ngModel)]="personsFilterService.firstName" [upperInputValue]="true" [placeholder]="''"
                        [showComparatorType]="true" [disabledCommaList]="true" [label]="'Nombre:'"
                        [optionSettings]="optionSettings" [maxlength]="50"
                        [regularExpression]="'[a-zñA-ZÑ ]'">
                    </k-search-input-text>
                </div>
                <!--SEARCH BY SECONDNAME - FILTER: ONLY ALPHANUMERIC-->
                <div class="k-search-space-top">
                    <k-search-input-text class="k-search-space-top" id="lastName" name="Apellido"
                        [(ngModel)]="personsFilterService.lastName" [upperInputValue]="true"
                        [placeholder]="''" [showComparatorType]="true" [disabledCommaList]="true"
                        [label]="'Apellido:'" [optionSettings]="optionSettings" [maxlength]="50"
                        [regularExpression]="'[a-zñA-ZÑ 0-9]'">
                    </k-search-input-text>
                </div>
                <!--SEARCH BY DOCUMMENT - FILTER: ONLY NUMBERS-->
                <div class="k-search-space-top">
                    <k-search-input-text class="k-search-space-top" id="documentNumber" name="Cédula"
                        [(ngModel)]="personsFilterService.documentNumber" [upperInputValue]="true"
                        [placeholder]="''" [showComparatorType]="false" [disabledCommaList]="false"
                        [label]="'Cédula:'" [optionSettings]="rangeOptionSettings" [maxlength]="10"
                        [regularExpression]="'[0-9]'">
                    </k-search-input-text>
                </div>
                <!--SEARCH BY EMAIL-->
                <div class="k-search-space-top">
                    <k-search-input-text class="k-search-space-top" id="email" name="Correo"
                        [(ngModel)]="personsFilterService.email" [placeholder]="''" [showComparatorType]="false"
                        [disabledCommaList]="false" [label]="'Correo:'" [optionSettings]="optionSettings"
                        [maxlength]="50">
                    </k-search-input-text>
                </div>
                <!--SEARCH BY DATE REGISTER-->
                <div class="k-search-space-top">
                    <k-search-input-date class="k-search-space-top" id="createdDate" name="Fecha registro"
                        [label]="'Fecha registro:'" [optionSettings]="rangeOptionSettings" [required]="false"
                        [showComparatorType]="true" [showTime]="false"
                        [showIcon]="true" [(ngModel)]="personsFilterService.createdDate" [yearRange]="'1'">
                    </k-search-input-date>
                </div>

                <!--SEARCH BY Status-->
                <div class="k-search-space-top">
                    <k-search-select class="k-search-space-top" id="status" name="Estado"
                        [(ngModel)]="personsFilterService.status" [itemList]="statusList" [label]="'Estado:'"
                        [optionSettings]="optionSettings" [optionValue]="'value'"
                        [descriptionValue]="['status']" [placeholder]="'Seleccione'"
                        [notFoundText]="'No se encontraron resultados.'">
                    </k-search-select>
                </div>

            </k-fieldset>
        </div>
    </div>

    <!--SEARCH BUTTONS-->
    <div class="row k-search-button float-right">
        <button class="btn btn-primary"><em class="fa fa-search"></em> Buscar</button>
    </div>
</form>
</div>
</div>
```

### Propiedades de los componentes de búsqueda

* **k-search-input-text**:
  * required: Especifica true o false para definir si el campo es obligatorio.
  * upperInputValue: Especifica true o false para convertir automáticamente a mayúsculas el texto ingresado.
  * placeholder: Establece el texto guía dentro del campo de entrada.
  * showComparatorType: Especifica true o false para mostrar las opciones de comparación (igual, contiene, etc).
  * disabledCommaList: Especifica true o false para deshabilitar la entrada de listas separadas por comas.
  * label: Establece el texto de la etiqueta del campo.
  * optionSettings: Configura las opciones de búsqueda mediante el modelo OptionConfigModel.
  * maxlength: Establece el número máximo de caracteres permitidos.
  * regularExpression: Define una expresión regular para validar el texto ingresado.

* **k-search-input-date**:
  * label: Establece el texto de la etiqueta del campo.
  * optionSettings: Configura las opciones de búsqueda mediante el modelo OptionConfigModel.
  * required: Especifica true o false para definir si el campo es obligatorio.
  * showComparatorType: Especifica true o false para mostrar las opciones de comparación (mayor que, menor que, etc).
  * showTime: Especifica true o false para mostrar la selección de hora.
  * showIcon: Especifica true o false para mostrar el icono del calendario.
  * yearRange: Establece el rango de años disponibles en el selector.

* **k-search-select**:
  * itemList: Establece el array de opciones a mostrar en el selector.
  * label: Establece el texto de la etiqueta del campo.
  * optionSettings: Configura las opciones de búsqueda mediante el modelo OptionConfigModel.
  * optionValue: Define la propiedad utilizada como valor en el selector.
  * descriptionValue: Define la propiedad o propiedades mostradas como texto en el selector.
  * placeholder: Establece el texto guía cuando no hay selección.
  * notFoundText: Establece el mensaje cuando no se encuentran resultados.

### Eventos principales

* onSearchEvent: Evento emitido cuando se realiza una búsqueda.
* cleanFilters: Método para limpiar todos los filtros aplicados.

### Estructura Completa del Componente

Para ver la estructura completa del componente, consulte el ejemplo en la documentación inicial.
