+++
date = '2025-06-23T10:01:29+08:00'
draft = false
title = 'JS: Express.js'
tags = ["javascript","JS","Node.js", "Node", "Express", "API", "Backend"]
+++

`Express.js` is a minimalist and flexible `Node.js` web application framework that provides a robust set of features for building web and mobile applications and APIs. If you're looking to build fast, scalable, and efficient server-side applications with JavaScript, Express.js is your go-to choice. Its unopinionated nature gives you immense freedom,
<br>

### Setting Up

Getting started with Express.js is straightforward. If you already have a Node.js project, or if you're starting a new one, follow these simple steps:

- Initializing a Node.js project (`npm init`).
- Installing Express.js (`npm install express`).

Now, you're ready to create your first Express server!

### Core Concepts

Understanding these fundamental concepts is key to mastering Express.js:

#### Routing

Routing is the process of determining how an application responds to a client request to a particular endpoint, which is a URI (or path) and a specific HTTP request method (GET, POST, PUT, DELETE, etc.).

In Express.js, you define routes using methods corresponding to HTTP verbs on the app object (an instance of Express).

HTTP Methods (Verbs): These map directly to common operations:

- `GET`: Retrieve data (e.g., fetching a list of users).
- `POST`: Submit data to be processed (e.g., creating a new user).
- `PUT`: Update existing data (e.g., modifying a user's details).
- `DELETE`: Remove data (e.g., deleting a user).

```js
const express = require("express");
const app = express();
const port = 3000;

// GET request to the root URL
app.get("/", (req, res) => {
  res.send("Hello from Express!");
});

// GET request to /users
app.get("/users", (req, res) => {
  res.json([
    { id: 1, name: "Alice" },
    { id: 2, name: "Bob" },
  ]);
});

// POST request to /users
app.post("/users", (req, res) => {
  // Logic to create a new user
  res.status(201).send("User created successfully!");
});

app.listen(port, () => {
  console.log(`Server listening at http://localhost:${port}`);
});
```

```js
// Route Parameters:
// Example URL: /users/123
app.get("/users/:id", (req, res) => {
  const { id } = req.params;
  res.send(`Fetching user with ID: ${id}`);
});

// Query Parameters:
// Example URL: /search?q=nodejs&category=backend
app.get("/search", (req, res) => {
  const { q: searchTerm, category } = req.query;
  res.send(`Searching for "${searchTerm}" in "${category}" category.`);
});
```

#### Middleware

Middleware functions are core to Express.js. They are functions that have access to the `request` object (`req`), the response object (`res`), and the `next()` function in the application's request-response cycle. The `next()` function is crucial as it passes control to the next middleware function.

Think of middleware as a series of steps a request goes through before reaching its final route handler.

- How Middleware Works: Requests flow sequentially through middleware functions. Each function can perform operations, modify `req` or `res`, end the cycle by sending a response, or pass control to the next middleware via `next()`.

- Common Use Cases:
  - **Logging**: Recording details about incoming requests.
  - **Authentication/Authorization**: Verifying user credentials and permissions.
  - **Body Parsing**: Express itself doesn't parse request bodies by default. Middleware like `express.json()` and `express.urlencoded()` are essential for handling JSON and URL-encoded form data.
  - **Serving Static Files**: Handled by express.static().
  - **Error Handling**: Special middleware for catching and processing errors.

Example of Custom Middleware:

```js
// A simple logger middleware
const logger = (req, res, next) => {
  console.log(`[${new Date().toISOString()}] ${req.method} ${req.url}`);
  next(); // Pass control to the next handler
};

app.use(logger); // Use the middleware for all incoming requests

app.get("/", (req, res) => {
  res.send("Home Page with Logger!");
});
```

#### Handling Request (req) and Response (res)

- `req` (Request Object):
  - Accessing request headers (`req.header`).
  - Accessing route and query parameters (`req.params`, `req.query`).
  - Accessing the request body (`req.body`).
- `res` (Response Object):
  - Sending various types of responses: `res.send()`, `res.json()`, `res.sendFile()`.
  - Setting HTTP status codes: `res.status()`.
  - Redirecting requests: `res.redirect()`.
  - Chaining methods (e.g., `res.status(200).json(...)`).

### Typical Project Structure

While Express is unopinionated, a well-organized project structure is crucial for maintainability and scalability, especially as your application grows. Here's a common pattern:

```
my-express-app/
├── node_modules/
├── server.js             # Entry point: Starts the server, sets up environment
├── app.js                # Express app configuration: Defines middleware, connects routes
├── routes/               # Defines API endpoints and links to controllers
│   ├── auth.routes.js
│   └── user.routes.js
├── controllers/          # Contains request handlers: Logic for specific routes, interacts with services
│   ├── auth.controller.js
│   └── user.controller.js
├── services/             # Business logic: Handles complex operations, orchestrates data flow
│   ├── auth.service.js
│   └── user.service.js
├── models/               # Data schema definitions (e.g., Mongoose schemas, Sequelize models)
│   ├── User.js
│   └── Product.js
├── middlewares/          # Custom middleware functions
│   ├── auth.middleware.js
│   └── error.middleware.js
├── config/               # Configuration files (database settings, environment variables)
│   └── db.config.js
├── package.json
├── package-lock.json
└── .env                  # Environment variables
```

### Sample Project

( coming soon )
