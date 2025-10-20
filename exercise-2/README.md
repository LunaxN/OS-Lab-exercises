## exercise 2
### 1: Create Directory Structure

```bash
/project
├── /assets
│ ├── /css
│ └── /py
└── /pages
```

#### Solution:

```bash
mkdir -p /project/assets/css /project/assets/py /project/pages
```

### 2: Haed Link vs Symbolic Link

```bash
touch info.txt
ln info.txt info_hardlink.txt
ln -s info.txt info_softlink.txt
rm info.txt
cat info_hardlink.txt
cat info_softlink.txt
```

#### Solution:

- Hard Link: Still work - data remains accessible
- Soft Link: Broken - shows "No such file or directory" error

### 3: `rm` Command Options

what are the `rm` options for:
- Asking confirmation before each deletion
- Force deletion (disable confirmation)

#### Solution:

```bash
#Asking confirmation before each deletion
rm -i filename

#Force deletion
rm -f filename
```