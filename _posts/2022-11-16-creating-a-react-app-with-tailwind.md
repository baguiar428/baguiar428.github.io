---
layout: post
title: How to bundle TailwindCSS into a new React Project
subtitle: Use TailwindCSS in your React App
cover-img: assets/img/tailwind_logo.jpg
share-img: assets/img/tailwind_blog.jpg
tags: [React, Javascript, TailwindCSS, Tailwind, CSS]
---

**Tailwind sure looks pretty**

I must confess...Up until this point working with grid/flex layout and CSS wasn't clicking. When I saw some TailwindCSS examples though, they were so nice I couldn't help but want to try it out. The talk around town was that it was pretty, but hard to setup and "harder" to use then other solutions like Bootstrap and etc. But if you learn it, it has many advantanges. Upon hearing that..I was sold and determined to dive in and get better with some tools I had struggled with until now. It seems, according to some Googling, that a recent release of React/Create React App didn't play well with Tailwind out-of-the-box but that has been resolved. I am glad I paid my dues because Tailwind is well documented, quick and powerful.

**Using Create React App and Tailwind**

I will be using "Create React App" to initialize the React app and then we will be bundling in Tailwind and other essentials for a modern React app.

First create the React app and then cd into it.

~~~
npx create-react-app my-project
cd my-project
~~~
Then we need to install Tailwind and it's dependencies and then initialize them.

~~~
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p
~~~

The previous step should have generated a Tailwind config file named 'tailwind.config.js' which needs to be edited to reflect the following:

~~~
/** @type {import('tailwindcss').Config} */
module.exports = {
  content: [
    "./src/**/*.{js,jsx,ts,tsx}",
  ],
  theme: {
    extend: {},
  },
  plugins: [],
}
~~~

Once the config file has been configured add the Tailwinds directives to the './src/index.css' file. 

~~~
@tailwind base;
@tailwind components;
@tailwind utilities;
~~~

*You can delete the rest of the code that was previously in the file.*

At this point, Tailwind has been installed but I still had to do some further work to make my app and tailwind workable.

However now is a good time to check that your react app launches. You can do that withthe following command.

~~~
npm run start
~~~

Once you confirm that the base is working you will most likely be using React Router so you can install that.

~~~
npm install react-router-dom@6
~~~

You're almost there. Now you just have to create a folder named 'components' under the /src folder, so you can create your components and you're good to go.

Check out the Tailwinds Documentation site to get started: [Tailwind Docs](https://tailwindcss.com/docs/installation)

I am still learning how to create custom layouts to become a poweruser but Tailwind stands out because you an fine-tune and apply styles directly to elements via declaring them inline. So if you want one specific element to have white text and a green background you just have to do "<element className="text-white bg-green-500">".

There is much to learn and hopefully this gets you started so you have a fun time experimenting.

