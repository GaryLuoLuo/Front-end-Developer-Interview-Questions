---
title: HTML Questions
layout: layouts/page.njk
permalink: /questions/html-questions/index.html
---

* What does a `doctype` do?
    - All HTML documents must start with a <!DOCTYPE html> declaration. Its sole purpose is to prevent a browser from switching into so-called “quirks mode” when rendering a document, i.e. not following the relevant spec  
    -   https://developer.mozilla.org/en-US/docs/Web/HTML/Quirks_Mode_and_Standards_Mode
    -   https://developer.mozilla.org/en-US/docs/Glossary/Doctype
    -   document.doctype
* How do you serve a page with content in multiple languages?
    - ```<p> French " <span lang="fr"> Bonjour </span> " </p>``` 
    -  Please note that by changing the lang attribute, the visual of the HTML document remains the same. The only difference will be there in the translation of that language.
    -   The only difference is, that the browser will be able to understand or identify that the language of the whole HTML document is either French or English or some other language, and based on that, it will translate the page into your preferred language.
* What kind of things must you be wary of when designing or developing for multilingual sites?
    - not encoding other than UTF-8
    - use lang and dir attributes in HTML (Language reading direction)
    - Don't ever concatenate translated strings. Don't do anything like "The date today is " + date
    - Formatting dates and currencies 
* What are `data-` attributes good for?
    -  store some extra information that doesn't have any visual representation. Just use data attributes.
    -  JS access: get a data attribute through the dataset object, get the property by the part of the attribute name after data- (note that dashes are converted to camelCase). 
        -   ```const article = document.querySelector('#electric-cars'); article.dataset.columns; ```
    -  CSS access: ```content: attr(data-parent);``` or attribute selectors ```article[data-columns='3']```
* Consider HTML5 as an open web platform. What are the building blocks of HTML5?
* Describe the difference between a `cookie`, `sessionStorage` and `localStorage`.
* Describe the difference between `<script>`, `<script async>` and `<script defer>`.
* Why is it generally a good idea to position CSS `<link>`s between `<head></head>` and JS `<script>`s just before `</body>`? Do you know any exceptions?
* What is progressive rendering?
* Why you would use a `srcset` attribute in an image tag? Explain the process the browser uses when evaluating the content of this attribute.
* Have you used different HTML templating languages before?
* What is the difference between `canvas` and `svg`?
* What are empty elements in HTML ?
