# Learning Node.js

A comprehensive and step-by-step approach to learning back-end service development in Node.js

## Table of contents

- [Disclaimer](#disclaimer)
- [Prerequisite](#prerequisite)
- [Chapter 1 - What is Node](#chapter-1)
  - [In a (nut)shell](#in-a-nutshell)
  - [The event loop](#the-event-loop)
  - [Added features](#added-features)
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

### In a (nut)shell

First, some definitions. Javascript (js) is a programming language. It represents a set of keywords and an estiblished syntax based on the EcmaScript (es) specification. Javascript itself is not an application or a runtime. It needs to be parsed, interpreted and compiled - in realtime- by an engine. Such engines can be found in the form of runtimes or baked in applications like web browsers.

### The event loop

Node.js is an async, event-driven runtime built on top of libuv. It means that instructions from the application do not stall the process while waiting for it to complete. It is mostly written in C++.
To develop on the node runtime means to write programs using the Javascript syntax. The code gets interpreted via V8, Google's Javascript engine; and allows it to interact with libuv's IO methods, which control Network and Storage capabilities, among others.

The javascript syntax is a great fit for async programming. Structures for flow control like callbacks or promises allows applications to be written in a much cleaner and consise way while being fully leveraged by the underlying layer.

Consider this illustration that explains how the event loop works.

### Added features

It's important to understand the difference between Javascript in the browser and Javascript in Node. Browsers have V8 included, which allows them to parse and compile Javascript- the basic set of instructions- plus a set of browser-specific features. For example, DOM is not part of the default Javascript language spec. In the same way, Node includes a set of methods, such as:

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

### Using the REPL

Open a terminal window and type:

`node`

This should enter the REPL mode (Read–Eval–Print Loop), meaning that your terminal now behaves like the interactive console you can find in your browsers. You can enter commands and see them execute in real-time.

Let's try it out. Type the following, then press enter:

`1+1`

On the next line, you will see the result of the operation you entered on the first line (That should equal `2`, if my math is correct)

Now, let's try some *real* Javascript.

    function say_hi(name) { console.log(`Hi, ${name}!`); }
    
This will create a function. The REPL has the ability to retain the result and context of previous commands, so let's try to call that function we just created. You'll notice that the REPL also offers auto-completion/ typing suggestions just like unix shells. 

Next chapter, we'll try to write a script in a .js file and run it in the terminal.

[top](#table-of-contents)

---

## Chapter 3
*Building a script*

Ok, you can now open the code editor of your choice. My personal favorite is [VS Code](https://code.visualstudio.com/).

### Creating a .js file

Create a file named `index.js`

Let's try copying the same function we had in the previous chapter. Put this inside:

    function say_hi(name) { 
        console.log(`Hi, ${name}!`); 
    }
    
    say_hi('John');
    
Once that you have saved the file, you can now execute it by running

`node index.js`

*Make sure that you exited the REPL first*

Running this script should output `Hi, John!` in your console. 

### Exit conditions

You'll notice that, unlike the REPL, the script exits as soon as it reaches the end of the file and that it no longer needs to wait for anything. For example, if we had a timer running, it would prevent it from exiting.

Let try it out:

    function say_hi(name) { 
        console.log(`Hi, ${name}!`); 
    }
    
    setTimeout(() => {
      say_hi('John');
    }, 1000);
    
    console.log('End of the file');
    
When running this script, you'll see that even though the execution thread reached the end of the file, it noticed that a timer was running, and waited for it to finish.

### Exceptions

In Javascript though, there are exceptions... litterally. For instance, if your code has an error or throws an exception, the program will exit- regardless of the current state of things. You can observe it by volontarily inserting an error in our program.

    function say_hi(name) { 
        console.log(`Hi, ${name}!`); 
    }
    
    setTimeout(() => {
      say_hi('John');
    }, 1000);
    
    this.function.does.not.exist();
    
    console.log('End of the file');

You'll notice that we don't reach the end of the file, nor get the message at the end of the timeout- the program just quits.

### Process arguments

Next, we'll want to call our script as if it were a utility, by passing process arguments.

Processing input arguments and environment variables can be done simply, in a fashion similar to how Python does it.

    function say_hi(name) { 
        console.log(`Hi, ${name}!`); 
    }
    
    // Process Arguments ['node', 'index.js', ...]
    say_hi(process.argv[2]);
    
    // Process Environment variables
    say_hi(process.env.USER);
    
Running this script like this:

    node index.js John

Should will push `John` to the array of process arguments `process.argv`, allowing you to use it inside your code. Notice that you can also read from process environement variables from the `process.env` object.

These tools make Node.js a pretty neat language for writing small tools and scripts simply and easily.

[top](#table-of-contents)

---

## Chapter 4
*Modules and dependencies*

Most of the time, you will want to split your code into multiple files, or leverage other people's code in your application. This is where the `module.exports` and `require` statements come into play.

### Modules


### Require


### NPM


[top](#table-of-contents)

---

## Chapter 5
*Web servers, the basics*

As we saw in the previous chapters, scripts only run until they reach the end of the program, or until all timers are completed. There is actually another condition that would prevent a process from naturally ending: It's waiting for communication.

### The HTTP module


[top](#table-of-contents)

---

## Chapter 6
*Express, middlewares and the Rails way*

### Routing

### Express controllers


[top](#table-of-contents)

---

## Chapter 7
*Adding data*

### Setting up Mongo


[top](#table-of-contents)

---

## Chapter 8
*Tests*

### Unit testing

### Integration testing

### Mocha

### Chai


[top](#table-of-contents)

---

## Chapter 9
*Docs and validation*

### Code documentation

### JSDoc

### API Documentation

### Swagger

[top](#table-of-contents)

---

## Chapter 10
*Moving to production*

### Process Daemon

### Clustering

### Reverse Proxying

### Monitoring

### Caching

### SSL

[top](#table-of-contents)

---

## Epilogue
*The Node and the Ecosystem*

### Syntaxes and flavors

### Trustable packages and how to find them

[top](#table-of-contents)

---

## Acknowledgements

The awesome people at [Shutterstock](https://tech.shutterstock.com/) and the gang at Slacker-News for their support and council.

[top](#table-of-contents)

---
