![Kruger Corp](https://img.shields.io/badge/Kruger_Corp_®-Copyright_2022-blue)


# kng-components-v3

## k-modal

El Componente k-modal implementa un diálogo modal para mostrar contenido, formularios y acciones interactivas en aplicaciones web con `angular 17`. El componente se integra con `primeng/dynamicdialog` y proporciona estructura para formularios con botones de acción.

```typescript
import { Component, OnInit } from '@angular/core';
import { DynamicDialogRef, DynamicDialogConfig } from 'primeng/dynamicdialog';
import { KMessageService } from '@ec.com.kgr/kng-components-v3/k-common/k-message';
import { CommonModule } from '@angular/common';
import { FormsModule } from '@angular/forms';
import { KDirectivesModule } from '@ec.com.kgr/kng-components-v3/k-common/k-directives';

@Component({
  selector: 'app-parameter-modal',
  standalone: true,
  templateUrl: './parameter-modal.component.html',
  styleUrls: ['./parameter-modal.component.scss'],
  imports: [
    CommonModule,
    FormsModule,
    KDirectivesModule
  ]
})
export class ParameterModalComponent implements OnInit {
  parameter: any;

  constructor(
    public ref: DynamicDialogRef,
    public config: DynamicDialogConfig,
    private messageService: KMessageService
  ) { }

  ngOnInit() {
    if (this.config.data) {
      this.parameter = this.config.data;
    } else {
      this.parameter = {};
    }
  }

  save() {
    // Lógica para guardar
    this.ref.close(this.parameter);
  }
}
```

```html
<!--k-modal-content-->
<form class="form" #resultForm="ngForm" (submitValidForm)="save()" autocomplete="off">
    <div class="container">
         <div class="form-group">
           <label>Nombre:</label>
           <input type="text" class="form-control" [(ngModel)]="parameter.name" name="name" required>
         </div>
         <div class="form-group">
           <label>Descripción:</label>
           <input type="text" class="form-control" [(ngModel)]="parameter.description" name="description" required>
         </div>
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

### Uso en Componente Principal

```typescript
import { DialogService, DynamicDialogRef } from 'primeng/dynamicdialog';

export class MainComponent {
  ref: DynamicDialogRef;

  constructor(public dialogService: DialogService) {}

  openSaveModal() {
    this.ref = this.dialogService.open(ParameterModalComponent, {
      header: 'Agregar parámetro'
    });
    this.closeModal();
  }

  openEditModal(row: any) {
    this.ref = this.dialogService.open(ParameterModalComponent, {
      header: 'Editar parámetro',
      data: row
    });
    this.closeModal();
  }

  closeModal() {
    this.ref.onClose.subscribe((data: any) => {
      if (data) {
        // Lógica después de cerrar el modal
        this.onSearchEvent();
      }
    });
  }
}
```

### Propiedades del DynamicDialogConfig

* **header**: Establece el título del diálogo modal.
* **data**: Permite pasar datos al componente del modal.
* **width**: Define el ancho del modal (por defecto "90%").
* **height**: Define la altura del modal.
* **closeOnEscape**: Especifica si el modal se cierra al presionar la tecla Escape.
* **dismissableMask**: Especifica si se puede cerrar el modal al hacer clic fuera de él.
* **baseZIndex**: Establece el z-index base para el modal.
* **autoZIndex**: Controla si el z-index se calcula automáticamente.
* **style**: Permite aplicar estilos CSS adicionales al modal.
* **contentStyle**: Permite aplicar estilos CSS al contenido del modal.
* **modal**: Especifica si se muestra una máscara al fondo del modal.
* **showHeader**: Controla si se muestra o no el encabezado del modal.
* **maximizable**: Determina si el modal puede maximizarse.

### Métodos de DynamicDialogRef

* **close(result)**: Cierra el modal y devuelve un resultado opcional.
* **onClose**: Observable que se emite cuando el modal se cierra.

### Estilos y Clases

* **k-modal-footer**: Clase CSS para dar estilo al pie del modal donde se ubican los botones.
* **form**: Clase para el formulario dentro del modal.
* **form-group**: Clase para agrupar elementos del formulario.
* **container**: Contenedor para el contenido principal del modal. 