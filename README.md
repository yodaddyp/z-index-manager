# Z Index Manager
Simple Sass utility for managing z-indexes with mixins and functions.
Keeps track of all your layers, and avoid high z-indexes like 99999.

## Installation
Installation through bower
```
bower install z-index-manager --save
```

## Usage
### Variables
You can define you the z-indexes for your layers in a global variable called `$z-indexes`.
Example:
```
$z-indexes: (
		header: 10,
		modal: 20
);
```
These values can then be accessed via a function.
```
header {

    z-index: z-index-manager-get( header ); // returns 10
}

```

### Mixins
Mixins are exposed so you can quickly set z-indexes on specific elements and tell them to be above or below other layers.
Example:
```
header
{
  background: red;
  left: 0;
  position: fixed;
  right: 0;
  top: 0;

  @include z-index-above( footer );
}
```
You can save for reference on the fly by passing a unique id through as the second parameter.
Example: 
```
header
{
  @include z-index-above( footer, header ); // header is saved so can be used as a target later on.
}
```
Mixins available: `z-index-above`, `z-index-below`, `z-index-top` and `z-index-bottom`.

By default z-indexes are set by multiples of 5 (with the exception of `z-index-top` and `z-index-bottom`), but you can override this value by updating the `$z-index-buffer` variable.

## Examples
Examples stored in `/examples` directory. Run `npm example` in the project route.

## Inspiration
Inspired by the frustration that comes with working with the endless plugins that contain stooopidly high z-indexes, and this article on [Sitepoint](http://www.sitepoint.com/better-solution-managing-z-index-sass).

