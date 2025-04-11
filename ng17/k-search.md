![Kruger Corp](https://img.shields.io/badge/Kruger_Corp_®-Copyright_2022-blue)

# k-search-input-characters

Input text component that supports only characters. Properties: Single value, List of values. Query properties: Equals, Start, End, Contains, And, Or, k-filters-1-imports

## Dependencies

* `Component, EventEmitter, Output, ViewChild` from `@angular/core`
* `KSearchInputDateComponent, KSearchInputNumberComponent, KSearchInputNumericComponent, KSearchInputTextComponent, KSearchSelectComponent, KSearchTableComponent, OptionConfigModel, PrimeNgEs` from `@ec.com.kgr/kng-components-v3/k-search`
* `CommonModule` from `@angular/common`
* `FormsModule` from `@angular/forms`
* `KFieldsetComponent` from `@ec.com.kgr/kng-components-v3/k-fieldset`
* `NumbersDirective, UpperCaseDirective, ToUpperCaseDirective` from `@ec.com.kgr/kng-components-v3/k-common/k-directives`
* `PopoverModule` from `ngx-bootstrap/popover`
* `KValidationsModule` from `@ec.com.kgr/kng-components-v3/k-common/k-validations`
* `PersonsFilterService` from `@persons/services/persons-filter.service`

## TypeScript

```typescript
<!--k-filters-imports-->
import { Component, EventEmitter, Output, ViewChild } from '@angular/core';
import {
  KSearchInputDateComponent, KSearchInputNumberComponent, KSearchInputNumericComponent,
  KSearchInputTextComponent, KSearchSelectComponent, KSearchTableComponent,OptionConfigModel, PrimeNgEs
} from '@ec.com.kgr/kng-components-v3/k-search';
import { CommonModule } from '@angular/common';
import { FormsModule } from '@angular/forms';
import { KFieldsetComponent } from '@ec.com.kgr/kng-components-v3/k-fieldset';
import { NumbersDirective, UpperCaseDirective, ToUpperCaseDirective } from '@ec.com.kgr/kng-components-v3/k-common/k-directives';
import { PopoverModule } from 'ngx-bootstrap/popover';
import { KValidationsModule } from '@ec.com.kgr/kng-components-v3/k-common/k-validations';
import { PersonsFilterService } from '@persons/services/persons-filter.service';
```

## HTML

```html


<!--k-search-input-characters-->
<k-search-input-text class="k-search-space-top" id="${1:id}" name="${2:name}"
    [label]="'${3:label}:'" [placeholder]="'${4:placeholder}'" [(ngModel)]="${5:filtersService.searchModel}"
    [optionSettings]="optionSettings" [showComparatorType]="${6:true}" [disabledCommaList]="${7:true}"
    [upperInputValue]="${8:true}" [maxlength]="${9:50}" [regularExpression]="'[a-zñA-ZÑ ]'"
    [required]="${10:false}">
</k-search-input-text>
```

## Usage

Component can be used with the following selectors:

* `k-search-input-characters`
* `<k-search-input-characters`
* `k-filters-1-imports`

## Input Properties

* `[disabledCommaList]`: Defines the disabledCommaList.
* `[label]`: Defines the label.
* `[maxlength]`: Defines the maxlength.
* `[optionSettings]`: Defines the optionSettings.
* `[placeholder]`: Defines the placeholder.
* `[regularExpression]`: Defines the regularExpression.
* `[required]`: Defines the required.
* `[showComparatorType]`: Defines the showComparatorType.
* `[upperInputValue]`: Defines the upperInputValue.

## Output Events

* `(ngModel)`: Event emitted when ngModel occurs.

## Attributes

* `name`: Defines the name attribute.

