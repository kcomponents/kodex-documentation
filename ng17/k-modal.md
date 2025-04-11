![Kruger Corp](https://img.shields.io/badge/Kruger_Corp_®-Copyright_2022-blue)

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

