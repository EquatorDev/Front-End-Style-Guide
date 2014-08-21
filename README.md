# Front End Style Guide

The following is a first draft of front end development style guide which should be followed when developing websites for Equator.

Rules have exceptions. Use the common sense you got from your mother as to whether they actually do apply an a given situation. 

## Table of Contents

1. [HTML](#html)
2. [CSS](#css)
3. [LESS](#less)
4. [JavaScript](#javascript)

<a id="#html"></a>
## HTML

### Closing tags
Close your tags. It's tidier and easier to read and identify nesting.

### Images
Don't forget your alt tags which should be a concise description of what the image shows. Forgetting to do so fails to meet accessibility standards.   

### Presentational Tags

The &lt;b&gt; and &lt;i&gt; tags make your text bold and italic respectively. However, these are presentational tags and the styling should be handled by font-weight and font-style in your CSS. If you need highlighting use &lt;strong&gt; and &lt;em&gt; instead.

Using the &lt;center&gt; is bad practise because it has no other meaning other than making the text center. Leave the styling to your CSS.

### UL or OL

Lists where order is important use the OL tag. 

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
    
Class names should be readable and descriptive so don't be afraid to make them long. Long class names are better than more chaining.

Class names should not related to presentation. What is the div for, not what is looks like.

##### Specificity

The combination of a tag and a class is often uneccessary e.g. `h3.subtitle`. If your h3 becomes an h4 in your markup you don't want to have to revisit your CSS and change this. Ditch the tag.

##### Chaining

Try to keep the number of items in a single selector down to 4. The more you have, the more annoying overriding it further down in a your media queries.

### !important

If you follow the rules above, importants will be a rare occurance. They're discouraged.

### Sizes

Use `0` over `0px`. The `px` is redundant.

Avoid adding more widths than necessary. Allow the component to get it's width from it's container. 

Use `width: auto` over `width: 100%` for block elements. 

### Colours

Colours should be written as HEX with the exception of colours requiring an alpha channel. In this case RGBA should be used with a fallback written in RGB. Shorthand hex should be used where applicable. `color: #ff0;`

### Backgrounds

Don't redeclare the same background properties over and setting a colour changing image. Make use of inheritence. 

### Inline Styles

General bad as they force the need for importants to override. May be necessary when generated from CMS content though. 

### Comments

Make good use of comments. These will be removed in minification so won't make it up to the live site, but will come in handy during development.

### Anchors

:hover should generally be accompanied by :focus for accessibility reasons.

<a id="#less"></a>
## LESS

### Nesting

Nesting should ideally go no more than three levels deep. Following the CSS rules above, this shouldn't be too hard to achieve. 

### Mixins

Your CSS should be free from vendor prefixes. These should be injected via mixins. If you find yourself writing vendor prefixed multi line definitions, bundle it up as a mixin.

### Variables

Making good use of variables helps keep your CSS highly maintainable. Font and colour values should be saved as variables as a standard.

## JavaScript

## Inspired by 

[1](https://github.com/ginatrapani/ThinkUp/wiki/Code-Style-Guide:-CSS)
[2](http://csswizardry.com/2012/04/my-html-css-coding-style/)
[3](https://github.com/necolas/idiomatic-css)
