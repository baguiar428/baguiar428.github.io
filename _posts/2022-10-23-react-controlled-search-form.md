---
layout: post
title: Creating a controlled search box in React/JS
subtitle: Guide to setting up a controlled search input in React
cover-img: assets/img/add_search_bar.jpeg
share-img: assets/img/add_search_bar.jpeg
tags: [React, Javascript]
---

**Vanilla JS..Then what?**

After working with vanilla JS it was time to move onto React. I must confess I certainly prefer React..I'm still quite new on this journey to becoming a professional developer but it felt like an important step to recognize how I will need to learn to adapt and look for tools that might fit me better. I hope that evolution will lead to interleaving and make me stronger as I progress even though it feels overwhelming right now.

I really like the idea of declarative programming over imperative programming. With reusable components it also feels like playing with legos. React seems to emphasize that principal and makes coding more enjoyable once you get the syntax and flow down. After you have that down you just have to figure out where you want to put those "lego pieces" in your project.

**My first Lego set - Search**

The concept started to click when I put together the Search feature for a lab/project I was working on. The Search feature involves the use of controlled components. You need to control an input and sync/connect it to a state variable. That way, the program knows what you're typing into the search input as you type it and you can use the filter method to compare it to the dataset you want to search in.

I will be guiding through the creation of a simple search bar for a React S.P.A (single page app).

First you need to create a state variable and import the search component in the lowest common ancestor component (L.C.A). In this case, the L.C.A is usually App.js but can also be named SomethingElse.js

To be able to create a state variable you will need to hook in useState:
![Import useState and Search](assets/img/blog2/usestate_import.png)
