![Kruger Corp](https://img.shields.io/badge/Kruger_Corp_®-Copyright_2022-blue)

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

