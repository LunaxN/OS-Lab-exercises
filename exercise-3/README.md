## exercise 3
### 1: Count matching lines with `grep`

#### Solution:

```bash
grep -c "pattern" filename
```
- The `-c` option counts and prints the number of matching lines instead of displaying the lines themeselves

### 2: Find all `.conf` files in `/ect` directory

#### Solution:

```bash
find /ect -name "*.conf"
```

- `find` command searches for files
- `/ect` is the directory to search in
- `- name "*.conf"` looks for files ending with `.conf` extension

### 3: Extract 100 lines from the middle of a large file

#### Solution:

```bash
head -n 199 data.csv | tail -n 99
```

- `head -n 199` gets first 199 lines
- `tail -n 99` gets last 99 lines from those 199 lines
- Result: lines 99 - 199 (100 lines total)