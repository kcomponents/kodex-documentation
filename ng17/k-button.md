![Kruger Corp](https://img.shields.io/badge/Kruger_Corp_®-Copyright_2022-blue)


# kng-components-v3

## k-button

El Componente k-button proporciona una colección de botones estilizados y elementos de acción para aplicaciones web con `angular 17`. Los botones incluyen iconos, estilos y comportamientos predefinidos para operaciones comunes como guardar, cancelar, exportar a Excel, y más.

### Botones de Cabecera (Header)

Los botones de cabecera se utilizan en la sección de encabezado de los componentes, generalmente dentro de un template de header.

#### Botón Nuevo

```html
<!--k-button-header-new-->
<ul class="nav-ul">
    <li class="nav-item">
        <a class="nav-link text-a" (click)="openSaveModal()" [popover]="'Agregar nuevo parámetro'">
            <em class="fa fa-file-o text-info"></em> Nuevo
        </a>
    </li>
</ul>
```

#### Botón Excel

```html
<!--k-button-header-excel-->
<ul class="nav-ul">
    <li class="nav-item">
        <a class="nav-link text-a" (click)="exportToExcel()" [popover]="'Exportar a Excel'">
            <em class="fa fa-file-excel-o text-success"></em> Excel
        </a>
    </li>
</ul>
```

#### Botón PDF

```html
<!--k-button-header-pdf-->
<ul class="nav-ul">
    <li class="nav-item">
        <a class="nav-link text-a" (click)="exportToPdf()" [popover]="'Exportar a PDF'">
            <em class="fa fa-file-pdf-o text-primary-dark"></em> PDF
        </a>
    </li>
</ul>
```

#### Botón Atrás

```html
<!--k-button-header-back-->
<ul class="nav-ul">
    <li class="nav-item">
        <a class="nav-link text-a" routerLink="/">
            <em class="fa fa-arrow-left text-info"></em> Atrás
        </a>
    </li>
</ul>
```

### Botones de Acción

Los botones de acción se utilizan dentro de formularios y modales para realizar operaciones específicas.

#### Botón Guardar

```html
<!--k-button-save-->
<button class="btn btn-success btn-sm" (click)="save()">
   <em class="fa fa-save"></em> Guardar
</button>
```

#### Botón Cancelar/Cerrar

```html
<!--k-button-close-->
<button class="btn btn-danger btn-sm" type="reset" (click)="close()">
    <em class="fa fa-close"></em> Cancelar
</button>
```

#### Botón Genérico

```html
<!--k-button-->
<button class="btn btn-info btn-sm k-button" (click)="someFunction()">
    <em class="fa fa-info-circle"></em> Información
</button>
```

### Botones de Tabla

Estos botones se utilizan dentro de las celdas de una tabla para realizar acciones sobre registros específicos.

#### Botón Editar

```html
<!--k-table-button-edit-->
<span (click)="openEditModal(object)" [popover]="'Editar'">
    <em style="cursor: pointer; transform: scale(1.5);" class="fa fa-edit text-info"></em>
</span>
```

#### Botón Eliminar

```html
<!--k-table-button-delete-->
<span (click)="confirmDelete(object)" [popover]="'Eliminar'">
    <em style="cursor: pointer; transform: scale(1.5);"
        class="fa fa-trash text-danger"></em>
</span>
```

#### Conjunto de Botones de Acción para Tablas

```html
<!--k-td-buttons-actions-->
<td class="col-center">
  <div class="d-flex justify-content-around">
    <span (click)="openEditModal(value)" [popover]="'Editar'">
        <em style="cursor: pointer; transform: scale(1.5);" class="fa fa-edit text-info"></em>
    </span>
    <span (click)="confirmDelete(value)" [popover]="'Eliminar'">
        <em style="cursor: pointer; transform: scale(1.5);"
            class="fa fa-trash text-danger"></em>
    </span>
  </div>
</td>
```

### Estilos de Botones

Los siguientes son clases CSS que pueden ser aplicadas a los botones para darles estilos específicos.

#### Estilos de Botón

* **btn-success**: Estilo verde para acciones positivas o de confirmación.
* **btn-info**: Estilo azul para acciones informativas.
* **btn-danger**: Estilo rojo para acciones destructivas o de cancelación.
* **k-button**: Clase base para botones del sistema Kruger.

#### Iconos Font Awesome

* **fa-home**: Icono de inicio.
* **fa-search**: Icono de búsqueda.
* **fa-refresh**: Icono de actualización.
* **fa-info-circle**: Icono de información.
* **fa-history**: Icono de historial.
* **fa-file-excel**: Icono de archivo Excel.
* **fa-file-pdf**: Icono de archivo PDF.
* **fa-save**: Icono de guardar.
* **fa-close / fa-times**: Icono de cerrar o cancelar.
* **fa-edit**: Icono de editar.
* **fa-trash**: Icono de eliminar.
* **fa-arrow-left**: Icono de flecha hacia la izquierda para volver atrás.
* **fa-file-o**: Icono de nuevo archivo.
* **fa-eraser**: Icono de borrar o limpiar.

### Clases de Color para Iconos

* **text-primary**: Color primario del tema (generalmente azul).
* **text-primary-dark**: Variante oscura del color primario.
* **text-info**: Color informativo (generalmente azul claro).
* **text-success**: Color de éxito (generalmente verde).
* **text-danger**: Color de peligro o error (generalmente rojo).

### Ejemplos de Uso

#### Botones en Header Template

```html
<ng-template #headerTemplate>
  <div class="k-header-template">
    <!--k-button-header-new-->
    <ul class="nav-ul">
        <li class="nav-item">
            <a class="nav-link text-a" (click)="openSaveModal()" [popover]="'Agregar nuevo parámetro'">
                <em class="fa fa-file-o text-info"></em> Nuevo
            </a>
        </li>
    </ul>
    
    <!--k-button-header-excel-->
    <ul class="nav-ul">
        <li class="nav-item">
            <a class="nav-link text-a" (click)="exportToExcel()" [popover]="'Exportar a Excel'">
                <em class="fa fa-file-excel-o text-success"></em> Excel
            </a>
        </li>
    </ul>
  </div>
</ng-template>
```

#### Botones en Modal Footer

```html
<div class="modal-footer k-modal-footer">
    <!--k-button-save-->
    <button class="btn btn-success btn-sm" (click)="save()">
       <em class="fa fa-save"></em> Guardar
    </button>
    
    <!--k-button-close-->
    <button class="btn btn-danger btn-sm" type="reset" (click)="close()">
        <em class="fa fa-close"></em> Cancelar
    </button>
</div>
``` 