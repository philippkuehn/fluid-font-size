[![npm version](https://badge.fury.io/js/fluid-font-size.svg)](https://badge.fury.io/js/fluid-font-size)

# Fluid font-size

This Sass mixin doesn't create just viewport-based font-sizes.
The ratio between small font-sizes and large font-sizes is smaller at a smaller window width.
So you don't have problems with line-breaks at large headlines on mobile devices.

## Usage

After installing with `npm install fluid-font-size` you can import it.

```scss
@import "node_modules/fluid-font-size/fluid-font-size.scss";

.foo {
  @include fluid-font-size(20px);
}
```

This will create something like:

```scss
.foo {
  font-size: 20px;
  font-size: calc(15.06173px + 0.5487vw);
  content: "viewport-units-buggyfill; font-size: calc(15.06173px + 0.5487vw)";
}
```
Wonder what the `viewport-units-buggyfill` stuff is? <a href="https://github.com/rodneyrehm/viewport-units-buggyfill">It's a polyfill for viewport units</a>. So basically you'll have IE9 support with it.

### Min and max font-size

Minimum and maximum font-sizes are also supported. Yay! 🎉 

```scss
.foo {
  @include fluid-font-size(20px, (
    min: 15px,
    max: 25px,
  ));
}
```

### Options

To change the intensity of the effect to influence the ratio between small and large font-sizes you can change the variable `$fluid-font-size-ratio`.

```scss
$fluid-font-size-ratio: 1;
```

To decrease the effect set it to an higher number than `1`. To increase the effect decrease it to something between `0` and `1`.
