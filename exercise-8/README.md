## exercise 8
### 1: Option `-c` in `gcc`

#### Solution:
- `-c` : This command compile the source file and give the object file as output(`.o`), which is used to make libraries. 

```bash
gcc -c file.c
```
output: `file.o`


### 2: Difference between `next` and `step` in GDB

#### Solution:
- `next` (shortcut `n`):
Executes the next line of code. If the next line is a function call, it will **not** enter the function.

- `step` (shortcut `s`):
Executes the next line of code. If the next line is a function call, it **will** enter the function.

Given this line in `main()`:
```c
int result = add(a, b);
```

- `next` &rarr; Runs `add(a, b)` completely and moves to the next line after the call.
- `step` &rarr; Jumps into `add()` and pauses at its first line, allowing you to debug inside `add()`.



### 3: Multi-File C Project with Makefile

#### Solution:

`helper.c`:
```c
#include <stdio.h>

void print_message() {
    printf("Hello from helper.c!\n");
}
```

`main.c`:
```c
#include <stdio.h>

void print_message(); // declaration

int main() {
    printf("Hello from main.c!\n");
    print_message();
    return 0;
}
```

`Makefile`:
```makefile
CC=gcc
CFLAGS=-g -Wall

all: myprogram

myprogram: main.o helper.o
    $(CC) $(CFLAGS) -o myprogram main.o helper.o

main.o: main.c
    $(CC) $(CFLAGS) -c main.c

helper.o: helper.c
    $(CC) $(CFLAGS) -c helper.c

clean:
    rm -f myprogram main.o helper.o
```

`./myprogram` output:
```bash
Hello from main.c!
Hello from helper.c!
```