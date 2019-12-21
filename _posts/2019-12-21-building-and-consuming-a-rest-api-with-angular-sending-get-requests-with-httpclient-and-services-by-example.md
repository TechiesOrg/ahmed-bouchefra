---
layout: post
title:  "Building and Consuming a REST API with Angular 9: Sending GET Requests with HttpClient and Services by Example"
date:   2019-12-21
---

In this part of our Angular 9 tutorial, we'll build a fake REST API backend for our Angular frontend using `json-server` and `faker.js` and next we'll see how to create a service to send GET requests to our backend to fetch and consume data which will be rendered in the home components using the `ngFor` and `ngIf` directives.

These are the steps of this part:

- What is an Angular Service?
- Tutorial Step 7 — Simulating a Fully-Working REST API Using JSON-Server
- Tutorial Step 8 — Sending HTTP Requests with Angular 9 HttpClient
- - Creating an Angular 9 Service
- - Sending an HTTP Request 
- - Injecting and Calling the Service 
- - Rendering the Fetched Data with ngFor



## What is an Angular Service?

We can send HTTP requests directly from the home component but that's not realy the recommended way to do it —  here comes the role of Angular services.

An Angular service is a TypeScript class that encapsuates a set of similar functionalities, like fetching data from a server, in your project's code. It's injectable in any other service or component thanks to Angular dependency injector and it's reusable across the module where it's provided.

We mark a TypeScript class as injectable using the `@Injectable` decorator which also takes a `providedIn` property to secifies the modue where the service should be provided. By default this is `root` which is simply an alias for `AppModule`.
   
## Tutorial Step 7 — Simulating a Fully-Working REST API Using JSON-Server

Almost every frontend app needs a data which can be most of the times fetched from a backend that exposes a REST API. Since our tutorial is about frontend web development with Angular 9, we either need a third-party REST API which are available from public servers on the web or better we can use tools like json-server to generate fully working backend APIs with fake data. The process is quick and easy so let's do it!

Go to a new command-line interface and run the following commands to navigate to your project's folder and install `json-server`  from npm:

```bash
$ cd ~/first-angular-app
$ npm install --save json-server 
```

Next, go ahead and create a `backend`  folder in your Angular project:

```bash
$ mkdir backend
```

Next, we'll use  [Faker.js](https://github.com/marak/Faker.js/)  for generating massive amounts of realistic fake data.

Head back to your command-line interface and install  `Faker.js`  from npm using the following command:

```bash
$ npm install faker --save
```

At the time of building this example,  **faker v4.1.0**  will gets installed on our machine.

Now, create a `init.js`  file and add the following code:

```js
var faker = require('faker');

var database = { products: []};

for (var i = 1; i<= 300; i++) {
  database.products.push({
    id: i,
    name: faker.commerce.productName(),
    description: faker.lorem.sentences(),
    price: faker.commerce.price(),
    imageUrl: "https://source.unsplash.com/1600x900/?product",
    quantity: faker.random.number()
  });
}

console.log(JSON.stringify(database));
```

We first imported faker, and next we defined an object with one empty array for products. Next, we entered a  _for_  loop to create  _300_  fake entries using faker methods like `faker.commerce.productName()`  for generating product names.  [Check all the available methods](https://github.com/marak/Faker.js/#api-methods). Finally we converted the database object to a string and logged it to standard output.

Next, add the `init-api`  and `serve-api`  scripts to the `package.json`  file as follows:

```json
  "scripts": {
    "ng": "ng",
    "start": "ng serve",
    "build": "ng build",
    "test": "ng test",
    "lint": "ng lint",
    "e2e": "ng e2e",
    "init-api": "node ./backend/init.js > ./backend/data.json",
    "serve-api": "json-server --watch ./backend/data.json"
  },


```

Next, go to your command-line interface and run the `init-api` script as follows:

```bash
$ npm run init-api


```

Next, run the REST API server:

```bash
$ npm run init-api


```

You can now consume the REST API just like any typical REST API server. It will be available from the `http://localhost:3000/`  address.

These are the API endpoints we'll be able to use via our REST API server:

-   `GET /products`  for getting the products
-   `GET /products/<id>`  for getting a single product by id
-   `POST /products`  for creating a new product
-   `PUT /products/<id>`  for updating a product by id
-   `PATCH /products/<id>`  for partially updating a product by id
-   `DELETE /products/<id>`  for deleting a product by id

You can use `_page`  and `_limit`  parameters to get paginated data. In the `Link`  header you'll get `first`, `prev`, `next`  and `last`  links.

If you managed to follow this step successfully, you should have a working REST API server that you can connect to from your Anguar 9 frontend. Congratulations, you are ready for the next step!

## Tutorial Step 8 — Sending HTTP Requests with Angular 9 HttpClient

In this step, we’ll send HTTP GET requests to fetch data from our REST API server using Angular HttpClient and a service.
      
We’ll need to create an Angular service for encapsulating the code that allows us to consume data from our REST API server.

### Creating an Angular 9 Service

Go to your command-line interface and run the following command:

```bash
$ ng generate service api

```

Next, head to the `src/app/api.service.ts`  file, import and inject `HttpClient`:

```ts
import { Injectable } from '@angular/core';
import { HttpClient } from '@angular/common/http';

@Injectable({
  providedIn: 'root'
})
export class ApiService {

  private SERVER_URL = "http://localhost:3000";

  constructor(private httpClient: HttpClient) { }
}

```

We imported and injected the `HttpClient`  service via the service constructor and defined the `SERVER_URL`  variable that has the address of our locally-running REST API server.

### Sending an HTTP Request 
 
Next, define a `fetchData()`  method that simply sends an HTTP GET request to the REST API endpoint for products i.e `/products`:

```ts
import { Injectable } from '@angular/core';  
import { HttpClient } from '@angular/common/http';

@Injectable({  
	providedIn: 'root'  
})  
export class ApiService {

	private SERVER_URL = "http://localhost:3000";
	constructor(private httpClient: HttpClient) { }

	public fetchData(){  
		return this.httpClient.get(`${this.SERVER_URL}/products`);  
	}  
}

```

The method simply calls the `fetchData()`  method of `HttpClient`  to send a GET request to the REST API server.

### Injecting and Calling the Service 

Next, we need to use this service in our home component. Open the  `src/app/home/home.component.ts`  file, and import then inject the Angular service as follows:

```ts
import { Component, OnInit } from '@angular/core';  
import { ApiService } from '../api.service';

@Component({  
	selector: 'app-home',  
	templateUrl: './home.component.html',  
	styleUrls: ['./home.component.css']  
})  
export class HomeComponent implements OnInit {
	products = [];
	constructor(private apiService: ApiService) { }
	ngOnInit() {
		this.apiService.fetchData().subscribe((data: any[])=>{  
			console.log(data);  
			this.products = data;  
		})  
	}
}

```

We imported and injected `ApiService.`  Next, we defined a `products`  variable and called the `fetchData()`  method of the service for fetching data from the REST API server.

### Rendering the Fetched Data with ngFor

Next, open the `src/app/home/home.component.html`  file and update it as follows:

```html
<div style="padding: 13px;">
    <mat-spinner *ngIf="products.length === 0"></mat-spinner>

    <mat-card *ngFor="let product of products" style="margin-top:10px;">
        <mat-card-header>
            <mat-card-title>{{product.name}}</mat-card-title>
            <mat-card-subtitle>{{product.price}} $/ {{product.quantity}}
            </mat-card-subtitle>
        </mat-card-header>
        <mat-card-content>
            <p>
                {{product.description}}
            </p>
            <img style="height:100%; width: 100%;" src="{{ product.imageUrl }}" />
        </mat-card-content>
        <mat-card-actions>
      <button mat-button> Buy product</button>
    </mat-card-actions>
    </mat-card>
</div>

```

We used the `<mat-spinner>`  component for showing a loading spinner when the length of the `products`  array equals zero, that is before any data is received from the REST API server.

Next, we iterated over the `products`  array and used a Material card to display the  `name`, `price`, `quantity`, `description`  and `image`  of each product.

This is a screenshot of the home page after JSON data is fetched:

![](https://miro.medium.com/max/301/0*R7qs5jGg_IlOtTWF)

Next, we’ll see how to add error handling to our service.

## Wrap-up

In this part of our Angular 9 tutorial, we've seen what a service is and created one to encapsulate sending HTTP GET requests to our REST API backend to consume data and render it using the `ngFor` directive.
