# Bash Scripting Roadmap Study Notes

## Based on Roadmap Pictures and Class Planning

## Main Roadmap Idea

The best Bash Scripting roadmap should not start directly from script writing.

It should start from thinking like an automation engineer.

The learning journey should be:

```text
Foundation -> Input/Data -> Logic -> Repetition -> Reusable Code -> System Automation -> DevOps Use Cases -> Best Practices -> Interview Preparation
```

---

# 1. Complete Bash Scripting Roadmap

## Phase 1: Foundation of Shell Scripting

### Main Topics

```text
Shell Scripting Roadmap
What is Shell Scripting?
Shell Script Basics
```

### What Students Should Learn

Students should first understand:

```text
What is shell?
What is Bash?
What is a script?
Why do we need scripting?
What is automation?
How does a script run?
```

### Teaching Logic

Before writing any script, explain this:

```text
Linux command = one manual action
Bash script = many Linux commands saved in one file
Automation = script runs repeated tasks automatically
```

### Example

Manual work:

```bash
date
whoami
hostname
pwd
```

Script work:

```bash
#!/bin/bash

date
whoami
hostname
pwd
```

### Goal of This Phase

Students should understand:

```text
If I can run commands manually,
I can put them inside a file,
give permission,
and run them as a script.
```

---

# Phase 2: Script Structure and Execution

## Main Topics

```text
Shell Script Basics
Shebang
Comments
Execute Permission
Running Scripts
```

## What Students Should Learn

A basic Bash script has:

```text
Shebang
Comments
Commands
Permission
Execution
```

## Script Structure

```bash
#!/bin/bash

# This is my first script
echo "Welcome to Bash Scripting"
```

## Execution Flow

```text
Create file
Write script
Save file
Give execute permission
Run script
Check output
```

## Commands

```bash
nano first.sh
chmod +x first.sh
./first.sh
```

## Goal of This Phase

Students should be comfortable creating and running basic scripts.

---

# Phase 3: Variables and Data Handling

## Main Topics

```text
Variables
User Input
Command Line Arguments
Special Variables
```

## What Students Should Learn

After basic scripts, students need to learn how scripts store and receive data.

## Variables

```bash
name="Khalid"
echo "My name is $name"
```

## User Input

```bash
read -p "Enter your name: " name
echo "Hello $name"
```

## Command Line Arguments

```bash
#!/bin/bash

echo "First argument is $1"
echo "Second argument is $2"
```

Run:

```bash
./script.sh Khalid DevOps
```

## Special Variables

| Variable | Meaning |
|---|---|
| `$0` | Script name |
| `$1` | First argument |
| `$2` | Second argument |
| `$#` | Number of arguments |
| `$@` | All arguments |
| `$?` | Exit status |
| `$$` | Current script process ID |

## Teaching Logic

Explain like this:

```text
Variables store data.
User input takes data during script execution.
Arguments take data when running the script.
Special variables give script-related information.
```

## Goal of This Phase

Students should be able to make scripts flexible instead of hard-coded.

---

# Phase 4: Decision Making

## Main Topics

```text
Conditional Statements
Comparison Operators
File Test Operators
Exit Status
```

## What Students Should Learn

Scripts must be able to make decisions.

## Basic Logic

```text
If condition is true, do this.
Otherwise, do something else.
```

## Example

```bash
#!/bin/bash

read -p "Enter username: " username

if id "$username" &>/dev/null; then
    echo "User exists"
else
    echo "User does not exist"
fi
```

## Number Comparison Operators

| Operator | Meaning |
|---|---|
| `-eq` | Equal |
| `-ne` | Not equal |
| `-gt` | Greater than |
| `-lt` | Less than |
| `-ge` | Greater than or equal |
| `-le` | Less than or equal |

## String Comparison Operators

| Operator | Meaning |
|---|---|
| `=` | Equal |
| `!=` | Not equal |
| `-z` | String is empty |
| `-n` | String is not empty |

## File Test Operators

| Operator | Meaning |
|---|---|
| `-f` | File exists |
| `-d` | Directory exists |
| `-e` | File or directory exists |
| `-r` | Readable |
| `-w` | Writable |
| `-x` | Executable |

## Exit Status

```bash
echo $?
```

Meaning:

```text
0 = success
non-zero = failure
```

## Goal of This Phase

Students should understand script decision-making.

This is where they start thinking like:

```text
Check first, then act.
```

---

# Phase 5: Loops and Repetition

## Main Topics

```text
Loops
For Loop
While Loop
```

## What Students Should Learn

Loops are used when we want to repeat work.

## For Loop

```bash
for user in ali ahmad khalid
do
    echo "User: $user"
done
```

## While Loop

```bash
count=1

while [ "$count" -le 5 ]
do
    echo "Count is $count"
    count=$((count + 1))
done
```

## Real Use Cases

```text
Create multiple users
Check multiple files
Install multiple packages
Read logs
Process many servers
```

## Goal of This Phase

Students should stop repeating commands manually.

They should think:

```text
If I need to repeat something, I should use a loop.
```

---

# Phase 6: Functions and Reusable Logic

## Main Topics

```text
Functions
Reusable Code
Clean Script Structure
```

## What Students Should Learn

Functions are reusable blocks of code.

## Basic Function

```bash
show_date() {
    date
}

show_date
```

## Function with Argument

```bash
greet_user() {
    echo "Hello $1"
}

greet_user "Khalid"
```

## Real Example

```bash
check_user() {
    id "$1" &>/dev/null
}
```

## Teaching Logic

Explain like this:

```text
If you use the same logic again and again,
put it inside a function.
```

## Goal of This Phase

Students should write cleaner scripts.

---

# Phase 7: File Operations and System Work

## Main Topics

```text
File Operations
Useful Shell Commands
Linux System Commands
```

## What Students Should Learn

Most real Bash scripts work with files, directories, logs, and system commands.

## File Operations

```bash
touch file.txt
cp file.txt backup.txt
mv backup.txt backup/
rm file.txt
mkdir logs
```

## Useful Commands

```bash
grep
awk
sed
cut
sort
uniq
find
tar
df
free
uptime
systemctl
```

## Example

```bash
#!/bin/bash

mkdir -p logs
date >> logs/report.log
df -h >> logs/report.log
free -h >> logs/report.log
```

## Goal of This Phase

Students should learn Bash as a Linux administration tool.

---

# Phase 8: Input/Output, Redirection, Pipes, and Filters

## Main Topics

```text
Input/Output Redirection
Pipes and Filters
```

## What Students Should Learn

This is very important for real Linux scripting.

## Redirection

```bash
echo "Hello" > file.txt
echo "New line" >> file.txt
ls /wrong/path 2> error.log
command > output.log 2>&1
```

## Pipes

```bash
ps aux | grep nginx
cat /etc/passwd | cut -d: -f1
df -h | grep /dev
```

## Teaching Logic

Explain like this:

```text
Redirection saves output.
Pipes pass output from one command to another.
Filters clean or search the output.
```

## Goal of This Phase

Students should be able to process command output professionally.

---

# Phase 9: Real DevOps Automation Examples

## Main Topics

```text
DevOps Automation Examples
Linux Admin Scripts
Production Style Scripts
```

## What Students Should Learn

Now students are ready for real-world scripts.

---

## Project 1: System Health Check Script

```bash
#!/bin/bash

echo "System Health Check"
date
hostname
uptime
df -h
free -h
```

## Project 2: User Creation Script

```bash
#!/bin/bash

read -p "Enter username: " username

if id "$username" &>/dev/null; then
    echo "User already exists"
else
    sudo useradd -m "$username"
    echo "User created"
fi
```

## Project 3: Backup Script

```bash
#!/bin/bash

source_dir="/home/khalid/project"
backup_dir="/home/khalid/backups"
date_now=$(date +%F-%H-%M-%S)

mkdir -p "$backup_dir"
tar -czf "$backup_dir/backup-$date_now.tar.gz" "$source_dir"
```

## Project 4: Service Monitor Script

```bash
#!/bin/bash

service="nginx"

if systemctl is-active --quiet "$service"; then
    echo "$service is running"
else
    echo "$service is not running"
fi
```

## Goal of This Phase

Students should connect Bash scripting with Linux Admin and DevOps work.

---

# Phase 10: Best Practices

## Main Topics

```text
Shell Scripting Best Practices
Safety
Clean Code
Error Handling
```

## What Students Should Learn

Now teach students how to write safe and professional scripts.

## Best Practice: Strong Script Start

```bash
#!/bin/bash
set -euo pipefail
```

## Use Quotes

```bash
"$username"
```

## Use Meaningful Variable Names

```bash
backup_dir="/home/khalid/backups"
```

## Check Before Deleting

```bash
if [ -f "$file" ]; then
    rm "$file"
fi
```

## Add Comments

```bash
# Create backup directory if it does not exist
```

## Goal of This Phase

Students should write scripts that are safe, clean, and production-friendly.

---

# Phase 11: Interview Preparation

## Main Topics

```text
DevOps Interview Questions
Shell Scripting Interview Practice
Real Scenario Questions
```

## What Students Should Prepare

Students should be able to answer:

```text
What is shell scripting?
What is the difference between $@ and $*?
What is exit status?
What is shebang?
What is chmod +x?
What is the difference between > and >>?
What is the use of grep, awk, and sed?
How do you check if a file exists?
How do you check if a user exists?
How do you schedule a script?
How do you debug a Bash script?
```

## Goal of This Phase

Students should be ready for real interviews and practical tasks.

---

# 2. Final Roadmap Table

| Phase | Topic | Main Skill |
|---|---|---|
| 1 | What is Bash/Shell Scripting | Concept building |
| 2 | Script Basics | Create and run scripts |
| 3 | Variables/Input/Arguments | Handle data |
| 4 | Conditions/Comparisons/File Tests | Make decisions |
| 5 | Loops | Repeat tasks |
| 6 | Functions | Reuse logic |
| 7 | File Operations/Shell Commands | Work with Linux system |
| 8 | Redirection/Pipes/Filters | Process output |
| 9 | DevOps Automation Examples | Real-world scripts |
| 10 | Best Practices | Write professional scripts |
| 11 | Interview Preparation | Job readiness |

---

# 3. Best Teaching Order

For teaching, do not follow only picture numbers.

Teach in this order:

```text
1. What is Shell Scripting?
2. Why Bash Scripting?
3. Automation concept
4. First script
5. Shebang, comments, permission
6. Variables
7. User input
8. Command-line arguments
9. Special variables
10. Conditional statements
11. Comparison operators
12. File test operators
13. Exit status
14. Loops
15. Functions
16. File operations
17. Redirection
18. Pipes and filters
19. Useful shell commands
20. DevOps automation examples
21. Best practices
22. Interview questions
```

---

# 4. 15-Day Bash Scripting Class Plan

| Day | Class Topic | Practice |
|---|---|---|
| Day 1 | What is Bash scripting and automation | First script |
| Day 2 | Script basics, shebang, comments, permissions | Welcome script |
| Day 3 | Variables | Profile script |
| Day 4 | User input | Input-based greeting script |
| Day 5 | Command-line arguments and special variables | Argument script |
| Day 6 | Conditional statements | User check script |
| Day 7 | Comparison operators | Marks/pass-fail script |
| Day 8 | File test operators | File/directory checker |
| Day 9 | Exit status and error handling | Command success/failure script |
| Day 10 | Loops | Multiple users/files script |
| Day 11 | Functions | Function-based menu script |
| Day 12 | File operations | Backup folder script |
| Day 13 | Redirection, pipes, filters | Log/report script |
| Day 14 | DevOps automation examples | Health check/service check |
| Day 15 | Best practices and interview review | Final project |

---

# 5. How to Think Before Writing a Bash Script

A student should not just memorize Bash commands.

The student should learn how to think:

```text
What is the task?
What input do I need?
What should I check first?
What decision should the script make?
What action should happen?
What output should be shown?
What error can happen?
How can I make it safer?
```

---

# 6. Professional Script Thinking Model

Use this model before writing any script:

```text
Input -> Validation/Check -> Decision -> Action -> Output -> Error Handling
```

## Example: Create User Script

```text
Input:
Ask for username

Validation/Check:
Check if user already exists using id command

Decision:
If user exists, stop
If user does not exist, continue

Action:
Create user with useradd -m

Output:
Show success or failure message

Error Handling:
Handle user already exists, invalid username, and permission issues
```

---

# 7. Bash Scripting Learning Flow

The correct design is:

```text
First build understanding.
Then teach syntax.
Then teach logic.
Then teach repetition.
Then teach real Linux automation.
Then teach professional best practices.
Then prepare for interview.
```

---

# 8. Student Learning Milestones

## Beginner Level

Student can:

- Explain what Bash scripting is
- Create a `.sh` file
- Add shebang
- Use `echo`
- Run basic commands inside a script
- Give execute permission
- Run script with `./script.sh`

## Basic Automation Level

Student can:

- Use variables
- Take user input
- Use command-line arguments
- Use special variables
- Create simple automation scripts

## Logic Level

Student can:

- Use `if/else`
- Compare numbers
- Compare strings
- Check files and directories
- Understand exit status

## Practical Linux Level

Student can:

- Use loops
- Use functions
- Work with files and directories
- Use pipes and redirection
- Create logs
- Read command output

## DevOps Ready Level

Student can:

- Write health check scripts
- Write backup scripts
- Write user management scripts
- Write service monitor scripts
- Follow best practices
- Explain scripts in interviews

---

# 9. Recommended Final Projects

## Project 1: System Health Check

Checks:

```text
Date
Hostname
Current user
Uptime
Disk usage
Memory usage
Service status
```

## Project 2: User Creation Script

Features:

```text
Take username input
Check user exists
Create user if not exists
Show success/failure
```

## Project 3: Backup Script

Features:

```text
Take source directory
Take backup directory
Create timestamp backup
Compress with tar
Log result
```

## Project 4: Service Monitor Script

Features:

```text
Take service name
Check status with systemctl
Show running/not running
Optional restart service
```

## Project 5: Log Analyzer

Features:

```text
Read log file
Search errors
Count warnings
Create report
Save output
```

---

# 10. Final Explanation

This roadmap is not only a list of Bash topics.

It is a complete learning journey from beginner to DevOps-ready Bash scripting.

The best order is:

```text
Concept -> Command -> Script -> Logic -> Automation -> Real Project -> Best Practice -> Interview
```

The main purpose is to help students understand:

```text
Bash scripting is not only writing commands.
Bash scripting is thinking logically and automating Linux work safely.
```

---

# Final Summary

A good Bash scripting roadmap should teach students:

- What Bash is
- Why scripting is needed
- What automation means
- How to write and run scripts
- How to use variables and input
- How to make decisions
- How to repeat tasks
- How to reuse code
- How to work with Linux files and commands
- How to process output
- How to create real DevOps automation scripts
- How to write safe and professional scripts
- How to prepare for interviews

Final roadmap sentence:

```text
Learn Bash commands first, then convert those commands into scripts, then convert scripts into real automation.
```
