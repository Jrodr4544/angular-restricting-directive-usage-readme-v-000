# Restricting Directive usage

## Overview

We've learned that directives can be used as HTML attributes and HTML elements, but did you know you can tell Angular to only allow your directive to be used in a certain way?

## Objectives

- Describe the syntaxes for declaring Directives
- Restrict our Directive

## Restrict

Angular allows us to set a property named `restrict` on the object we return on our directive definition. We can pass through a string with certain letters letting Angular know how our directive can be used.

```js
function MyDirective() {
	return {
		restrict: 'E',
		template: '<div>Hello world!</div>'
	};
}

angular
	.module('app')
	.directive('myDirective', MyDirective);
```

Above, we've got `restrict` set to `E`. This stands for element, meaning our directive can only be used as an element.

The letters available are:

`A` - used as an attribute
`E` - used as an element
`C` - used as a class name
`M` - used as a comment

You might've noticed that we can use directives in class names and comments too. This isn't recommended however, as it is unclear if we're just doing a normal HTML comment or invoking a directive. It also isn't clear if we're adding a class to an element or invoking a directive too.

You can use the individual letters or put them together - `'EA'` will allow the directive to be used as an element and an attribute.

By default, restrict is set to 'EA'.