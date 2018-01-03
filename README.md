# FRONTENDLER SASS LIBRARY

[![npm version](https://badge.fury.io/js/frontendler-sass.svg)](https://badge.fury.io/js/frontendler-sass)

This package contains all scss files used in [frontendler](http://frontendler.io) project.

## Dependencies

This library is browser prefixes free so if you want to use this package in your personal project **we strongly recommend** you to use [Autoprefixer](https://www.npmjs.com/package/gulp-autoprefixer) for manager your prefixes.

## Documentation

**_IMPORTANT:_** Now the Frontendler grid is entirely based on the flexbox display property.

### Grid

**grid-gutter `var`**

```scss
$grid-gutter: 2em !default;
```

**grid-spaces `var`**

Simple example:

```scss
$grid-spaces: ("small": 1em, "medium": 2em, "large": 4em)!default;
```

This space list have the objective to keep the proportionality of the grid in all the spaces between all elements with the goal to get groups of content based on the proportional proximity respecting the responsive aspects.

> The Gestalt law of proximity states that "objects or shapes that are close to one another appear to form groups". <https://en.wikipedia.org/wiki/Principles_of_grouping#Proximity>

In the link below you can get a very well done explanation about space scales.

<https://medium.com/eightshapes-llc/space-in-design-systems-188bcbae0d62>

With Frontendler you can define you own list of spaces as you can do in grid-breakpoints, colors, font-sizes, etc..
However the default value of the space list, based in geometric progression, is:

Default value:

```scss
$grid-spaces: grid-spaces($grid-gutter, 2) !default;
```

**grid-spaces `function`**

Return a list of spaces in em unit based in a scale factor (multiplier) .

```scss
grid-spaces($grid-gutter, $scale-factor)
```

**grid-space `function`**

```scss
.class {
  padding: grid-space($grid-space-name);
}
```

**grid-breakpoints `var`**

```scss
$grid-breakpoints: (
    "xsmall": 100% max 600px,
    "small": 100% min 601px max 960px,
    "medium": 100% min 961px max 1280px,
    "large": 1280px min 1281px max 1600px,
    "xlarge": 1600px min 1601px
  )!default;
```

**grid-row `mixin`**

```scss
@include grid-row();
```

**grid-column `mixin`**

```scss
@include grid-column($flex: 1, $gutter: $grid-gutter);
```

**grid-column-breakpoint `mixin`**

```scss
@include grid-column-breakpoint($breakpoint, $flex: 1, $gutter: false);
```

**or**

```scss
@include grid-column-breakpoint($breakpoint, $flex: 1, $gutter: false) {
    ...
}
```

**grid-breakpoint `mixin`**

```scss
@include grid-breakpoint($breakpoints...) {
    ...
};
```

**grid-breakpoint-hide `mixin`**

```scss
@include grid-breakpoint-hide ($breakpoints...);
```

---

### Font

**font-family-base `var`**

```scss
$font-family-base: -apple-system, system-ui, BlinkMacSystemFont, "Segoe UI",
  Roboto !default;
```

**font-family-mono `var`**

```scss
$font-family-mono: "SF Mono", "Segoe UI Mono", "Roboto Mono", Menlo, Courier,
  monospace !default;
```

**font-family-fallback `var`**

```scss
$font-family-fallback: "Helvetica Neue", sans-serif !default;
```

**font-family `var`**

```scss
$font-family: $font-family-base, $font-family-fallback !default;
```

**font-size `var`**

```scss
$font-size: 16px !default;
```

**font-sizes `var`**

Simple example:

```scss
$font-sizes: (
  "small": 0.8em,
  "medium": 1em,
  "large": 2em
);
```

Default value:

```scss
$font-sizes: font-sizes($perfect-fourth);
```

**font-sizes `function`**

Return a list of font sizes based in a type scale factor.
Based on this very useful tool http://type-scale.com/.

```scss
// Example of use in settings file:
$font-sizes: font-sizes($perfect-fourth);
```

Where `$perfect-fourth` is a predefined value as these values below:

```scss
$minor-second: 1.067;
$major-second: 1.125;
$minor-third: 1.2;
$major-third: 1.25;
$perfect-fourth: 1.333;
$augmented-fourth: 1.414;
$perfect-fifth: 1.5;
$golden-ratio: 1.618;
```

**font-size `function`**

```scss
@function font-size($size-name);
```

**font-weights `var`**

```scss
$font-weights: ("light" : lighter, "regular" : normal, "bold" : bold)!default;
```

**font-weight `function`**

```scss
@function font-weight($weight-name);
```

---

### Colors

**colors `var`**

```scss
$colors: (
    "ocean": #00a7ca,
    "blue": #0075d3,
    "purple": #8244a7,
    "pink": #dd318a,
    "green": #71be48,
    "yellow": #f59d37,
    "orange": #f75925,
    "red": #dd202b,
    "dark": #1c2731,
    "gray": #606c78,
    "silver": #939fac
  )
  !default;
```

**color `function`**

```scss
.class {
  color: color($color-name, $amount:50%);
}
```

---

### Animations

**animations `include`** Add animation keyframes listed in `$animation-keyframes`.

```scss
@include animations;
```

**animation-duration `var`**

```scss
$animation-duration: 0.25s !default;
```

**animation-time-functions `var`**

```scss
$animation-time-functions: (
    "in-out-quad": cubic-bezier(0.455, 0.03, 0.515, 0.955),
    "in-out-cubic": cubic-bezier(0.645, 0.045, 0.355, 1),
    "in-out-quart": cubic-bezier(0.77, 0, 0.175, 1),
    "in-out-quint": cubic-bezier(0.86, 0, 0.07, 1),
    "in-out-sine": cubic-bezier(0.445, 0.05, 0.55, 0.95),
    "in-out-expo": cubic-bezier(1, 0, 0, 1),
    "in-out-circ": cubic-bezier(0.785, 0.135, 0.15, 0.86)
  )
  !default;
```

**animation-keyframes `var`**

```scss
$animation-keyframes: (
    "fade-in",
    "fade-out",
    "bounce-in-down",
    "bounce-in-up",
    "rubber-band",
    "zoom-in",
    "slide-in-up",
    "slide-in-down",
    "alert"
  )
  !default;
```

---

### Utils

**clearfix `mixin`**

More about this mixin in this [link](http://cssmojo.com/latest_new_clearfix_so_far/).

```scss
@include clearfix;
```

**box-shadow `mixin`**

Based in this awesome [freebie](https://medium.com/@Florian/freebie-google-material-design-shadow-helper-2a0501295a2d).

```scss
@include box-shadow ($level);
```

---

Made with ♥ by [Daniel Beff](http://www.danielbeff.com.br/) ([@dbeff](https://github.com/dbeff))
