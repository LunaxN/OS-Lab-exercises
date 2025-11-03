## exercise 3
### 1: Count matching lines with `grep`

#### Solution:

```bash
grep -c "pattern" filename
```
- The `-c` option counts and prints the number of matching lines instead of displaying the lines themselves

### 2: Find all `.conf` files in `/e‍tc` directory and its subdirectories

#### Solution:

```bash
find /etc -name "*.conf"
```

- `find` command searches for files
- `/etc` is the directory to search in
- `- name "*.conf"` looks for files ending with `.conf` extension

### 3: Extract 100 lines from the middle of a large file

#### Solution:

```bash
head -n 1099 data.csv | tail -n 100
```

- `head -n 1099` gets first 1099 lines
- `tail -n 100` gets last 100 lines from those 1099 lines
- Result: lines 1000 through 1099 (100 lines total)