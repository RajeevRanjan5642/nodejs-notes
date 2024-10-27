# nodejs-notes

## What is NodeJS?
- Ryan Dahl developed NodeJS by embedding V8 engine with C++.
- NodeJS is a runtime environment for JavaScript.
- It allows us to execute JavaScript outside browser.
- Now, JavaScript can talk to native machine because of C++.
- Can create web servers in JavaScript language.
- It is open-source and cross-platform.
- Doesn't support DOM manipulation.
- NodeJS is built on Google Chrome's V8 engine and is used to develop I/O intensive web applications such as video streaming sites, single page applications, online chat applications etc.
- V8 Engine is responsible for compiling and executing JavaScript code.

## NodeJS Architecture
- NodeJS is based on single threaded Event Loop architecture which allows nodeJS to handle multiple concurrent client requests.

- Workflow:
  - The incoming client requests are queued in the Event Queue.
  - The requests from Event Queue are sent to the Event Loop one by one in the FIFO manner.
  - Requests may be blocking or non-blocking.
  - The non-blocking requests are processed by the Event Loop itself and the response is sent to the client.
  - The blocking requests are sent to the Thread Pool where a thread is assigned to each blocking request (no. of threads are limited usually 4) to process it by accessing external resources such as database, file system, compute etc.
  - After processing the request, the response is sent to the Event Loop which in turn sends the response to client.

## How to create an http server?

    const http = require('http');

    const server = http.createServer((req,res)=>{
      res.end("Hello from server !!");
    });
    const port = 8000;
    server.listen(port,()=>{
      console.log(`The server is running at port ${port}`);
    })

## URL
- URL stands for Uniform Resource Locator.
- protocol-domain-pathname-query
- req.url gives the path.
- If you want to parse your request url, you need to import url package.

      const url = require('url')
      const myUrl = url.parse(req.url,true)

## HTTP Methods
- GET : used to retrieve some data from the server.
- POST : used to send some data to the server.
- PUT : Replaces the entire resource with the new one provided in the rquest.If the resource doesn't exist, it can create it.
- PATCH : Partially updates the resource. It only changes the fields provided in the request, leaving the rest unchanged.
- DELETE : deletes the specified resource.

## Express
- A fast and minimalist web framework for Node.js.
- There's a lot of built-in things in Express.
- It makes our code look clean and readable.
- It makes the developer job a bit easy.

- ### How to build an Express App

      const express = require('express');
      const app = express();

      app.get('/',(req,res)=>{
          res.send('Hello from express app !!');
      });

      const port = 8000;
      app.listen(port,()=>{
          console.log(`Server is listening at port ${port}`);
      })

## How Versioning Works in NodeJS?

4.18.3 -> major.minor.patch

- major : major/breaking update
- minor : new features or critical security fixes (recommended), backward compatible
- patch : bug fixes (optional), backward compatible

- ### Version Modifiers (^,~)
  
  - ^: This allows the automatic installation of all future minor and patch versions without changing the major version. for e.g. "lodash":"^4.17.5". This configuration permits updates to any 4.x.x version up to, but not including , 5.0.0.
    
  - ~: This is more restrictive, allowing only patch updates within a minor version.
 
## What is REST API?

Rules/Standards

1. It is based on Client-Server Architecture. Client and server are different entities and work in isolation.
2. Always respect all HTTP methods. Use the appropriate method to handle requests. 





