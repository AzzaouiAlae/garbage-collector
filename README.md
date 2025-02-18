Below is an improved version of your README with a clearer structure, enhanced language, and more detailed instructions:

---

# Garbage Collector

A lightweight garbage collector for 42 projects written in C.  
This project helps simplify memory management by automating the freeing of dynamically allocated memory.

---

## Overview

Managing memory in C can be challenging. When you use `malloc`, you must remember to call `free` at the appropriate times. Tracking down every allocation can be time-consuming and error-prone. The Garbage Collector project replaces manual calls to `malloc` and `free` with its own functions (`ft_calloc` and `ft_free`), and provides a convenient function `ft_free_all` to free all allocated memory at the end of your program.

---

## Features

- **Automatic Memory Management:** Use `ft_calloc` in place of `malloc` and let the collector track your allocations.
- **Bulk Freeing:** Instead of freeing memory individually, call `ft_free_all()` once at the end of your program to release all allocated resources.
- **Optional Individual Freeing:** Still have the option to free individual allocations using `ft_free`.

---

## Installation

### Clone the Repository

Clone the repository into a folder of your choice:

```bash
git clone https://github.com/AzzaouiAlae/garbage-collector.git garbage_collector
```

### Remove Git History

Remove the `.git` directory to detach this project from its Git history:

```bash
rm -fr garbage_collector/.git/
```

### Copy to Your Project

Copy the `garbage_collector` directory into your project folder:

```bash
cp -r garbage_collector ~/your/project/path
```

---

## Usage

### 1. Include the Header

Include the Garbage Collector header in your source files:

```c
#include "garbage_collector.h"
```

### 2. Replace Memory Allocation

Instead of using `malloc`, use `ft_calloc`:

```c
void    *ft_calloc(size_t n, size_t type_size);

// Example:
int *nums;
nums = ft_calloc(10, sizeof(int));
```

### 3. Freeing Memory

At the end of your program, free all allocated memory using:

```c
void    ft_free_all(void);

// Call this once when your program is about to exit:
ft_free_all();
```

If you need to free a specific allocation before the end of your program, replace `free` with `ft_free`:

```c
void    ft_free(void *mem);

// Example:
ft_free(nums);
```

*Note:* It's generally recommended to rely on `ft_free_all()` at program termination to avoid manual tracking of every allocation.

---

## Example

Below is a simple example demonstrating the use of the Garbage Collector:

```c
#include "garbage_collector.h"

void example()
{
    // Allocate memory for an array of 10 integers
    int *nums = ft_calloc(10, sizeof(int));
    // you don't need to check if the it fail because it will exit
    /*if (!nums)
        return (1);*/

    // Use the allocated memory
    for (int i = 0; i < 10; i++)
        nums[i] = i * 2;

    // Optionally free one allocation early (not necessary if using ft_free_all)
    // ft_free(nums);
}

int main(void)
{   

    example();

    // Free all allocations at the end of the program
    ft_free_all();
    
    return (0);
}
```

---

## Contributing

Contributions are welcome! Feel free to fork this repository, submit pull requests, or open issues for suggestions and improvements.

---
