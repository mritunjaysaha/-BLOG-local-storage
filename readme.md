---
title: Theme Switching Using Local Storage
date: "2020-05-12T22:12:03.284Z"
description: "Save the theme even after page reload"
---

Suppose we want to store the theme of the website so that the user need not set the theme every time he visits a website like [airqualitymonitor](https://airqualitymonitor.netlify.app). Local storage will help to give a better user experience since the site will not feel buggy.

###How to store the theme?
We will use local storage to store the class name of the themes.

###What is local storage?
Local storage allows us to store only strings. These strings can be class names, JSON objects, etc. We can store the class name say dark for dark theme and light for the light theme. When the user changes the theme, we will store the class name to the local storage. And whenever the user revisits the site, we will load the class name from the local storage and set the last selected theme.

###How to send data to local storage and how to fetch data from local storage?
The local storage stores data in key-value pairs.
Sending data to local storage: localStorage.setItem(“key”,”data”)
Fetching data from local storage: localStorage.getItem(“key”)
There are more commands but we will need only these two for our purpose.

####Let us see how local storage works using a small example.

![example 1](ex1.png)

It will send the data as a string to local storage. And using localStorage.getItem(“key”) we get the value of the key and store it in a variable. And print the data to the console.

The data of a website is stored in local storage and can be seen in Chrome Dev Tools “Application” tab. From the application tab, one can delete the key-value pair.

###How to make the toggle switch?
You can try the following code to implement the theme switch.

####HTML
![ex 2 html](carbon.png)
####JS
![ex 2 js1](ex2js1.png)
####CSS
You can copy the CSS files from [here](https://github.com/mritunjaysaha/-BLOG-local-storage)

Initially, the theme is set to light. If the theme is switched then we will remove the light theme and set it to the dark theme. And update the key (“theme”) in the localStorage using setItem() to "dark". Now a question arises that when the site is refreshed, how will it know that it has to load the dark theme?

![Alt Text](ex2js2.png)

When the window loads checkTheme() function, it will check if the theme key exists in the local storage. If it exists and the value is dark then it will set it to dark.

The end result will look like this

<img src="demo.gif" style="display:block; margin: 0 auto;">

###If the key of your website is the same as the key to some other website?

Suppose we have two files with the same filename if we paste them in the same folder then only the contents of one file will be retained. But if we have two separate folders and we paste one file in say folder A and the other file in folder B, then the contents of both the files will not be altered.

In a similar manner, the key-value pairs of one website are stored in a folder with its domain name.

###If someone wants to store a JSON object in local storage? Will he be able to store the JSON object in localStorage?

Since localStorage can only store strings, we have to convert the JSON object to string using JSON.stringify(object). The syntax would look like:- **localStorage(“key”,JSON.stringify(object));**
