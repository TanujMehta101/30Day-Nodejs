In this implementation:

The **executeCommand function** takes a **command** parameter representing the shell command you want to execute.

The **exec function** from the **child_process module** is used to execute the shell command asynchronously.

The **callback function (err, stdout, stderr) => { /* ... */ }** is executed once the command execution is complete. It receives three parameters:

```javascript
err: An error object (if any) during the command execution.
stdout: The standard output of the command.
stderr: The standard error output of the command.
```
Inside the callback function:

If there is an error (err is not null), it handles the error and prints an error message to the console.
If the operation is successful, it prints the standard output of the command to the console.
The function also prints any error output to the console if there is standard error output (stderr).

```javascript
const { exec } = require('child_process');

function executeCommand(command) {
    // Execute shell command
    exec(command, (err, stdout, stderr) => {
        if (err) {
            // Handle error and print to console
            console.error(`Error executing command: ${err.message}`);
            return;
        }

        // Print the output of the command to the console
        console.log('Command Output:');
        console.log(stdout);

        // Print any error output to the console
        if (stderr) {
            console.error('Error Output:');
            console.error(stderr);
        }
    });
}

// Test Cases
executeCommand('ls -la');
executeCommand('echo "Hello, Node.js!"');

```
