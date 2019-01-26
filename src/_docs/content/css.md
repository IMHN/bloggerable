---
title: Overview
description: Utilize our source Sass files to take advantage of variables, functions, mixins, and more.
category: CSS
subcategory: none
---

The main CSS.

<figure>
  <div class="doc-badges">
    <div class="doc-badge">
      <span class="doc-badge-item">Source</span>
      <span class="doc-badge-item doc-badge-item-info">src/_scss</span>
    </div>
  </div>
</figure>


## File structure

```plaintext
[root theme directory]
└── src/
    └── _scss/
        ├── _custom.scss
        └── **/*.scss
```

<table>
  <thead>
    <tr>
      <th>File / Directory</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><code style="white-space: nowrap;">_custom.scss</code></td>
      <td>Copy variables from `_variables.scss` to this file to override default values without modifying source files.</td>
    </tr>
    <tr>
      <td><code style="white-space: nowrap;">\*\*/*.scss</code></td>
      <td>Other Sass files are variables, functions, mixins, and components.</td>
    </tr>
  </tbody>
</table>


## Sass options

You can find and customize these variables for key global options in `_variables.scss`.

| Variable | Values | Description |
| --- | --- | --- |
| `$enable-rounded` | `true` (default) or `false` | Enables predefined `border-radius` styles on various components. |
| `$enable-shadows` | `true` or `false` (default) | Enables predefined `box-shadow` styles on various components. |
| `$enable-transitions` | `true` (default) or `false` | Enables predefined `transition`s on various components. |


## Modify variables and maps

Every Sass variable includes the `!default` flag allowing you to override the variable’s default value in `_custom.scss` without modifying source code.

Just like Sass variables, all Sass maps include the `!default` flag and can be overridden and extended.

Example:

```scss
# src/_scss/_custom.scss

// Customize options
$enable-rounded: false;

// Variable overrides
$body-color:  #fff;
$body-bg:     #000;

// Modify map
$theme-colors: (
  "primary": #ff5722
);

// Add to map
$theme-colors: (
  "custom-color": #900
);
```


## Functions

We utilizes several Sass functions in `_functions.scss`.

### Color maps

Functions for getting values from the color maps.

```scss
// Retrieve color Sass maps
@function theme-color($key: "primary") {
  @return map-get($theme-colors, $key);
}
```

Example:

```scss
// Example to pick one color from a Sass map
.custom-element {
  background-color: theme-color("dark");
}
```

### Color contrast

The color contrast function, `color-yiq`. It utilizes the [YIQ color space](https://en.wikipedia.org/wiki/YIQ) to automatically return a light (`#fff`) or dark (`#111`) contrast color based on the specified base color.

```scss
// Color contrast
@function color-yiq($color) {
  $r: red($color);
  $g: green($color);
  $b: blue($color);

  $yiq: (($r * 299) + ($g * 587) + ($b * 114)) / 1000;

  @if ($yiq >= $yiq-contrasted-threshold) {
    @return $yiq-text-dark;
  } @else {
    @return $yiq-text-light;
  }
}
```

Example:

```scss
$bg: #000;

.custom-element {
  color: color-yiq(#000); // returns `color: #fff`
  background-color: #000;
}

.custom-element2 {
  color: color-yiq($bg); // returns `color: #fff`
  background-color: $bg;
}
```


## Responsive breakpoints

[Media queries](https://developer.mozilla.org/en-US/docs/Web/CSS/Media_Queries/Using_media_queries) for creating sensible breakpoints for our layouts and interfaces. These breakpoints are mostly based on minimum viewport widths and allow us to scale up elements as the viewport changes.

### Breakpoint up

CSS:

```css
/* Extra small devices (portrait phones, less than 576px) */
/* No media query for `xs` since this is the default */

/* Small devices (landscape phones, 576px and up) */
@media (min-width: 576px) { ... }

/* Medium devices (tablets, 768px and up) */
@media (min-width: 768px) { ... }

/* Large devices (desktops, 992px and up) */
@media (min-width: 992px) { ... }

/* Extra large devices (large desktops, 1200px and up) */
@media (min-width: 1200px) { ... }
```

Sass mixins:

```scss
// No media query necessary for xs breakpoint as it's effectively `@media (min-width: 0) { ... }`
@include media-breakpoint-up(sm) { ... }
@include media-breakpoint-up(md) { ... }
@include media-breakpoint-up(lg) { ... }
@include media-breakpoint-up(xl) { ... }

// Example: Hide starting at `min-width: 0`, and then show at the `sm` breakpoint
.custom-class {
  display: none;
}
@include media-breakpoint-up(sm) {
  .custom-class {
    display: block;
  }
}
```

### Breakpoint down

Media queries that go in the other direction (the given screen size or smaller).

CSS:

```css
/* Extra small devices (portrait phones, less than 576px) */
@media (max-width: 575.98px) { ... }

/* Small devices (landscape phones, less than 768px) */
@media (max-width: 767.98px) { ... }

/* Medium devices (tablets, less than 992px) */
@media (max-width: 991.98px) { ... }

/* Large devices (desktops, less than 1200px) */
@media (max-width: 1199.98px) { ... }

/* Extra large devices (large desktops) */
/* No media query since the extra-large breakpoint has no upper bound on its width */
```

Sass mixins:

```scss
@include media-breakpoint-down(xs) { ... }
@include media-breakpoint-down(sm) { ... }
@include media-breakpoint-down(md) { ... }
@include media-breakpoint-down(lg) { ... }
// No media query necessary for xl breakpoint as it has no upper bound on its width

// Example: Style from medium breakpoint and down
@include media-breakpoint-down(md) {
  .custom-class {
    display: block;
  }
}
```

### Breakpoint only

Media queries for targeting a single segment of screen sizes using the minimum and maximum breakpoint widths.

CSS:

```css
/* Extra small devices (portrait phones, less than 576px) */
@media (max-width: 575.98px) { ... }

/* Small devices (landscape phones, 576px and up) */
@media (min-width: 576px) and (max-width: 767.98px) { ... }

/* Medium devices (tablets, 768px and up) */
@media (min-width: 768px) and (max-width: 991.98px) { ... }

/* Large devices (desktops, 992px and up) */
@media (min-width: 992px) and (max-width: 1199.98px) { ... }

/* Extra large devices (large desktops, 1200px and up) */
@media (min-width: 1200px) { ... }
```

Sass mixins:

```scss
@include media-breakpoint-only(xs) { ... }
@include media-breakpoint-only(sm) { ... }
@include media-breakpoint-only(md) { ... }
@include media-breakpoint-only(lg) { ... }
@include media-breakpoint-only(xl) { ... }
```

### Breakpoint between

Similarly, media queries may span multiple breakpoint widths.

CSS:

```css
/* Example */
/* Apply styles starting from medium devices and up to extra large devices */
@media (min-width: 768px) and (max-width: 1199.98px) { ... }
```

Sass mixins:

```scss
@include media-breakpoint-between(md, xl) { ... }
```
