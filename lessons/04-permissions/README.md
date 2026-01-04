# Lesson 4: File Permissions and Ownership

## Learning Objectives

By the end of this lesson, you will be able to:
- Understand Linux permission system
- Read and interpret permission notations
- Change file permissions with `chmod`
- Understand file ownership
- Use both symbolic and numeric permission notation

## Commands Covered

- `chmod` - Change file permissions
- `chown` - Change file ownership
- `ls -l` - View permissions

---

## 1. Understanding File Permissions

Every file and directory in Linux has three types of permissions for three categories of users.

### Permission Types

| Symbol | Permission | Meaning for Files | Meaning for Directories |
|--------|------------|-------------------|------------------------|
| `r` | Read | View file contents | List directory contents |
| `w` | Write | Modify file | Create/delete files in directory |
| `x` | Execute | Run file as program | Enter directory (cd) |

### User Categories

| Category | Description |
|----------|-------------|
| Owner (u) | The user who owns the file |
| Group (g) | Users in the file's group |
| Others (o) | Everyone else |

### Reading Permission Output

```bash
$ ls -l myfile.txt
-rw-r--r-- 1 user group 1234 Jan 1 10:00 myfile.txt
```

Breaking down the permissions: `-rw-r--r--`

```
-  rw-  r--  r--
│   │    │    │
│   │    │    └─ Others: read only
│   │    └────── Group: read only
│   └─────────── Owner: read, write
└─────────────── File type (- = regular file, d = directory)
```

### File Type Indicators

| Symbol | Type |
|--------|------|
| `-` | Regular file |
| `d` | Directory |
| `l` | Symbolic link |
| `b` | Block device |
| `c` | Character device |

---

## 2. Changing Permissions with `chmod`

The `chmod` command changes file permissions.

### Syntax
```bash
chmod [options] mode file
```

### Two Notation Methods

1. **Symbolic notation** (letters): easier to understand
2. **Numeric notation** (numbers): more precise

---

## 3. Symbolic Notation

### Format
```bash
chmod [who][operator][permissions] file
```

### Components

**Who:**
- `u` - User/Owner
- `g` - Group
- `o` - Others
- `a` - All (u+g+o)

**Operator:**
- `+` - Add permission
- `-` - Remove permission
- `=` - Set exact permission

**Permissions:**
- `r` - Read
- `w` - Write
- `x` - Execute

### Examples

**Give owner execute permission:**
```bash
$ chmod u+x script.sh
```

**Remove write permission from group:**
```bash
$ chmod g-w file.txt
```

**Add read permission for everyone:**
```bash
$ chmod a+r document.txt
```

**Set exact permissions (owner: rw, group: r, others: none):**
```bash
$ chmod u=rw,g=r,o= file.txt
```

**Multiple changes at once:**
```bash
$ chmod u+x,g+x,o+x script.sh
# or simply:
$ chmod a+x script.sh
```

---

## 4. Numeric (Octal) Notation

Each permission has a numeric value:
- `r` (read) = 4
- `w` (write) = 2
- `x` (execute) = 1

### How to Calculate

Add the values for each category:

| Permission | Calculation | Value |
|------------|-------------|-------|
| `---` | 0 + 0 + 0 | 0 |
| `--x` | 0 + 0 + 1 | 1 |
| `-w-` | 0 + 2 + 0 | 2 |
| `-wx` | 0 + 2 + 1 | 3 |
| `r--` | 4 + 0 + 0 | 4 |
| `r-x` | 4 + 0 + 1 | 5 |
| `rw-` | 4 + 2 + 0 | 6 |
| `rwx` | 4 + 2 + 1 | 7 |

### Common Permission Patterns

```bash
# 644: Owner: rw, Group: r, Others: r (common for files)
$ chmod 644 file.txt

# 755: Owner: rwx, Group: rx, Others: rx (common for executables/directories)
$ chmod 755 script.sh

# 600: Owner: rw, Group: none, Others: none (private file)
$ chmod 600 private.txt

# 700: Owner: rwx, Group: none, Others: none (private script)
$ chmod 700 private_script.sh

# 777: Everyone: rwx (dangerous! Avoid unless necessary)
$ chmod 777 file.txt
```

---

## 5. Common Permission Scenarios

### Making a Script Executable
```bash
# Create a script
$ cat > hello.sh
#!/bin/bash
echo "Hello, World!"
^D

# Make it executable
$ chmod +x hello.sh
# or
$ chmod 755 hello.sh

# Run it
$ ./hello.sh
```

### Protecting Sensitive Files
```bash
# Private file - only owner can read/write
$ chmod 600 passwords.txt

# Private script - only owner can execute
$ chmod 700 admin_script.sh
```

### Web Server Files (typical)
```bash
# HTML files
$ chmod 644 index.html

# CGI scripts
$ chmod 755 script.cgi

# Configuration files
$ chmod 600 config.ini
```

---

## 6. Recursive Permission Changes

Use `-R` to change permissions recursively.

### Examples

**Make all files in directory readable:**
```bash
$ chmod -R a+r documents/
```

**Set permissions for entire directory tree:**
```bash
$ chmod -R 755 website/
```

⚠️ **Warning:** Be careful with recursive changes! They affect all files and subdirectories.

---

## 7. File Ownership (`chown`)

The `chown` command changes file ownership. (Usually requires root/sudo)

### Syntax
```bash
chown [options] user:group file
```

### Examples

**Change owner:**
```bash
$ sudo chown newowner file.txt
```

**Change owner and group:**
```bash
$ sudo chown newowner:newgroup file.txt
```

**Change group only:**
```bash
$ sudo chown :newgroup file.txt
# or use chgrp
$ sudo chgrp newgroup file.txt
```

**Recursive ownership change:**
```bash
$ sudo chown -R user:group directory/
```

---

## Practical Exercises

### Exercise 1: Reading Permissions
```bash
# List files with permissions
$ ls -l /usr/bin/ls
$ ls -l /etc/passwd
$ ls -ld /tmp

# Identify:
# - What are the permissions?
# - Who can read, write, execute?
```

### Exercise 2: Using Symbolic Notation
```bash
# Create a test file
$ touch testfile.txt

# Practice adding permissions
$ chmod u+x testfile.txt
$ ls -l testfile.txt

# Practice removing permissions
$ chmod g-r testfile.txt
$ ls -l testfile.txt

# Set exact permissions
$ chmod u=rw,g=r,o= testfile.txt
$ ls -l testfile.txt
```

### Exercise 3: Using Numeric Notation
```bash
# Create files with different permissions
$ touch file1.txt file2.txt file3.txt

# Set different numeric permissions
$ chmod 644 file1.txt
$ chmod 755 file2.txt
$ chmod 600 file3.txt

# Verify
$ ls -l file*.txt
```

### Exercise 4: Making Scripts Executable
```bash
# Create a simple script
$ cat > greet.sh << 'EOF'
#!/bin/bash
echo "Hello from a script!"
EOF

# Try to run it (will fail)
$ ./greet.sh
-bash: ./greet.sh: Permission denied

# Make it executable
$ chmod +x greet.sh

# Run it successfully
$ ./greet.sh
```

### Exercise 5: Protecting Sensitive Files
```bash
# Create a "sensitive" file
$ echo "secret information" > secret.txt

# Set restrictive permissions
$ chmod 600 secret.txt

# Verify
$ ls -l secret.txt
-rw------- 1 user group 19 Jan 1 10:00 secret.txt
```

---

## Real-World Scenario: Setting Up a Project

```bash
# Create project structure
$ mkdir -p myproject/{src,docs,scripts}

# Create various files
$ touch myproject/src/main.py
$ touch myproject/docs/README.md
$ touch myproject/scripts/deploy.sh
$ touch myproject/scripts/backup.sh

# Set appropriate permissions
# Regular files: 644
$ chmod 644 myproject/src/main.py
$ chmod 644 myproject/docs/README.md

# Executable scripts: 755
$ chmod 755 myproject/scripts/*.sh

# Verify
$ ls -lR myproject/
```

---

## Permission Best Practices

1. **Principle of Least Privilege:**
   - Give minimum permissions necessary
   - Don't use 777 unless absolutely required

2. **Default File Permissions:**
   - Regular files: 644 (rw-r--r--)
   - Executable files: 755 (rwxr-xr-x)
   - Private files: 600 (rw-------)

3. **Directory Permissions:**
   - Public directories: 755 (rwxr-xr-x)
   - Private directories: 700 (rwx------)

4. **Be Careful with Recursive:**
   - Test on small subset first
   - Verify changes afterward

5. **Security Considerations:**
   ```bash
   # Good for sensitive data
   $ chmod 600 ~/.ssh/id_rsa
   
   # Good for shared scripts
   $ chmod 755 /usr/local/bin/myscript
   ```

---

## Command Cheat Sheet

```bash
# View permissions
ls -l file.txt
ls -ld directory/

# Symbolic notation
chmod u+x file                  # Add execute for owner
chmod g-w file                  # Remove write for group
chmod o=r file                  # Set read-only for others
chmod a+r file                  # Add read for all

# Numeric notation
chmod 644 file.txt             # rw-r--r--
chmod 755 script.sh            # rwxr-xr-x
chmod 600 private.txt          # rw-------
chmod 700 private_dir          # rwx------

# Recursive
chmod -R 755 directory/

# Ownership (requires sudo)
sudo chown user:group file
sudo chown -R user:group dir/
```

---

## Common Permission Values Reference

| Numeric | Symbolic | Typical Use |
|---------|----------|-------------|
| 644 | rw-r--r-- | Regular files (documents, images) |
| 755 | rwxr-xr-x | Executables, directories |
| 600 | rw------- | Private files (passwords, keys) |
| 700 | rwx------ | Private scripts, directories |
| 666 | rw-rw-rw- | Rarely used (too open) |
| 777 | rwxrwxrwx | Avoid! (security risk) |

---

## Next Steps

Now that you understand permissions, proceed to [Lesson 5: Searching and Finding](../05-searching/README.md) to learn how to locate files and content effectively.

---

## Additional Resources

- Use `man chmod` for complete documentation
- Practice with test files before modifying important files
- Learn about special permissions (setuid, setgid, sticky bit) for advanced usage
- Research umask for default permission settings
