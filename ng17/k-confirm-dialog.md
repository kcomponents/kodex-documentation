![Kruger Corp](https://img.shields.io/badge/Kruger_Corp_®-Copyright_2022-blue)

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

