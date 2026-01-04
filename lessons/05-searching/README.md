# Lesson 5: Searching and Finding Files

## Learning Objectives

By the end of this lesson, you will be able to:
- Search for files by name, type, and properties
- Search within file contents
- Use wildcards and patterns effectively
- Locate commands and executables
- Combine search commands for powerful queries

## Commands Covered

- `find` - Search for files and directories
- `locate` - Quick file search using database
- `grep` - Search text within files
- `which` - Find command locations
- `whereis` - Locate binary, source, and manual pages

---

## 1. Finding Files by Name (`find`)

The `find` command is the most powerful file search tool in Linux.

### Basic Syntax
```bash
find [path] [options] [expression]
```

### Search by Name

**Find files by exact name:**
```bash
$ find /home/user -name "document.txt"
```

**Case-insensitive search:**
```bash
$ find /home/user -iname "document.txt"
```

**Find with wildcards:**
```bash
# Find all .txt files
$ find . -name "*.txt"

# Find all files starting with "test"
$ find . -name "test*"

# Find all files containing "data"
$ find . -name "*data*"
```

### Search in Current Directory
```bash
# Search in current directory
$ find . -name "*.py"

# Search only in current directory (not subdirectories)
$ find . -maxdepth 1 -name "*.txt"
```

---

## 2. Finding by File Type

**Find only directories:**
```bash
$ find . -type d
```

**Find only files:**
```bash
$ find . -type f
```

**Find symbolic links:**
```bash
$ find . -type l
```

---

## 3. Finding by Size

**Find files larger than 100MB:**
```bash
$ find . -type f -size +100M
```

**Find files smaller than 10KB:**
```bash
$ find . -type f -size -10k
```

**Find files exactly 1GB:**
```bash
$ find . -type f -size 1G
```

**Size units:**
- `b` - 512-byte blocks (default)
- `c` - bytes
- `k` - kilobytes
- `M` - megabytes
- `G` - gigabytes

---

## 4. Finding by Time

**Find files modified in last 7 days:**
```bash
$ find . -mtime -7
```

**Find files modified more than 30 days ago:**
```bash
$ find . -mtime +30
```

**Find files accessed in last 24 hours:**
```bash
$ find . -atime -1
```

**Find files modified in last 2 hours:**
```bash
$ find . -mmin -120
```

Time options:
- `-mtime` - Modification time (days)
- `-atime` - Access time (days)
- `-ctime` - Change time (days)
- `-mmin` - Modification time (minutes)

---

## 5. Finding by Permissions

**Find files with specific permissions:**
```bash
# Find files with 644 permissions
$ find . -perm 644

# Find files with at least read permission for others
$ find . -perm -o=r

# Find executable files
$ find . -perm /u+x
```

---

## 6. Executing Commands on Found Files

**Delete found files (be careful!):**
```bash
$ find . -name "*.tmp" -delete
```

**Execute command on each file:**
```bash
# Show details of found files
$ find . -name "*.log" -exec ls -lh {} \;

# Copy found files to another directory
$ find . -name "*.txt" -exec cp {} /backup/ \;
```

**Confirm before executing:**
```bash
$ find . -name "*.bak" -ok rm {} \;
# Asks for confirmation for each file
```

---

## 7. Complex Find Queries

**Combine multiple conditions (AND):**
```bash
# Find .txt files larger than 1MB
$ find . -name "*.txt" -size +1M

# Find directories modified in last 7 days
$ find . -type d -mtime -7
```

**OR conditions:**
```bash
# Find .txt OR .pdf files
$ find . -name "*.txt" -o -name "*.pdf"

# Better readable version:
$ find . \( -name "*.txt" -o -name "*.pdf" \)
```

**NOT conditions:**
```bash
# Find all files EXCEPT .txt files
$ find . -type f ! -name "*.txt"
```

---

## 8. Quick File Location (`locate`)

The `locate` command searches a pre-built database for fast results.

### Update the Database
```bash
$ sudo updatedb
```

### Basic Usage

**Find files containing "document":**
```bash
$ locate document
```

**Case-insensitive search:**
```bash
$ locate -i DOCUMENT
```

**Limit results:**
```bash
$ locate -n 10 document
# Shows only first 10 results
```

**Search for exact filename:**
```bash
$ locate -b "\filename.txt"
```

### Locate vs Find

| Feature | locate | find |
|---------|--------|------|
| Speed | Very fast | Slower |
| Real-time | No (uses database) | Yes |
| Flexibility | Limited | Extensive |
| Installation | May need setup | Built-in |

---

## 9. Searching File Contents (`grep`)

The `grep` command searches for text patterns within files.

### Basic Syntax
```bash
grep [options] pattern [file...]
```

### Basic Usage

**Search in a single file:**
```bash
$ grep "error" log.txt
```

**Search in multiple files:**
```bash
$ grep "TODO" *.py
```

**Case-insensitive search:**
```bash
$ grep -i "warning" log.txt
```

**Show line numbers:**
```bash
$ grep -n "error" log.txt
```

---

## 10. Advanced grep Options

**Recursive search in directories:**
```bash
$ grep -r "function_name" src/
```

**Show only filenames with matches:**
```bash
$ grep -l "error" *.log
```

**Show only filenames without matches:**
```bash
$ grep -L "success" *.log
```

**Count matches:**
```bash
$ grep -c "error" log.txt
```

**Show context around matches:**
```bash
# Show 2 lines before and after
$ grep -C 2 "error" log.txt

# Show 3 lines before
$ grep -B 3 "error" log.txt

# Show 3 lines after
$ grep -A 3 "error" log.txt
```

**Invert match (show non-matching lines):**
```bash
$ grep -v "debug" log.txt
```

---

## 11. grep with Regular Expressions

**Match lines starting with pattern:**
```bash
$ grep "^Error" log.txt
```

**Match lines ending with pattern:**
```bash
$ grep "failed$" log.txt
```

**Match multiple patterns:**
```bash
$ grep -E "error|warning|critical" log.txt
# or
$ grep -e "error" -e "warning" log.txt
```

---

## 12. Finding Commands (`which` and `whereis`)

**Find executable location:**
```bash
$ which python
/usr/bin/python

$ which bash
/bin/bash
```

**Find command, source, and manual:**
```bash
$ whereis python
python: /usr/bin/python /usr/lib/python3.8 /usr/share/man/man1/python.1.gz
```

---

## Practical Exercises

### Exercise 1: Basic Find Operations
```bash
# Find all Python files in current directory and subdirectories
$ find . -name "*.py"

# Find all directories named "test"
$ find . -type d -name "test"

# Find files modified in the last day
$ find . -mtime -1
```

### Exercise 2: Finding Large Files
```bash
# Find files larger than 50MB
$ find /home -type f -size +50M

# Find and list them with sizes
$ find /home -type f -size +50M -exec ls -lh {} \;
```

### Exercise 3: Searching File Contents
```bash
# Create test files
$ echo "Error: file not found" > test1.txt
$ echo "Warning: low memory" > test2.txt
$ echo "Success: operation completed" > test3.txt

# Search for "Error"
$ grep "Error" test*.txt

# Case-insensitive search
$ grep -i "warning" test*.txt

# Show line numbers
$ grep -n ":" test*.txt
```

### Exercise 4: Combining Find and Grep
```bash
# Find all .txt files containing "error"
$ find . -name "*.txt" -exec grep -l "error" {} \;

# Find and display matches with context
$ find . -name "*.log" -exec grep -C 2 "failed" {} +
```

### Exercise 5: Cleaning Up Old Files
```bash
# Find files older than 30 days in /tmp
$ find /tmp -type f -mtime +30

# Delete them (be careful!)
$ find /tmp -type f -mtime +30 -delete

# Or interactively:
$ find /tmp -type f -mtime +30 -ok rm {} \;
```

---

## Real-World Scenarios

### Finding Duplicate File Names
```bash
# Find files with same name in different locations
$ find . -name "config.txt"
```

### Finding Empty Files and Directories
```bash
# Find empty files
$ find . -type f -empty

# Find empty directories
$ find . -type d -empty
```

### Finding Recently Modified Code
```bash
# Find Python files modified in last 7 days
$ find . -name "*.py" -mtime -7 -ls
```

### Searching Logs for Errors
```bash
# Find all log files and search for errors
$ find /var/log -name "*.log" -exec grep -i "error" {} +

# Count errors in each log file
$ find /var/log -name "*.log" -exec sh -c 'echo "{}:"; grep -c "error" "{}"' \;
```

### Finding Files by Owner
```bash
# Find files owned by specific user
$ find /home -user username

# Find files owned by specific group
$ find /home -group groupname
```

---

## Tips and Best Practices

1. **Test Before Deleting:**
   ```bash
   # First, see what will be deleted
   $ find . -name "*.tmp"
   
   # Then delete
   $ find . -name "*.tmp" -delete
   ```

2. **Use Quotes with Wildcards:**
   ```bash
   $ find . -name "*.txt"    # Correct
   $ find . -name *.txt      # May not work as expected
   ```

3. **Limit Search Depth:**
   ```bash
   $ find . -maxdepth 2 -name "*.txt"
   # Searches only 2 levels deep
   ```

4. **Combine grep with Other Commands:**
   ```bash
   $ ls -l | grep "Jan"      # Filter ls output
   $ history | grep "find"   # Search command history
   ```

5. **Save Search Results:**
   ```bash
   $ find . -name "*.log" > log_files.txt
   $ grep -r "TODO" src/ > todos.txt
   ```

---

## Command Cheat Sheet

```bash
# Find
find . -name "*.txt"                    # Find by name
find . -iname "*.TXT"                   # Case-insensitive
find . -type f                          # Find files only
find . -type d                          # Find directories only
find . -size +100M                      # Files larger than 100MB
find . -mtime -7                        # Modified in last 7 days
find . -name "*.tmp" -delete            # Find and delete

# Locate
locate filename                         # Quick search
sudo updatedb                           # Update locate database

# Grep
grep "pattern" file.txt                 # Search in file
grep -r "pattern" directory/            # Recursive search
grep -i "pattern" file                  # Case-insensitive
grep -n "pattern" file                  # Show line numbers
grep -v "pattern" file                  # Invert match
grep -l "pattern" *                     # Show only filenames
grep -c "pattern" file                  # Count matches

# Which/Whereis
which command                           # Find command location
whereis command                         # Find binary, source, manual
```

---

## Common Search Patterns

**Find all scripts:**
```bash
$ find . -name "*.sh" -o -name "*.py" -o -name "*.pl"
```

**Find large files:**
```bash
$ find / -type f -size +1G 2>/dev/null
```

**Find world-writable files (security):**
```bash
$ find / -perm -002 -type f 2>/dev/null
```

**Find and count lines in all Python files:**
```bash
$ find . -name "*.py" -exec wc -l {} + | tail -1
```

---

## Next Steps

Now that you can find files efficiently, proceed to [Lesson 6: File Content Operations](../06-content-operations/README.md) to learn advanced content manipulation.

---

## Additional Resources

- Practice with different find predicates
- Learn regular expressions for powerful grep patterns
- Explore `ack` and `ag` as modern grep alternatives
- Use `man find`, `man grep`, `man locate` for complete documentation
