# Quick Reference Guide

Quick reference for common Linux filesystem commands. For detailed explanations, see the individual lessons.

## Navigation

```bash
pwd                     # Show current directory
ls                      # List files
ls -la                  # List all files with details
cd directory            # Change to directory
cd ~                    # Go to home directory
cd ..                   # Go to parent directory
cd -                    # Go to previous directory
```

## File Operations

```bash
touch file.txt          # Create empty file
cat file.txt            # View file contents
cp file.txt copy.txt    # Copy file
mv old.txt new.txt      # Rename/move file
rm file.txt             # Delete file
rm -i file.txt          # Delete with confirmation
```

## Directory Operations

```bash
mkdir dirname           # Create directory
mkdir -p path/to/dir    # Create nested directories
rmdir dirname           # Remove empty directory
rm -r dirname           # Remove directory and contents
rm -ri dirname          # Remove interactively (safer)
cp -r dir1 dir2         # Copy directory
```

## Permissions

```bash
chmod 644 file.txt      # Set permissions (rw-r--r--)
chmod 755 script.sh     # Set permissions (rwxr-xr-x)
chmod +x script.sh      # Make executable
chmod u+x file          # Add execute for owner
chmod g-w file          # Remove write for group
chmod o=r file          # Set read-only for others
ls -l                   # View permissions
```

## Searching

```bash
find . -name "*.txt"              # Find files by name
find . -type f -size +100M        # Find large files
find . -mtime -7                  # Files modified in last 7 days
grep "pattern" file.txt           # Search in file
grep -r "pattern" directory/      # Recursive search
grep -i "pattern" file            # Case-insensitive search
which command                     # Find command location
locate filename                   # Quick file search
```

## File Content

```bash
cat file.txt            # Display file
head file.txt           # First 10 lines
head -20 file.txt       # First 20 lines
tail file.txt           # Last 10 lines
tail -f log.txt         # Follow file updates
less file.txt           # Page through file
more file.txt           # Page through file (basic)
wc file.txt             # Count lines, words, bytes
wc -l file.txt          # Count lines only
sort file.txt           # Sort lines
uniq file.txt           # Remove duplicates
diff file1.txt file2.txt # Compare files
```

## Combining Commands

```bash
# Pipes (|) - send output to next command
cat file.txt | grep "pattern"
find . -name "*.log" | wc -l
ls -l | sort -k 5 -rn | head -10

# Redirection
command > file.txt          # Write output to file (overwrite)
command >> file.txt         # Append output to file
command 2> error.log        # Redirect errors to file
command &> all.log          # Redirect all output to file
```

## Wildcards

```bash
*               # Matches any characters
?               # Matches single character
[abc]           # Matches a, b, or c
[a-z]           # Matches any lowercase letter
[0-9]           # Matches any digit

# Examples
ls *.txt        # All .txt files
rm test?.log    # test1.log, test2.log, etc.
cp [A-Z]*.txt backup/  # Files starting with capital letter
```

## Special Characters

```bash
~               # Home directory
.               # Current directory
..              # Parent directory
/               # Root directory
-               # Previous directory (with cd)
```

## Shortcuts

```bash
Ctrl+C          # Cancel current command
Ctrl+D          # Exit (or end input)
Ctrl+L          # Clear screen
Ctrl+R          # Search command history
Tab             # Auto-complete
Up/Down Arrow   # Browse command history
!!              # Repeat last command
!$              # Last argument of previous command
```

## Useful Combinations

### Find and delete old temporary files
```bash
find /tmp -name "*.tmp" -mtime +7 -delete
```

### Count total lines in all Python files
```bash
find . -name "*.py" -exec wc -l {} + | tail -1
```

### Find largest files
```bash
find . -type f -exec ls -lh {} + | sort -k 5 -rh | head -10
```

### Search and count occurrences
```bash
grep -r "ERROR" logs/ | wc -l
```

### Monitor log for errors
```bash
tail -f /var/log/syslog | grep --line-buffered "error"
```

### Create backup with timestamp
```bash
cp -r project project_backup_$(date +%Y%m%d_%H%M%S)
```

### Find duplicate file names
```bash
find . -type f -printf "%f\n" | sort | uniq -d
```

### Disk usage of directories
```bash
du -sh */ | sort -h
```

## Common Patterns

### Safe file deletion
```bash
# Always check first
ls file_to_delete.txt
# Then delete
rm file_to_delete.txt
```

### Creating directory structure
```bash
mkdir -p project/{src,docs,tests}/{python,java}
```

### Batch rename files
```bash
for file in *.txt; do mv "$file" "${file%.txt}.md"; done
```

### Recursive permission change
```bash
# Directories
find . -type d -exec chmod 755 {} \;
# Files
find . -type f -exec chmod 644 {} \;
```

## Tips

1. **Use Tab completion** - Start typing and press Tab
2. **Use history** - Press Up arrow for previous commands
3. **Test before executing** - Use `echo` to preview commands
4. **Use `-i` flag** - Interactive mode asks for confirmation
5. **Read man pages** - `man command` for detailed help
6. **Start simple** - Master basic commands before complex ones
7. **Practice regularly** - Repetition builds proficiency
8. **Use `--help`** - Quick help for most commands

## Getting Help

```bash
man command             # Full manual page
command --help          # Quick help
info command            # Info documentation
which command           # Find command location
type command            # Show command type
apropos keyword         # Search man pages
```

## Safety Checks

### Before deleting
```bash
# Preview what will be deleted
ls file_to_delete
# Or with find
find . -name "*.tmp"
# Then delete
rm file_to_delete
```

### Before recursive operations
```bash
# Test with echo
echo rm -r directory/
# Verify
ls -R directory/
# Then execute
rm -r directory/
```

## Common Mistakes to Avoid

1. ❌ `rm -rf *` without checking location
2. ❌ `chmod 777` on sensitive files
3. ❌ Forgetting quotes with spaces: `cd my folder` vs `cd "my folder"`
4. ❌ Not backing up before major changes
5. ❌ Assuming case-insensitivity (Linux is case-sensitive)
6. ❌ Using wildcards without testing first

## Learn More

- **Lessons**: See [lessons/](lessons/) directory for detailed tutorials
- **Exercises**: Practice with [exercises/](exercises/)
- **Main README**: [README.md](README.md) for full documentation
- **Contributing**: [CONTRIBUTING.md](CONTRIBUTING.md) to help improve this guide

---

**Remember**: Type commands yourself rather than copy-pasting to build muscle memory!
