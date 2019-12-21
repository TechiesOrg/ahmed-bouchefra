---
layout: post
title:  "Adding Angular 9 Routing and Material Design by Example"
date:   2019-12-21
---

In these steps of our Angular 9 tutorial, we'll continue building our example app by setting up the router and adding routing for the home and about components. Next, we set up Angular Material in our project and use Material components such as `MatToolbar`, `MatIcon`, `MatCard`, `MatButton`, and  `MatProgressSpinner` to style the UI of our app. 

We'll see how to use the router properties of each route such as `path`, `pathMatch`, `redirectTo` and `component` to create routes for associating components with URL paths. And the `routerLink` directive to create navigation links. This will allow us to create an app with multiple views.

These are the steps of this part:

- Tutorial Step 5 — Setting up Routing in your Anguar 9 Project
- Tutorial Step 6 — Styling the UI with Angular 9 Material Components

Let's get started!

## Tutorial Step 5 — Setting up Routing in your Anguar 9 Project

In this step, we’ll learn how to add routing to our example application. This will alllow us to map or associate our home and about components to specific URL paths i.e `/home` and `/about`.

This will allow us to create an app with multiple views.

Fortunatly for us, routing was already set up by Angular CLI when the project was generated. If you look inside your project's folder, you'll find the `src/app/app-routing.module.ts`  file which contains the routing module with an empty  `routes` array.

What you need to do is to simply add routes to your component inside the `routes` array as follows:

```ts
import { NgModule } from '@angular/core';
import { Routes, RouterModule } from '@angular/router';
import { HomeComponent } from './home/home.component';
import { AboutComponent } from './about/about.component';


const routes: Routes = [
  { path: '', redirectTo: 'home', pathMatch: 'full'},
  { path: 'home', component: HomeComponent },
  { path: 'about', component: AboutComponent },
];

@NgModule({
  imports: [RouterModule.forRoot(routes)],
  exports: [RouterModule]
})
export class AppRoutingModule { }
```

A route is a JavaScript object that has some properties such as `path`, `pathMatch`, `redirectTo` and `component`:

- `path` contains the path segment of the URL of the route,
- `pathMatch` specifies how the router should match the path,
- `redirectTo` specifies the path to redirect to,
- `component` specifies the component to associate with a specific path 

There are other properties and not all of them need be present in each route. Most of the times, it's the `path` and `component` pairs that exist in a route.

In our example, we associated the home path with the `HomeComponent` and about with `AboutComponent` and we added a redirection route that redirects the empty path to `home` path so when users first land in our app via the main URL they will be redirected to the home view where they can find something useful.

That’s it! If you have successfully managed to add routing to your app , you already have a working web app and you are ready for the next step!

## Tutorial Step 6 — Styling the UI with Angular 9 Material Components: `MatToolbar`, `MatIcon`, `MatCard`, `MatButton`, and  `MatProgressSpinner` 

In this step, we’ll learn to set up  [Angular Material](https://material.angular.io/)  in our project and build our application UI using Material Design components.

Head back to your command-line interface and run the following command:

```bash
$ ng add @angular/material
```

Make sure the command is executed from the root folder of your project not a sub-folder.

The command will prompt to pick a theme, simply go with  **Indigo/Pink**.

You'll also be prompted if you would like to  **set up HammerJS for gesture recognition**  and to  **set up browser animations for Angular Material**  - Just pick the default answers.

That's it! Wait for the command to install the necessaru dependencies from npm and set up Angular Material in your project.

### Importing Material Components: `MatToolbar`, `MatIcon`, `MatCard`, `MatButton`, and  `MatProgressSpinner` 

Next, before you can use any Material Design component, you'll need to import it to your project.

This can be achieved by creating a seprate module and import your needed Material components in it then you'll need to import that module itself into the main app module of our app. Or you can also directly import the components into the app module which is fine for small examples. Let's go with this seconf choice!
    
Go to the `src/app/app.module.ts`  file and add the following imports:

```ts
import { MatToolbarModule,
  MatIconModule,
  MatCardModule,
  MatButtonModule,
  MatProgressSpinnerModule } from '@angular/material';

```


Next, you need to include these modules in the `imports`  array of `@NgModule` as follows:

```ts
@NgModule({
  declarations: [
    AppComponent,
    HomeComponent,
    AboutComponent
  ],
  imports: [
    BrowserModule,
    AppRoutingModule,
    HttpClientModule,
    BrowserAnimationsModule,
    MatToolbarModule,
    MatIconModule,
    MatButtonModule,
    MatCardModule,
    MatProgressSpinnerModule
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }

```
> Note that we are actually importing the modules containing the components not the components themselves.

By importing these modules, you'll be able to use the following Material Design components:

-   [MatToolbar](https://material.angular.io/components/toolbar/overview)  that provides a container for headers, titles, or actions.
-   [MatCard](https://material.angular.io/components/card/overview)  that provides a content container for text, photos, and actions in the context of a single subject.
-   [MatButton](https://material.angular.io/components/button/overview)  that provides a native `<button>`  or `<a>`  element enhanced with Material Design styling and ink ripples.
-   [MatProgressSpinner](https://material.angular.io/components/progress-spinner/overview)  that provides a circular indicator of progress and activity.

### Creating the Toolbar of our App

Next, go to the `src/app/app.component.html`  file where the template of the root app component exists and update it as follows:

```html
<mat-toolbar color="primary">  
<h1>  
My First Angular App  
</h1>  
<button mat-button routerLink="/">Home</button>  
<button mat-button routerLink="/about">About</button></mat-toolbar>

<router-outlet></router-outlet>
```

The app component contains the shell of our application i.e the part of our app that never changes between route navigations. This is where the router outlet exists which marks where the router can insert the macthed component against a specific URL path.

On top of te router outlet, we have added a toolbar with a primary color which contains a header and two buttons that take the users to `/home` and `/about` paths.

We secify where the button can take us when clicked using the `routerLink` directive which simly takes a path.

## Wrap-up

In this part of our tutorial, we've set up routing and material design in our Angular 9 example. We've seen how to configure routes using various properties such as `path`, `pathMatch`, `redirectTo` and `component` and create navigation links using the builtin `routerLink` directive. We've also seen how to build and style a professional UI with various Material design components like `MatToolbar`, `MatIcon`, `MatCard`, `MatButton`, and  `MatProgressSpinner`.     

