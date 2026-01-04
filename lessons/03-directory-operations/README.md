# Lesson 3: Directory Operations

## Learning Objectives

By the end of this lesson, you will be able to:
- Create single and nested directories
- Remove directories safely
- Understand directory structures
- Copy and move directories
- Work with directory trees

## Commands Covered

- `mkdir` - Make directories
- `rmdir` - Remove empty directories
- `rm -r` - Remove directories recursively
- `tree` - Display directory structure (if available)

---

## 1. Creating Directories (`mkdir`)

The `mkdir` command creates new directories.

### Syntax
```bash
mkdir [options] directory_name
```

### Common Options

| Option | Description |
|--------|-------------|
| `-p` | Create parent directories as needed |
| `-v` | Verbose (show directories being created) |
| `-m` | Set permissions while creating |

### Examples

**Create a single directory:**
```bash
$ mkdir myproject
```

**Create multiple directories:**
```bash
$ mkdir dir1 dir2 dir3
```

**Create nested directories (parent and child):**
```bash
$ mkdir -p projects/web/frontend
```

**Create with verbose output:**
```bash
$ mkdir -v newdir
mkdir: created directory 'newdir'
```

**Create with specific permissions:**
```bash
$ mkdir -m 755 public_dir
```

### Understanding `-p` option

Without `-p`:
```bash
$ mkdir parent/child
mkdir: cannot create directory 'parent/child': No such file or directory
```

With `-p`:
```bash
$ mkdir -p parent/child
# Creates both parent and child directories
```

---

## 2. Removing Empty Directories (`rmdir`)

The `rmdir` command removes empty directories only.

### Syntax
```bash
rmdir [options] directory_name
```

### Examples

**Remove an empty directory:**
```bash
$ rmdir emptydir
```

**Remove multiple empty directories:**
```bash
$ rmdir dir1 dir2 dir3
```

**Try to remove a non-empty directory (will fail):**
```bash
$ rmdir nonemptydir
rmdir: failed to remove 'nonemptydir': Directory not empty
```

### When to use `rmdir`
- Safety: Only removes empty directories
- Good for cleaning up directory structures
- Prevents accidental deletion of files

---

## 3. Removing Directories with Contents (`rm -r`)

To remove directories with contents, use `rm` with the `-r` (recursive) option.

### Syntax
```bash
rm -r [options] directory_name
```

### Common Option Combinations

| Options | Description |
|---------|-------------|
| `rm -r` | Remove directory and contents |
| `rm -ri` | Interactive removal (safer) |
| `rm -rf` | Force removal (dangerous!) |
| `rm -rv` | Verbose removal |

### Examples

**Remove a directory and its contents:**
```bash
$ rm -r myproject
```

**Interactive removal (recommended):**
```bash
$ rm -ri oldproject
rm: descend into directory 'oldproject'? y
rm: remove regular file 'oldproject/file.txt'? y
rm: remove directory 'oldproject'? y
```

**Verbose removal:**
```bash
$ rm -rv tempdir
removed 'tempdir/file1.txt'
removed 'tempdir/file2.txt'
removed directory 'tempdir'
```

⚠️ **Warning:** Be extremely careful with `rm -rf`! It will delete everything without asking.

---

## 4. Copying Directories (`cp -r`)

To copy directories, use `cp` with the `-r` (recursive) option.

### Syntax
```bash
cp -r source_directory destination_directory
```

### Examples

**Copy a directory and its contents:**
```bash
$ cp -r project project_backup
```

**Copy to a different location:**
```bash
$ cp -r mydir /path/to/destination/
```

**Copy with verbose output:**
```bash
$ cp -rv folder1 folder2
'folder1/file1.txt' -> 'folder2/file1.txt'
'folder1/subdir' -> 'folder2/subdir'
```

---

## 5. Moving Directories (`mv`)

Moving directories works the same as moving files.

### Examples

**Rename a directory:**
```bash
$ mv oldname newname
```

**Move a directory to another location:**
```bash
$ mv myproject /path/to/new/location/
```

**Move and rename:**
```bash
$ mv old_project /path/to/new/new_project_name
```

---

## 6. Viewing Directory Structure (`tree`)

The `tree` command displays directory structure in a tree format. (May need to install separately)

### Installation
```bash
# On Debian/Ubuntu
$ sudo apt install tree

# On Android Termux
$ pkg install tree
```

### Examples

**Display current directory tree:**
```bash
$ tree
.
├── documents
│   ├── file1.txt
│   └── file2.txt
├── projects
│   └── web
│       └── index.html
└── README.md
```

**Limit depth:**
```bash
$ tree -L 2
# Shows only 2 levels deep
```

**Show only directories:**
```bash
$ tree -d
```

**Show with file sizes:**
```bash
$ tree -h
```

---

## Practical Exercises

### Exercise 1: Creating a Project Structure
```bash
# Create a complete project structure in one command
$ mkdir -p myproject/{src,docs,tests,bin}

# Verify the structure
$ ls -R myproject/
```

### Exercise 2: Working with Nested Directories
```bash
# Create a deep directory structure
$ mkdir -p company/departments/engineering/teams/backend

# Navigate to the deepest level
$ cd company/departments/engineering/teams/backend

# Verify location
$ pwd
```

### Exercise 3: Copying Directory Trees
```bash
# Create a sample project
$ mkdir -p project/src
$ touch project/src/main.py project/src/utils.py
$ touch project/README.md

# Create a backup
$ cp -r project project_backup

# Verify both exist
$ ls -R project project_backup
```

### Exercise 4: Safe Directory Removal
```bash
# Create test directories
$ mkdir -p test/subdir1/subdir2
$ touch test/file.txt test/subdir1/file.txt

# Try to remove with rmdir (will fail)
$ rmdir test
rmdir: failed to remove 'test': Directory not empty

# Remove correctly
$ rm -ri test
```

### Exercise 5: Organizing Files into Directories
```bash
# Create some files
$ touch doc1.txt doc2.txt image1.jpg image2.jpg

# Create directories for organization
$ mkdir documents images

# Move files to appropriate directories
$ mv doc*.txt documents/
$ mv *.jpg images/

# Verify organization
$ ls documents/ images/
```

---

## Real-World Scenario: Setting Up a Web Project

```bash
# Create a complete web project structure
$ mkdir -p mywebsite/{css,js,images,pages}

# Create some initial files
$ touch mywebsite/index.html
$ touch mywebsite/css/style.css
$ touch mywebsite/js/script.js
$ touch mywebsite/pages/about.html

# View the structure (if tree is installed)
$ tree mywebsite/

# Or without tree:
$ ls -R mywebsite/

# Create a backup before making changes
$ cp -r mywebsite mywebsite_backup

# Make changes to the project
# ... work on your project ...

# If you need to start over
$ rm -r mywebsite
$ mv mywebsite_backup mywebsite
```

---

## Tips and Best Practices

1. **Use `-p` for creating nested directories:**
   ```bash
   # Instead of:
   $ mkdir parent
   $ cd parent
   $ mkdir child
   
   # Do this:
   $ mkdir -p parent/child
   ```

2. **Always verify before removing:**
   ```bash
   $ ls -R dirtoremove/    # See what's inside
   $ rm -ri dirtoremove/   # Remove interactively
   ```

3. **Create directory structures in one command:**
   ```bash
   $ mkdir -p project/{src,test,docs}/{python,java,cpp}
   # Creates: project/src/python, project/src/java, etc.
   ```

4. **Backup before major changes:**
   ```bash
   $ cp -r important_dir important_dir_backup_$(date +%Y%m%d)
   ```

5. **Use descriptive directory names:**
   ```bash
   # Good:
   $ mkdir user-authentication-module
   
   # Avoid:
   $ mkdir stuff
   ```

---

## Common Directory Patterns

### Application Structure
```bash
mkdir -p app/{src,tests,docs,config}
```

### Document Organization
```bash
mkdir -p documents/{2024,2025,2026}/{projects,reports,drafts}
```

### Media Organization
```bash
mkdir -p media/{images,videos,audio}/{personal,work}
```

### Development Project
```bash
mkdir -p project/{src/{main,test},lib,docs,build,dist}
```

---

## Command Cheat Sheet

```bash
mkdir dir                        # Create directory
mkdir -p parent/child           # Create nested directories
mkdir dir1 dir2 dir3            # Create multiple directories
rmdir emptydir                  # Remove empty directory
rm -r dir                       # Remove directory and contents
rm -ri dir                      # Remove interactively (safer)
cp -r source dest               # Copy directory
mv olddir newdir                # Rename/move directory
tree                            # Display directory tree
tree -L 2                       # Limit tree depth to 2
ls -R                           # List recursively (alternative to tree)
```

---

## Common Mistakes to Avoid

1. **Forgetting `-r` when copying directories:**
   ```bash
   $ cp mydir backup  # Wrong! Won't work
   $ cp -r mydir backup  # Correct
   ```

2. **Using `rm -rf` without checking:**
   ```bash
   # NEVER do this without being absolutely sure:
   $ rm -rf /    # Would try to delete your entire system!
   ```

3. **Not using `-p` for nested directories:**
   ```bash
   $ mkdir project/src/main  # Will fail if project doesn't exist
   $ mkdir -p project/src/main  # Works correctly
   ```

---

## Next Steps

Now that you understand directory operations, proceed to [Lesson 4: File Permissions](../04-permissions/README.md) to learn about Linux security and permissions.

---

## Additional Resources

- Practice creating complex directory structures
- Experiment with different organization schemes
- Use `man mkdir` and `man rmdir` for more details
- Consider using `tree` to visualize your directory structures
