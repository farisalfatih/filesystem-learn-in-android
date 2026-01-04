# Lesson 6: File Content Operations

## Learning Objectives

By the end of this lesson, you will be able to:
- View file contents in different ways
- Extract specific portions of files
- Count lines, words, and characters
- Compare files
- Process and manipulate text files
- Combine commands with pipes

## Commands Covered

- `cat` - Display file contents
- `head` - View beginning of files
- `tail` - View end of files
- `less` / `more` - Page through files
- `wc` - Word count statistics
- `sort` - Sort lines
- `uniq` - Remove duplicate lines
- `diff` - Compare files

---

## 1. Displaying File Contents (`cat`)

We've seen `cat` before, but let's explore it more deeply.

### Basic Usage
```bash
# Display file
$ cat file.txt

# Display multiple files
$ cat file1.txt file2.txt

# Display with line numbers
$ cat -n file.txt

# Display with line numbers (non-blank lines only)
$ cat -b file.txt

# Show tab characters as ^I
$ cat -T file.txt

# Show end of lines as $
$ cat -E file.txt

# Show all special characters
$ cat -A file.txt
```

### Creating Files with cat
```bash
# Create a new file
$ cat > newfile.txt
Type your content here
Press Ctrl+D to save

# Append to existing file
$ cat >> existingfile.txt
Additional content
Press Ctrl+D to save

# Combine files into new file
$ cat file1.txt file2.txt > combined.txt
```

---

## 2. Viewing File Beginning (`head`)

The `head` command shows the first part of files.

### Syntax
```bash
head [options] file
```

### Examples

**Show first 10 lines (default):**
```bash
$ head file.txt
```

**Show first N lines:**
```bash
$ head -n 20 file.txt
# or simply
$ head -20 file.txt
```

**Show first N bytes:**
```bash
$ head -c 100 file.txt
```

**View first lines of multiple files:**
```bash
$ head -n 5 file1.txt file2.txt
==> file1.txt <==
[first 5 lines]

==> file2.txt <==
[first 5 lines]
```

**Useful for:**
- Previewing file contents
- Reading log file headers
- Checking file format
- Quick file verification

---

## 3. Viewing File End (`tail`)

The `tail` command shows the last part of files.

### Syntax
```bash
tail [options] file
```

### Examples

**Show last 10 lines (default):**
```bash
$ tail file.txt
```

**Show last N lines:**
```bash
$ tail -n 20 file.txt
# or simply
$ tail -20 file.txt
```

**Show last N bytes:**
```bash
$ tail -c 100 file.txt
```

**Follow file updates (monitoring):**
```bash
$ tail -f log.txt
# Press Ctrl+C to stop
```

**Start from line N:**
```bash
# Show from line 100 to end
$ tail -n +100 file.txt
```

**Useful for:**
- Monitoring log files in real-time
- Viewing recent entries
- Debugging applications
- Watching file changes

---

## 4. Paging Through Files (`less` and `more`)

For large files, use `less` or `more` to view content page by page.

### Using `less` (recommended)

```bash
$ less largefile.txt
```

**Navigation in less:**
- `Space` or `Page Down` - Next page
- `b` or `Page Up` - Previous page
- `Enter` or `Down Arrow` - Next line
- `Up Arrow` - Previous line
- `/pattern` - Search forward
- `?pattern` - Search backward
- `n` - Next search result
- `N` - Previous search result
- `g` - Go to beginning
- `G` - Go to end
- `q` - Quit

### Using `more`

```bash
$ more file.txt
```

**Navigation in more:**
- `Space` - Next page
- `Enter` - Next line
- `q` - Quit
- `/pattern` - Search

**Less vs More:**
- `less` is more powerful (can scroll backward)
- `less` doesn't need to read entire file first
- `less` has better search capabilities
- Use `less` when available

---

## 5. Counting File Statistics (`wc`)

The `wc` command counts lines, words, and characters.

### Syntax
```bash
wc [options] file
```

### Options

**Count lines:**
```bash
$ wc -l file.txt
100 file.txt
```

**Count words:**
```bash
$ wc -w file.txt
500 file.txt
```

**Count characters:**
```bash
$ wc -m file.txt
2500 file.txt
```

**Count bytes:**
```bash
$ wc -c file.txt
2500 file.txt
```

**All statistics (default):**
```bash
$ wc file.txt
100  500  2500 file.txt
# lines words bytes filename
```

**Multiple files:**
```bash
$ wc -l file1.txt file2.txt file3.txt
100 file1.txt
200 file2.txt
150 file3.txt
450 total
```

---

## 6. Sorting Lines (`sort`)

The `sort` command arranges lines in order.

### Basic Usage

**Sort alphabetically:**
```bash
$ sort names.txt
```

**Sort in reverse:**
```bash
$ sort -r names.txt
```

**Sort numerically:**
```bash
$ sort -n numbers.txt
```

**Sort and remove duplicates:**
```bash
$ sort -u file.txt
```

**Case-insensitive sort:**
```bash
$ sort -f file.txt
```

**Sort by column:**
```bash
# Sort by second column
$ sort -k 2 data.txt

# Sort by numeric value in third column
$ sort -k 3 -n data.txt
```

### Examples

**Sort and save:**
```bash
$ sort unsorted.txt > sorted.txt
```

**Sort multiple files:**
```bash
$ sort file1.txt file2.txt > combined_sorted.txt
```

---

## 7. Removing Duplicate Lines (`uniq`)

The `uniq` command filters out repeated lines. **Note:** Input must be sorted first!

### Basic Usage

**Remove adjacent duplicates:**
```bash
$ sort file.txt | uniq
```

**Count occurrences:**
```bash
$ sort file.txt | uniq -c
```

**Show only duplicates:**
```bash
$ sort file.txt | uniq -d
```

**Show only unique lines:**
```bash
$ sort file.txt | uniq -u
```

**Case-insensitive:**
```bash
$ sort file.txt | uniq -i
```

### Examples

**Find duplicate entries:**
```bash
$ sort access.log | uniq -c | sort -rn
# Shows most frequent entries first
```

---

## 8. Comparing Files (`diff`)

The `diff` command shows differences between files.

### Basic Usage

**Compare two files:**
```bash
$ diff file1.txt file2.txt
```

**Side-by-side comparison:**
```bash
$ diff -y file1.txt file2.txt
```

**Unified format (easier to read):**
```bash
$ diff -u file1.txt file2.txt
```

**Ignore case differences:**
```bash
$ diff -i file1.txt file2.txt
```

**Ignore whitespace:**
```bash
$ diff -w file1.txt file2.txt
```

**Compare directories:**
```bash
$ diff -r dir1/ dir2/
```

### Understanding diff Output

```bash
$ diff file1.txt file2.txt
2c2
< This line is different
---
> This line is changed
```

- `2c2` means line 2 changed
- `<` indicates line from first file
- `>` indicates line from second file
- `a` means added
- `d` means deleted
- `c` means changed

---

## 9. Piping Commands Together

Combine commands using pipes (`|`) for powerful text processing.

### Examples

**Count unique words:**
```bash
$ cat file.txt | tr ' ' '\n' | sort | uniq -c | sort -rn
```

**Find most common lines in log:**
```bash
$ cat access.log | sort | uniq -c | sort -rn | head -10
```

**Show largest files:**
```bash
$ ls -l | sort -k 5 -rn | head -10
```

**Count total lines in multiple files:**
```bash
$ cat *.txt | wc -l
```

**Search and count:**
```bash
$ grep "error" log.txt | wc -l
```

---

## Practical Exercises

### Exercise 1: Viewing Files Different Ways
```bash
# Create a test file with 100 lines
$ for i in {1..100}; do echo "Line $i" >> test.txt; done

# View first 10 lines
$ head test.txt

# View last 10 lines
$ tail test.txt

# View middle section (lines 40-60)
$ head -60 test.txt | tail -21

# Page through file
$ less test.txt
```

### Exercise 2: Monitoring a Log File
```bash
# In one terminal, watch log file
$ tail -f /var/log/syslog

# In another terminal, generate activity
$ logger "Test log entry"

# You should see it appear in the first terminal
```

### Exercise 3: Working with Statistics
```bash
# Create a sample file
$ cat > colors.txt
red
blue
red
green
blue
red
^D

# Count total lines
$ wc -l colors.txt

# Sort and count occurrences
$ sort colors.txt | uniq -c
  1 blue
  2 blue
  1 green
  3 red

# Find most common
$ sort colors.txt | uniq -c | sort -rn | head -1
```

### Exercise 4: Text Processing Pipeline
```bash
# Create a CSV file
$ cat > data.csv
Name,Age,City
Alice,25,NYC
Bob,30,LA
Charlie,25,NYC
David,30,NYC
^D

# Extract ages column, sort, count unique
$ cat data.csv | tail -n +2 | cut -d',' -f2 | sort | uniq -c
```

### Exercise 5: Comparing Files
```bash
# Create two versions of a file
$ echo -e "Line 1\nLine 2\nLine 3" > version1.txt
$ echo -e "Line 1\nLine 2 modified\nLine 3\nLine 4" > version2.txt

# Compare them
$ diff version1.txt version2.txt

# Side-by-side comparison
$ diff -y version1.txt version2.txt
```

---

## Real-World Scenarios

### Finding Top IP Addresses in Access Log
```bash
$ cat access.log | cut -d' ' -f1 | sort | uniq -c | sort -rn | head -10
```

### Analyzing System Logs
```bash
# Count errors per hour
$ grep "error" /var/log/syslog | cut -d' ' -f1-3 | uniq -c
```

### Monitoring Live Log with Filtering
```bash
$ tail -f application.log | grep --line-buffered "ERROR"
```

### Creating Reports
```bash
# Word frequency analysis
$ cat document.txt | tr '[:upper:]' '[:lower:]' | tr -s ' ' '\n' | sort | uniq -c | sort -rn > word_freq.txt
```

### Comparing Configuration Files
```bash
$ diff -u /etc/config.conf /etc/config.conf.backup > config_changes.patch
```

---

## Command Cheat Sheet

```bash
# Viewing
cat file.txt                      # Display entire file
cat -n file.txt                   # Display with line numbers
head file.txt                     # First 10 lines
head -20 file.txt                 # First 20 lines
tail file.txt                     # Last 10 lines
tail -20 file.txt                 # Last 20 lines
tail -f file.txt                  # Follow file updates
less file.txt                     # Page through file
more file.txt                     # Page through file (basic)

# Statistics
wc file.txt                       # Lines, words, bytes
wc -l file.txt                    # Count lines
wc -w file.txt                    # Count words
wc -c file.txt                    # Count bytes

# Processing
sort file.txt                     # Sort lines
sort -r file.txt                  # Reverse sort
sort -n file.txt                  # Numeric sort
uniq file.txt                     # Remove duplicates
uniq -c file.txt                  # Count occurrences
diff file1.txt file2.txt          # Compare files
diff -y file1.txt file2.txt       # Side-by-side diff
```

---

## Tips and Best Practices

1. **Use less for large files:**
   ```bash
   $ less huge_file.log   # Better than cat
   ```

2. **Always sort before uniq:**
   ```bash
   $ sort file.txt | uniq   # Correct
   $ uniq file.txt          # May miss duplicates
   ```

3. **Combine commands efficiently:**
   ```bash
   # Good: single pipeline
   $ grep "error" log.txt | wc -l
   
   # Inefficient: multiple steps
   $ grep "error" log.txt > temp.txt
   $ wc -l temp.txt
   $ rm temp.txt
   ```

4. **Monitor logs effectively:**
   ```bash
   $ tail -f log.txt | grep --line-buffered "pattern"
   ```

5. **Save processing results:**
   ```bash
   $ sort large_file.txt | uniq > processed.txt
   ```

---

## Next Steps

You've now completed the core filesystem lessons! Proceed to the [Practical Exercises](../../exercises/README.md) to apply everything you've learned in real-world scenarios.

---

## Additional Resources

- Learn text editors: `nano`, `vim`, `emacs`
- Explore advanced tools: `awk`, `sed`, `cut`, `paste`
- Study regular expressions for powerful pattern matching
- Use `man` pages for detailed command documentation
