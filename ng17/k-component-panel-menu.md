![Kruger Corp](https://img.shields.io/badge/Kruger_Corp_®-Copyright_2022-blue)

# k-component-panel-menu

Complete component containing all modules available per user profile, A complete component that contains the logic for all modules available to each user profile

## Class Name

`HomeContentComponent`

## Dependencies

* `Component` from `@angular/core`
* `KLayoutComponent` from `@ec.com.kgr/kng-components-v3/k-layout`
* `KPanelMenuComponent` from `@ec.com.kgr/kng-components-v3/k-panel-menu`
* `UserService` from `@ec.com.kgr/kng-components-v3/k-security`

## Selector

`app-home-content`

This is a standalone component.

### Required Imports

* `KLayoutComponent`
* `KPanelMenuComponent`

## Import

```typescript
import { HomeContentComponent } from '@ec.com.kgr/kng-components-v3/home-content';
```

## TypeScript

```typescript
import { Component } from '@angular/core';
import { KLayoutComponent } from '@ec.com.kgr/kng-components-v3/k-layout';
import { KPanelMenuComponent } from '@ec.com.kgr/kng-components-v3/k-panel-menu';
import { UserService } from '@ec.com.kgr/kng-components-v3/k-security';

/**
 * Home content
 *
 * @author components on 2024/06/18.
 * @version 1.0
 * @since 1.0.0
 */

@Component({
  selector: 'app-home-content',
  standalone: true,
  providers: [],
  templateUrl: './home-content.component.html',
  styleUrl: './home-content.component.scss',
  imports: [KLayoutComponent, KPanelMenuComponent]
})
export class HomeContentComponent {

  /**
   * constructor
   */
  constructor(private userService: UserService) {}

  /**
   * Logout
   */
  logout(): void {
    this.userService.logout();
  }
}
```

## HTML

```html
<!--k-panel-menu-->
<k-layout [appName]="'${1:app name}'" [showHome]="false" [pageTitle]="'${2:page title}'" (logout)="logout()">
   <k-panel-menu></k-panel-menu>
</k-layout>
```

## Usage

Component can be used with the following selectors:

* `k-component-panel-menu`
* `<k-component-panel-menu`

## Input Properties

* `[appName]`: Defines the appName.
* `[pageTitle]`: Defines the pageTitle.
* `[showHome]`: Defines the showHome.

## Output Events

* `(logout)`: Event emitted when logout occurs.

## Attributes

* `name`: Defines the name attribute.

