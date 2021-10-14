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
* Describe BFC (Block Formatting Context) and how it works.
* What are the various clearing techniques and which is appropriate for what context?
* How would you approach fixing browser-specific styling issues?
* How do you serve your pages for feature-constrained browsers?
  * What techniques/processes do you use?
* What are the different ways to visually hide content (and make it available only for screen readers)?
* Have you ever used a grid system, and if so, what do you prefer?
* Have you used or implemented media queries or mobile specific layouts/CSS?
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
