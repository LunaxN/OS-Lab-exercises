## exercise 4
### 1: Convert `---rwxr-x` to Octal format

#### Solution:

`---rwxr-x` = 075 in Octal:

- `---` &rarr; 0 + 0 + 0 = 0
- `rwx` &rarr; 4 + 2 + 1 = 7
- `r-x` &rarr; 4 + 0 + 1 = 5

### 2: Command to remove execute permission only from group for `deploy.sh`

#### Solution:

```bash
chmod g-x deploy.sh
```

- `chmod` command changes file permissions
- `g` refers to the file's group ownership
- `-` removes permission
- `x` is execute permission
- `deploy.sh` is the target script file


### 3: Default permissions for new file and directory with umask `0027`

#### Solution:

##### For a new file:

- Base permission: 666 (`rw-rw-rw-`)
- Calculation: 666 - 027 = 640 in Octal
- Symbolic: `-rw-r-----`

##### For a new directory:

- Base permission: 777 (`rwxrwxrwx`)
- Calculation: 777 - 027 = 750 in Octal
- Symbolic: `drwxr-x---`