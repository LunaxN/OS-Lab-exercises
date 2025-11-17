## exercise 5
### 1: The First Process (`init` or `systemd`)

#### Solution:

- Its PID is always 1.
- **Parent of all processes** because it's the first process started by the kernel after booting.
- Primary role to initialize the system, start all essential services and manage other processes.

### 2: `SIGTSTP` Signal's Number

#### Solution:

Its number using `kill -l` is 20.

### 3: Difference between `SIGTERM` and `SIGKILL`

#### Solution:

- `SIGTERM`: This is a **polite request for termination**. it allows the process to perform clean up operation before exiting gracefully. 
- `SIGKILL`: This is a **forceful, immediate kill signal**. The operating system terminates the process instantly without giving it any chance to clean up.

### 4: Difference between two `grep` commands

```bash
cat file.txt | grep "word"
grep "word" file.txt
```

#### Solution:

Both commands perform the same task (searching for "word" in `file.txt`). However, the first command is a "**Useless Use of** `cat`". It unnecessarily creates an extra process (`cat`) because `grep` is perfectly capable of reading the file directly. The second command is more efficient and is the correct way to use `grep`.

### 5: Filtering Kernel Messages

#### Solution:

```bash
dmesg | grep -E "error|fail" > kernel_errors.log
```

The `-E` option enables extended regular expressions, allowing the use of `|` to mean "OR".

### 6:  The `tr` command and an example

#### Solution:

- The `tr` (translate) command is used to **translate, delete, or squeeze characters** from standard input.
- Example: Let's say a file `names.txt` contains mixed-case names. The following command converts all uppercase letters to lowercase and then sorts the list:

```bash
cat names.txt | tr '[:upper:]' '[:lower:]' | sort
```

This pipeline:
- `cat` reads the file.
- `tr` translates all uppercase characters to lowercase.
- `sort` sorts the final result alphabetically.