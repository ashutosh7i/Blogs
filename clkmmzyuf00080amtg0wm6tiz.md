---
title: "All you need to Know about HTML"
datePublished: Fri Jul 28 2023 13:46:18 GMT+0000 (Coordinated Universal Time)
cuid: clkmmzyuf00080amtg0wm6tiz
slug: all-you-need-to-know-about-html
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690563134899/f5cd6db6-3f1c-4632-a70a-d00698e0317f.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1690563225111/7db5a008-6706-4efc-972f-3fcd58eda94b.png
tags: web-development, html, html5, frontend-development, html-tags

---

This Blog/Documentation contains everything you need to know about HTML, Either you are a beginner starting with HTML or a Seasoned Developer, this blog got you covered🚀✨

Before this Go through this [Blog](https://blog.ashutosh7i.dev/supercharge-your-coding-experience-with-visual-studio-code) for VsCode Setup

Let's Begin 🚀✨

## What is HTML?🌐

HTML stands for Hyper Text Markup Language, it is the standard markup language for creating Web pages.📄

HTML describes the structure of a Web page HTML tells the browser how to display the content on Web page. 🌐🎨

### How HTML looks? 🎨

(This is a basic HTML Boilerplate)

```xml
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>HTML 5 Boilerplate</title>
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <script src="index.js"></script>
    <!--This is a comment. -->
    <h1>Jessy, Wanna Cook?🍳</h1>
    <img
      src="https://media.vanityfair.com/photos/53f0fd829b1e228549e7ba22/1:1/w_800%2Cc_limit/you-wanna-cook-crystal-meth.gif"
      alt="Failed"
    />
  </body>
</html>
```

%[https://codepen.io/ashutosh7i/pen/dyQQPxP] 

This code represents a basic HTML document that includes an external CSS file and a JavaScript file. It has the following sections:

1. 📋`<!DOCTYPE html>` declares that this is an HTML5 document.
    
2. 🌐The `<html>` tag is the root element of the document, and the `lang` attribute specifies the language as "en" (English).
    
3. 📄The `<head>` section contains metadata about the document, such as character encoding, viewport settings, and the page title.
    
4. 🔤Character Encoding: `<meta charset="UTF-8" />` specifies that the document is encoded in UTF-8 to support various characters.
    
5. 🖥️Viewport Settings: `<meta name="viewport" content="width=device-width, initial-scale=1.0" />` sets the initial scale and width of the page to adapt to different device screens.
    
6. 🌐Compatibility: `<meta http-equiv="X-UA-Compatible" content="ie=edge" />` indicates that the document should be rendered using the latest version of Internet Explorer's rendering engine.
    
7. 📝Title: `<title>HTML 5 Boilerplate</title>` sets the title of the web page, which is displayed in the browser's title bar or tab.
    
8. 🎨External CSS: `<link rel="stylesheet" href="style.css" />` links an external CSS file named "style.css" to style the content of the page.
    
9. 👀Body Section: The `<body>` tag contains the visible content of the web page.
    
10. 💡JavaScript: `<script src="index.js"></script>` includes an external JavaScript file named "index.js" to add interactive behavior to the page.
    
11. 💬Comment: `<!--This is a comment. -->` is an HTML comment, which won't be displayed on the web page but can be used for documenting the code.
    
12. 📚Heading: `<h1>Jessy, Wanna Cook?</h1>` displays a level 1 heading with the text "Jessy, Wanna Cook?".
    
13. 🖼️Image: `<img src="..." alt="Failed" />` inserts an image into the page with the specified source URL and an alternative text "Failed" that will be shown if the image cannot be loaded.
    

### Page Structure-

![HTML PAGE STRUCTURE AND NESTING | QA Tech Hub](https://qatechhub.com/wp-content/uploads/2016/09/BasicHtmlStructure.png align="center")

---

## HTML Tags🏷️ and Their Usage

HTML is a versatile language with a wide range of tags to structure content and create interactive web pages. Understanding these tags is essential for building well-formatted and accessible websites. Let's explore some of the most commonly used HTML tags:

### 1\. `<h1>`, `<h2>`, ..., `<h6>`📑

Headings are used to create different levels of headings on a web page, with `<h1>` being the highest level and `<h6>` the lowest. They are useful for dividing content into sections and creating a hierarchical structure.

Example:

%[https://codepen.io/ashutosh7i/pen/zYMMKrR] 

### 2\. `<p>`📝

The `<p>` tag represents a paragraph of text. It is used to structure and separate blocks of text within the content.

Example:

```html
<p>This is a paragraph of text.</p>
<p>Another paragraph here.</p>
```

### 3\. `<a>`🔗

The `<a>` tag creates hyperlinks, allowing users to navigate to other web pages or resources. The `href` attribute specifies the URL of the linked page.

Example:

```html
<a href="https://www.example.com">Visit Example Website</a>
```

### 4\. `<img>`🖼️

The `<img>` tag embeds images on a web page. The `src` attribute specifies the image URL, and the `alt` attribute provides alternative text that describes the image for accessibility.

Example:

```html
<img src="image.jpg" alt="A beautiful landscape">
```

### 5\. `<ul>`, `<ol>`, and `<li>` 📃

These tags are used to create lists on a web page. `<ul>` represents an unordered (bullet-point) list, `<ol>` represents an ordered (numbered) list, and `<li>` defines list items.

Example:

%[https://codepen.io/ashutosh7i/pen/poQQEye] 

### 6\. `<div>` and `<span>`📦

The `<div>` tag is a block-level container used to group elements together, while the `<span>` tag is an inline-level container used to apply styles to specific parts of text.

Example:

%[https://codepen.io/ashutosh7i/pen/LYXXRNg] 

### 7\. `<table>`, `<tr>`, `<th>`, and `<td>` 🗃️

These tags are used to create tables for organizing tabular data. `<table>` defines the table, `<tr>` represents table rows, `<th>` represents table headers, and `<td>` represents table cells.

Example:

%[https://codepen.io/ashutosh7i/pen/MWzzjeo] 

### 8\. `<form>`, `<input>`, and `<button>` 📝

The `<form>` tag is used to create interactive forms for user input. `<input>` elements inside the form define input fields, and `<button>` elements represent buttons.

Example:

%[https://codepen.io/ashutosh7i/pen/abQQmBK] 

### 9\. `<iframe>` 🖼️

The `<iframe>` tag embeds an inline frame that can display content from another web page within the current page.

Example:

```html
<iframe src="https://www.example.com"></iframe>
```

### 10\. `<audio>`🎵 and `<video>`🎥

These tags allow embedding audio and video content on a web page.

Example:

%[https://codepen.io/ashutosh7i/pen/mdQQrMd] 

### 🌟Other important HTML concepts-

### **1\. Semantic HTML**🌐:

Semantic HTML involves using tags that carry meaningful information about the structure of the content. Instead of just using generic div containers for layout, you can use semantic elements like `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<footer>`, etc., to give your web page a clear and meaningful structure. Semantic HTML enhances accessibility and makes it easier for search engines to understand the content.

Example:

```xml
<html>
<header>
  <h1>Website Name 🏠</h1>
  <nav>
    <ul>
      <li><a href="#home">Home 🏡</a></li>
      <li><a href="#about">About ℹ️</a></li>
      <li><a href="#contact">Contact 📞</a></li>
    </ul>
  </nav>
</header>
<main>
  <section id="about">
    <h2>About Us ℹ️</h2>
    <p>...</p>
  </section>
  <section id="contact">
    <h2>Contact Us 📞</h2>
    <p>...</p>
  </section>
</main>
<footer>
  <p>© 2023 Your Company. All rights reserved. 📅</p>
</footer>
</html>
```

### **2\. HTML Data Attributes**🔍:

HTML data attributes allow you to store custom data private to the page or application. They start with `data-` followed by your chosen attribute name. Data attributes are useful for storing additional information for JavaScript or CSS to interact with.

Example:

```xml
<div data-id="123" data-category="product">Product Card 🛍️</div>
```

### **3\. Importance of Proper HTML Usage**⚙️:

Using HTML tags correctly and employing semantic elements and forms has several significant benefits:

* **Accessibility:** Properly structured HTML using semantic elements improves website accessibility for people using assistive technologies, such as screen readers.
    
* **Search Engine Optimization (SEO):** Search engines use the structure of your HTML to understand the content and relevance of your web pages, improving your website's search rankings.
    
* **Code Maintainability:** Semantic HTML provides a more logical and organized structure, making it easier for developers to maintain and update the codebase.
    
* **Compatibility:** Writing clean, valid HTML ensures that your website renders correctly across different browsers and devices.
    
* **User Experience:** Well-designed forms enhance the user experience by providing clear input fields and validation messages.
    

### **4\. HTML Validation**✔️:

To ensure your HTML code is error-free and adheres to the standard syntax, you can use online validators like the W3C Markup Validation Service. These validators help identify and fix any HTML errors, leading to a more robust and reliable website.

---

In this blog, we covered some of the fundamental HTML tags used for structuring content and creating interactive elements on a web page. As you continue to learn HTML, remember that there are many more tags and attributes available, each serving specific purposes. With practice, you'll become more proficient in using them to build dynamic and engaging web pages.

Stay curious and keep experimenting with HTML to unleash its full potential in web development. Happy coding! 🚀✨