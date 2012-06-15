#remixin.scss

remixin is a simple and efficient [SCSS](http://sass-lang.com) (*Syntactically Awesome Stylesheets*) [mixin](http://sass-lang.com/docs/yardoc/file.SASS_REFERENCE.html#mixins) (like macros — re-usable css properties, selectors with arguments) to generate vendor specific css properties.
<br /><br />


##Usage
Call remixin with the property and value(s).

	@include remixin(property, value);
	
**Note:** Property has to be the first argument and value can be a list of parameters separated by space. See individual properties below for usage.

<br />
####animation
**Usage:** `(animation, [<animation-name> || <animation-duration> || <animation-timing-function> || <animation-delay> || <animation-iteration-count> || <animation-direction>][, [<animation-name> || <animation-duration> || <animation-timing-function> || <animation-delay> || <animation-iteration-count> || <animation-direction>] ]*)`.
<br />**Support:** Chrome 4, Firefox 5+, IE 10+, Safari 4+.

    Ex. @include remixin(animation, move 1s infinite);

<br />
####background-clip
**Usage:** `(background-clip, border-box | padding-box | content-box [, border-box | padding-box | content-box]*)`.
<br />**Support:** Chrome 4+, Firefox 3.5+, IE9+, Safari 3+.

    Ex. @include remixin(background-clip, border-box);

<br />
####background-size
**Usage:** `(background-size, [<length> | <percentage> | auto ]{1,2} | cover | contain [, [ <length> | <percentage> | auto ]{1,2} | cover | contain]*)`.
<br />**Support:** Chrome 1+, Firefox 3.6+, IE9+, Safari 3+.

    Ex. @include remixin(background-size, 20px 20px);

<br />
####border-radius
**Usage:** `(border-radius, [<length> | <percentage> ]{1,4} [ / [ <length> | <percentage> ]{1,4}]?)`. 
<br />**Support:** Chrome 4+, Firefox 4+, IE9+ (Use https://github.com/lojjic/PIE's solution for IE8), Safari 3+.

    Ex. @include remixin(border-radius, 20px);

<br />
####box-direction
**Usage:** `(box-direction, normal|reverse|inherit)`. 
<br />**Support:** Chrome 1+, Firefox 1+, Safari 2+.

    Ex. @include remixin(box-direction, reverse);

<br />
####box-shadow
**Usage:** `(box-shadow, none | < inset? && [ <length>{2,4} && <color>? ]> [, < inset? && [ <length>{2,4} && <color>? ]> ]*)`.
<br />**Support:** Chrome 1+, Firefox 3.5+, IE9+ (Use https://github.com/lojjic/PIE's solution for IE8), Safari 3+.

    Ex. @include remixin(box-shadow, 20px 20px 20px #f00);

<br />
####box-sizing
**Usage:** `(box-sizing, content-box | border-box | inherit)`.
<br />**Support:** Chrome 1+, Firefox 1+, IE 8+, Safari 3+.

    Ex. @include remixin(box-sizing, content-box);

<br />
####font-face
**Usage:** `(font-face, <font> | style || weight)`.
<br />**Support:** Chrome 4+, Firefox 3.5+, IE4+, Safari 3.1+.

    Ex. @include remixin('font-face', Consolas);
    	@include remixin('font-face', Consolas normal);
    	@include remixin('font-face', Consolas normal 200);

<br />
####hyphens
**Usage:** `(hyphens, none | manual | auto`.
<br />**Support:** Chrome 13+ Firefox 6+, IE 10+, Safari 5.1+.

    Ex. @include hyphens('hyphens', none);

<br />
####linear-gradient
**Usage:** `(linear-gradient, ([<point> || <angle>,]? <stop>, <stop> [, <stop>]))`:
<br />**Support:** Chorome 3+, Firefox 3.6+, IE10+, Safari 4+.

    Ex. @include remixin(linear-gradient, left #f00 #00f));

<br />
####opacity
**Usage:** `(opacity, <alphavalue> | inherit)`. 
<br />**Support:** Chrome 1+, Firefox 1+, IE9+ (compatible down to IE 8), Safari 1.2+.

    Ex. @include remixin(opacity, 0.2);

<br />
####transform
**Usage:** `(transform, none | matrix | matrix3d | translate | translate3d | translateX | translateY | translateZ | scale | scale3d | scaleX | scaleY | scaleZ | rotate | rotate3d | rotateX | rotateY | rotateZ | skew | skewX | skewY | perspective)`. 
<br />**Support:** Chrome 1+, Firefox 3.5+, IE9+, Safari 3.1+.

    Ex. @include remixin(transform, rotate(200deg));

<br />
####transition
**Usage:** `(transition, none|all|property time linear|ease|ease-in|ease-out|ease-in-out|cubic-bezier(n,n,n,n) time)`.
<br />**Support:** Chrome 1+, Firefox 4+, IE 10+, Safari 3.2+.

    Ex. @include remixin(transition, all 2s);

<br />
####user-select
**Usage:** `(user-select, none | text | toggle | element | elements | all | inherit)`. 
<br />**Support:** Chrome 1+, Firefox 1+, IE 10+, Safari 1+.

    Ex. @include remixin(user-select, none);

<br />
####::selection
**Usage:** `(selection, background color)`. 
<br />**Support:** Chrome 1+, Firefox 1+, IE 9+, Safari 1.1+.

    Ex. @include remixin(selection, #f00);
<br />

##Browser Support
* Chrome (-webkit) as $webkit.
* Firefox (-moz) as $moz.
* Internet Explorer (-ms) as $ms (IE 10), $ms9 (IE 9), $ms8 (IE 8).
* Safari (-webkit) as $webkit.

See individual properties above for implementation.
<br /><br />

##Advanced Usage (suggested)
In the remixin() enable/disable vendors for your needs. Defaults are: 

	$moz: true, $ms8: false, $ms9:true, $ms: true, $webkit: true
	
If you are developing for Chrome/Safari set $webkit to true, for Firefox set $moz to true,
for IE 10 but not IE8/9, set $ms8 and $ms9 to false and $ms to true.

You can also target these when you are calling your remixin. Here is an example for applying border. Declare your variables:

    $fontStyle: normal;
    $fontWidth: 600;

Decide on which vendor you don't need and then turn it off:

    $ms: false
**Note:** This will also disable IE 8 ($ms8)  and IE 9 ($ms9). IE ($ms) > IE 8 ($ms8) | IE 9 ($ms9)

<br />
Then use them in your remixin:

    @include remixin(font-face, $fontStyle $fontWidth, $ms: false);


Multiple vendors can be passed as arguments separated by commas:

      @include remixin(transform, rotate(200deg), $moz: false, $ms: false);

This will not generate any -moz nor -ms properties.
<br /><br />

##TextMate Bundle (snippet).
The SCSS file extension must be selected in TextMate. Type *remixin*	then press tab, it will generate the following code and place the cursor before the comma.
	
	@include remixin(, ); 
<br />

##License
See the LICENSE file.
<br /><br />

##History
**v0.1.1 - 2012-06-14**

  * Updated incorrect usage for ::selection property in the README.md.
  * Added $fontPath variable to be used with font-face property.
  * Added these properties:
  	* animation
  	* box-direction
  	* hyphens
  	* linear-gradient
  	* transform
  	* transition properties
  *	Added remixin snippet as TextMate bundle.

***

**v0.1 - 2012-06-14**

* Added these properties:
  * background-clip
  * background-size
  * border-radius
  * box-shadow
  * box-sizing
  * font-face
  * opacity
  * ::selection
  * user-select