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
 <!--BASIC EXAMPLE-->

 <!--k-modal-content-->
    <form class="form" #resultForm="ngForm" autocomplete="off">
        <div class="container">
             <!-- ADD COMPONENTS -->
    
    
            <br>
        </div>
        <div class="modal-footer k-modal-footer">
            <button class="btn btn-success btn-sm">
                <em class="fa fa-save"></em> Guardar
            </button>
            <button class="btn btn-danger btn-sm" type="reset">
                <em class="fa fa-close"></em> Cancelar
            </button>
        </div>
    </form>
´´´


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


