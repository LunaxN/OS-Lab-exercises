## exercise 7
### 1: A script for argument validation & check file/directory

#### Solution:

```bash
#!/bin/bash

if [[ $# -ne 1 ]]; then
    echo "Error: Script must accept exactly one argument!"
    exit 1
fi

if [[ -e "$1" ]]; then
    echo "File or directory $1 exists."

else
    echo "File or directory $1 doesn't exist."
fi
```

### 2: The importance of quoting variables

#### Solution:

Using double quotes around variables in shell scripts is essential to prevent word splitting and globbing. When a variable is not quoted:

- If `VAR=""` (empty), `[ $VAR = "value" ]` becomes `[ = "value" ]` &rarr; syntax error
- If `VAR="file name.txt"` (contains spaces), it splits into multiple arguments &rarr; `[ file name.txt = "value" ]` &rarr; syntax error
- If `VAR="*"`, it expands to all files in directory &rarr; `[ a.txt b.txt c.txt = "value" ]`

Double quotes preserve the variable's value as a single string, even if it contains spaces, special characters, or is empty.

### 3: A script for determine files or directories in current directory

#### Solution:

```bash
#!/bin/bash

for item in *;
do
    if [[ -f "$item" ]]; then
        echo "$item is a file."

    elif [[ -d "$item" ]]; then
        echo "$item is a directory."
    
    else
        echo "$item is not a file/directory."
    fi
done
```