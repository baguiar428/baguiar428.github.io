---
layout: post
title: Using Routes with React Router 6
subtitle: Guide to setting React Router 6 and configuring routes
cover-img: /assets/img/react_router.png
share-img: /assets/img/react_router.png
tags: [React, React Router, Routes, Javascript]
---

What is React Router and why do I need it?
React Router is a standard library for routing in React. It enables the navigation among views of various components in a React Application, allows changing the browser URL, and keeps the UI in sync with the URL. Essentially it lets you set up the different routes (or pages) of your website and lets you link between them. The objective is to go from https://www.yourwebsite.com to https://www.yourwebsite.com/login and etc. That is a very critical functionality. There are 2 major versions of React Router being used at the moment. Version 5.x and 6.x. We will be looking at 6.x because who doesn't like playing with the newest and shinest toys?

To start you will need to create a React app, or be working in a current project. As a quick refresher to create a React app you would use the following command using "Create React App":
~~~
npx create-react-app your-app-name
~~~
Afterwards, you would cd into your project folder.

Once you are inside your project you can start by installing React Router. To install the latest version (6.x) you run the following command:
~~~
npm install react-router-dom@6
~~~

In the next step we will be making React Router available to the whole application by editing the **index.js** file. You should see the following code in the file:
~~~
ReactDOM.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>,
  document.getElementById('root')
);
~~~
Replace React.StrictMode with BrowserRouter and make sure it is imported into the app.
~~~
import { BrowserRouter } from "react-router-dom";

ReactDOM.render(
  <BrowserRouter>
    <App />
  </BrowserRouter>,
  document.getElementById("root")
);
~~~
The above edit will let us use React Router throughout the whole application.

Now to the fun part. Create a folder called **components** so we have some pages to route to. Some examples would be **home and about**.

Once your components are ready we can Route them by editing the **App** component to look like the following which imports Routes and Route and sets up the routes.
~~~
import { Routes, Route } from "react-router-dom"
import Home from "./Home"
import About from "./About"
import Contact from "./Contact"

function App() {
  return (
    <div className="App">
      <Routes>
        <Route path="/" element={ <Home/> } />
        <Route path="about" element={ <About/> } />
      </Routes>
    </div>
  )
}

export default App
~~~

Now that we have the routes defined in the App component. We need **"useNavigate"** inside our components actually use the links. First import , useNavigate into the component, then create a function for the link you want and then you can call the function via onClick. The example below established a link to the About page from Home, based off teh route defined in App.
~~~
import React from 'react';
import {useNavigate} from "react-router-dom";

function Home() {

  const navigate = useNavigate();

  function about() {
    navigate('/about');
  }
  ...
    <div>
      <a onClick={about}>"Something Clickable that goes to About"</a>
    </div>
~~~

**Final Thoughts**
React Router is essential for a modern application and is relatively quick to get started with. I hope my guide helped demystify it for you and will get you started on your path to having fun with React.