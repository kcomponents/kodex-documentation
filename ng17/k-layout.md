![Kruger Corp](https://img.shields.io/badge/Kruger_Corp_®-Copyright_2022-blue)

# k-layout

Component containing the layout with the application name, title, headerTemplate, helpTemplate, sidebarTemplate, mycontent

## TypeScript

No TypeScript implementation available.

## HTML

```html
<k-layout [appName]="'${1:app name}'" [pageTitle]="'${2:page title}'" [sidebarTemplate]="sidebarTemplate"
[headerTemplate]="headerTemplate" (logout)="logout()" [toolTipHomeText]="'Inicio'" [helpTemplate]="helpTemplate"
[titleHelpText]="'${3:Ayuda}'">
   <ng-container *ngTemplateOutlet="contentTemplate">
   </ng-container>
</k-layout>


<ng-template #headerTemplate>
  <ul class="nav-ul">
      <li  class="nav-item">
          <a class="nav-link text-a" (click)="${4:openNewModal()}" [popover]="'${5:Nuevo}'">
              <em class="fa fa-file-o text-info"></em> ${6:Nuevo}
          </a>
      </li>
  </ul>
  <!--ADD K-BUTTON-HEADER -->


</ng-template>


<ng-template #sidebarTemplate>
    <${7:component-filters} (onSearchEvent)="onSearchEvent()">
    </${7:component-filters}>
</ng-template>


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
            <!--ADD HELP ICONS-->


          </div>
        </k-fieldset>
      </div>
    </div>
</ng-template>


<ng-template #contentTemplate>
    <!-- ADD K-P-TABLE -->


</ng-template>
```

## Usage

Component can be used with the following selectors:

* `k-layout`
* `<k-layout`

## Input Properties

* `[appName]`: Defines the appName.
* `[headerTemplate]`: Defines the headerTemplate.
* `[helpTemplate]`: Defines the helpTemplate.
* `[pageTitle]`: Defines the pageTitle.
* `[popover]`: Defines the popover.
* `[sidebarTemplate]`: Defines the sidebarTemplate.
* `[titleHelpText]`: Defines the titleHelpText.
* `[toolTipHomeText]`: Defines the toolTipHomeText.

## Output Events

* `(click)`: Event emitted when click occurs.
* `(logout)`: Event emitted when logout occurs.
* `(onSearchEvent)`: Event emitted when onSearchEvent occurs.

## Attributes

* `ADD`: Defines the ADD attribute.
* `HELP`: Defines the HELP attribute.
* `ICONS`: Defines the ICONS attribute.
* `K`: Defines the K attribute.
* `kFieldsetLegend`: Defines the kFieldsetLegend attribute.
* `name`: Defines the name attribute.

