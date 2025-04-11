![Kruger Corp](https://img.shields.io/badge/Kruger_Corp_®-Copyright_2022-blue)

# k-tree

Tree component

## TypeScript

No TypeScript implementation available.

## HTML

```html


<k-tree [treeValue]="${1:treeValue}" [treeSelection]="single" (nodeSelected)="isNodeSelect($event)"
    (nodeUnselected)="isNodeUnSelect()" [filterValue]="${3:filterValue}" [filterMode]="'strict'">
</k-tree>
```

## Usage

Component can be used with the following selectors:

* `k-tree`
* `<k-tree`

## Input Properties

* `[filterMode]`: Defines the filterMode.
* `[filterValue]`: Defines the filterValue.
* `[treeSelection]`: Defines the treeSelection.
* `[treeValue]`: Defines the treeValue.

## Output Events

* `(nodeSelected)`: Event emitted when nodeSelected occurs.
* `(nodeUnselected)`: Event emitted when nodeUnselected occurs.

