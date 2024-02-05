```javascript
const path = require('path');

function checkFileExtension(filePath, expectedExtension) {
    const actualExtension = path.extname(filePath).toLowerCase();

    if (actualExtension === expectedExtension.toLowerCase()) {
        console.log(`File has the expected extension: ${expectedExtension}`);
    } else {
        console.log(`File does not have the expected extension. Expected: ${expectedExtension}, Actual: ${actualExtension}`);
    }
}

// Test Cases
checkFileExtension('test-files/file1.txt', '.txt');
checkFileExtension('test-files/image.png', '.jpg');
```

The **checkFileExtension function** takes two parameters: **filePath and expectedExtension**.

The **path.extname method** is used to extract the actual file extension from the filePath. It is converted to lowercase for a case-insensitive comparison.

The function compares the actual extension with the expected extension and prints the result to the console.

Test cases demonstrate checking whether a file has the expected extension or not.




