# Front End Style Guide

The following is a first draft of front end development style guide which should be followed when developing websites for Equator.

Rules have exceptions. Use the common sense to determine whether they actually do apply to a given situation. 

## Table of Contents

1. [HTML](#html)
2. [CSS](#css)
3. [LESS](#less)
3. [JavaScript](#javascript)
4. [Performance Techniques](#perf)

<a id="#html"></a>
## HTML

### Closing tags

Close your tags. It's tidier and easier to read and identify nesting.

### Image Alt Tags

All images should have an alt tag. It should be a concise description of what the image shows. Forgetting to do so fails to meet accessibility standards.   

### Presentational Tags

The &lt;b&gt; and &lt;i&gt; tags make your text bold and italic respectively. However, these are presentational tags and the styling should be handled by font-weight and font-style in your CSS. If you need highlighting use &lt;strong&gt; and &lt;em&gt; instead.

Using the &lt;center&gt; is bad practise because it has no other meaning other than making the text center. Leave the styling to your CSS.

### UL or OL

Lists where order is important use the OL tag. 

### Attributes ###

Attribute values should be wrapped double quotes. Single quotes are acceptable too. Just be consistent. 

<a id="#css"></a>
## CSS

Rules should be seperated by a single blank line.

Include one declaration per line in a declaration block.

Specify one selector per line in multi-selector rules e.g.

    .selector-a,
    .selector-b,
    .selector-c {
      color: #f0d;
      text-align: center;
    }

### Class names

Classes should be lowercase with words seperated by a single dash e.g. `.booking-component`
    
Class names should be readable and descriptive so don't be afraid to make them long. Long class names are better than more chaining. We like BEM. Consider using it on your project. http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/

Class names should not related to presentation. What is the div for, not what it looks like.

### IDs

IDs should not be used for styling purposes. It's far too restrictive when styling against IDs. No opportunity for reusing shared styles. Having more than one item on the page will cause problems that can and probably will happen.

### Specificity

The combination of a tag and a class is often uneccessary e.g. `h3.subtitle`. If your h3 becomes an h4 in your markup you don't want to have to revisit your CSS and change this. Ditch the tag.

### Chaining

Try to keep the number of items in a single selector down to 4. The more you have, the more annoying overriding it further down in a your media queries.

### !important

If you follow the rules above, importants will be a rare occurance. They're discouraged.

### Sizes

Use `0` over `0px`. The `px` is redundant.

Avoid adding more widths than necessary. Allow the component to get it's width from it's container. 

Use `width: auto` over `width: 100%` for block elements. 

### Colours

Use HEX with the exception of RGBA. If using RGBA a fallback written in RGB should be provided. Shorthand hex should be used where applicable. `color: #ff0;`

### Inline Styles

General bad as they force the need for importants to override. May be necessary when generated from CMS content though.

### Comments

Make good use of comments. These will be removed in minification so won't make it up to the live site, but will come in handy during development.

Please don't commit large chunks of commented out code to source control without a description as to why it's commented out. It's confusing months later why it's there and why it was removed.

### Anchors

:hover should generally be accompanied by :focus for accessibility reasons.



<a id="#less"></a>
### LESS

#### Nesting

Nesting should ideally go no more than three levels deep. Following the CSS rules above, this shouldn't be too hard to achieve. 

#### Mixins

Your CSS should be free from vendor prefixes. These should be injected via mixins. If you find yourself writing vendor prefixed multi line definitions, bundle it up as a mixin.

#### Variables

Making good use of variables helps keep your CSS highly maintainable. Font and colour values should be saved as variables as a standard.

<a id="#javascript"></a>
## JavaScript

### Naming conventions

* Avoid the user of reserved words and use readable synonyms

``` javascript
var element; //opt for this one
var variable;
```

* Don't name a parameter within a function 'arguments' as this will override the default 'arguments' object in the function scope. If there's a lack of imagination use 'args' but please, try to be descriptive
 
### Declarations

* It's better to declare objects & arrays in a literal way

``` javascript
//Arrays
var array = [];

//Objects
var obj = {};
```

### Variables

* avoid Global variables. Lot of developers use the same names for variables so best define their scope and keep the Global scope free and organised.

### Strings

* Use ' ' instead of " " for strings - most times you'll want to use " " for DOM element tags within JS

### Use of elements

* Avoid adding to array with element index but use push function instead (you may not know the length of the array at a given time)

```
var array = [];

array.push('newElement');

//instead of
array[array.length - 1] = 'newElement';
```

* Use of dot notation on objects is a good thing. Use the [''] notation when using a parameter

``` javascript
var options = {
    option1: 1,
    option2: 2
};

myObject.option1 = 3;

var getOption = function(optionName){
    return options[optionName];
};
```

* Don't use a trailing comma in objects - it's the end and it causes issues on some versions of IE

``` javascript
var options = {
    option1: 1,
    option2: 2
};

var options = {
    option1: 1,
    option2: 2, //there's nothing after so no trailing comma
};

```

* If statement brackets are brownie points - keep it organised and easy to read.

When using single line returns this can go all in one line

``` javascript
if($('.class').length == 0){ return false;}
```

### Functions

* Always assign functions to variables if used within if statements, loops and so on.

``` javascript
var readyToDoSomething = true;
var usableFunciton = function(){
//do something
};

if(readyToDoSomething){
    usableFunction();
}
```

### Hoisting

* Hoisting is a nice feature but please avoid hoisting issues (and readability issues)
** Assign variables at the top of their scope - When hoisting variables go to the top but their assignment doesn't!

### jQuery

* Cache jQuery lookups to save you calculation time

``` javascript
var myElement =  $('.element');

myElement.find('.children').addClass('newClass');

myElement.addClass('newParentClass');
```

### Design Patterns

#### Modular Structure

## Plugins

Consider each plugin carefully. It should be lightweight. If it's a slider how does it perform with loads of slides? Does it work with multiple instances on the same page?

<a id="#perf"></a>
## Performance Techniques

### Dynamic Image Processing

You'll more than likely be building against a content management system. We cannot assume the website administrator will be uploading an image which is the optimal size. All content managed images should be processed through an image processing tool such as ImageGen. Images should be shrunk if larger than a predefined size. 

### Concatenation & Minification

Multiple CSS and JavaScript files should be combined into as few files as possible. Many tools are available to allow this to happen on the fly e.g. ASP.Net's built in bundling or the DotLESS NuGet package. These tools also include the ability to minify the generated output to keep filesize as small as possible. 

## Inspired by 

* [1](https://github.com/ginatrapani/ThinkUp/wiki/Code-Style-Guide:-CSS)
* [2](http://csswizardry.com/2012/04/my-html-css-coding-style/)
* [3](https://github.com/necolas/idiomatic-css)
* [4] (https://github.com/airbnb/javascript#objects)
