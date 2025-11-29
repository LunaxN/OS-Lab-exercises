## exercise 6
### 1: The reason for using `./` before a script name

#### Solution:

The `PATH` environment variable is a list of directories that the shell searches through when you type a command. For security and organization, the current directory (`.`) is typically not included in the `PATH` variable.

If you type just `script_name.sh`, the shell searches all the directories listed in `PATH` and will not find your script.

By using `./script_name.sh`, you are explicitly telling the shell the exact path to the script: "in the current directory (`.`), look for a file named `script_name.sh`" This bypasses the `PATH` search and allows the script to be executed.

### 2: A script to calculate the area and perimeter of a rectangle

#### Solution:

```bash
#!/bin/bash

# Prompt the user for the length and width
read -p "Enter length: " LENGTH
read -p "Enter width: " WIDTH

# Calculate area and perimeter
AREA=$((LENGTH * WIDTH))
PERIMETER=$((2 * (LENGTH + WIDTH)))

# Print the results
echo "Perimeter is: $PERIMETER"
echo "Area is: $AREA"
```

### 3: The difference between `"$@"` and `"$*"` variables

#### Solution:

##### Using `"$*"`
Enclosing the variable `$*` with double quotes means all arguments will be treated as a single string jointly.

To illustrate the usage of this variable, let's create a Bash script named `dollarStarQuoted.sh`:

```bash
for arg in "$*"; do
    echo "$arg"
done
```
and give it the executive permission, we'll get:

```bash
$ ./dollarStarQuoted.sh Journey to the cloud
Journey to the cloud
```
All the arguments are combined into a single word, with spaces between them.

##### Using `"$@"`
Both `$@` and `"$@"` treat each command-line argument separately. If we replace `"$*"` with `"$@"` in `dollarStarQuoted.sh` and name the new script as `dollarAtQuoted.sh`:

```bash
for arg in "$@"; do 
    echo "$arg" 
done
```
the result will be:

```bash
$ ./dollarAtQuoted.sh Journey to the cloud  
Journey 
to 
the 
cloud
```

##### Comparison of `"$*"` and `"$@"`
If we pass quoted command-line arguments like `"Journey to" "the cloud"` to `"$@"` and `"$*"` we get different outputs. **The quoted variable `"$@"` treats each quoted sequence of characters as an individual argument, but `"$*"` treats them as a single entity:**

```bash
$ ./dollarStarQuoted.sh "Journey to" "the cloud"
Journey to the cloud
```

```bash
$ ./dollarAtQuoted.sh "Journey to" "the cloud"
Journey to
the cloud
```