![Kruger Corp](https://img.shields.io/badge/Kruger_Corp_®-Copyright_2022-blue)

# kng-components-v3

## Documentación de Componentes Angular 17

Esta documentación describe los componentes y utilidades disponibles en la librería kng-components-v3 para Angular 17. La librería ofrece una colección de componentes predefinidos para construir aplicaciones web con un diseño y funcionalidad estandarizados.

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

![Kruger Corp](https://img.shields.io/badge/Kruger_Corp_®-Copyright_2022-blue)


# kng-components-v3

## k-layout

El Componente k-layout organiza los elementos de la página en el diseño estándar de las aplicaciones web con `angular 17`. El modulo KLayoutModule depende de librerías de terceros tales como `bootstrap4`, `primeng` con el tema de Bootstrap y `toastr`, los cuales deben ser incluidos.



```typescript
import { KLayoutComponent } from '@ec.com.kgr/kng-components-v3/k-layout';
 
 @Component({
   selector: 'app-parameters-content',
   standalone: true,
   templateUrl: './app-parameters-content.html',
   styleUrls: ['./app-parameters-content.scss'],
   imports: [
     KLayoutComponent
   ]
 })
export class ParametersContentComponent implements OnInit {...}
```

```html
<!-- Example with functionality-->
<k-layout 
[appName]="'Proyecto Base'" 
[pageTitle]="'Administración de parámetros.'" 
[sidebarTemplate]="sidebarTemplate"
[headerTemplate]="headerTemplate" 
(logout)="logout()" 
[toolTipHomeText]="'Inicio'" 
[helpTemplate]="helpTemplate"
[titleHelpText]="'Ayuda del módulo parámetros'" 
[disableLoading]="false">
  <ng-container *ngTemplateOutlet="contentTemplate">
  </ng-container>
</k-layout>
```

* headerTemplate: Establece el nombre de la aplicación.
* pageTitle: Establece el título de la página.
* defaultCollapsed: Especifica true o false para definir si se mostrara colapsado por defecto de la barra lateral o no.
* cancelReload: Especifica true o false para definir si se activa la recarga de la página al presionar la tecla F5.
* disableLoading: Especifica true o false para definir si se desea activar la animación de cargando a la hora de realizar una petición ya sea: Consulta, inserción o actualización.
* showHeader: Especifica true o false para definir si se mostrará la cabecera del componente.
* showExit: Se especifica true o false para mostrar el botón de salida.
* showHome: Se especifica true o false para mostrar el botón de inicio.
* showHelp: Se especifica true o false para mostrar el botón de ayuda.
* showChat: Se especifica true o false para mostrar el botón de chat (k-chat).
* showWindowsManager: Especifica true o false para definir si se muestra la lista de sistemas abiertos (k-windows-manager).
* sidebarColumnNumbers: Establece el número de columnas que tomará la barra lateral (De 2 hasta 12).
* redirectUrl: Establece la url la cuál va ser redirigida desde la cabecera.
* imageHeader: Establece la url del ícono a mostrarse en la parte izquierda del header.
* disableLinkHome: Tanto el ícono como el nombre se deshabilitan o habilitan.  



 # k-modal

El Componente k-modal permite la creación de ventanas modales en aplicaciones web con `angular 17`. Este componente es útil para mostrar contenido adicional o formularios sin salir de la página actual.

## Propiedades del Componente

* **modalTitle**: Establece el título de la ventana modal.
* **disableClose**: Especifica true o false para definir si se permite cerrar la ventana modal al hacer clic fuera de ella.
* **showFooter**: Especifica true o false para mostrar u ocultar el pie de la ventana modal.
* **modalSize**: Establece el tamaño de la ventana modal (ej. 'sm', 'lg', 'xl').
* **closeButtonText**: Establece el texto del botón de cerrar.
* **saveButtonText**: Establece el texto del botón de guardar.

## Ejemplo Básico
 
 ```html


<!--EXAMPLE WITH METHODS-->
<!--k-modal-content-->
   <form class="form" #resultForm="ngForm" (submitValidForm)="clickForm()" autocomplete="off">
       <div class="container">
            <!-- ADD COMPONENTS -->
   
   
           <br>
       </div>
       <div class="modal-footer k-modal-footer">
           <button class="btn btn-success btn-sm">
               <em class="fa fa-save"></em> Guardar
           </button>
           <button class="btn btn-danger btn-sm" type="reset" (click)="this.ref.close()">
               <em class="fa fa-close"></em> Cancelar
           </button>
       </div>
   </form>

```


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
