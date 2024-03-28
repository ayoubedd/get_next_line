# get_next_line

## Table of Contents
- [Overview](#overview)
- [Requirements](#requirements)
- [Build](#build)
- [Usage](#usage)
    - [Example](#example)
- [Lisence](#lisence)

## Overview

`get_next_line` is a basic C function, which each time run on the same file descriptor returns the next line until the file descriptor returns EOL. It comes handy when reading from a file of getting user input from `stdin`.

## Requirements

All you need is a C compiler.

## Build

Since this is just a simple function no build system required.

## Usage

To use `get_next_line` include the src file to src list to your compilation process.

### Example

main.c:

```c
#include "get_next_line.h"

void main() {
    int fd = open("/etc/passwd", O_RDONLY);
    char *str = get_next_line(fd);
    printf("%s\n", str);
}
```

This is a example using the basic version of `get_next_line`.

```sh
gcc get_next_line.c get_next_line_utils.c main.c -D BUFFER_SIZE=<size> -o main
```

replace `<size>` with the number of bytes to be read each time a `read` system call is trigged.

## Notes

- Using the standard version does not support reading from multiple file descriptor. To do so use the files ending with `_bonus`
- Returned buffers is up to used to memory manage.

## Lisence

This project is licensed under MIT license. See the LICENSE file for details.
