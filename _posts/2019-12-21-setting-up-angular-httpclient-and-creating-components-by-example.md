---
layout: post
title:  "Setting up Angular 9 HttpClient & Creating Components by Example"
date:   2019-12-21
---

In the previous steps of our Angular 9 tutorial, we've created an example project using Angular CLI. We'll now see how to import and set up HttpClient in our project and we'll also create the components that compose the UI.

- Tutorial Step 3 — Importing Angular HttpClient in your Angular 9 Project
- Tutorial Step 4 — Generating your App Components


##  Tutorial Step 3 — Importing Angular HttpClient in your Angular 9 Project


In this step, we’ll import `HttpClient`  in our Angular project.

HttpClient is a builtin Angular service but doesn't get included in the project by default so you'll need to import it by yourself. 

This can be easily done by importing [HttpClientModule](https://angular.io/api/common/http/HttpClientModule#description)  and add it to the module where you want to use it. At this step, we have only one module - the application module so we'll import HttpClient in that module.
  
Open the `src/app/app.module.ts`  file and update it as follows:

```ts
import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';

import { AppRoutingModule } from './app-routing.module';
import { AppComponent } from './app.component';
import { HttpClientModule } from '@angular/common/http';

@NgModule({
  declarations: [
    AppComponent,
  ],
  imports: [
    BrowserModule,
    AppRoutingModule,
    HttpClientModule
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
```


This is all what you need to do to become ready to send HTTP requests with HttpClient in your app.

If you manage to get this step working, you are ready for the next step!

## Tutorial Step 4 — Generating your App Components

In this step, we'll proceed to create our app components.

In modern frontend frameworks, you build your app using components.

A component is piece of code that controls a part of the UI or a complete view.

Our project already comes with one component - the `App` component, it's called the root component and it's the parent of every component that will be added to our app.

But we need a couple of more components for displaying the home and about views of our app.

### Generating the Home Component

Since we have started our development server in the previous command-line interface, leave it running and open a new terminal then run the following commands:

```bash
$ cd ~/first-angular-app  
$ ng generate component home

```

You'll get a bunch of files with the necessary code for a basic component:

- `src/app/home/home.component.html`   
- `src/app/home/home.component.spec.ts`   
- `src/app/home/home.component.ts`   
- `src/app/home/home.component.css`  

A component needs to be "declared" in a module. You'll notice that our home component is automatically added by Angular CLI to app module in the `declarations` array. That's nice! 

Now how can we see this component (even if it's almost blank except from some boilerplate text that says **It works!**)? 

We have tow ways:

- Include the component inside the template of the `App` component using its selector (You'll find it inside the `selector` property of the `@Component` decorator in the `src/app/home/home.component.ts` file). 
- The previous method will make the component always render but we don't actually want that! We want to the component to be associed with a unique URL path and view -- here comes the role of the Angular Router which we'll see how to configure in the next steps.  
 
### Generating the About Component 

Head back to your command-line interface and run the following command to generate the about component:

```bash
$ ng generate component about
```

Let's also add some text in the template of this component. Open the `src/app/about/about.component.html`  file and add this HTML markup:

```html
<p style="padding: 20px;"> Your first Angular 9 app! </p>
```

This component will be associated with the about view using the Anguar Router.

If you managed to create the two components, you are ready for the next step(s)!

## Wrap-up

In this tutorial, we've setup Angular HttpClient in our example and created the home and about components for representing the home and about views of our application which will be done using the router. We'll see this in the next part. 

