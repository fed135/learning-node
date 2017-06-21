# Learning Node.js

A comprehensive and step-by-step approach to learning back-end service development in Node.js

## Table of contents

- [Disclaimer](#disclaimer)
- [Requirements](#requirements)
- [Chapter 1 - What is Node](#chapter-1)
  - ...
- [Chapter 2 - Running Javascript in the terminal](#chapter-2)
  - ...
- [Chapter 3 - Building a script](#chapter-3)
  - ...
- [Chapter 4 - Modules and dependencies](#chapter-4)
  - ...
- [Chapter 5 - Web servers, the basics](#chapter-5)
  - ...
- [Chapter 6 - Express, middlewares and the Rails way](#chapter-6)
  - ...
- [Chapter 7 - Adding data](#chapter-7)
  - ...
- [Chapter 8 - Tests](#chapter-8)
  - ...
- [Chapter 9 - Docs and validation](#chapter-9)
  - ...
- [Chapter 10 - Moving to production](#chapter-10)
  - ...
- [Epilogue](#epilogue)
- [Acknowledgements](#acknowledgements)

#### Disclaimer

> This is a work in progress. Feel free to contribute!
>
> I'm not a great writer (and English isn't my mother tongue). I appreciate pointers or corrections.
>
> I've been doing Node.js professionnaly for 5+ years and have been in software development for ~12 years, yet I don't claim to know everything. Furthermore, mentorship is somewhat new to me. Input, wether it be technical or in my approach is always welcomed.


#### Prerequisite

- Familiarity with the Javascript language 
  * Reference [eloquent-javascript](http://eloquentjavascript.net/) Chapters 1-10
- Understanding of web technologies
  * Reference [eloquent-javascript](http://eloquentjavascript.net/) Chapters 17
- Having a CLI environement set-up
  * Windows : Try [cmder](http://cmder.net/) or use the default CMD application
  * Mac : Launch the terminal application
  * Linux : Launch the terminal application
- Knowledge of Git source control and have Git installed
  * Reference [Git setup](https://help.github.com/articles/set-up-git/)
- Having Node.js installed
  * Reference [Node.js](https://nodejs.org)
  
The exercices will use the syntax and features of Node 4+


## Chapter 1
*What is Node ?*

### In a nut(shell)

First, some definitions. Javascript (js) is a programming language. It represents a set of keywords and an estiblished syntax based on the EcmaScript (es) specification. Javascript itself is not an application or a runtime. It needs to be parsed, interpreted and compiled - in realtime- by an engine. Such engines can be found in the form of runtimes or baked in applications like web browsers.

### The event loop

Node.js is an async, event-driven runtime built on top of libuv. It means that instructions from the application do not stall the process while waiting for it to complete. It is mostly written in C++.
To develop on the node runtime means to write programs using the Javascript syntax. The code gets interpreted via V8, Google's Javascript engine; and allows it to interact with libuv's IO methods, which control Network and Storage capabilities, among others.

The javascript syntax is a great fit for async programming. Structures for flow control like callbacks or promises allows applications to be written in a much cleaner and consise way while being fully leveraged by the underlying layer.

Consider this illustration that explains how the event loop works.

### Added features

It's important to understand the difference between Javascript in the browser and Javascript in Node. Browsers have V8 included, which allows them to parse and compile Javascript- the basic set of instructions- plus a set of browser-specific features. For example, DOM is not part of the default Javascript language spec. In the same way, Node includes a set of methods for FileSystem or process management which are not part of the es spec.

- Buffers
- C++ Addons
- Child Processes
- Crypto
- DNS
- Domains
- Filesystem
- Globals
- HTTP/HTTPS Client or Server
- Modules
- Low-level sockets (IPC, TCP, UDP)
- OS info
- Path utils
- Process utils
- Streams
- TLS/SSL
- Compression
- ...and [much more](https://nodejs.org/dist/latest-v8.x/docs/api)!

[top](#table-of-contents)

---

## Chapter 2
*Running Javascript in the terminal*


[top](#table-of-contents)

---

## Chapter 3
*Building a script*


[top](#table-of-contents)

---

## Chapter 4
*Modules and dependencies*


[top](#table-of-contents)

---

## Chapter 5
*Web servers, the basics*


[top](#table-of-contents)

---

## Chapter 6
*Express, middlewares and the Rails way*


[top](#table-of-contents)

---

## Chapter 7
*Adding data*


[top](#table-of-contents)

---

## Chapter 8
*Tests*


[top](#table-of-contents)

---

## Chapter 9
*Docs and validation*


[top](#table-of-contents)

---

## Chapter 10
*Moving to production*


[top](#table-of-contents)

---

## Epilogue
*The Node and the Ecosystem*


[top](#table-of-contents)

---

## Acknowledgements



[top](#table-of-contents)

---
