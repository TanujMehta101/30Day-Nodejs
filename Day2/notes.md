```javascript
const fs = require('fs');

function writeToFile(filePath, content) {
    // Asynchronous file write operation
    fs.writeFile(filePath, content, 'utf8', (err) => {
        if (err) {
            // Handle error and print to console
            console.error(`Error writing to file: ${err.message}`);
            return;
        }

        // Print success message to the console
        console.log('Data written to', filePath);
    });
}

// Test Cases
writeToFile('test-files/output1.txt', 'Sample content.');
writeToFile('test-files/nonexistent-folder/output.txt', 'Content in a non-existent folder.');
```

In this implementation:

The **writeToFile** function takes two parameters:

**filePath**: The path to the file where you want to write the content.
**content**: The data you want to write to the file.
The **fs.writeFile** method is used for **asynchronous file writing**. It takes four arguments:

**filePath**: The path to the file where you want to write the content.
**content**: The data you want to write to the file.
**'utf8'**: The encoding of the file, specifying how the data should be interpreted.
**(err) => { /* ... */ }**: A callback function that is executed once the file writing operation is complete. 
The err parameter will be null if the operation is successful.
Inside the callback function:

If there is an error (err is not null), it handles the error and prints an error message to the console.
If the operation is successful, it prints a success message to the console.
Test cases demonstrate writing content to an existing file ('test-files/output1.txt') and handling the scenario where the specified folder does not exist ('test-files/nonexistent-folder/output.txt').






