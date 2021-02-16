# Diversus Front-end Reference Guide

All front-end code from Diversus should be accessible, maintainable and efficient.

To ensure that all Diversus developers maintain a base level of consistency regardless of skill level or confidence, this guide should be used as a reminder before starting and a set of criteria during QA/code review.



## Table of Contents

1. [Naming Conventions](#naming-conventions)
2. [SCSS Nesting](#scss-nesting)



## Naming Conventions

While working on any project, it is important for there to be a set and consistent naming conventions while creating components. 

If you're working on an existing project (eg. St John of God), it is likely they have their own naming convention already in place. Read through some existing code and ascertain what that naming convention is **before** starting.

If you're working on a new project and are setting a naming convention, try [BEM](http://getbem.com/naming).

**BEM** (`.block__element--modifier`)

```html
<div class="block block--modifier">
    <div class="block__element-1"> ... </div>
    <div class="block__element-2 block__element-2--modifier"> ... </div>
</div>
```

```scss
.block {
    // ...
    
    &__element-1 {
    	// ...
    }
    
    &__element-2 {
    	// ...    
        &--modifier {
            // ...
        }
    }
    
    &--modifier {
    	// ...
    }
}
```



## SCSS Nesting

While writing SCSS, try to take advantage of the nesting functionality in conjunction with the `&` parent selector. `&` is a special selector that includes all of the nested selectors above it. Using the `&` parent selector can help to minimise [CSS Specificity](https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity) and produce less problems with over-specific styles which are difficult to override.

For example:

```scss
.alert {    
        // ... 
    & + & {
        // ... 
    }
    
	&--warning {
        // ... 
	}
    
    &__title {
        // ... 
    }
    
    &__body {
        // ... 
        
        &-actions {
        	// ... 
        }
    }
}
```

Will output to 

```css
.alert { ... }
.alert + .alert { ... }
.alert--warning { ... }
.alert__title { ... }
.alert__body { ... }
.alert__body-actions { ... }
```
