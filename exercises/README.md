# Practical Exercises

Welcome to the practical exercises section! Here you'll apply everything you've learned across all lessons in real-world scenarios.

## Exercise Categories

1. [Basic Practice](#basic-practice)
2. [Intermediate Challenges](#intermediate-challenges)
3. [Advanced Projects](#advanced-projects)
4. [Real-World Scenarios](#real-world-scenarios)

---

## Basic Practice

### Exercise 1: Personal File Organization System

**Objective:** Create a well-organized personal directory structure.

**Tasks:**
1. Create a directory structure for organizing personal files:
   ```
   ~/personal/
   ├── documents/
   │   ├── work/
   │   ├── personal/
   │   └── archive/
   ├── media/
   │   ├── photos/
   │   ├── videos/
   │   └── music/
   └── projects/
       ├── active/
       └── completed/
   ```

2. Create sample files in appropriate directories
3. Set appropriate permissions (private: 700, shared: 755)
4. Practice moving files between directories
5. Create backups of important directories

**Commands to use:** `mkdir -p`, `touch`, `chmod`, `cp -r`, `mv`

---

### Exercise 2: Log File Analysis

**Objective:** Practice searching and analyzing text files.

**Tasks:**
1. Create a sample log file with various entries
2. Find all ERROR entries
3. Count how many warnings occurred
4. Extract entries from last hour
5. Find unique error messages
6. Generate a summary report

**Sample log content:**
```
2026-01-04 10:00:01 INFO Application started
2026-01-04 10:00:15 ERROR Database connection failed
2026-01-04 10:01:02 WARNING Low memory
2026-01-04 10:01:30 ERROR File not found
2026-01-04 10:02:45 INFO User logged in
```

**Commands to use:** `grep`, `wc`, `sort`, `uniq`, `cut`

---

### Exercise 3: Cleanup Script Practice

**Objective:** Clean up temporary and old files.

**Tasks:**
1. Create a test directory with various file types
2. Find all `.tmp` files
3. Find files larger than 10MB
4. Find files older than 30 days
5. Remove them safely (test first without `-delete`)

**Commands to use:** `find`, `rm`, `ls -lh`

---

## Intermediate Challenges

### Exercise 4: Backup System

**Objective:** Create a simple backup system using shell commands.

**Tasks:**
1. Create a script that backs up a directory
2. Name backups with timestamps
3. Compress backups if possible
4. Keep only last 5 backups
5. Verify backup integrity

**Example workflow:**
```bash
# Create backup
$ cp -r myproject myproject_backup_$(date +%Y%m%d_%H%M%S)

# Or with tar (if available)
$ tar -czf myproject_backup_$(date +%Y%m%d).tar.gz myproject/

# Clean old backups
$ ls -t myproject_backup_* | tail -n +6 | xargs rm -rf
```

**Commands to use:** `cp -r`, `date`, `ls -t`, `tail`

---

### Exercise 5: File Inventory Report

**Objective:** Generate a comprehensive inventory of a directory.

**Tasks:**
1. Count total files and directories
2. List largest files
3. Show file type distribution (.txt, .jpg, etc.)
4. Calculate total disk usage
5. Find duplicate file names
6. Generate a formatted report

**Sample report format:**
```
Directory Inventory Report
==========================
Location: /home/user/projects
Date: 2026-01-04

Summary:
- Total Files: 234
- Total Directories: 45
- Total Size: 1.2 GB

Largest Files:
1. video.mp4 (500 MB)
2. database.db (250 MB)
3. archive.zip (100 MB)

File Types:
- .txt: 50 files
- .py: 30 files
- .jpg: 25 files
```

**Commands to use:** `find`, `wc`, `sort`, `du`, `uniq`

---

### Exercise 6: Development Project Setup

**Objective:** Set up a standard development project structure.

**Tasks:**
1. Create project structure:
   ```
   myapp/
   ├── src/
   │   ├── main/
   │   └── test/
   ├── docs/
   ├── config/
   ├── scripts/
   ├── .gitignore
   └── README.md
   ```

2. Set appropriate permissions:
   - Scripts: executable (755)
   - Config files: read-only (644)
   - Sensitive configs: private (600)

3. Create sample files in each directory
4. Add content to README.md
5. Create a simple setup script

---

## Advanced Projects

### Exercise 7: System Health Monitor

**Objective:** Create a monitoring system using filesystem commands.

**Tasks:**
1. Check disk space usage
2. Find large files consuming space
3. Monitor log file growth
4. Identify old temporary files
5. Generate health report

**Monitoring points:**
- Disk usage > 80% (warning)
- Files > 1GB (list them)
- Logs growing rapidly
- `/tmp` files older than 7 days

---

### Exercise 8: Multi-User File Sharing Setup

**Objective:** Set up a directory structure for file sharing with proper permissions.

**Tasks:**
1. Create shared directories:
   - Public (everyone can read)
   - Team (specific group can read/write)
   - Private (only owner can access)

2. Set appropriate permissions:
   - Public: 755
   - Team: 770
   - Private: 700

3. Test access from different permission perspectives
4. Document the permission scheme

---

### Exercise 9: Media Library Organization

**Objective:** Organize a large media collection.

**Tasks:**
1. Create directory structure by type and date:
   ```
   media/
   ├── photos/
   │   ├── 2024/
   │   └── 2025/
   ├── videos/
   └── audio/
   ```

2. Find all media files (various extensions)
3. Organize by file type
4. Generate catalog of all media
5. Find and remove duplicates
6. Create thumbnails directory structure

---

## Real-World Scenarios

### Scenario 1: Website Deployment

**Context:** You need to deploy a website to a web server.

**Tasks:**
1. Create web directory structure:
   ```
   /var/www/mysite/
   ├── public/
   ├── logs/
   └── backups/
   ```

2. Set proper permissions:
   - HTML/CSS: 644
   - Directories: 755
   - Scripts: 755

3. Copy website files
4. Create symbolic links for easy access
5. Verify all files are accessible

---

### Scenario 2: Code Repository Cleanup

**Context:** A code repository has become messy over time.

**Tasks:**
1. Find and remove:
   - Compiled files (*.o, *.pyc)
   - Temporary files (*.tmp, *~)
   - Log files (*.log)
   - Empty directories

2. Organize source files by language
3. Create proper .gitignore
4. Verify nothing important was removed
5. Document cleanup process

---

### Scenario 3: Server Log Analysis

**Context:** Analyze web server logs for security and performance.

**Tasks:**
1. Extract unique IP addresses
2. Find most accessed pages
3. Identify suspicious activity
4. Generate access statistics
5. Create summary report

**Sample log format:**
```
192.168.1.1 - - [04/Jan/2026:10:00:00] "GET /index.html HTTP/1.1" 200
```

---

### Scenario 4: Data Migration

**Context:** Migrate data from old structure to new structure.

**Tasks:**
1. Survey old directory structure
2. Plan new structure
3. Create migration mapping
4. Copy files to new locations
5. Verify migration success
6. Keep backup of original

---

## Challenge Exercises

### Challenge 1: One-Liner Masters

Complete these tasks using a single command line:

1. Find all .txt files, count total lines
2. List 10 largest files with human-readable sizes
3. Find files modified today, sorted by size
4. Count unique words in all .txt files
5. Find duplicate file names across directories

---

### Challenge 2: Speed Challenges

How fast can you:

1. Create 100 directories with sequential names
2. Create 1000 empty files
3. Find all files larger than 10MB
4. Count total lines in all .py files
5. Organize 100 files into 10 directories

---

### Challenge 3: Complex Pipeline

Create a single pipeline that:

1. Finds all log files
2. Extracts error messages
3. Counts occurrences
4. Sorts by frequency
5. Saves top 10 to report

---

## Exercise Solutions

### Tips for Success

1. **Start Simple:** Begin with basic exercises before attempting advanced ones
2. **Test Safely:** Use test directories, not production data
3. **Document Your Work:** Write down commands that work
4. **Experiment:** Try different approaches to solve problems
5. **Learn from Mistakes:** Understand why something didn't work

### Getting Help

- Review relevant lesson materials
- Use `man` pages for command details
- Search online for specific problems
- Ask questions in forums or communities
- Practice regularly to build skills

---

## Creating Your Own Exercises

As you become more comfortable, create exercises based on your actual needs:

1. **Identify a task** you do regularly
2. **Break it down** into filesystem operations
3. **Write the steps** you need to take
4. **Practice** until you can do it efficiently
5. **Document** your solution for future reference

---

## Progress Tracking

Use this checklist to track your progress:

**Basic Practice:**
- [ ] Exercise 1: Personal File Organization
- [ ] Exercise 2: Log File Analysis
- [ ] Exercise 3: Cleanup Script Practice

**Intermediate Challenges:**
- [ ] Exercise 4: Backup System
- [ ] Exercise 5: File Inventory Report
- [ ] Exercise 6: Development Project Setup

**Advanced Projects:**
- [ ] Exercise 7: System Health Monitor
- [ ] Exercise 8: Multi-User File Sharing
- [ ] Exercise 9: Media Library Organization

**Real-World Scenarios:**
- [ ] Scenario 1: Website Deployment
- [ ] Scenario 2: Code Repository Cleanup
- [ ] Scenario 3: Server Log Analysis
- [ ] Scenario 4: Data Migration

---

## Next Steps

After completing these exercises:

1. Review the main [README](../README.md)
2. Revisit lessons for deeper understanding
3. Explore advanced topics (shell scripting, automation)
4. Apply skills to your own projects
5. Contribute your own exercises to this repository

---

**Remember:** The best way to learn is by doing. Practice these exercises regularly, and you'll become proficient with Linux filesystem commands!
