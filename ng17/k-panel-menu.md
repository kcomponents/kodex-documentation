![Kruger Corp](https://img.shields.io/badge/Kruger_Corp_®-Copyright_2022-blue)

# k-panel-menu

Component that contains the modules available by profile and user

## TypeScript

No TypeScript implementation available.

## HTML

```html
<!--k-panel-menu-->
<k-layout [appName]="'${1:app name}'" [showHome]="false" [pageTitle]="'${2:page title}'" (logout)="logout()">
   <k-panel-menu></k-panel-menu>
</k-layout>
```

## Usage

Component can be used with the following selectors:

* `k-panel-menu`
* `<k-panel-menu`

## Input Properties

* `[appName]`: Defines the appName.
* `[pageTitle]`: Defines the pageTitle.
* `[showHome]`: Defines the showHome.

## Output Events

* `(logout)`: Event emitted when logout occurs.

## Attributes

* `name`: Defines the name attribute.

