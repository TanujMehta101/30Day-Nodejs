A **relative path** is a way to specify the location of a file or directory with **respect to a current working directory**. 
Unlike **absolute paths**, which specify the **complete path from the root directory**.

Here are some key concepts related to relative paths:

Current Working Directory (CWD):

Single-Dot (.) and Double-Dot (..):

. represents the **current directory**.
.. represents the **parent directory**.
Examples of Relative Paths:

./subdirectory/file.txt: Specifies a file named file.txt located in the subdirectory within the current working directory.
../parent_directory/file.txt: Specifies a file named file.txt located in the parent_directory (one level up from the current working directory).

```javascript
const path = require('path');

function resolvePath(relativePath) {
    // Resolve the relative path to an absolute path
    const absolutePath = path.resolve(relativePath);

    // Print the resolved path to the console
    console.log('Resolved Path:', absolutePath);
}

// Test Cases
resolvePath('../project/folder/file.txt');
resolvePath('nonexistent-folder/file.txt');
```

In this implementation:

The **resolvePath function** takes a **relativePath parameter** representing the relative path you want to resolve.

The **path.resolve method** is used to resolve the **relative path to an absolute path**. This method takes one or more path segments and returns an absolute path.
