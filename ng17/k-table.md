![Kruger Corp](https://img.shields.io/badge/Kruger_Corp_®-Copyright_2022-blue)


# kng-components-v3

## p-table

El Componente p-table implementa una tabla de datos paginada y con funcionalidades avanzadas para aplicaciones web con `angular 17`. El componente depende de librerías de terceros tales como `primeng/table` y `ngx-bootstrap/popover` para proporcionar una experiencia de usuario óptima.

parameters-content.component.ts
```typescript
import { Component, ViewChild } from '@angular/core';
import { CommonModule } from '@angular/common';
import { ResponseVO } from '@ec.com.kgr/kng-components-v3/k-common';
import { KLayoutComponent } from '@ec.com.kgr/kng-components-v3/k-layout';
import { KMessageService } from '@ec.com.kgr/kng-components-v3/k-common/k-message';
import { KFieldsetComponent } from '@ec.com.kgr/kng-components-v3/k-fieldset';
import { ConfirmationService } from 'primeng/api';
import { DialogService, DynamicDialogRef } from 'primeng/dynamicdialog';
import { ConfirmDialogModule } from 'primeng/confirmdialog';
import { Table, TableModule } from 'primeng/table';
import { PopoverModule } from 'ngx-bootstrap/popover';
import { ParametersService } from '@parameters/services/parameters.service';
import { FilterVO } from '@shared/vo/filter-vo';
import { ParameterVo } from '@parameters/vo/parameter-vo';
import { constants } from '@const/constants';
import { ParametersModalComponent } from '@parameters/modals/parameters-modal/parameters-modal.component';
import { ParametersFiltersComponent } from '@parameters/components/parameters-filters/parameters-filters.component';
import { ParametersFilterService } from '@parameters/services/parameters-filter.service';
import { UserService } from '@ec.com.kgr/kng-components-v3/k-security';

/**
 * Parameters content module
 *
 * @author components on 2024/06/18.
 * @version 1.0
 * @since 1.0.0
 */

@Component({
  selector: 'app-parameters-content',
  standalone: true,
  imports: [
    KLayoutComponent,
    KFieldsetComponent,
    CommonModule,
    TableModule,
    PopoverModule,
    ConfirmDialogModule,
    ParametersFiltersComponent
  ],
  templateUrl: './parameters-content.component.html',
  styleUrls: ['./parameters-content.component.scss'],
  providers: [DialogService, ConfirmationService, ParametersFilterService]

})
export class ParametersContentComponent {

  @ViewChild('dataTable', { static: false }) private dataTable: Table;
  parameters: ParameterVo[] = [];
  ref: DynamicDialogRef;
  rows = 15;
  totalRecords: number;
  request: FilterVO;

  /**
  * Constructor.
  * @param dialogService service for pop up modal.
  * @param confirmationService service for pop up confirmation.
  * @param messageService service for message into the window.
  * @param filterService filters from search inputs.
  * @param parametersService service to connect to API REST.
  */

  constructor(
    public dialogService: DialogService,
    private confirmationService: ConfirmationService,
    private messageService: KMessageService,
    private userService: UserService,
    private filterService: ParametersFilterService,
    private parametersService: ParametersService
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
    this.parametersService.findByFilter(this.request).subscribe((response: ResponseVO) => {
      const data = response.data;
      if (data.content) {
        this.parameters = data.content;
      } else {
        this.parameters = [];
      }
      this.totalRecords = data.total;
      if (0 === data.total) {
        this.messageService.info('No se encontraron resultados con los filtros ingresados.');
      }
    });
  }

  /**
   * Close modal process
   */
  closeModal() {
    this.ref.onClose.subscribe((data: ParameterVo) => {
      if (data) {
        this.onSearchEvent();
      }
    });
  }

  /**
   *  open the modal to  save person.
   */
  openSaveModal() {
    this.ref = this.dialogService.open(ParametersModalComponent, {
      header: 'Agregar parámetro',
    });
    this.closeModal();
  }

  /**
  * open the modal to  update person.
  * @param row is the person selected
  */
  openUpdateModal(row: ParameterVo) {
    this.ref = this.dialogService.open(ParametersModalComponent, {
      header: 'Editar parámetro',
      data: row
    });
    this.closeModal();
  }

  /**
   * @param row * open the confirm dualog to delete parameter.
   */
  confirmDelete(row: ParameterVo) {
    this.confirmationService.confirm({
      message: row.parameterCode + constants.MESSAGES.PARAMETERS.CONFIRM_DELETE,
      header: 'Eliminar parámetro',
      accept: () => {
        this.parametersService.deleteData(row.parameterCode).subscribe(() => {
          this.onSearchEvent();
          this.messageService.success('Parámetro ' + row.parameterCode + ' ' + constants.MESSAGES.PARAMETERS.DELETE);
        });
      }
    });
  }

  /**
   * Logout function.
   */
  logout() {
    this.userService.logout();
  }

}

```

parameters-content.component.html
```html
<div class="scroll-content-elements k-ptable-header k-paginator">
    <p-table #dataTable [value]="parameters" [paginator]="true" [rows]="15" paginatorPosition="top" [lazy]="true"
            [totalRecords]="totalRecords" (onLazyLoad)="paginationEvent($event)" responsiveLayout="scroll" styleClass="p-datatable-lg p-datatable-striped">
            <ng-template pTemplate="caption">
                <div class="k-ptable-header">
                    Listado de datos
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
                    <th>Nombre</th>
                    <th>Descripción</th>
                    <th>Acciones</th>
                </tr>
            </ng-template>
            <ng-template pTemplate="body" let-value let-rowIndex="rowIndex">
                <tr>
                    <td class="k-ellipsis-index" [popover]="rowIndex + 1">
                        {{ rowIndex + 1}}
                    </td>
                    <td>{{value.name}}</td>
                    <td>{{value.description}}</td>
                    <td class="col-center">
                      <div class="d-flex justify-content-around">
                        <span (click)="openEditModal(value)" [popover]="'Editar'">
                            <em style="cursor: pointer; transform: scale(1.5);" class="fa fa-edit text-info"></em>
                        </span>
                        <span (click)="confirmDelete(value)" [popover]="'Eliminar'">
                            <em style="cursor: pointer; transform: scale(1.5);" class="fa fa-trash text-danger"></em>
                        </span>
                      </div>
                    </td>
                </tr>
            </ng-template>
           <ng-template pTemplate="emptymessage">
             <tr>
               <td [attr.colspan]="4" class="k-empty-table">
                   Seleccione un criterio de búsqueda.
               </td>
             </tr>
           </ng-template>
    </p-table>
</div>
```

### Propiedades

* **value**: Establece el arreglo de datos que se mostrará en la tabla.
* **paginator**: Especifica true o false para definir si se mostrará la paginación.
* **rows**: Establece el número de filas por página.
* **paginatorPosition**: Define la posición del paginador (top, bottom, both).
* **lazy**: Cuando es true, permite la carga perezosa/bajo demanda de datos.
* **totalRecords**: Establece el número total de registros para la paginación.
* **onLazyLoad**: Evento que se dispara cuando se debe cargar datos para una página.
* **responsiveLayout**: Define el comportamiento de la tabla en dispositivos pequeños.
* **styleClass**: Establece las clases CSS adicionales para la tabla.

### Templates

* **pTemplate="caption"**: Define el encabezado superior de la tabla.
* **pTemplate="paginatorleft"**: Personaliza la parte izquierda del paginador.
* **pTemplate="paginatorright"**: Personaliza la parte derecha del paginador.
* **pTemplate="header"**: Define las columnas y encabezados de la tabla.
* **pTemplate="body"**: Define cómo se renderizan las filas y celdas de datos.
* **pTemplate="emptymessage"**: Define el mensaje cuando no hay datos para mostrar.

### Funciones Principales

```typescript
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
  this.service.findByFilter(this.request).subscribe((response: ResponseVO) => {
    const data = response.data;
    if (data.content) {
        this.parameters = data.content;
    } else {
        this.parameters = [];
    }
    this.totalRecords = data.total;
    if (0 === data.total) {
        this.messageService.info('No se encontraron resultados con los filtros ingresados.');
    }
  });
}
``` 
