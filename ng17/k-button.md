![Kruger Corp](https://img.shields.io/badge/Kruger_Corp_®-Copyright_2022-blue)

# k-button-header-new

New button for header template section

## TypeScript

No TypeScript implementation available.

## HTML

```html


<!--k-button-header-new-->
  <ul class="nav-ul">
      <li  class="nav-item">
          <a class="nav-link text-a" (click)="${1:function name}" [popover]="'${2:action name popover}'">
              <em class="fa fa-file-o text-info"></em> ${3:action name}
          </a>
      </li>
  </ul>
```

## Usage

Component can be used with the following selectors:

* `<k-button-header-new`
* `k-button-header-new`

## Input Properties

* `[popover]`: Defines the popover.

## Output Events

* `(click)`: Event emitted when click occurs.

## Attributes

* `name`: Defines the name attribute.

