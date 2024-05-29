# FILE PROCESSOR SCRIPT

## Introduction

The File Processor script processes files within a specified directory, retrieving file metadata and extracting the first 20 bytes of the file header. It uses the `os`, `time`, `binascii`, and `pwd` modules to gather and display file information.

## Features

- **Retrieve File Metadata**: Collects file size, creation time, modification time, access time, and owner.
- **Extract File Header**: Reads the first 20 bytes of the file and converts it to a hexadecimal format.
- **Interactive Directory Scanning**: Prompts the user to input a directory path and processes each file in the directory.
- **Error Handling**: Gracefully handles errors for non-existent files or directories.

## Prerequisites

- Python 3.6 or higher.
- Unix/Linux system (for the `pwd` module).

## Modules

- **os**: Provides functions for interacting with the operating system.
- **time**: Provides time-related functions.
- **binascii**: Converts binary data to hexadecimal.
- **pwd**: Accesses user information in Unix/Linux systems.

```python
import os
import time
from binascii import hexlify
import pwd
```

## Functions

### `FileProcessor.__init__(self, filepath)`

Initializes the `FileProcessor` class with the file path, checks if the file exists, and retrieves file metadata.

- **Parameters:**
  - `filepath` (str): The path to the file to be processed.
- **Raises:**
  - `ValueError`: If the file does not exist.

### `FileProcessor._get_file_metadata(self, filepath)`

Retrieves file metadata such as size, creation time, modification time, access time, and owner.

- **Parameters:**
  - `filepath` (str): The path to the file.
- **Returns:**
  - `dict`: A dictionary containing file metadata.

### `FileProcessor.GetFileHeader(self)`

Extracts the first 20 bytes of the file's header.

- **Returns:**
  - `None`

### `FileProcessor.PrintFileDetails(self)`

Prints the file path, metadata, and header (if available) in hexadecimal format.

- **Returns:**
  - `None`

### `main()`

Prompts the user for a directory, processes each file in the directory, and prints the file details.

- **Returns:**
  - `None`

## Usage

1. **Set the Directory Path**: Replace the `directory` variable in the `main()` function with the directory you want to scan.

    ```python
    directory = "path_to_your_directory"
    ```

    **Note**: Make sure to replace `"path_to_your_directory"` with the actual path to the directory on your system that you want to scan.

2. **Run the Script**: Execute the script in your Python environment.

    ```bash
    python script_name.py
    ```

3. **Follow Prompts**: Enter the directory path when prompted, or enter `Q` to quit.

## Example Output

```plaintext
Enter a Directory to Scan or Q to Quit: /path/to/directory
File: /path/to/directory/file1.txt
Size: 1234
Creation_time: Mon Jan 01 00:00:00 2024
Modified_time: Mon Jan 01 00:00:00 2024
Access_time: Mon Jan 01 00:00:00 2024
Owner: username
Header (hex): 48656c6c6f20576f726c6421

File: /path/to/directory/file2.txt
Size: 5678
Creation_time: Tue Jan 02 00:00:00 2024
Modified_time: Tue Jan 02 00:00:00 2024
Access_time: Tue Jan 02 00:00:00 2024
Owner: username
Header (hex): 507974686f6e2050726f6772616d
```

## Error Handling

- **Non-Existent Directory**: If the directory does not exist, the script prompts the user to try again.
- **Non-Existent File**: If a file cannot be read, the script prints an error message and continues processing other files.

```plaintext
Directory does not exist. Please try again.
Could not read file: /path/to/directory/restricted_file.txt
```

## Security Considerations

- **Input Validation**: Ensure the directory path provided does not contain sensitive or unauthorized information.
- **Permission Handling**: Make sure the script has appropriate permissions to read files in the specified directory.

## FAQs

**Q: What happens if the directory is empty?**
A: The script will simply prompt for another directory or to quit.

**Q: Can the script process large directories?**
A: Yes, the script uses `os.listdir` to iterate through directories and files, making it efficient for large directories.

**Q: How does the script handle different file types?**
A: The script processes all files in binary mode, so it can handle any file type.

## Troubleshooting

- **Invalid Directory Path**: Ensure that the directory path is correct and accessible.
- **Module Not Found Errors**: Make sure Python is installed correctly and all necessary modules are available.

For further assistance or to report bugs, please reach out to the repository maintainers or open an issue on the project's issue tracker.
