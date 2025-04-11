![Kruger Corp](https://img.shields.io/badge/Kruger_Corp_®-Copyright_2022-blue)

# k-component-filter

Component with search filters for sidebar Template, Component that contains the logic for search filters

## Class Name

`PersonsFiltersComponent`

## Dependencies

* `Component, EventEmitter, Output, ViewChild` from `@angular/core`
* `KSearchInputDateComponent, KSearchInputNumberComponent, KSearchInputNumericComponent, KSearchInputTextComponent, KSearchSelectComponent, KSearchTableComponent, OptionConfigModel, PrimeNgEs` from `@ec.com.kgr/kng-components-v3/k-search`
* `CommonModule` from `@angular/common`
* `FormsModule` from `@angular/forms`
* `KFieldsetComponent` from `@ec.com.kgr/kng-components-v3/k-fieldset`
* `NumbersDirective, UpperCaseDirective, ToUpperCaseDirective` from `@ec.com.kgr/kng-components-v3/k-common/k-directives`
* `PersonsFilterService` from `@persons/services/persons-filter.service`
* `PopoverModule` from `ngx-bootstrap/popover`
* `KValidationsModule` from `@ec.com.kgr/kng-components-v3/k-common/k-validations`

## Selector

`app-persons-filters`

This is a standalone component.

### Required Imports

* `CommonModule`
* `FormsModule`
* `KFieldsetComponent`
* `KSearchInputTextComponent`
* `KSearchInputDateComponent`
* `KSearchSelectComponent`
* `PopoverModule`
* `KValidationsModule`

## Import

```typescript
import { PersonsFiltersComponent } from '@ec.com.kgr/kng-components-v3/persons-filters';
```

## TypeScript

```typescript
import { Component, EventEmitter, Output, ViewChild } from '@angular/core';
import {
  KSearchInputDateComponent, KSearchInputNumberComponent, KSearchInputNumericComponent,
  KSearchInputTextComponent, KSearchSelectComponent, KSearchTableComponent,OptionConfigModel, PrimeNgEs
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
  styleUrl: './persons-filters.component.scss'
})
export class PersonsFiltersComponent {

  /** Output event */
  @Output() onSearchEvent: EventEmitter<any> = new EventEmitter();
  @Output() change = new EventEmitter<any>();
  statusList: Array<any>;

  optionSettings: OptionConfigModel = new OptionConfigModel(true, true, true);
  rangeOptionSettings: OptionConfigModel = new OptionConfigModel(true, true, true);


  constructor(
    public personsFilterService: PersonsFilterService) {
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
      {
        'status': 'Todos',
        'value': 'TODOS'
      },
      {
        'status': 'Activo',
        'value': 'true'
      },
      {
        'status': 'Inactivo',
        'value': 'false'
      }
    ];
  }
}
```

## HTML

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

## Usage

Component can be used with the following selectors:

* `<k-component-filter`
* `k-component-filter`

## Input Properties

* `[descriptionValue]`: Defines the descriptionValue.
* `[disabledCommaList]`: Defines the disabledCommaList.
* `[itemList]`: Defines the itemList.
* `[label]`: Defines the label.
* `[maxlength]`: Defines the maxlength.
* `[notFoundText]`: Defines the notFoundText.
* `[optionSettings]`: Defines the optionSettings.
* `[optionValue]`: Defines the optionValue.
* `[placeholder]`: Defines the placeholder.
* `[popover]`: Defines the popover.
* `[regularExpression]`: Defines the regularExpression.
* `[required]`: Defines the required.
* `[showComparatorType]`: Defines the showComparatorType.
* `[showIcon]`: Defines the showIcon.
* `[showTime]`: Defines the showTime.
* `[upperInputValue]`: Defines the upperInputValue.
* `[yearRange]`: Defines the yearRange.

## Output Events

* `(click)`: Event emitted when click occurs.
* `(ngModel)`: Event emitted when ngModel occurs.
* `(submitValidForm)`: Event emitted when submitValidForm occurs.

## Attributes

* `0`: Defines the 0 attribute.
* `ALPHANUMERIC`: Defines the ALPHANUMERIC attribute.
* `BUTTONS`: Defines the BUTTONS attribute.
* `BY`: Defines the BY attribute.
* `Buscar`: Defines the Buscar attribute.
* `CHARACTERS`: Defines the CHARACTERS attribute.
* `DATE`: Defines the DATE attribute.
* `DOCUMMENT`: Defines the DOCUMMENT attribute.
* `EMAIL`: Defines the EMAIL attribute.
* `FILTER`: Defines the FILTER attribute.
* `NAME`: Defines the NAME attribute.
* `NUMBERS`: Defines the NUMBERS attribute.
* `ONLY`: Defines the ONLY attribute.
* `REGISTER`: Defines the REGISTER attribute.
* `SECONDNAME`: Defines the SECONDNAME attribute.
* `Status`: Defines the Status attribute.
* `búsqueda`: Defines the búsqueda attribute.
* `de`: Defines the de attribute.
* `encontraron`: Defines the encontraron attribute.
* `filtros`: Defines the filtros attribute.
* `kFieldsetLegend`: Defines the kFieldsetLegend attribute.
* `los`: Defines the los attribute.
* `name`: Defines the name attribute.
* `registro`: Defines the registro attribute.
* `resultados`: Defines the resultados attribute.
* `se`: Defines the se attribute.
* `todos`: Defines the todos attribute.

