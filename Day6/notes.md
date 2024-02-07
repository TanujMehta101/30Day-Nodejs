**Express Route Handling**

1. Create an Express route to handle GET requests to the endpoint "/greet" that takes a query parameter "name" and returns a personalized greeting.
2. If the name parameter is not provided, the default greeting should be "Hello, Guest!".

Expected Output:

If the "name" parameter is provided: "Hello, {name}!"
If the "name" parameter is not provided: "Hello, Guest!"
Test Cases:

Request to /greet?name=John should return "Hello, John!"
Request to /greet should return "Hello, Guest!"

```javascript
/**
 * Handles GET requests to "/greet" endpoint
 * @param {Object} req - Express request object
 * @param {Object} res - Express response object
 */
function greetHandler(req, res) {
    // Extract the "name" query parameter from the request
    const name = req.query.name;

    // Check if the "name" parameter is provided
    if (name) {
        // If provided, send a personalized greeting
        res.send(`Hello, ${name}!`);
    } else {
        // If not provided, send a default greeting
        res.send('Hello, Guest!');
    }
}
```
```javascript
const express = require('express');
const app = express();

// Define the route for the "/greet" endpoint
app.get('/greet', greetHandler);

// Start the server
const port = 3000;
app.listen(port, () => {
    console.log(`Server is listening on port ${port}`);
});
```
function greetHandler(req, res) {: This line declares a JavaScript function named greetHandler that takes two parameters: req (representing the Express request object) and res (representing the Express response object). This function is responsible for handling GET requests to the "/greet" endpoint.

const name = req.query.name;: This line extracts the value of the query parameter named "name" from the request object. In Express, query parameters are accessible via the req.query object. If the query parameter "name" is present in the request URL, its value will be assigned to the variable name.
For example:

If the request URL is /greet?name=John, then req.query.name will be 'John'.
If the request URL is /greet, then req.query.name will be undefined.

if (name) {: This line checks if the name variable has a truthy value. In JavaScript, an empty string, null, undefined, 0, and false are considered falsy, while any other value is considered truthy. This condition checks if the "name" query parameter is provided in the request.
```
        // If provided, send a personalized greeting
        res.send(`Hello, ${name}!`);
```
res.send(Hello, ${name}!);: This line sends a response back to the client with a personalized greeting using the res.send() method. It uses template literals to construct the greeting message by interpolating the value of the name variable.
For example:

If the request URL is /greet?name=John, the response will be "Hello, John!".
If the request URL is /greet?name=Alice, the response will be "Hello, Alice!".

} else {: This line represents the else block of the conditional statement. If the name variable is falsy (meaning the "name" query parameter is not provided in the request), the execution will proceed to this block.

```
        // If not provided, send a default greeting
        res.send('Hello, Guest!');

```
res.send('Hello, Guest!');: This line sends a response back to the client with a default greeting message using the res.send() method. If the "name" query parameter is not provided in the request, this message "Hello, Guest!" will be sent as the response.
For example:

If the request URL is /greet (without any query parameters), the response will be "Hello, Guest!".
