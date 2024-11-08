<p align="center">
   <img src="https://img.shields.io/badge/get_next_line-125%2F100-brightgreen?style=flat-square"/>
   <img src="https://img.shields.io/badge/language-C-blue.svg?style=flat-square"/>
   <img src="https://img.shields.io/badge/file-descriptors-important.svg?style=flat-square"/>
</p>

# 📜 get_next_line - Read a Line from a File Descriptor

**get_next_line** is a critical project in the 42 school curriculum, where the goal is to implement a function that reads a single line from a file descriptor, handling variable buffer sizes and edge cases gracefully. This project focuses on **file I/O**, **memory management**, and **buffer optimization**, making it an important step in mastering systems programming in C.

## 📚 Overview

The **get_next_line** project challenges developers to build a function capable of reading individual lines from a file descriptor, handling standard input, files, and even network streams efficiently. This project strengthens your understanding of **file descriptors**, **dynamic memory allocation**, and **buffer management**—skills that are essential for systems-level programming.

---

## ✨ Features

- **Core Functionality**:
  - Implements the `get_next_line` function that reads a line from a file descriptor, returning the line as a string.
  - Handles multiple calls to the same file descriptor, allowing for continuous reading.
  
- **File Descriptor Handling**:
  - Manages multiple file descriptors simultaneously by using static variables, ensuring that each descriptor maintains its own state.
  
- **Buffer Optimization**:
  - Reads data in customizable buffer sizes, making the function adaptable to different input sources and improving performance for large files.

- **Edge Case Handling**:
  - Properly handles end-of-file (EOF) detection, empty lines, and partial buffer reads.
  - Manages memory efficiently to avoid leaks by allocating and freeing memory dynamically as needed.

---

## 📂 File Structure

The project is composed of several key files:

###📜 Core Files
get_next_line.c: The primary function that reads from a file descriptor and returns the next line of text.
get_next_line_utils.c: Utility functions for memory management and string manipulation utilized by get_next_line.
###📜 Bonus Files
get_next_line_bonus.c: An extension of the core functionality designed to handle multiple file descriptors. This version efficiently manages reading operations from various sources simultaneously.
get_next_line_utils_bonus.c: Enhanced utility functions that support the bonus features, including mechanisms for managing static variables within the project to preserve state across multiple invocations.
---

## 🔍 Key Concepts

### 1. **File Descriptors**
   - The function makes use of file descriptors to reference open files in the system. By using static variables, the function can handle multiple open file descriptors simultaneously.

### 2. **Buffer Handling**
   - **get_next_line** reads data in chunks (buffers) and stores it in memory until a newline (`\n`) is encountered. This allows the function to handle large files and streams efficiently.

### 3. **Dynamic Memory Management**
   - Memory is dynamically allocated for each line, ensuring that the function can handle input of any length without memory overflows or leaks.

### 4. **Edge Case Management**
   - The function carefully handles edge cases such as:
     - Files without newlines.
     - Empty lines.
     - End-of-file (EOF) detection.
     - Reading from standard input (stdin).

---

## 🌟 Bonus Features

The bonus version extends the core functionality to allow **get_next_line** to:

- Handle multiple file descriptors at the same time (e.g., reading from `fd1`, then switching to `fd2`).
- Continue reading from a file even after a partial read (if the buffer ends in the middle of a line).


## 🏆 Project Evaluation

I achieved **125/100** on this project, mastering file descriptor handling, dynamic memory management, and efficient buffer usage across multiple file descriptors. This accomplishment demonstrates my ability to implement advanced systems programming techniques in C.

---

To add a concise and professional **Compilation** section for your GitHub **get_next_line** repository, here’s a streamlined version with the essential commands and instructions:

---

## 🛠️ Compilation

To compile **get_next_line** without a `Makefile`, use these commands. Adjust the buffer size as needed (example uses 42).

### Standard Version

```bash
cc -Wall -Wextra -Werror -D BUFFER_SIZE=42 get_next_line.c get_next_line_utils.c main.c -o get_next_line_exe
```

- Compiles the core **get_next_line** files (`get_next_line.c` and `get_next_line_utils.c`) with `main.c` for testing.
- `-D BUFFER_SIZE=42` sets the buffer size to 42 (adjust as necessary).

### Bonus Version (Multiple File Descriptors)

```bash
cc -Wall -Wextra -Werror -D BUFFER_SIZE=42 get_next_line_bonus.c get_next_line_utils_bonus.c main.c -o get_next_line_bonus_exe
```

- Use this to compile the **bonus** version, supporting multiple file descriptors.

### Running the Program

After compilation, you can execute the program like this:

```bash
./get_next_line_exe   # For standard version
./get_next_line_bonus_exe   # For bonus version
```

### Sample `main.c`

You can use this `main.c` file to test your program by reading lines from a file, `file.txt`:

```c
#include "get_next_line.h"
#include <fcntl.h>
#include <stdio.h>

int main(void)
{
    int fd = open("file.txt", O_RDONLY);
    if (fd == -1)
    {
        perror("Error opening file");
        return 1;
    }

    char *line;
    while ((line = get_next_line(fd)) != NULL)
    {
        printf("%s\n", line);
        free(line);
    }

    close(fd);
    return 0;
}
```

Add a text file (`file.txt`) to test the output, which should print each line until EOF. This gives you a clear and straightforward setup for **get_next_line**.

---
## 🔗 Related Projects

- **Libft**: Foundational library of C functions used across multiple projects. Check it out [here](https://github.com/AhmadHirzallah/Libft).
- **ft_printf**: Custom implementation of the `printf()` function, available [here](https://github.com/AhmadHirzallah/ft_printf).

---


## 🚀 Conclusion

The **get_next_line** project was an incredible learning experience, allowing me to dive deep into the intricacies of file handling, memory management, and buffer optimization. Through this project, I’ve solidified my understanding of core systems programming concepts and am well-prepared to tackle more complex challenges in the future.

---
