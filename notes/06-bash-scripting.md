# 06 - Bash Scripting

Bash scripts are plain text files containing a series of commands that the shell executes in order.

---

## Creating a Script

```bash
touch script.sh         # Create the file
chmod +x script.sh      # Make it executable
./script.sh             # Run it
```

Every script starts with a shebang line:

```bash
#!/bin/bash
```

This tells the system to use bash to run the file.

---

## Variables

```bash
name="arslan"
echo $name              # Print variable
echo "Hello, $name"     # Use inside string
```

Rules:
- No spaces around `=`
- Use `$` to access the value
- Variable names are case-sensitive

### Special Variables

| Variable | Meaning |
|----------|---------|
| `$0` | Script name |
| `$1`, `$2` | First, second argument passed to script |
| `$#` | Number of arguments |
| `$@` | All arguments |
| `$?` | Exit status of last command (0 = success) |
| `$$` | PID of current script |

---

## User Input

```bash
read name
echo "You entered: $name"

read -p "Enter your name: " name
echo "Hello, $name"
```

---

## Conditions

```bash
if [ condition ]; then
    # commands
elif [ condition ]; then
    # commands
else
    # commands
fi
```

### Comparison Operators

**Numbers:**

| Operator | Meaning |
|----------|---------|
| `-eq` | Equal |
| `-ne` | Not equal |
| `-lt` | Less than |
| `-gt` | Greater than |
| `-le` | Less than or equal |
| `-ge` | Greater than or equal |

**Strings:**

| Operator | Meaning |
|----------|---------|
| `=` | Equal |
| `!=` | Not equal |
| `-z` | Empty string |
| `-n` | Non-empty string |

**Files:**

| Operator | Meaning |
|----------|---------|
| `-f file` | File exists |
| `-d dir` | Directory exists |
| `-e path` | Path exists |
| `-r file` | File is readable |
| `-x file` | File is executable |

### Example

```bash
#!/bin/bash

read -p "Enter a number: " num

if [ $num -gt 10 ]; then
    echo "Greater than 10"
elif [ $num -eq 10 ]; then
    echo "Equal to 10"
else
    echo "Less than 10"
fi
```

---

## Loops

### For Loop

```bash
for i in 1 2 3 4 5; do
    echo "Number: $i"
done

# Loop over files
for file in *.txt; do
    echo "File: $file"
done

# C-style for loop
for ((i=0; i<5; i++)); do
    echo $i
done
```

### While Loop

```bash
count=1
while [ $count -le 5 ]; do
    echo "Count: $count"
    ((count++))
done
```

### Until Loop

```bash
count=1
until [ $count -gt 5 ]; do
    echo "Count: $count"
    ((count++))
done
```

---

## Functions

```bash
greet() {
    echo "Hello, $1"
}

greet "Arslan"      # Call the function
```

Functions with return value:

```bash
add() {
    result=$(( $1 + $2 ))
    echo $result
}

sum=$(add 3 5)
echo "Sum: $sum"
```

---

## Useful Commands in Scripts

```bash
echo "message"              # Print text
read var                    # Take input
exit 0                      # Exit script (0 = success, 1 = error)
sleep 2                     # Wait 2 seconds
date                        # Current date/time
$(command)                  # Command substitution
$(( 5 + 3 ))                # Arithmetic
```

---

## Example Script

```bash
#!/bin/bash

# backup.sh - Simple file backup script

source=$1
dest=$2

if [ -z "$source" ] || [ -z "$dest" ]; then
    echo "Usage: ./backup.sh <source> <destination>"
    exit 1
fi

if [ ! -d "$source" ]; then
    echo "Source directory does not exist"
    exit 1
fi

cp -r "$source" "$dest"
echo "Backup complete: $source -> $dest"
```
