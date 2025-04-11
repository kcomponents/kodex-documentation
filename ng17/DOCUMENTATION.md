![Kruger Corp](https://img.shields.io/badge/Kruger_Corp_®-Copyright_2022-blue)

# kng-components-v3

## Documentación de Componentes Angular 17

Esta documentación describe los componentes y utilidades disponibles en la librería kng-components-v3 para Angular 17. La librería ofrece una colección de componentes predefinidos para construir aplicaciones web con un diseño y funcionalidad estandarizados.

### Índice de Componentes

1. [k-layout](https://github.com/kcomponents/kodex-documentation/blob/simple/ng17/k-layout.md) - Estructura principal de la aplicación, con cabecera, barra lateral y área de contenido.
2. [k-table](https://github.com/kcomponents/kodex-documentation/blob/simple/ng17/k-table.md) - Tabla de datos con paginación, ordenamiento y acciones.
3. [k-modal](https://github.com/kcomponents/kodex-documentation/blob/simple/ng17/k-modal.md) - Ventanas modales para formularios y contenido interactivo.
4. [k-search](https://github.com/kcomponents/kodex-documentation/blob/simple/ng17/k-search.md) - Componentes de búsqueda y filtrado avanzados.
5. [k-button](https://github.com/kcomponents/kodex-documentation/blob/simple/ng17/k-button.md) - Botones estilizados para diferentes acciones y contextos.
6. [k-component-filter](https://github.com/kcomponents/kodex-documentation/blob/simple/ng17/k-component-filter.md) - Componente completo para implementar filtros de búsqueda.
7. [k-component-panel-menu](https://github.com/kcomponents/kodex-documentation/blob/simple/ng17/k-component-panel-menu.md)
8. [k-confirm-dialog](https://github.com/kcomponents/kodex-documentation/blob/simple/ng17/k-confirm-dialog.md)
9. [k-footer](https://github.com/kcomponents/kodex-documentation/blob/simple/ng17/k-footer.md)
10. [k-message](https://github.com/kcomponents/kodex-documentation/blob/simple/ng17/k-message.md)
11. [k-panel-menu](https://github.com/kcomponents/kodex-documentation/blob/simple/ng17/k-panel-menu.md)
12. [k-scss](https://github.com/kcomponents/kodex-documentation/blob/simple/ng17k-scss.md)
13. [k-tree](https://github.com/kcomponents/kodex-documentation/blob/simple/ng17/k-tree.md)
14. [k-user-service](https://github.com/kcomponents/kodex-documentation/blob/simple/ng17/k-user-service.md)
15. [k-validations](https://github.com/kcomponents/kodex-documentation/blob/simple/ng17/k-validations.md)
16. [k-viewer](https://github.com/kcomponents/kodex-documentation/blob/simple/ng17/k-viewer.md)
17. [typescript](https://github.com/kcomponents/kodex-documentation/blob/simple/ng17/typescript.md)


### Instalación

Para utilizar estos componentes, es necesario incluir las siguientes dependencias en su proyecto:

- Angular 17
- Bootstrap 4
- PrimeNG con tema Bootstrap
- Toastr
- Font Awesome

### Importación

Cada componente puede ser importado de forma individual o mediante módulos principales:

```typescript
// Importación individual de componentes
import { KLayoutComponent } from '@ec.com.kgr/kng-components-v3/k-layout';
import { KSearchModule } from '@ec.com.kgr/kng-components-v3/k-search';

// Ejemplo de uso en un componente standalone
@Component({
  selector: 'app-my-component',
  standalone: true,
  imports: [
    KLayoutComponent,
    KSearchModule
  ]
})
export class MyComponent { }
```

### Características Generales

- **Componentes Standalone**: Diseñados para Angular 17 con el enfoque standalone.
- **Diseño Responsivo**: Adaptables a diferentes tamaños de pantalla.
- **Estilo Consistente**: Aplicación de estilos uniformes a través de todos los componentes.
- **Integración con PrimeNG**: Utiliza y extiende componentes de PrimeNG.
- **Soporte para Formularios**: Integración con Angular Forms para validación y manejo de datos.
- **Internacionalización**: Preparados para soportar múltiples idiomas.

### Uso Recomendado

Para una experiencia óptima, se recomienda utilizar los componentes en conjunto para mantener la coherencia visual y funcional. El flujo típico de una aplicación incluiría:

1. Definir la estructura general con k-layout
2. Implementar filtros de búsqueda con k-component-filter
3. Mostrar datos en tablas con k-table
4. Gestionar formularios en modales con k-modal
5. Utilizar botones estandarizados con k-button

Consulte la documentación específica de cada componente para más detalles de implementación y ejemplos.






# k-button-header-new

New button for header template section

## TypeScript

No TypeScript implementation available.

## HTML

```html


<!--k-button-header-new-->
  <ul class="nav-ul">
      <li  class="nav-item">
          <a class="nav-link text-a" (click)="${1:function name}" [popover]="'${2:action name popover}'">
              <em class="fa fa-file-o text-info"></em> ${3:action name}
          </a>
      </li>
  </ul>
```

## Usage

Component can be used with the following selectors:

* `<k-button-header-new`
* `k-button-header-new`

## Input Properties

* `[popover]`: Defines the popover.

## Output Events

* `(click)`: Event emitted when click occurs.

## Attributes

* `name`: Defines the name attribute.






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




# k-component-layout

Complete component containing the layout with the app name, title, headerTemplate, helpTemplate, sidebarTemplate, mycontent and paginated table, Complete component containing the logic for: layout with app name, title, headerTemplate, helpTemplate, sidebarTemplate, mycontent and paginated table

## Class Name

`PersonsContentComponent`

## Dependencies

* `Component, ViewChild` from `@angular/core`
* `constants` from `@const/constants`
* `ResponseVO` from `@ec.com.kgr/kng-components-v3/k-common`
* `PersonsService` from `@persons/services/persons.service`
* `DialogService, DynamicDialogRef` from `primeng/dynamicdialog`
* `HttpClientModule` from `@angular/common/http`
* `KLayoutComponent` from `@ec.com.kgr/kng-components-v3/k-layout`
* `CommonModule` from `@angular/common`
* `KDirectivesModule` from `@ec.com.kgr/kng-components-v3/k-common/k-directives`
* `FormsModule` from `@angular/forms`
* `KFieldsetComponent` from `@ec.com.kgr/kng-components-v3/k-fieldset`
* `PopoverModule` from `ngx-bootstrap/popover`
* `Table, TableModule` from `primeng/table`
* `PersonVO` from `@persons/vo/persons-vo`
* `KMessageService` from `@ec.com.kgr/kng-components-v3/k-common/k-message`
* `ConfirmationService` from `primeng/api`
* `ConfirmDialogModule` from `primeng/confirmdialog`
* `PersonsModalComponent` from `@persons/modals/persons-modal/persons-modal.component`
* `PersonsFiltersComponent` from `@persons/components/persons-filters/persons-filters.component`
* `PersonsFilterService` from `@persons/services/persons-filter.service`
* `UserService` from `@ec.com.kgr/kng-components-v3/k-security`
* `FilterVO` from `@ec.com.kgr/kng-components-v3/k-search`

## Selector

`app-persons-content`

This is a standalone component.

### Required Imports

* `HttpClientModule`
* `KLayoutComponent`
* `KFieldsetComponent`
* `CommonModule`
* `KDirectivesModule`
* `FormsModule`
* `TableModule`
* `PopoverModule`
* `ConfirmDialogModule`
* `PersonsFiltersComponent`

## Import

```typescript
import { PersonsContentComponent } from '@ec.com.kgr/kng-components-v3/persons-content';
```

## TypeScript

```typescript
import { Component, ViewChild } from '@angular/core';
import { constants } from '@const/constants';
import { ResponseVO } from '@ec.com.kgr/kng-components-v3/k-common';
import { PersonsService } from '@persons/services/persons.service';
import { DialogService, DynamicDialogRef } from 'primeng/dynamicdialog';
import { HttpClientModule } from '@angular/common/http';
import { KLayoutComponent } from '@ec.com.kgr/kng-components-v3/k-layout';
import { CommonModule } from '@angular/common';
import { KDirectivesModule } from '@ec.com.kgr/kng-components-v3/k-common/k-directives';
import { FormsModule } from '@angular/forms';
import { KFieldsetComponent } from '@ec.com.kgr/kng-components-v3/k-fieldset';
import { PopoverModule } from 'ngx-bootstrap/popover';
import { Table, TableModule } from 'primeng/table';
import { PersonVO } from '@persons/vo/persons-vo';
import { KMessageService } from '@ec.com.kgr/kng-components-v3/k-common/k-message';
import { ConfirmationService } from 'primeng/api';
import { ConfirmDialogModule } from 'primeng/confirmdialog';
import { PersonsModalComponent } from '@persons/modals/persons-modal/persons-modal.component';
import { PersonsFiltersComponent } from '@persons/components/persons-filters/persons-filters.component';
import { PersonsFilterService } from '@persons/services/persons-filter.service';
import { UserService } from '@ec.com.kgr/kng-components-v3/k-security';
import { FilterVO } from '@ec.com.kgr/kng-components-v3/k-search';

/**
 * Persons content module
 *
 * @author components on 2024/06/18.
 * @version 1.0
 * @since 1.0.0
 */

@Component({
  selector: 'app-persons-content',
  standalone: true,
  imports: [
    HttpClientModule,
    KLayoutComponent,
    KFieldsetComponent,
    CommonModule,
    KDirectivesModule,
    FormsModule,
    TableModule,
    PopoverModule,
    ConfirmDialogModule,
    PersonsFiltersComponent
  ],
  providers: [
    DialogService,
    ConfirmationService
  ],
  templateUrl: './persons-content.component.html',
  styleUrl: './persons-content.component.scss'
})

export class PersonsContentComponent {

  @ViewChild('dataTable', { static: false }) private dataTable: Table;
  text: string;
  persons: any[];
  ref: DynamicDialogRef;
  rows = 15;
  totalRecords: number;
  request: FilterVO;

  /**
   * Constructor.
   */
  constructor(
    private messageService: KMessageService,
    public dialogService: DialogService,
    private confirmationService: ConfirmationService,
    private userService: UserService,
    public filterService: PersonsFilterService,
    private personsService: PersonsService
  ) {
    this.request = new FilterVO();
  }

  /**
   * search event to throw pagination event.
   */
  onSearchEvent() {
    this.dataTable.clear();
  }

  /**
   * pagination event to call load data and changue datatable.
   * @param event have the page and rows of the datatable.
   */
  paginationEvent(event) {
    this.loadData((event.first / this.rows));
  }

  /**
  * load data call the API REST to get data by page and params.
  * @param page the calculated page for the API REST.
  */
  loadData(page) {
    this.request.filters = this.filterService.getFilters();
    this.request.page = page;
    this.request.size = this.rows;
    this.personsService.findByFilter(this.request).subscribe((response: ResponseVO) => {
      const data = response.data;
      if (data.content) {
        this.persons = data.content;
      } else {
        this.persons = [];
      }
      this.totalRecords = data.total;
      if (0 === data.total) {
        this.messageService.info('No se encontraron resultados con los filtros ingresados.');
      }
    });
  }

  /**
  * open the modal to  save person.
  */
  openSaveModal() {
    this.ref = this.dialogService.open(PersonsModalComponent, {
      header: 'Agregar persona',
    });
    this.closeModal();
  }

  /**
  * open the modal to  update person.
  * @param row is the person selected
  */
  openEditModal(row: PersonVO) {
    this.ref = this.dialogService.open(PersonsModalComponent, {
      header: 'Editar persona',
      data: row
    });
    this.closeModal();
  }

  closeModal() {
    this.ref.onClose.subscribe((data: PersonVO) => {
      if (data) {
        this.onSearchEvent();
      }
    });
  }

  /**
  * open the confirm dualog to delete person.
  * @param is the person selected
  */
  deletePerson(row: PersonVO) {
    this.confirmationService.confirm({
      message: row.firstName + ' ' + row.lastName + constants.MESSAGES.PERSON.CONFIRM_DELETE,
      header: 'Eliminar persona',
      accept: () => {
        this.personsService.deleteData(row.personId).subscribe(() => {
          this.onSearchEvent();
          this.messageService.success('Persona ' + row.firstName + ' ' + constants.MESSAGES.PERSON.DELETE + '.');
        });
      }
    });
  }

  logout(): void {
    this.userService.logout();
  }

}

```

## HTML

```html
<k-layout [appName]="'Proyecto Base'" [pageTitle]="'Administración de personas.'" [headerTemplate]="headerTemplate"
   (logout)="logout()" [disableLinkHome]="false" [sidebarTemplate]="sidebarTemplate" [disableLoading]="false"
   [helpTemplate]="helpTemplate" [audit]="false">
   <ng-container *ngTemplateOutlet="mycontent">
   </ng-container>
</k-layout>
<ng-template #headerTemplate>
  <ul class="nav-ul">
    <li class="nav-item">
      <a class="nav-link text-a" (click)="openSaveModal()" [popover]="'Nueva persona'">
        <em class="fa fa-file-o text-info"></em> Nuevo
      </a>
    </li>
  </ul>
</ng-template>
<ng-template #sidebarTemplate>
  <app-persons-filters (onSearchEvent)="onSearchEvent()"></app-persons-filters>
</ng-template>
<ng-template #mycontent>
  <div class="scroll-content-elements k-ptable-header k-paginator">
    <p-table #dataTable [value]="persons" [paginator]="true" [rows]="rows" paginatorPosition="top" [lazy]="true"
      [totalRecords]="totalRecords" (onLazyLoad)="paginationEvent($event)" responsiveLayout="scroll"
      styleClass="p-datatable-lg p-datatable-striped">
      <ng-template pTemplate="caption">
        <div class="k-ptable-header">
          Listado de personas
        </div>
      </ng-template>
      <ng-template pTemplate="paginatorleft" let-state>
        <a class="p-disabled">Pág. {{state.totalRecords > 0 ? state.page + 1:0}} de {{state?.pageCount || "0"}}</a>
      </ng-template>
      <ng-template pTemplate="paginatorright" let-state>
        <a class="p-disabled">Total Reg: {{state.totalRecords > 0 ? state.totalRecords : 0}}</a>
      </ng-template>
      <ng-template pTemplate="header">
        <tr>
          <th pSortableColumn="name" [style]="{width: '20%'}">
            Nombre
            <p-sortIcon field="name"></p-sortIcon>
          </th>
          <th pSortableColumn="lastName" [style]="{width: '20%'}">
            Apellido
            <p-sortIcon field="lastName"></p-sortIcon>
          </th>
          <th pSortableColumn="email" [style]="{width: '20%'}">
            Email
            <p-sortIcon field="email"></p-sortIcon>
          </th>
          <th pSortableColumn="phone" [style]="{width: '20%'}">
            Teléfono
            <p-sortIcon field="phone"></p-sortIcon>
          </th>
          <th [style]="{width: '20%'}">
            Acciones
          </th>
        </tr>
      </ng-template>
      <ng-template pTemplate="body" let-person>
        <tr>
          <td>
            {{person.name}}
          </td>
          <td>
            {{person.lastName}}
          </td>
          <td>
            {{person.email}}
          </td>
          <td>
            {{person.phone}}
          </td>
          <td>
            <button pButton type="button" icon="pi pi-pencil" class="p-button-rounded p-button-warning" (click)="openEditModal(person)"></button>
            <button pButton type="button" icon="pi pi-trash" class="p-button-rounded p-button-danger" (click)="deletePerson(person)"></button>
          </td>
        </tr>
      </ng-template>
    </p-table>
  </div>
</ng-template>
<!--HELP TEMPLATE-->
<ng-template #helpTemplate>
  <div class='row'>
    <div class='col-12'>
      <k-fieldset kFieldsetLegend='Iconografía'>
        <div class='row modal-help-body'>
          <div class='col-1'>
            <span class="fa fa-home icon-big text-primary"></span>
          </div>
          <div class='col-11'>
            <p class="mb-1">Inicio</p>
          </div>
          <div class='col-1'>
            <span class="fa fa-file-o text-info"></span>
          </div>
          <div class='col-11'>
            <p class="mb-1">Nueva persona</p>
          </div>
          <div class='col-1'>
            <span class="fa fa-check-circle-o text-success"></span>
          </div>
          <div class='col-11'>
            <p class="mb-1">Estado persona</p>
          </div>
          <div class='col-1'>
            <span class="fa fa-edit text-info"></span>
          </div>
          <div class='col-11'>
            <p class="mb-1">Editar persona</p>
          </div>
          <div class='col-1'>
            <span class="fa fa-trash text-danger"></span>
          </div>
          <div class='col-11'>
            <p class="mb-1">Eliminar persona</p>
          </div>
        </div>
      </k-fieldset>
    </div>
  </div>
</ng-template>
<!--CONFIRM DELETE DIALOG-->
<p-confirmDialog #button header="Confirmation" icon="pi pi-question-circle">
  <ng-template pTemplate="footer">
    <button class="k-button-accept" type="button" pButton icon="pi pi-check" label="Si"
      (click)="button.accept()"></button>
    <button type="button" pButton icon="pi pi-times" label="No" (click)="button.reject()"></button>
  </ng-template>
</p-confirmDialog>
```

## Usage

Component can be used with the following selectors:

* `k-component-layout`

## Input Properties

* `[appName]`: Defines the appName.
* `[audit]`: Defines the audit.
* `[disableLinkHome]`: Defines the disableLinkHome.
* `[disableLoading]`: Defines the disableLoading.
* `[headerTemplate]`: Defines the headerTemplate.
* `[helpTemplate]`: Defines the helpTemplate.
* `[lazy]`: Defines the lazy.
* `[pageTitle]`: Defines the pageTitle.
* `[paginator]`: Defines the paginator.
* `[popover]`: Defines the popover.
* `[rows]`: Defines the rows.
* `[sidebarTemplate]`: Defines the sidebarTemplate.
* `[style]`: Defines the style.
* `[totalRecords]`: Defines the totalRecords.
* `[value]`: Defines the value.

## Output Events

* `(click)`: Event emitted when click occurs.
* `(logout)`: Event emitted when logout occurs.
* `(onLazyLoad)`: Event emitted when onLazyLoad occurs.
* `(onSearchEvent)`: Event emitted when onSearchEvent occurs.

## Attributes

* `0`: Defines the 0 attribute.
* `1`: Defines the 1 attribute.
* `Acciones`: Defines the Acciones attribute.
* `Apellido`: Defines the Apellido attribute.
* `Base`: Defines the Base attribute.
* `DELETE`: Defines the DELETE attribute.
* `DIALOG`: Defines the DIALOG attribute.
* `Email`: Defines the Email attribute.
* `Listado`: Defines the Listado attribute.
* `Nombre`: Defines the Nombre attribute.
* `Nuevo`: Defines the Nuevo attribute.
* `Reg`: Defines the Reg attribute.
* `TEMPLATE`: Defines the TEMPLATE attribute.
* `Teléfono`: Defines the Teléfono attribute.
* `de`: Defines the de attribute.
* `field`: Defines the field attribute.
* `header`: Defines the header attribute.
* `icon`: Defines the icon attribute.
* `kFieldsetLegend`: Defines the kFieldsetLegend attribute.
* `label`: Defines the label attribute.
* `let`: Defines the let attribute.
* `pButton`: Defines the pButton attribute.
* `pSortableColumn`: Defines the pSortableColumn attribute.
* `pTemplate`: Defines the pTemplate attribute.
* `paginatorPosition`: Defines the paginatorPosition attribute.
* `persona`: Defines the persona attribute.
* `personas`: Defines the personas attribute.
* `responsiveLayout`: Defines the responsiveLayout attribute.
* `state`: Defines the state attribute.
* `styleClass`: Defines the styleClass attribute.




# k-component-panel-menu

Complete component containing all modules available per user profile, A complete component that contains the logic for all modules available to each user profile

## Class Name

`HomeContentComponent`

## Dependencies

* `Component` from `@angular/core`
* `KLayoutComponent` from `@ec.com.kgr/kng-components-v3/k-layout`
* `KPanelMenuComponent` from `@ec.com.kgr/kng-components-v3/k-panel-menu`
* `UserService` from `@ec.com.kgr/kng-components-v3/k-security`

## Selector

`app-home-content`

This is a standalone component.

### Required Imports

* `KLayoutComponent`
* `KPanelMenuComponent`

## Import

```typescript
import { HomeContentComponent } from '@ec.com.kgr/kng-components-v3/home-content';
```

## TypeScript

```typescript
import { Component } from '@angular/core';
import { KLayoutComponent } from '@ec.com.kgr/kng-components-v3/k-layout';
import { KPanelMenuComponent } from '@ec.com.kgr/kng-components-v3/k-panel-menu';
import { UserService } from '@ec.com.kgr/kng-components-v3/k-security';

/**
 * Home content
 *
 * @author components on 2024/06/18.
 * @version 1.0
 * @since 1.0.0
 */

@Component({
  selector: 'app-home-content',
  standalone: true,
  providers: [],
  templateUrl: './home-content.component.html',
  styleUrl: './home-content.component.scss',
  imports: [KLayoutComponent, KPanelMenuComponent]
})
export class HomeContentComponent {

  /**
   * constructor
   */
  constructor(private userService: UserService) {}

  /**
   * Logout
   */
  logout(): void {
    this.userService.logout();
  }
}
```

## HTML

```html
<!--k-panel-menu-->
<k-layout [appName]="'${1:app name}'" [showHome]="false" [pageTitle]="'${2:page title}'" (logout)="logout()">
   <k-panel-menu></k-panel-menu>
</k-layout>
```

## Usage

Component can be used with the following selectors:

* `k-component-panel-menu`
* `<k-component-panel-menu`

## Input Properties

* `[appName]`: Defines the appName.
* `[pageTitle]`: Defines the pageTitle.
* `[showHome]`: Defines the showHome.

## Output Events

* `(logout)`: Event emitted when logout occurs.

## Attributes

* `name`: Defines the name attribute.




# k-confirm-dialog

Confirm dialog component, k-confirm-dialog-1-imports

## Dependencies

* `ConfirmDialogModule` from `primeng/confirmdialog`

## TypeScript

```typescript
import { ConfirmDialogModule } from 'primeng/confirmdialog';
```

## HTML

```html


<!--k-confirm-dialog-->
<p-confirmDialog #button header="Confirmation" icon="pi pi-question-circle">
    <ng-template pTemplate="footer">
        <button class="k-button-accept" type="button" pButton icon="pi pi-check" label="${1:Si}"
            (click)="button.accept()"></button>
        <button type="button" pButton icon="pi pi-times" label="${2:No}" (click)="button.reject()"></button>
    </ng-template>
</p-confirmDialog>
```

## Usage

Component can be used with the following selectors:

* `k-confirm-dialog-1-imports`
* `k-confirm-dialog`
* `<k-confirm-dialog`

## Output Events

* `(click)`: Event emitted when click occurs.

## Attributes

* `header`: Defines the header attribute.
* `icon`: Defines the icon attribute.
* `label`: Defines the label attribute.
* `pButton`: Defines the pButton attribute.
* `pTemplate`: Defines the pTemplate attribute.



# k-fieldset

Expandable component grouper

## TypeScript

No TypeScript implementation available.

## HTML

```html
<k-fieldset kFieldsetLegend='${1:title}' class='d-block mt-2'>


</k-fieldset>
```

## Usage

Component can be used with the following selectors:

* `<k-fieldset`
* `k-fieldset`

## Attributes

* `kFieldsetLegend`: Defines the kFieldsetLegend attribute.



# k-footer

Footer component with logged in user information

## TypeScript

No TypeScript implementation available.

## HTML

```html
<k-footer></k-footer>
```

## Usage

Component can be used with the following selectors:

* `<k-footer`
* `k-footer`





# k-layout

Component containing the layout with the application name, title, headerTemplate, helpTemplate, sidebarTemplate, mycontent

## TypeScript

No TypeScript implementation available.

## HTML

```html
<k-layout [appName]="'${1:app name}'" [pageTitle]="'${2:page title}'" [sidebarTemplate]="sidebarTemplate"
[headerTemplate]="headerTemplate" (logout)="logout()" [toolTipHomeText]="'Inicio'" [helpTemplate]="helpTemplate"
[titleHelpText]="'${3:Ayuda}'">
   <ng-container *ngTemplateOutlet="contentTemplate">
   </ng-container>
</k-layout>


<ng-template #headerTemplate>
  <ul class="nav-ul">
      <li  class="nav-item">
          <a class="nav-link text-a" (click)="${4:openNewModal()}" [popover]="'${5:Nuevo}'">
              <em class="fa fa-file-o text-info"></em> ${6:Nuevo}
          </a>
      </li>
  </ul>
  <!--ADD K-BUTTON-HEADER -->


</ng-template>


<ng-template #sidebarTemplate>
    <${7:component-filters} (onSearchEvent)="onSearchEvent()">
    </${7:component-filters}>
</ng-template>


<ng-template #helpTemplate>
   <div class='row'>
      <div class='col-12'>
        <k-fieldset kFieldsetLegend='Iconografía'>
          <div class='row modal-help-body'>
            <div class='col-1'>
              <span class="fa fa-home icon-big text-primary"></span>
            </div>
            <div class='col-11'>
                <p class="mb-1">Inicio</p>
            </div>
            <!--ADD HELP ICONS-->


          </div>
        </k-fieldset>
      </div>
    </div>
</ng-template>


<ng-template #contentTemplate>
    <!-- ADD K-P-TABLE -->


</ng-template>
```

## Usage

Component can be used with the following selectors:

* `k-layout`
* `<k-layout`

## Input Properties

* `[appName]`: Defines the appName.
* `[headerTemplate]`: Defines the headerTemplate.
* `[helpTemplate]`: Defines the helpTemplate.
* `[pageTitle]`: Defines the pageTitle.
* `[popover]`: Defines the popover.
* `[sidebarTemplate]`: Defines the sidebarTemplate.
* `[titleHelpText]`: Defines the titleHelpText.
* `[toolTipHomeText]`: Defines the toolTipHomeText.

## Output Events

* `(click)`: Event emitted when click occurs.
* `(logout)`: Event emitted when logout occurs.
* `(onSearchEvent)`: Event emitted when onSearchEvent occurs.

## Attributes

* `ADD`: Defines the ADD attribute.
* `HELP`: Defines the HELP attribute.
* `ICONS`: Defines the ICONS attribute.
* `K`: Defines the K attribute.
* `kFieldsetLegend`: Defines the kFieldsetLegend attribute.
* `name`: Defines the name attribute.




# k-message-1-imports

Adds imports for the message service component

## Dependencies

* `KMessageService` from `@ec.com.kgr/kng-components-v3/k-common/k-message`

## TypeScript

```typescript
import { KMessageService } from '@ec.com.kgr/kng-components-v3/k-common/k-message';
```

## HTML

No HTML implementation available.

## Usage

Component can be used with the following selectors:

* `k-message-1-imports`




# k-modal-content

k-modal-content, k-modal-open-1-imports

## Dependencies

* `DialogService, DynamicDialogRef` from `primeng/dynamicdialog`

## TypeScript

```typescript
import { DialogService, DynamicDialogRef } from 'primeng/dynamicdialog';
```

## HTML

```html
<!--k-modal-content-->
<form class="form" #resultForm="ngForm" (submitValidForm)="${1:clickForm()}" autocomplete="off">
    <div class="container">
         <!-- ADD COMPONENTS -->


        <br>
    </div>
    <div class="modal-footer k-modal-footer">
        <button class="btn btn-success btn-sm">
            <em class="fa fa-save"></em> ${2:Guardar}
        </button>
        <button class="btn btn-danger btn-sm" type="reset" (click)="this.ref.close()">
            <em class="fa fa-close"></em> ${3:Cancelar}
        </button>
    </div>
</form>
```

## Usage

Component can be used with the following selectors:

* `k-modal-open-1-imports`
* `k-modal-content`
* `<k-modal-content`

## Output Events

* `(click)`: Event emitted when click occurs.
* `(submitValidForm)`: Event emitted when submitValidForm occurs.

## Attributes

* `ADD`: Defines the ADD attribute.
* `COMPONENTS`: Defines the COMPONENTS attribute.
* `autocomplete`: Defines the autocomplete attribute.





# k-panel-menu

Component that contains the modules available by profile and user

## TypeScript

No TypeScript implementation available.

## HTML

```html
<!--k-panel-menu-->
<k-layout [appName]="'${1:app name}'" [showHome]="false" [pageTitle]="'${2:page title}'" (logout)="logout()">
   <k-panel-menu></k-panel-menu>
</k-layout>
```

## Usage

Component can be used with the following selectors:

* `k-panel-menu`
* `<k-panel-menu`

## Input Properties

* `[appName]`: Defines the appName.
* `[pageTitle]`: Defines the pageTitle.
* `[showHome]`: Defines the showHome.

## Output Events

* `(logout)`: Event emitted when logout occurs.

## Attributes

* `name`: Defines the name attribute.




# k-width-action

k-width-action

## TypeScript

No TypeScript implementation available.

## HTML

```html
.k-width-action {
  width: 7em;
}
```

## Usage

Component can be used with the following selectors:

* `k-width-action`

## Attributes

* `7em`: Defines the 7em attribute.
* `width`: Defines the width attribute.




# k-search-input-characters

Input text component that supports only characters. Properties: Single value, List of values. Query properties: Equals, Start, End, Contains, And, Or, k-filters-1-imports

## Dependencies

* `Component, EventEmitter, Output, ViewChild` from `@angular/core`
* `KSearchInputDateComponent, KSearchInputNumberComponent, KSearchInputNumericComponent, KSearchInputTextComponent, KSearchSelectComponent, KSearchTableComponent, OptionConfigModel, PrimeNgEs` from `@ec.com.kgr/kng-components-v3/k-search`
* `CommonModule` from `@angular/common`
* `FormsModule` from `@angular/forms`
* `KFieldsetComponent` from `@ec.com.kgr/kng-components-v3/k-fieldset`
* `NumbersDirective, UpperCaseDirective, ToUpperCaseDirective` from `@ec.com.kgr/kng-components-v3/k-common/k-directives`
* `PopoverModule` from `ngx-bootstrap/popover`
* `KValidationsModule` from `@ec.com.kgr/kng-components-v3/k-common/k-validations`
* `PersonsFilterService` from `@persons/services/persons-filter.service`

## TypeScript

```typescript
<!--k-filters-imports-->
import { Component, EventEmitter, Output, ViewChild } from '@angular/core';
import {
  KSearchInputDateComponent, KSearchInputNumberComponent, KSearchInputNumericComponent,
  KSearchInputTextComponent, KSearchSelectComponent, KSearchTableComponent,OptionConfigModel, PrimeNgEs
} from '@ec.com.kgr/kng-components-v3/k-search';
import { CommonModule } from '@angular/common';
import { FormsModule } from '@angular/forms';
import { KFieldsetComponent } from '@ec.com.kgr/kng-components-v3/k-fieldset';
import { NumbersDirective, UpperCaseDirective, ToUpperCaseDirective } from '@ec.com.kgr/kng-components-v3/k-common/k-directives';
import { PopoverModule } from 'ngx-bootstrap/popover';
import { KValidationsModule } from '@ec.com.kgr/kng-components-v3/k-common/k-validations';
import { PersonsFilterService } from '@persons/services/persons-filter.service';
```

## HTML

```html


<!--k-search-input-characters-->
<k-search-input-text class="k-search-space-top" id="${1:id}" name="${2:name}"
    [label]="'${3:label}:'" [placeholder]="'${4:placeholder}'" [(ngModel)]="${5:filtersService.searchModel}"
    [optionSettings]="optionSettings" [showComparatorType]="${6:true}" [disabledCommaList]="${7:true}"
    [upperInputValue]="${8:true}" [maxlength]="${9:50}" [regularExpression]="'[a-zñA-ZÑ ]'"
    [required]="${10:false}">
</k-search-input-text>
```

## Usage

Component can be used with the following selectors:

* `k-search-input-characters`
* `<k-search-input-characters`
* `k-filters-1-imports`

## Input Properties

* `[disabledCommaList]`: Defines the disabledCommaList.
* `[label]`: Defines the label.
* `[maxlength]`: Defines the maxlength.
* `[optionSettings]`: Defines the optionSettings.
* `[placeholder]`: Defines the placeholder.
* `[regularExpression]`: Defines the regularExpression.
* `[required]`: Defines the required.
* `[showComparatorType]`: Defines the showComparatorType.
* `[upperInputValue]`: Defines the upperInputValue.

## Output Events

* `(ngModel)`: Event emitted when ngModel occurs.

## Attributes

* `name`: Defines the name attribute.




# k-table

Table component with pagination, k-table-1-imports

## Dependencies

* `Table, TableModule` from `primeng/table`
* `PopoverModule` from `ngx-bootstrap/popover`
* `KMessageService` from `@ec.com.kgr/kng-components-v3/k-common/k-message`
* `Component, ViewChild` from `@angular/core`
* `ResponseVO` from `@ec.com.kgr/kng-components-v3/k-common`
* `UserService` from `@ec.com.kgr/kng-components-v3/k-security`
* `FilterVO` from `@shared/vo/filter-vo`

## TypeScript

```typescript
import { Table, TableModule } from 'primeng/table';
import { PopoverModule } from 'ngx-bootstrap/popover';
import { KMessageService } from '@ec.com.kgr/kng-components-v3/k-common/k-message';
import { Component, ViewChild } from '@angular/core';
import { ResponseVO } from '@ec.com.kgr/kng-components-v3/k-common';
import { UserService } from '@ec.com.kgr/kng-components-v3/k-security';
import { FilterVO } from '@shared/vo/filter-vo';
```

## HTML

```html


<!--k-table-->
<div class="scroll-content-elements k-ptable-header k-paginator">
    <p-table #dataTable [value]="${1:values}" [paginator]="true" [rows]="15" paginatorPosition="top" [lazy]="true"
            [totalRecords]="totalRecords" (onLazyLoad)="paginationEvent(\$event)" responsiveLayout="scroll" styleClass="p-datatable-lg p-datatable-striped">
            <ng-template pTemplate="caption">
                <div class="k-ptable-header">
                    Listado de ${2:table name}
                </div>
            </ng-template>
            <ng-template pTemplate="paginatorleft" let-state>
                <a class="p-disabled">Pág. {{state.totalRecords > 0 ? state.page + 1:0}} de {{state?.pageCount || "0"}}</a>
            </ng-template>
            <ng-template pTemplate="paginatorright" let-state>
                <a class="p-disabled">Total Reg: {{state.totalRecords > 0 ? state.totalRecords : 0}}</a>
            </ng-template>
            <ng-template pTemplate="header">
                <tr>
                    <th class="k-width-index">Nro.</th>
                    <!-- ADD ADDITIONAL HEADERS -->


                </tr>
            </ng-template>
            <ng-template pTemplate="body" let-value let-rowIndex="rowIndex">
                <tr>
                    <td class="k-ellipsis-index" [popover]="rowIndex + 1">
                        {{ rowIndex + 1}}
                    </td>
                    <!-- ADD ADDITIONAL DATA CELLS -->


                </tr>
            </ng-template>
           <ng-template pTemplate="emptymessage">
             <tr>
               <td [attr.colspan]="${3|1,2,4,6,8,10|}" class="k-empty-table">
                   Seleccione un criterio de búsqueda.
               </td>
             </tr>
           </ng-template>
    </p-table>
</div>
```

## Usage

Component can be used with the following selectors:

* `k-table`
* `<k-table`
* `k-table-1-imports`

## Input Properties

* `[lazy]`: Defines the lazy.
* `[paginator]`: Defines the paginator.
* `[popover]`: Defines the popover.
* `[rows]`: Defines the rows.
* `[totalRecords]`: Defines the totalRecords.
* `[value]`: Defines the value.

## Output Events

* `(onLazyLoad)`: Event emitted when onLazyLoad occurs.

## Attributes

* `0`: Defines the 0 attribute.
* `1`: Defines the 1 attribute.
* `ADD`: Defines the ADD attribute.
* `ADDITIONAL`: Defines the ADDITIONAL attribute.
* `CELLS`: Defines the CELLS attribute.
* `DATA`: Defines the DATA attribute.
* `HEADERS`: Defines the HEADERS attribute.
* `Listado`: Defines the Listado attribute.
* `Reg`: Defines the Reg attribute.
* `Seleccione`: Defines the Seleccione attribute.
* `búsqueda`: Defines the búsqueda attribute.
* `criterio`: Defines the criterio attribute.
* `de`: Defines the de attribute.
* `let`: Defines the let attribute.
* `name`: Defines the name attribute.
* `pTemplate`: Defines the pTemplate attribute.
* `paginatorPosition`: Defines the paginatorPosition attribute.
* `responsiveLayout`: Defines the responsiveLayout attribute.
* `rowIndex`: Defines the rowIndex attribute.
* `state`: Defines the state attribute.
* `styleClass`: Defines the styleClass attribute.
* `un`: Defines the un attribute.



# k-tree

Tree component

## TypeScript

No TypeScript implementation available.

## HTML

```html


<k-tree [treeValue]="${1:treeValue}" [treeSelection]="single" (nodeSelected)="isNodeSelect($event)"
    (nodeUnselected)="isNodeUnSelect()" [filterValue]="${3:filterValue}" [filterMode]="'strict'">
</k-tree>
```

## Usage

Component can be used with the following selectors:

* `k-tree`
* `<k-tree`

## Input Properties

* `[filterMode]`: Defines the filterMode.
* `[filterValue]`: Defines the filterValue.
* `[treeSelection]`: Defines the treeSelection.
* `[treeValue]`: Defines the treeValue.

## Output Events

* `(nodeSelected)`: Event emitted when nodeSelected occurs.
* `(nodeUnselected)`: Event emitted when nodeUnselected occurs.



# k-user-info-1-imports

k-user-info-1-imports

## Dependencies

* `UserProfileVO, UserService` from `@ec.com.kgr/kng-components-v3/k-security`

## TypeScript

```typescript
import { UserProfileVO, UserService } from '@ec.com.kgr/kng-components-v3/k-security';
```

## HTML

No HTML implementation available.

## Usage

Component can be used with the following selectors:

* `k-user-info-1-imports`




# k-validator-required-not-empty

Non-empty required field.

## TypeScript

No TypeScript implementation available.

## HTML

```html
[requiredNotEmpty]
```

## Usage

Component can be used with the following selectors:

* `k-validator-required-not-empty`

## Input Properties

* `[requiredNotEmpty]`: Defines the requiredNotEmpty.



# k-pdf-viewer

PDF viewer by: url, google url, base64 and with download button

## TypeScript

No TypeScript implementation available.

## HTML

```html
<k-pdf-viewer [base64DataFile]="${1:base64DataFile}" [find]="${2:true}" [download]="${3:true}" [viewBookmark]="${4:false}"
[downloadFileName]="'${5:file name}'" [fullScreen]="${6:false}" [externalWindow]="${7:false}" [print]="${8:false}"
[width]="'${9:1100px}'" [height]="'${10:570px}'">
</k-pdf-viewer>
```

## Usage

Component can be used with the following selectors:

* `<k-pdf-viewer`
* `k-pdf-viewer`

## Input Properties

* `[base64DataFile]`: Defines the base64DataFile.
* `[download]`: Defines the download.
* `[downloadFileName]`: Defines the downloadFileName.
* `[externalWindow]`: Defines the externalWindow.
* `[find]`: Defines the find.
* `[fullScreen]`: Defines the fullScreen.
* `[height]`: Defines the height.
* `[print]`: Defines the print.
* `[viewBookmark]`: Defines the viewBookmark.
* `[width]`: Defines the width.

## Attributes

* `name`: Defines the name attribute.



# k-route-path-component

k-route-path-component

## TypeScript

No TypeScript implementation available.

## HTML

```html
{
path: '',
component: ${1:DashboardContentComponent}
}
```

## Usage

Component can be used with the following selectors:

* `k-route-path-component`

## Attributes

* `component`: Defines the component attribute.
* `path`: Defines the path attribute.


