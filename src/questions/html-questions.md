---
title: HTML Questions
layout: layouts/page.njk
permalink: /questions/html-questions/index.html
---

https://frontendinterviewhandbook.com/html-questions/#table-of-contents
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
    - more semantic text markup
      new form elements
      vedio and audio
      new javascript API
      canvas and SVG
      new communication API
      geolocation API
      web worker API
      new data storage
* Describe the difference between a `cookie`, `sessionStorage` and `localStorage`.
    - The Web Storage API provides mechanisms by which browsers can store key/value pairs (store Info), in a much more intuitive fashion than using cookies.
    - ![cI5kT](https://user-images.githubusercontent.com/35388473/136591575-2d1a3226-4627-4830-b7f2-ee359a7c8ae9.jpg)

* Describe the difference between `<script>`, `<script async>` and `<script defer>`.
    - client side script, async allows execute script while page continues the parsing, defer tells the browser to only execute the script file once the HTML document has been fully parsed
* Why is it generally a good idea to position CSS `<link>`s between `<head></head>` and JS `<script>`s just before `</body>`? Do you know any exceptions?
    - The main reason as to why JS files are linked at the bottom of the body is because whenever a browser encounters any JS, it parses it and executes that on the spot. Hence if it was to be added at the top, it would make the page rendering slow and thus it would take more time for page load. Moreover since the DOM won't be rendered fully, JS won't be able to manipulate the elements.
    - On the contrary, CSS files are linked in the head because they get applied regardless of DOM already rendered or not. If link the CSS at the end, the CSS load would take considerable amount of time, which means that the webpage shows just the HTML meanwhile. This might make the user close the website without waiting for it to load fully.
    - if you use Jquery, that won't be an issue since it would execute only after the document is ready
* What is progressive rendering?
    - Client Side Rendering: server sends a simple HTML without any content in the body and script tags in the head. Once the scripts are loaded, the browser parses them and makes API requests and loads all the content asynchronously.
    - Server Side Rendering: the whole HTML is rendered on the server and sent to client.
    - PSSR bridges the benefits of both CSR and SSR: https://medium.com/the-thinkmill/progressive-rendering-the-key-to-faster-web-ebfbbece41a4
    - PSSR: once you render the critical content on the server, you start streaming it to the client without waiting for non-critical content.
    - techniques: Lazy loading of images, Prioritizing visible content
* Why you would use a `srcset` attribute in an image tag? Explain the process the browser uses when evaluating the content of this attribute.
    - https://imagekit.io/responsive-images/#chapter-4---srcset
    - responsive images: load the right image based on device resolution and so on.
    - used srcset (source set) to provide the browser with three different size images. The browser picked the right option based on the actual viewport size of the device.
    - density descriptor or width descriptor - This lets the browser pick the best image
    - img width = viewport(screen) width * DPR (Device Pixel Ratio)   
* Have you used different HTML templating languages before?
    - React (JSX)
    - Embedded JavaScript(EJS), Handlebars, Pug, Mustache
* What is the difference between `canvas` and `svg`?
    - Vector Based. The Scalable Vector Graphics (SVG), define two-dimensional vector-based graphics. SVG has better scalability. So it can be printed with high quality at any resolution.
    - Pixel Based. The element is only a container for graphics. draw graphics on the fly, via scripting (usually JavaScript). Canvas has poor scalability. Hence it is not suitable for printing on higher resolution.
* What are empty elements in HTML ?
    - An empty element is an element from HTML, SVG, or MathML that cannot have any child nodes (i.e., nested elements or text nodes).
    - The empty elements are used to embed images, lists, breaks, horizontal lines, hyperlinks, for input, meta-data, area, etc.
    - no closing tag e.g. `</input>`
* 自我补充：DOM and HTML
    - DOM is a model of a document with an associated API for manipulating it. HTML is a markup language that lets you represent a certain kind of DOM in text.
    -  The Document Object Model (DOM) is a language-independent model made up of objects representing the structure of a document. HTML is one language for writing such documents. Other kinds of DOMs can be expressed in other markup languages, for example RSS and Atom can be converted to a DOM and manipulated with the same API as an HTML or XHTML document
    -  The Document Object Model (DOM) is a programming interface for web documents. It represents the page so that programs can change the document structure, style, and content. the DOM specifies that the querySelectorAll method ```const paragraphs = document.querySelectorAll("p");```
    -  The Document interface represents any web page loaded in the browser and serves as an entry point into the web page's content, which is the DOM tree.
