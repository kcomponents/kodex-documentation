![Kruger Corp](https://img.shields.io/badge/Kruger_Corp_®-Copyright_2022-blue)


# kng-components-v3

## k-table

El Componente k-table implementa una tabla de datos paginada y con funcionalidades avanzadas para aplicaciones web con `angular 17`. El componente depende de librerías de terceros tales como `primeng/table` y `ngx-bootstrap/popover` para proporcionar una experiencia de usuario óptima.

```typescript
import { Table, TableModule } from 'primeng/table';
import { PopoverModule } from 'ngx-bootstrap/popover';
import { KLayoutComponent } from '@ec.com.kgr/kng-components-v3/k-layout';
import { CommonModule } from '@angular/common';
 
@Component({
  selector: 'app-parameters-content',
  standalone: true,
  templateUrl: './app-parameters-content.html',
  styleUrls: ['./app-parameters-content.scss'],
  imports: [
    TableModule,
    PopoverModule,
    KLayoutComponent,
    CommonModule
  ]
})
export class ParametersContentComponent implements OnInit {
  @ViewChild('dataTable', { static: false }) private dataTable: Table;
  // ... more code
}
```

```html
<div class="scroll-content-elements k-ptable-header k-paginator">
    <p-table #dataTable [value]="values" [paginator]="true" [rows]="15" paginatorPosition="top" [lazy]="true"
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
        this.values = data.content;
    } else {
        this.values = [];
    }
    this.totalRecords = data.total;
    if (0 === data.total) {
        this.messageService.info('No se encontraron resultados con los filtros ingresados.');
    }
  });
}
``` 