```javascript
const express = require('express');
const app = express();

// Express route to handle requests with a positive integer parameter
function positiveIntegerHandler(req, res) {
  const number = parseInt(req.query.number);
  if (Number.isInteger(number) && number > 0) {
    res.status(200).send("Success: Number is a positive integer.");
  } else {
    throw new Error('Number must be a positive integer.');
  }
}

// Error handling middleware to catch specific errors
function errorHandler(err, req, res, next) {
  if (err.message === 'Number must be a positive integer.') {
    res.status(400).send('Bad Request: Number must be a positive integer.');
  } else {
    next(err); // Pass the error to the default error handler
  }
}

// Register the error handling middleware
app.use(errorHandler);

// Define the route
app.get('/positive', positiveIntegerHandler);

// Start the server
app.listen(3000, () => {
  console.log('Server is running on port 3000');
});
```
The positiveIntegerHandler function parses the "number" parameter from the query string of the request. If the parsed number is a positive integer, it sends a success message with status 200. Otherwise, it throws an error with the message "Number must be a positive integer."

The errorHandler middleware catches errors thrown by the route handler or any middleware that precedes it. If the error message matches "Number must be a positive integer.", it sends a custom error message with status 400 (Bad Request). Otherwise, it passes the error to the default error handler by calling next(err).

The error handling middleware is registered using app.use() so that it applies to all routes and middleware defined after it.

Finally, the route /positive is defined to handle GET requests, invoking the positiveIntegerHandler.

The server is started listening on port 3000.
