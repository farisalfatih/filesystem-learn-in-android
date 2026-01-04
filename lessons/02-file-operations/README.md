# Lesson 2: File Operations

## Learning Objectives

By the end of this lesson, you will be able to:
- Create empty files and files with content
- View file contents in various ways
- Copy files to different locations
- Move and rename files
- Delete files safely

## Commands Covered

- `touch` - Create empty files
- `cat` - Concatenate and display files
- `cp` - Copy files
- `mv` - Move or rename files
- `rm` - Remove files

---

## 1. Creating Files (`touch`)

The `touch` command creates an empty file or updates the timestamp of an existing file.

### Syntax
```bash
touch [options] filename
```

### Examples

**Create a single file:**
```bash
$ touch myfile.txt
```

**Create multiple files at once:**
```bash
$ touch file1.txt file2.txt file3.txt
```

**Create a file with a space in the name:**
```bash
$ touch "my document.txt"
# or
$ touch my\ document.txt
```

### Try it yourself
```bash
# Create a test file
$ touch test.txt

# Verify it was created
$ ls -l test.txt
```

---

## 2. Viewing File Contents (`cat`)

The `cat` command displays the contents of files.

### Syntax
```bash
cat [options] filename
```

### Examples

**View a single file:**
```bash
$ cat myfile.txt
```

**View multiple files:**
```bash
$ cat file1.txt file2.txt
```

**Create a file with content:**
```bash
$ cat > newfile.txt
Type your content here
Press Ctrl+D when done
```

**Append to a file:**
```bash
$ cat >> existingfile.txt
More content to add
Press Ctrl+D when done
```

**Display with line numbers:**
```bash
$ cat -n myfile.txt
```

### Alternative viewing commands
- `less` - View file page by page (recommended for large files)
- `more` - Similar to less (older version)
- `head` - View first few lines
- `tail` - View last few lines

---

## 3. Copying Files (`cp`)

The `cp` command copies files from one location to another.

### Syntax
```bash
cp [options] source destination
```

### Common Options

| Option | Description |
|--------|-------------|
| `-i` | Interactive (prompt before overwrite) |
| `-r` | Recursive (copy directories) |
| `-v` | Verbose (show what's being copied) |
| `-u` | Update (copy only when source is newer) |
| `-p` | Preserve (keep original permissions and timestamps) |

### Examples

**Copy a file to the same directory with new name:**
```bash
$ cp original.txt copy.txt
```

**Copy to a different directory:**
```bash
$ cp file.txt /home/username/Documents/
```

**Copy with a new name to different directory:**
```bash
$ cp file.txt /home/username/Documents/newname.txt
```

**Copy multiple files to a directory:**
```bash
$ cp file1.txt file2.txt file3.txt /destination/directory/
```

**Interactive copy (ask before overwriting):**
```bash
$ cp -i source.txt destination.txt
```

**Copy with verbose output:**
```bash
$ cp -v file.txt backup/
'file.txt' -> 'backup/file.txt'
```

---

## 4. Moving and Renaming Files (`mv`)

The `mv` command moves files to a new location or renames them.

### Syntax
```bash
mv [options] source destination
```

### Common Options

| Option | Description |
|--------|-------------|
| `-i` | Interactive (prompt before overwrite) |
| `-v` | Verbose (show what's being moved) |
| `-n` | No clobber (don't overwrite existing files) |
| `-u` | Update (move only when source is newer) |

### Examples

**Rename a file:**
```bash
$ mv oldname.txt newname.txt
```

**Move a file to another directory:**
```bash
$ mv file.txt /home/username/Documents/
```

**Move and rename simultaneously:**
```bash
$ mv file.txt /home/username/Documents/newname.txt
```

**Move multiple files to a directory:**
```bash
$ mv file1.txt file2.txt file3.txt /destination/
```

**Interactive move:**
```bash
$ mv -i source.txt destination.txt
mv: overwrite 'destination.txt'? 
```

---

## 5. Removing Files (`rm`)

The `rm` command deletes files. **Be careful!** Deleted files cannot be easily recovered.

### Syntax
```bash
rm [options] filename
```

### Common Options

| Option | Description |
|--------|-------------|
| `-i` | Interactive (prompt before each removal) |
| `-f` | Force (ignore nonexistent files, no prompts) |
| `-v` | Verbose (show what's being removed) |
| `-r` | Recursive (remove directories and contents) |

### Examples

**Remove a single file:**
```bash
$ rm file.txt
```

**Remove multiple files:**
```bash
$ rm file1.txt file2.txt file3.txt
```

**Interactive removal (safer):**
```bash
$ rm -i important.txt
rm: remove regular file 'important.txt'? 
```

**Remove with verbose output:**
```bash
$ rm -v oldfile.txt
removed 'oldfile.txt'
```

**Remove all .txt files in current directory:**
```bash
$ rm *.txt
```

⚠️ **Warning:** The `rm` command is permanent. There is no "recycle bin" in Linux command line!

---

## Practical Exercises

### Exercise 1: File Creation
```bash
# Create three empty files
$ touch notes.txt ideas.txt tasks.txt

# Verify they were created
$ ls -l *.txt
```

### Exercise 2: File Copying
```bash
# Create a directory for backups
$ mkdir backup

# Copy a file to the backup directory
$ cp notes.txt backup/

# Verify the copy
$ ls backup/

# Copy with a new name
$ cp notes.txt notes_backup.txt
```

### Exercise 3: File Renaming
```bash
# Create a file with a temporary name
$ touch temp.txt

# Rename it to something more descriptive
$ mv temp.txt important_notes.txt

# Verify the rename
$ ls -l important_notes.txt
```

### Exercise 4: File Moving
```bash
# Create a test directory structure
$ mkdir -p projects/project1

# Create a file
$ touch document.txt

# Move it to the project directory
$ mv document.txt projects/project1/

# Verify it's there
$ ls projects/project1/
```

### Exercise 5: Safe File Removal
```bash
# Create some test files
$ touch test1.txt test2.txt test3.txt

# Remove one file with confirmation
$ rm -i test1.txt

# Remove remaining test files
$ rm test*.txt

# Verify they're gone
$ ls test*.txt
```

---

## Real-World Scenario

Let's organize some document files:

```bash
# Create some sample files
$ touch report.txt draft.txt final.txt

# Create directories for organization
$ mkdir documents archive

# Move current work to documents
$ mv report.txt draft.txt documents/

# Move old work to archive
$ mv final.txt archive/

# Create a backup of an important file
$ cp documents/report.txt documents/report_backup.txt

# View the organized structure
$ ls -R
```

---

## Tips and Best Practices

1. **Always use `-i` with `rm`** when you're starting out:
   ```bash
   alias rm='rm -i'  # Add to your .bashrc
   ```

2. **Make backups before overwriting:**
   ```bash
   $ cp important.txt important.txt.backup
   ```

3. **Use wildcards carefully:**
   ```bash
   $ ls *.txt    # Preview what will be affected
   $ rm *.txt    # Then remove
   ```

4. **Test with `echo` first:**
   ```bash
   $ echo rm *.txt    # See what would be executed
   ```

5. **Create backups automatically:**
   ```bash
   $ cp -i file.txt backup/  # -i prevents accidental overwrites
   ```

---

## Command Cheat Sheet

```bash
touch file.txt                    # Create empty file
cat file.txt                      # View file contents
cat > file.txt                    # Create file with content (Ctrl+D to save)
cat file1.txt file2.txt          # View multiple files
cp file.txt newfile.txt          # Copy file
cp -r dir1 dir2                  # Copy directory
mv oldname.txt newname.txt       # Rename file
mv file.txt /path/to/dir/        # Move file
rm file.txt                      # Remove file
rm -i file.txt                   # Remove with confirmation
```

---

## Common Mistakes to Avoid

1. **Don't do this:**
   ```bash
   $ rm -rf *    # This removes everything in the current directory!
   ```

2. **Be careful with spaces:**
   ```bash
   $ rm my file.txt     # This tries to remove "my" and "file.txt"
   $ rm "my file.txt"   # Correct way
   ```

3. **Check your location before removing:**
   ```bash
   $ pwd              # Where am I?
   $ ls              # What's here?
   $ rm -i file.txt  # Now remove safely
   ```

---

## Next Steps

Now that you can work with files, proceed to [Lesson 3: Directory Operations](../03-directory-operations/README.md) to learn how to manage directories effectively.

---

## Additional Resources

- Practice in a test directory before working with important files
- Use `man cp`, `man mv`, `man rm` to see full documentation
- Consider using a GUI file manager alongside the command line while learning
