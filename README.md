#remixin.scss
***
remixin is a simple and efficient [SCSS](http://sass-lang.com) (*Syntactically Awesome Stylesheets*) [mixin](http://sass-lang.com/docs/yardoc/file.SASS_REFERENCE.html#mixins) (like macros — re-usable css properties, selectors with arguments).
<br /><br />

##Installation

Download the .scss file then add or import it to your .scss file.

    git clone http://git@github.com:ialphan/remixin.scss.git
<br />

##Usage

	remixin(property, value);
	
**Note:** Property has to be the first argument. Value can be a list of parameters separated by space (not comma). See individual properties below for implementation.

####background-clip
**Usage:** `(background-clip, border-box | padding-box | content-box [, border-box | padding-box | content-box]*)`. 
**Support:** Chrome 4+, Firefox 3.5+, IE9+, Safari 3+.

    @include remixin(background-clip, border-box);


####background-size
**Usage:** `(background-size, [<length> | <percentage> | auto ]{1,2} | cover | contain [, [ <length> | <percentage> | auto ]{1,2} | cover | contain]*)`. 
**Support:** Chrome 1+, Firefox 3.6+, IE9+, Safari 3+.

    @include remixin(background-size, 20px 20px);


####border-radius
**Usage:** `(border-radius, [<length> | <percentage> ]{1,4} [ / [ <length> | <percentage> ]{1,4}]?)`. 
**Support:** Chrome 4+, Firefox 4+, IE9+ (Use https://github.com/lojjic/PIE's solution for IE8), Safari 3+.

    @include remixin(border-radius, 20px);


####box-shadow
**Usage:** `(box-shadow, none | < inset? && [ <length>{2,4} && <color>? ]> [, < inset? && [ <length>{2,4} && <color>? ]> ]*)`. 
**Support:** Chrome 1+, Firefox 3.5+, IE9+ (Use https://github.com/lojjic/PIE's solution for IE8), Safari 3+.

    @include remixin(box-shadow, 20px 20px 20px #f00);


####box-sizing
**Usage:** `(box-sizing, content-box | border-box | inherit)`. 
**Support:** Chrome 1+, Firefox 1+, IE 8+, Safari 3+.

    @include remixin(box-sizing, content-box);


####font-face
**Usage:** `(font-face, <font> | style || weight)`. 
**Support:** Chrome 4+, Firefox 3.5+, IE4+, Safari 3.1+. 
**Note:** Font style or weight does not have to be in order.

    @include remixin('font-face', Consolas);
    @include remixin('font-face', Consolas normal);
    @include remixin('font-face', Consolas normal 200);


####opacity
**Usage:** `(opacity, <alphavalue> | inherit)`. 
**Support:** Chrome 1+, Firefox 1+, IE9+ (compatible down to IE 8), Safari 1.2+.

    @include remixin(opacity, 0.2);


####user-select
**Usage:** `(user-select, none | text | toggle | element | elements | all | inherit)`. 
**Support:** Chrome 1+, Firefox 1+, IE 10+, Safari 1+.

    @include remixin(user-select, none);


####::selection
**Usage:** `(::selection, background || color)`. 
**Support:** Chrome 1+, Firefox 1+, IE 9+, Safari 1.1+.

    @include remixin(::selection, #f00);
<br />

##Browser Support
* Chrome (-webkit) as $webkit.
* Firefox (-moz) as $moz.
* Internet Explorer (-ms) as $ms (IE 10), $ms9 (IE 9), $ms8 (IE 8).
* Safari (-webkit) as $webkit.

See individual properties above for implementation.
<br /><br />

##Advanced Usage (suggested)
In the remixin( ), enable/disable vendors for your needs. Defaults are: 

	$moz: true, $ms8: false, $ms9:true, $ms: true, $webkit: true
	
If you are developing for Chrome/Safari set $webkit to true,for Firefox set $moz to true,
for IE 10 but not IE8/9, set $ms8 and $ms9 to false and $ms to true.


You can also target these when you are calling your remixin. Here is an example for applying border. Declare your variables:

    $fontStyle: normal;
    $fontWidth: 600;

Decide on which vendor you don't need and then turn it off:

    $ms: false
**Note:** This will also disable IE 8 ($ms8)  and IE 9 ($ms9). IE ($ms) > IE 8($ms8) | IE 9 ($ms9)

<br />
Then use them in your remixin:

    @include remixin(font-face, $fontStyle $fontWidth, $ms: false);


Multiple vendors can be passed as arguments separated by commas:

    @include remixin(font-face, $fontStyle $fontWidth, $moz: false, $ms: false);  

This will not generate any -moz nor -ms properties.
<br /><br />

##History
**v0.1 - 2012-06-14**

Added properties:

  * background-clip
  * background-size
  * border-radius
  * box-shadow
  * box-sizing
  * font-face
  * opacity
  * ::selection
  * user-select