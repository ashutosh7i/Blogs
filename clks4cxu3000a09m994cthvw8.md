---
title: "📝 What is RSS Feed and How I Used It to My Advantage 🌐"
datePublished: Tue Aug 01 2023 09:51:07 GMT+0000 (Coordinated Universal Time)
cuid: clks4cxu3000a09m994cthvw8
slug: what-is-rss-feed-and-how-i-used-it-to-my-advantage
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690883280084/4c488a56-cd95-414f-b797-3f66fd809036.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1690883455117/7693d5d7-b016-4e39-b976-e51a0148fbe2.png
tags: ideas, blogging, rss, cors, rss-parser

---

sit tight, lots of interesting things ahead ✅; let's begin-

### **Introduction to RSS Feed** 📰

RSS (*Rich Site Summary or Really Simple Syndication*) is a standard format used to publish and distribute frequently updated content on the web. It allows websites and blogs to share their content & updates in an organized way, making it a breeze for users and applications to stay up-to-date without the hassle of manually visiting each site.

RSS feeds are usually represented in XML (eXtensible Markup Language) format, which is a human-readable and machine-readable markup language (similar to HTML).XML provides a hierarchical structure to organize data, making it ideal for representing various types of information.

### **How RSS Feed Works** ?🔄

![](https://twistarticle.com/wp-content/uploads/2019/08/What-Is-RSS-Feed-And-How-Does-It-Work-For-News-Update.jpg align="center")

Imagine your favourite blog site, "[**blog.ashutosh7i.dev**](https://blog.ashutosh7i.dev)**😁**", constantly churning out captivating articles. With ***RSS***, this blog site creates a summarized version of each article, along with essential details like the title, link, and cover image. These summarized versions are packed into an XML file known as the RSS feed. It's like a scroll of enchantment, holding all the latest and greatest blog updates in one place.

Now, whenever a new article is published, the RSS feed gets updated automatically. It's as if the blog site sends out a signal to all the RSS subscribers, saying, "Hey, I've got some fresh content for you! Come and take a look!" This signal, represented by the updated RSS feed, allows users and applications to fetch the latest content effortlessly.

**What exactly it looks like🤔?**

(click this to see an RSS feed- [blog.ashutosh7i.dev/rss.xml](https://blog.ashutosh7i.dev/rss.xml))

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690882693390/d0bc75c6-9b69-4bd1-b9b6-c626d6daca2e.png align="center")

### **🌟Now Comes the "I have an Idea🤩!" Moment** 💡

Here's where my lightbulb moment happened💡! As a web developer itching to create something dynamic and exciting for my users, I stumbled upon the incredible power of RSS feeds.

![](https://media.giphy.com/media/UpvAgsFsw0M02f66Ra/giphy.gif align="center")

***"Why not use this fantastic tech to my advantage and create a dynamic component?"*** I thought to myself. And let me tell you, the possibilities were endless🤩🚀!

### **The Dynamic Component!** 🎉

*Picture this:* a beautifully crafted component that automatically updates itself with the latest and greatest blog posts. No more static content or boring pages! Thanks to the magic of RSS feeds, my dynamic component would fetch the freshest content from my blog site, "[**blog.ashutosh7i.dev**](https://blog.ashutosh7i.dev)," and present it on my portfolio in a visually stunning carousel🚀.

### **Fetching, Parsing, and Creating Magic!** ✨

Okay, so let's break down how I pulled off this enchanting feat. First,

I used Express.js and the `HTTP` module to fetch the RSS feed from "[**https://blog.ashutosh7i.dev/rss.xml**](https://blog.ashutosh7i.dev/rss.xml)." Then, I skillfully parsed the XML data using the DOMParser, extracting the blog titles, cover images, and links to each blog post.

With the data in hand, I set out to create my dynamic blog card carousel. The HTML, CSS, and JavaScript trio worked their magic to display the blog cards. As the user landed on my portfolio, they were greeted with a mesmerizing array of Sliding blog cards, each enticing them to explore more with a simple click.

**Fetching the RSS Feed** ➡️ **Parsing XML Data ➡️ Render the Dynamic Component**🚀

also on the latest blog, it shows "Latest" too😁;

### Let's Talk Code-

**Implementation of Dynamic Component** 🚀

here is what I created-

%[https://codepen.io/ashutosh7i/pen/VwVqrZP] 

so theoretically the thing was complete-

![](https://31.media.tumblr.com/tumblr_mcca8gOjgy1qi5jk5o1_500.gif align="center")

{ i too thought this initially😅;; Ever heard of CORS?? I did🥲🥹it was such a P.I.T.A resolving it, I had to create a *reverse proxy* for this, if ever you encounter a CORS error, read this Blog(upcoming) for a solution💖✅}

while trying to parse data from [https://blog.ashutosh7i.dev/rss.xml](https://blog.ashutosh7i.dev/rss.xml) it was giving me CORS policy errors in the code, which is subjected to my Blog Server.  
to overcome this we used [https://ashutosh7i.dev/blog-rss-xml](https://ashutosh7i.dev/blog-rss-xml) this gives the same data as the above url, just without CORS🫡.

### **Other Possibilities with RSS Feed**🌟

The usage of RSS feeds opens up numerous possibilities:

1. **Automated Content Updates**: By using RSS feeds, we can keep our application content updated in real-time without manual intervention. This is particularly beneficial for news websites, blogs, and content-heavy platforms.
    
2. **Content Aggregation**: RSS feeds enable content aggregation from multiple sources, allowing users to view content from various websites in a centralized location.
    
3. **Customized User Experience**: With RSS feeds, users can subscribe to specific topics or authors they are interested in, providing them with a personalized content experience.
    
4. **SEO Benefits**: Utilizing RSS feeds can improve search engine optimization (SEO) as search engines can easily crawl and index updated content.
    

***In conclusion***, *my fondness for older technologies and backend development is driven by their time-tested reliability and the solid foundation they offer🗿. As a fan of these classic tools, I appreciate their* ***simplicity***, ***efficiency***, and ***ability*** *to stand the test of time. Embracing older technologies is not just a* ***nostalgic choice***, *but a strategic one that allows me to focus on crafting elegant solutions and building a future-proof tech ecosystem.*

In a rapidly evolving world, these timeless tools remain a source of inspiration, reminding me of the enduring power of simplicity and the beauty of a well-crafted backend. 💙🔧Happy coding! 🚀✨

![](https://media.giphy.com/media/l44QePXW2Tf2swCru/giphy.gif align="center")

Thank you for reading this far, 💙🔧Happy coding! 🚀✨