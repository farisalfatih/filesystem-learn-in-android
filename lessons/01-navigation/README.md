# Lesson 1: Navigation Basics

## Learning Objectives

By the end of this lesson, you will be able to:
- Understand the Linux filesystem hierarchy
- Navigate between directories
- List directory contents with various options
- Understand absolute vs relative paths

## Commands Covered

- `pwd` - Print Working Directory
- `ls` - List directory contents
- `cd` - Change Directory

---

## 1. Print Working Directory (`pwd`)

The `pwd` command shows your current location in the filesystem.

### Syntax
```bash
pwd
```

### Example
```bash
$ pwd
/home/username
```

### Try it yourself
1. Open your terminal
2. Type `pwd` and press Enter
3. Note your current directory

---

## 2. List Directory Contents (`ls`)

The `ls` command displays files and directories in the current or specified directory.

### Basic Syntax
```bash
ls [options] [directory]
```

### Common Options

| Option | Description | Example |
|--------|-------------|---------|
| `ls` | List files in current directory | `ls` |
| `ls -l` | Long format (detailed view) | `ls -l` |
| `ls -a` | Show all files (including hidden) | `ls -a` |
| `ls -h` | Human-readable file sizes | `ls -lh` |
| `ls -la` | Combination: long format + hidden | `ls -la` |
| `ls -R` | Recursive listing | `ls -R` |
| `ls -t` | Sort by modification time | `ls -lt` |

### Examples

**Basic listing:**
```bash
$ ls
Documents  Downloads  Pictures  Videos
```

**Long format with details:**
```bash
$ ls -l
total 16
drwxr-xr-x 2 user user 4096 Jan  1 10:00 Documents
drwxr-xr-x 2 user user 4096 Jan  1 10:00 Downloads
drwxr-xr-x 2 user user 4096 Jan  1 10:00 Pictures
drwxr-xr-x 2 user user 4096 Jan  1 10:00 Videos
```

**Show hidden files:**
```bash
$ ls -a
.  ..  .bashrc  .profile  Documents  Downloads
```

**Human-readable sizes:**
```bash
$ ls -lh
total 16K
drwxr-xr-x 2 user user 4.0K Jan  1 10:00 Documents
drwxr-xr-x 2 user user 4.0K Jan  1 10:00 Downloads
```

---

## 3. Change Directory (`cd`)

The `cd` command allows you to move between directories.

### Syntax
```bash
cd [directory]
```

### Special Directories

| Symbol | Meaning | Example |
|--------|---------|---------|
| `.` | Current directory | `cd .` |
| `..` | Parent directory | `cd ..` |
| `~` | Home directory | `cd ~` |
| `-` | Previous directory | `cd -` |
| `/` | Root directory | `cd /` |

### Examples

**Go to home directory:**
```bash
$ cd ~
# or simply
$ cd
```

**Go to parent directory:**
```bash
$ cd ..
```

**Go to a specific directory:**
```bash
$ cd /home/username/Documents
```

**Go back to previous directory:**
```bash
$ cd -
```

**Navigate multiple levels up:**
```bash
$ cd ../../..
```

---

## 4. Understanding Paths

### Absolute Paths
- Start from the root directory (`/`)
- Complete path from root to the target
- Example: `/home/username/Documents/file.txt`

### Relative Paths
- Start from current directory
- Relative to where you are now
- Example: `Documents/file.txt` or `../Downloads/file.txt`

### Examples

If you're in `/home/username/`:

**Absolute path:**
```bash
$ cd /home/username/Documents
```

**Relative path:**
```bash
$ cd Documents
```

---

## Practical Exercises

### Exercise 1: Basic Navigation
1. Open your terminal
2. Use `pwd` to see where you are
3. Use `ls` to see what's in your current directory
4. Navigate to your home directory using `cd ~`
5. Verify you're in your home directory with `pwd`

### Exercise 2: Exploring Directories
1. From your home directory, use `ls -la` to see all files
2. Navigate to a subdirectory (e.g., `cd Documents`)
3. Use `pwd` to confirm your location
4. Go back to the parent directory using `cd ..`
5. Verify you're back with `pwd`

### Exercise 3: Path Practice
1. Navigate to your home directory
2. Create this path mentally: `/home/username/Documents/projects`
3. Try navigating there using both absolute and relative paths
4. Use `cd -` to toggle between your previous location and current location

### Exercise 4: Hidden Files
1. In your home directory, run `ls` (without options)
2. Now run `ls -a` and observe the difference
3. Look for files starting with `.` (these are hidden files)
4. Research what `.bashrc` or `.profile` files do

---

## Tips and Best Practices

1. **Use Tab Completion**: Press Tab while typing a path to auto-complete
2. **Case Sensitivity**: Linux is case-sensitive: `Documents` ≠ `documents`
3. **Spaces in Names**: Use quotes or escape spaces: `cd "My Documents"` or `cd My\ Documents`
4. **Frequent Locations**: Create aliases in your `.bashrc` for frequently visited directories

---

## Command Cheat Sheet

```bash
pwd                  # Show current directory
ls                   # List files
ls -la               # List all files with details
cd ~                 # Go to home directory
cd /path/to/dir      # Go to specific directory (absolute)
cd relative/path     # Go to directory (relative)
cd ..                # Go to parent directory
cd -                 # Go to previous directory
```

---

## Next Steps

Once you're comfortable with navigation, proceed to [Lesson 2: File Operations](../02-file-operations/README.md) to learn how to create, view, copy, move, and delete files.

---

## Additional Resources

- [Linux Filesystem Hierarchy Standard](https://refspecs.linuxfoundation.org/FHS_3.0/fhs/index.html)
- Practice navigation in your terminal daily to build muscle memory
- Explore your system's directory structure using these commands
