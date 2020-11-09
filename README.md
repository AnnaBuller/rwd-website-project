# RWD Website Project

RWD Website is a responsive landing page modeled after [Colorlib free Applab template](https://colorlib.com/wp/template/applab/). 

See [the RWD Website](https://annabuller.github.io/rwd-website-project/).


## Installation

The project uses [node](https://nodejs.org/en/) and [npm](https://www.npmjs.com/). Having them installed, type into the terminal: `npm i` to install node-sass package.

## Solutions provided in the project

- CSS file created with [node-sass library](https://www.npmjs.com/package/node-sass).

- Sass mixins used to define breakpoints – having all breakpoints in one place makes it possible to change them at any time, all at once. See the example of mixin for desktop breakpoint beneath:
```
@mixin desktop {
	@media (min-width: 1330px) {
		@content;
	}
}
```
- Responsive font size created with CSS function: [clamp()](https://developer.mozilla.org/en-US/docs/Web/CSS/clamp). Using vw unit for the middle parameter value makes the font grow and shrink smoothly while resolution changes.
As clamp() is not fully supported yet, it was necessary to provide also the media queries breakpoints. Here is the example of using both - mixins and clamp(): 
```
&__headline {
		font-size: 1.3rem;
	@include tablet-and-landscape {
		font-size: 1.5rem;
	}
	@include desktop{
		font-size: 1.7rem;
	}
	@supports (font-size: clamp(1.3rem, 2vw, 1.7rem)) {
		font-size: clamp(1.3rem, 2vw, 1.7rem);
	}}
```

- Linear-gradient used for CSS background property along with an image allowed to achieve the effect of colored overlay. As linear-gradient is now [well-supported](https://caniuse.com/mdn-css_types_image_gradient_linear-gradient) across different browsers, using it is a more convenient and space-saving way of creating an overlay than doing it with CSS pseudo-elements.
```
background: linear-gradient(rgba(97, 179, 255, 0.9), rgba(97, 179, 255, 0.9)),
		    url(../images/banner/testmonial.png) no-repeat center center/cover;
```

- Grid provides flexibility to footer elements – they can be stretched in one row as well as arranged in two or one column.

## Conclusions for future projects

I found a way to **improve** margin and padding changes depending on resolution. In this project they are modified with media queries in the place of their occurrence. In the future projects I will definitely use Sass @extend rule, keeping all shared measures in one place and changing them with only one time use of media queries per breakpoint. Example of usage beneath:

#### File storing resolution values:
```
%shared-pd {
  padding: 10px;
  @include tablet-and-landscape {
    padding: 50px;
  }
  @include desktop {
    padding: 100px;
  }
}

```
#### Values shared between different elements:
```
.footer-up {
	@extend %shared-pd;
}
```
```
.download {
	@extend %shared-pd;
}
```

## Thanks
- To [Colorlib](https://colorlib.com/wp/) for free templates.
- To my [mentor](https://github.com/devmentor-pl) for creating the task and for the code review.