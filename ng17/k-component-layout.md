![Kruger Corp](https://img.shields.io/badge/Kruger_Corp_®-Copyright_2022-blue)

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

