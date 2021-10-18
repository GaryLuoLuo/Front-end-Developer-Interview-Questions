---
title: CSS Questions
layout: layouts/page.njk
permalink: /questions/css-questions/index.html
---

* What is CSS selector specificity and how does it work?
    - browser decide which CSS property values to be applied to an element, increase:
    - Type selectors (e.g., h1) and pseudo-elements (e.g., ::before).
    - Class selectors (e.g., .example), attributes selectors (e.g., [type="radio"]) and pseudo-classes (e.g., :hover).
    - ID selectors (e.g., #example).
* What's the difference between "resetting" and "normalizing" CSS? Which would you choose, and why?
    - Resetting: Removing all styling from every element - margins, padding, etc. All elements will have the same font-size, same line-height and no spacing. Eric Meyer's Reset is the most common approach: http://meyerweb.com/eric/tools/css/reset/
    - Normalizing: Making elements render consistently across browsers. So all h1s will have the same size across browsers, for instance. Nicolas Gallagher's normalize.css is generally used for normalizing: http://necolas.github.io/normalize.css/
    - ?I personally prefer normalizing a bajillion times over resetting. There's no point in resetting everything only to style it again.
* Describe Floats and how they work.
    - The float CSS property places an element on the left or right side of its container, allowing text and inline elements to wrap around it. 
    - float: none;  float: left;  float: right;
* Describe z-index and how stacking context is formed.
    - z-index: the rendering order of certain elements. why? because these elements have special properties which cause them to form a stacking context. a list of scenarios...
    - stacking context hierarchy: root stacking context, stacking context level 1, stacking context level 2, ...
    - Note: The hierarchy of stacking contexts is a subset of the hierarchy of HTML elements because only certain elements create stacking contexts. We can say that elements that do not create their own stacking contexts are assimilated by the parent stacking context. So, it's important to tell if this element is creating a stacking context or not using the scenario lists.
    - Without z-indexes, elements are stacked in order of occurrence (Stacking). the z-index values of its child stacking contexts only have meaning in this parent
* Describe BFC (Block Formatting Context) and how it works. https://zhuanlan.zhihu.com/p/80855885
    - 为盒子准备的一套渲染规则。
    - Floats, overflows establish new block formatting contexts for their contents.
    - 一个BFC包含创建该上下文元素的所有子元素，但不包括创建了新BFC的子元素的内部元素。 (A block formatting context contains everything inside of the element creating it that is not also inside a descendant element that creates a new block formatting context.) 一个元素不能同时存在两个BFC中。
    - BFC features: boxes inside one BFC margin collapse, so to not collapse, create new BFC for one box（Margin collapsing）. 形成了BFC的区域不会与float box重叠（Exclude external floats）. 计算BFC的高度时，浮动子元素也参与计算（Contain internal floats）
    - (green盒子因为浮动原因，脱离normal flow, 如果想要让parent包裹住green，最简单的办法就是给parent盒子构建BFC。因为当我们计算BFC的高度时，浮动子元素也参与计算。这样一来我们就能让parent grey盒子的高度被green盒子撑开了。如何让sibling盒子接受”绿色盒子的存在？我们将红色盒子也构建出BFC，根据特性，形成了BFC的区域不会与float box重叠。于是这里红色盒子成功“接受”了绿色盒子。)
* What are the various clearing techniques and which is appropriate for what context? - use `clear` css property
    - Empty div method - `<div style="clear:both;"></div>`. 
    - Clearfix method - Refer to the .clearfix class above.
    - overflow: auto or overflow: hidden method - Parent will establish a new block formatting context and expand to contains its floated children.
    - In large projects, I would write a utility .clearfix class and use them in places where I need it. overflow: hidden might clip children if the children is taller than the parent and is not very ideal.
* How would you approach fixing browser-specific styling issues?
    - Always build responsive layouts.
    - check features of HTML5 and CSS3, and mdn and see browser support
    - when develop, test across browsers
    - Google Analytics, what browers my audience using
    - Use Reset CSS or Normalize.css, or bootstrap
* How do you serve your pages for feature-constrained browsers?  What techniques/processes do you use?
    - Graceful degradation — The practice of building an application for modern browsers while ensuring it remains functional in older browsers.
    - Progressive enhancement — The practice of building an application for a base level of user experience, but adding functional enhancements when a browser supports it.
    - Use caniuse.com to check for feature support.
* What are the different ways to visually hide content (and make it available only for screen readers)? https://webaim.org/techniques/css/invisiblecontent/
    - display:none or visibility: hidden. These styles will hide content from all users. ...
    - HTML hidden attribute
    - width:0px , height:0px or other 0 pixel sizing techniques (not recommended) ...
    - text-indent: -10000px; ...
    - Absolutely positioning content off-screen. left:-10000px;
    - CSS clip.
* Have you ever used a grid system, and if so, what do you prefer?
    - float -> flex -> grid
* Have you used or implemented media queries or mobile specific layouts/CSS?
    -  key component of responsive design, e.g. a media query can shrink the font size on small devices
    -  TBD
* Are you familiar with styling SVG?
* Can you give an example of an `@media` property other than `screen`?
* What are some of the "gotchas" for writing efficient CSS?
* What are the advantages/disadvantages of using CSS preprocessors?
  * Describe what you like and dislike about the CSS preprocessors you have used.
* How would you implement a web design comp that uses non-standard fonts?
* Explain how a browser determines what elements match a CSS selector.
* Describe pseudo-elements and discuss what they are used for.
* Explain your understanding of the box model and how you would tell the browser in CSS to render your layout in different box models.
* What does ```* { box-sizing: border-box; }``` do? What are its advantages?
* What is the CSS `display` property and can you give a few examples of its use?
* What's the difference between inline and inline-block?
* What's the difference between the "nth-of-type()" and "nth-child()" selectors?
* What's the difference between a relative, fixed, absolute and statically positioned element?
* What existing CSS frameworks have you used locally, or in production? How would you change/improve them?
* Have you used CSS Grid?
* Can you explain the difference between coding a web site to be responsive versus using a mobile-first strategy?
* Have you ever worked with retina graphics? If so, when and what techniques did you use?
* Is there any reason you'd want to use `translate()` instead of *absolute positioning*, or vice-versa? And why?
* How is clearfix css property useful?
* Can you explain the difference between px, em and rem as they relate to font sizing?
* Can you give an example of a pseudo class? Can you provide an example use case for a pseudo class? 
* What is the difference between a block level element and an inline element. Can you provide examples of each type of element?
* What is the difference between CSS Grid and Flexbox? When would you use one over the other?
* CSS Layout 
    - normal flow
    - display: block, inline, flex (1D), grid (2D)
    - float: left, right, none
    - position: static, relative, absolute, fixed, sticky
    - (Table layout, Multiple-column layout)
