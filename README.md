# Basic Search/Filter API

This is a basic search/filter API built using Express.js.

## Description

This API allows users to retrieve data based on specific search criteria. It supports filtering by various fields and categories.

## Usage

### Installation

1. Clone the repository.
2. Install dependencies by running `npm install`.

### Running the Server

To start the server, run:

```bash
node index.js
```

The server will start listening on port `8000`.

## Endpoints

### GET /:category

Retrieves data based on the specified category.

#### Parameters

- `category`: The category of data to retrieve.

#### Query Parameters

- `q`: The search query to filter the data.

#### Example

```http
GET http://localhost:8000/books?q=Harry
```

This endpoint retrieves books that contain "Harry" in their name, author, or description.

## Technologies Used

- Node.js: A JavaScript runtime environment that executes JavaScript code outside a web browser.
- Express.js: A web application framework for Node.js used to build APIs and web applications.

## Explanation

### Router Setup

```javascript
const express = require("express");
const app = express();
const router = express.Router();
```

- We import the `express` library and create an Express application instance.
- We also create an instance of Express router using `express.Router()`.

### Route Definition

```javascript
router.get("/:category", function (req, res) {
  // Route handler function
});
```

- We define a route using the router's `get` method, specifying the path pattern `/:category`.
- This route expects a `category` parameter in the URL path.

### Data Retrieval

```javascript
const category = req.params.category;
const sent = data[category];
```

- We extract the value of the `category` parameter from the request URL.
- We retrieve the corresponding data array from the `data` object based on the category.

### Query Parameter Handling

```javascript
const q = req.query.q;
const filteredData = sent.filter((item) => {
  return item.name.toLowerCase().includes(q.toLowerCase());
});
```

- We extract the value of the `q` query parameter from the request URL.
- We filter the `sent` array based on whether the `name` property of each object includes the query string (case-insensitive).

### Response

```javascript
res.send(filteredData);
```

- We send the filtered data back to the client as the HTTP response.

### Server Listening

```javascript
app.use("/", router);
app.listen(8000, function () {
  console.log("Server started at port : ", 8000);
});
```

- We mount the router at the root path (`"/"`) of the Express application.
- We start the server and make it listen on port `8000`. When the server starts, it logs a message to the console.
# Backend-Basic-Search-And-Filter-API
