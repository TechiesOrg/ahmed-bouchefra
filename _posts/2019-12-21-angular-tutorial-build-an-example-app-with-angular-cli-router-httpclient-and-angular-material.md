---
layout: post
title:  "Angular 9 Tutorial: Build an Example App with Angular CLI, Angular Router, HttpClient & Angular Material"
date:   2019-12-21
---

Throughout this Angular 9 tutorial, we’ll learn to build an example web application using APIs like HttpClient, Angular Router, and Material Design.

We'll learn to generate components and services using Angular CLI and depoly your final app to the cloud (Firebase).

This is what you'll learn by following this tutorial:

-   You'll learn to create a fake but completely working REST API server from a JSON file using json-server,
-   You'll learn install Angular CLI v9 in your development machine,
-   You'll learn to generate a new Angular 9 project,
-   You'll learn to fetch data from the REST API by sending HTTP requests using `Angular Httplient`
-   You'll learn to handle HTTP errors using various RxJS methods like `throwError()`  and `catchError()`,
-   You'll learn to retry HTTP requests that fails in weak network conditions and cancel pending requests using various RxJS methods such as `retry()`  and `takeUntil()`, 
-   You'll learn generate Angular components and services and wire them together to create a working frontend application,
-   You'll learn to add routing to your app to create multiple views and set up Angular Material to design a professional UI,
-   You'll learn to deploy the final application bundles to Firebase hosting using the `ng deploy`  command introduced in Angular 8.3+.

These are the steps of this tutorial:
  
-   Tutorial step 1 — Setting up Angular CLI 9 in your Development Machine
-   Tutorial step 2 — Initializing your Angular 9 Project Using Angular CLI v9
-   Tutorial step 3 — Importing Angular HttpClient in your Angular 9 Project
-   Tutorial step 4 — Generating your App Components
-   Tutorial step 5 — Setting up Routing in your Anguar 9 Project
-   Tutorial step 6 — Styling the UI with Angular 9 Material Components
-   Tutorial step 7 — Simulating a Fully-Working REST API Using JSON-server
-   Tutorial step 8 — Sending HTTP Requests with Angular 9 HttpClient
-   Tutorial step 9 — Handling HTTP Errors in your App
-   Tutorial step 10 — Implementing Pagination in your App
-   Tutorial step 11 — Building the Production Bundles and Deploying your Angular App to Firebase

The tutorial is divided into the following parts:

- [Setting up Angular 9 HttpClient & Creating Components by Example](https://www.shabang.dev/setting-up-angular-httpclient-and-creating-components-by-example/): In the previous steps of our Angular 9 tutorial, we’ve created an example project using Angular CLI. We’ll now see how to import and set up HttpClient in our project and we’ll also create the components that compose the UI.    
- [Adding Angular 9 Routing and Material Design by Example](https://www.shabang.dev/adding-angular-routing-and-material-design-by-example/): In these steps of our Angular 9 tutorial, we’ll continue building our example app by setting up the router and adding routing for the home and about components. Next, we set up Angular Material in our project and use Material components such as MatToolbar, MatIcon, MatCard, MatButton, and MatProgressSpinner to style the UI of our app.
- [Building and Consuming a REST API with Angular 9: Sending GET Requests with HttpClient and Services by Example](https://www.shabang.dev/building-and-consuming-a-rest-api-with-angular-sending-get-requests-with-httpclient-and-services-by-example/): In this part of our Angular 9 tutorial, we’ll build a fake REST API backend for our Angular frontend using json-server and faker.js and next we’ll see how to create a service to send GET requests to our backend to fetch and consume data which will be rendered in the home components using the ngFor and ngIf directives.
 
 
As always let's start with the prerequisites!

> **Note**: you can download our  [Angular 8 Book: Build your first web apps with Angular 8](https://leanpub.com/practical-angular) for free.

## What are the Prerequisites of this Tutorial?

Before proceeding with this tutorial, you'll need to make sure you have the following prerequisites:

-   Famiiarity with TypeScript. TS is a super-set of JavaScrit that adds features like strong types and OOP concepts to the language and gets eventually compiled to JavaScript before it can be executed by the web browser.
-   **Node 8.9+**  and **NPM 5.5.1+**  installed on your system. Node is required by the Angular CLI but not your frontend app since it's a server-side technology . You can go to  [the official website](https://nodejs.org/downloads)  and download the binaries for your target system. You can also use the [Node Version Manager](https://github.com/nvm-sh/nvm)  for quickly installing and working with multiple Node.js versions in your development machine.

If you have the prerequisites, let's go ahead and dive into the steps to build an Angular 9 application that fetches data from a REST API server using Angular HttpClient and display them using Material Design. 

##  Tutorial Step 1 — Setting up Angular CLI 9 in your Development Machine

In this step, we'll set up Angular CLI v9 in our development machine.

Angular CLI is built on top of Node.js so as mentionned before make sure you have it installed on your machine together with npm.

[Angular CLI](https://cli.angular.io/)  is the official tool for initializing and working with Angular projects. 

Open a new command-line interface and run the following command:

```bash
$ npm install -g @angular/cli

```

At the time of writing this tutorial, **angular/cli v9.0.0**  gets installed on our development machine.

If you manage to get this step working, congratulations, you are ready for the next step.

## Tutorial Step 2 — Initializing your Angular 9 Project Using Angular CLI v9

In this step, we’ll create a new Angular 9 with Angular CLI.

Head back to your command-line interface and run the following commands:

```bash
$ cd ~  
$ ng new first-angular-app

```

The CLI will prompt you if **You would like to add Angular routing.**  Say Yes and  **which stylesheet format you would like to use.**  Choose  **CSS**.

Angular CLI will set up a fully-working project with the necessary files and dependencies. No need to do complex configurations by yourself! All you need is to focus on your specific project requirements.

Navigate to your project's folder and serve your app locally using a development server as follows

```bash
$ cd first-angular-app  
$ ng serve

```

Your web application will be available from the [http://localhost:4200/](http://localhost:4200/)  address.

Go to web browser and navigate to the `http://localhost:4200/`  address to start playing with your web app. 

If you are able to get your Angular app running in a web browser without any errors, congratulations you are ready for the next step.

## Wrap-up

In these first two steps of our tutorial, we have seen the prerequisites needed for building our example app with Angular 9 such as the knowledge of TypeScript, Node.js and NPM installed on your development machine. Next, we have installed Angular CLI v9 from npm in our machine using the `npm install @angular/cli@next` command, initialized a new project and served it locally using a live-reload development server.   

In the next step(s), we'll continue buiding our example app by setting up HttpClient
