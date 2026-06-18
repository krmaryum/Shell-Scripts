# Bash Scripting Teaching Preparation Guide

**Teaching Style:** What? → Why need it? → How? → Lab → Summary  
**Purpose:** This guide is prepared for teaching Bash Scripting from beginner level to practical Linux/DevOps scripting level.

---

## Table of Contents

| Section | Topic |
|---|---|
| 1 | Introduction to Bash Scripting |
| 2 | Shebang |
| 3 | Comments |
| 4 | Echo Command |
| 5 | Variables |
| 6 | User Input |
| 7 | Command Substitution |
| 8 | If Statement |
| 9 | File Test Operators |
| 10 | Number Comparison |
| 11 | String Comparison |
| 12 | For Loop |
| 13 | While Loop |
| 14 | Case Statement |
| 15 | Functions |
| 16 | Script Arguments |
| 17 | Exit Status |
| 18 | Error Handling |
| 19 | Redirection |
| 20 | Pipes |
| 21 | Arrays |
| 22 | Checking Required Commands |
| 23 | Working with Files |
| 24 | Working with Directories |
| 25 | Logging |
| 26 | Cron Jobs |
| 27 | Backup Script Project |
| 28 | System Health Check Project |
| 29 | Service Check Script |
| 30 | Best Practices |
| 31 | Suggested Teaching Plan |

---

# 1. Introduction to Bash Scripting

## What?

Bash scripting means writing Linux commands inside a file and running them together automatically.

A Bash script usually ends with:

```bash
.sh
```

Example:

```bash
backup.sh
```

## Why need it?

We need Bash scripting to automate repeated Linux tasks.

For example, instead of typing these commands again and again:

```bash
mkdir logs
cd logs
touch app.log
```

We can put them inside one script and run that script whenever needed.

Bash scripting is useful for:

- Linux administration
- DevOps automation
- Backups
- Monitoring
- File management
- User management
- CI/CD tasks
- Server health checks

## How?

Create a file:

```bash
nano first-script.sh
```

Add this content:

```bash
#!/bin/bash

echo "Hello, this is my first Bash script"
```

Give execute permission:

```bash
chmod +x first-script.sh
```

Run it:

```bash
./first-script.sh
```

## Lab

Create a script named `hello.sh`.

The script should print:

```text
Welcome to Bash Scripting
Today I am learning automation
```

Run the script successfully.

## Summary

- Bash scripting helps automate Linux commands.
- Script files usually end with `.sh`.
- `chmod +x` gives execute permission.
- `./script-name.sh` runs the script.

---

# 2. Shebang

## What?

Shebang is the first line of a script.

```bash
#!/bin/bash
```

It tells Linux which interpreter should run the script.

## Why need it?

Linux needs to know whether the file should run with Bash, Python, or another interpreter.

For Bash scripts, we usually use:

```bash
#!/bin/bash
```

## How?

```bash
#!/bin/bash

echo "Running with Bash"
```

## Lab

Create a script named `shebang-test.sh`.

Add the shebang line and print:

```text
This script is running with Bash
```

## Summary

- Shebang tells Linux which interpreter to use.
- Bash scripts commonly start with `#!/bin/bash`.
- It should be the first line of the script.

---

# 3. Comments

## What?

Comments are notes inside a script.

```bash
# This is a comment
```

Bash ignores comments when running the script.

## Why need it?

Comments help us understand the script later.

They are very useful for:

- Explaining code
- Teaching students
- Making scripts readable
- Helping future troubleshooting

## How?

```bash
#!/bin/bash

# Print welcome message
echo "Welcome to Bash scripting"
```

## Lab

Create a script named `comments.sh`.

Add at least three comments explaining what your script does.

## Summary

- Comments start with `#`.
- Comments are ignored by Bash.
- Comments make scripts easy to understand.

---

# 4. Echo Command

## What?

`echo` prints text on the terminal.

## Why need it?

We use `echo` to display:

- Messages
- Output
- Script progress
- Errors
- Instructions for users

## How?

```bash
echo "System check started"
echo "Hello Khalid"
```

Example script:

```bash
#!/bin/bash

echo "Starting script..."
echo "Checking system..."
echo "Script completed."
```

## Lab

Create a script that prints your name, course name, and today’s learning topic.

## Summary

- `echo` displays output.
- It is useful for showing script progress.
- It helps users understand what the script is doing.

---

# 5. Variables

## What?

A variable stores a value.

Example:

```bash
name="Khalid"
```

## Why need it?

Variables help us reuse values instead of typing them again and again.

They also make scripts easy to update.

## How?

```bash
#!/bin/bash

name="Khalid"
course="DevOps"

echo "My name is $name"
echo "I am learning $course"
```

Important rule:

Correct:

```bash
name="Khalid"
```

Wrong:

```bash
name = "Khalid"
```

Bash does not allow spaces around `=` when assigning variables.

## Lab

Create a script named `variables.sh`.

Store these values in variables:

```text
name
course
city
```

Then print them using `echo`.

## Summary

- Variables store values.
- No spaces around `=`.
- Use `$variable_name` to access the value.

---

# 6. User Input

## What?

User input means taking information from the user while the script is running.

## Why need it?

It makes scripts interactive.

For example, a script can ask:

- What is your name?
- Which file do you want to create?
- Which service do you want to check?

## How?

```bash
#!/bin/bash

echo "Enter your name:"
read name

echo "Hello $name"
```

Better version:

```bash
#!/bin/bash

read -p "Enter your name: " name
echo "Hello $name"
```

## Lab

Create a script that asks the user for:

- Name
- Course
- City

Then print a full sentence using those values.

## Summary

- `read` takes input from the user.
- `read -p` shows a prompt on the same line.
- User input makes scripts flexible.

---

# 7. Command Substitution

## What?

Command substitution stores command output inside a variable.

## Why need it?

Sometimes we need to save command output and use it later.

Examples:

- Store current date
- Store current user
- Store hostname
- Store disk usage
- Store command results

## How?

```bash
today=$(date)

echo "Today is $today"
```

Another example:

```bash
current_user=$(whoami)

echo "Current user is $current_user"
```

Example script:

```bash
#!/bin/bash

hostname_name=$(hostname)
today=$(date)
user=$(whoami)

echo "Hostname: $hostname_name"
echo "Date: $today"
echo "User: $user"
```

## Lab

Create a script that stores and prints:

- Current date
- Current user
- Hostname
- Current working directory

## Summary

- Command substitution uses `$()`.
- It stores command output inside a variable.
- It is very useful in automation scripts.

---

# 8. If Statement

## What?

`if` is used to make decisions in a script.

## Why need it?

Scripts need logic.

Example:

- If file exists, print success.
- If service is running, print active.
- If disk usage is high, print warning.

## How?

```bash
#!/bin/bash

file="app.log"

if [ -f "$file" ]; then
  echo "File exists"
else
  echo "File does not exist"
fi
```

## Lab

Create a script that checks if `notes.txt` exists.

If it exists, print:

```text
File found
```

Otherwise, print:

```text
File missing
```

## Summary

- `if` is used for decision-making.
- Conditions are written inside `[ ]`.
- `then`, `else`, and `fi` are part of if statement syntax.

---

# 9. File Test Operators

## What?

File test operators check files and directories.

| Operator | Meaning |
|---|---|
| `-f` | File exists |
| `-d` | Directory exists |
| `-e` | File or directory exists |
| `-r` | Readable |
| `-w` | Writable |
| `-x` | Executable |

## Why need it?

Before deleting, copying, reading, or running files, we should check if they exist.

This prevents script errors and protects important files.

## How?

Check if directory exists:

```bash
if [ -d "/var/log" ]; then
  echo "Directory exists"
fi
```

Check if script is executable:

```bash
if [ -x "script.sh" ]; then
  echo "Script is executable"
fi
```

## Lab

Create a script that checks:

- If `/etc/passwd` exists
- If `/tmp` is a directory
- If your script is executable

## Summary

- File test operators help check files and directories.
- They make scripts safer.
- Common operators are `-f`, `-d`, `-e`, `-r`, `-w`, and `-x`.

---

# 10. Number Comparison

## What?

Number comparison is used to compare numeric values.

| Operator | Meaning |
|---|---|
| `-eq` | Equal |
| `-ne` | Not equal |
| `-gt` | Greater than |
| `-lt` | Less than |
| `-ge` | Greater than or equal |
| `-le` | Less than or equal |

## Why need it?

We use number comparison for checking:

- Disk usage
- Memory usage
- Age
- Marks
- Process count
- Number of files

## How?

```bash
#!/bin/bash

number=10

if [ "$number" -gt 5 ]; then
  echo "Number is greater than 5"
else
  echo "Number is 5 or less"
fi
```

## Lab

Create a script that asks the user for marks.

If marks are greater than or equal to 50, print:

```text
Pass
```

Otherwise, print:

```text
Fail
```

## Summary

- Use `-eq`, `-gt`, `-lt`, etc. for numbers.
- Always quote variables.
- Number comparison is common in monitoring scripts.

---

# 11. String Comparison

## What?

String comparison compares text values.

| Operator | Meaning |
|---|---|
| `=` | Equal |
| `!=` | Not equal |
| `-z` | String is empty |
| `-n` | String is not empty |

## Why need it?

We use string comparison to check:

- Username
- Environment
- User input
- Options
- File names
- Service names

## How?

```bash
#!/bin/bash

env="prod"

if [ "$env" = "prod" ]; then
  echo "Production environment"
else
  echo "Non-production environment"
fi
```

Check empty input:

```bash
#!/bin/bash

read -p "Enter username: " username

if [ -z "$username" ]; then
  echo "Username cannot be empty"
else
  echo "Username is $username"
fi
```

## Lab

Create a script that asks for environment name.

If the user enters `prod`, print:

```text
Production selected
```

Otherwise, print:

```text
Non-production selected
```

## Summary

- String comparison is used for text values.
- `-z` checks empty strings.
- `-n` checks non-empty strings.

---

# 12. For Loop

## What?

A `for` loop repeats commands for each item in a list.

## Why need it?

We use loops to avoid repeating the same command manually.

Examples:

- Create multiple users
- Install multiple packages
- Check multiple files
- Process multiple logs

## How?

```bash
#!/bin/bash

for user in ali ahmad khalid
do
  echo "Creating user: $user"
done
```

Another example:

```bash
for file in *.log
do
  echo "Found log file: $file"
done
```

## Lab

Create a script that prints the names of five Linux commands using a `for` loop.

Example:

```text
git
docker
pwd
hostname
df
```

## Summary

- `for` loop repeats tasks.
- It is useful for lists.
- It reduces repeated code.

---

# 13. While Loop

## What?

A `while` loop repeats commands while a condition is true.

## Why need it?

Useful when we do not know exactly how many times the loop should run.

Examples:

- Retry command until success
- Read a file line by line
- Keep checking service status
- Count numbers

## How?

```bash
#!/bin/bash

count=1

while [ "$count" -le 5 ]
do
  echo "Count is $count"
  count=$((count + 1))
done
```

## Lab

Create a script that prints numbers from 1 to 10 using a `while` loop.

## Summary

- `while` loop runs while condition is true.
- It is useful for repeated checks.
- Be careful to update the condition, otherwise it may create an infinite loop.

---

# 14. Case Statement

## What?

`case` is used when we have multiple choices.

## Why need it?

It makes scripts cleaner than writing many `if/elif` conditions.

Useful for:

- Start/stop/restart menus
- User options
- Script arguments
- Environment selection

## How?

```bash
#!/bin/bash

read -p "Enter option start/stop/restart: " option

case "$option" in
  start)
    echo "Starting service"
    ;;
  stop)
    echo "Stopping service"
    ;;
  restart)
    echo "Restarting service"
    ;;
  *)
    echo "Invalid option"
    ;;
esac
```

## Lab

Create a menu script with these options:

```text
1. Show date
2. Show current user
3. Show current directory
4. Exit
```

## Summary

- `case` is used for multiple options.
- `*)` handles invalid input.
- Each case block ends with `;;`.

---

# 15. Functions

## What?

A function is a reusable block of code.

## Why need it?

Functions make scripts:

- Clean
- Organized
- Reusable
- Easier to debug
- Easier to teach

## How?

```bash
#!/bin/bash

greet_user() {
  echo "Hello, welcome to Bash scripting"
}

greet_user
```

Function with argument:

```bash
#!/bin/bash

greet_user() {
  echo "Hello $1"
}

greet_user "Khalid"
```

## Lab

Create three functions:

- `show_date`
- `show_user`
- `show_disk`

Call all three functions in your script.

## Summary

- Functions group reusable code.
- A function must be called to run.
- Function arguments use `$1`, `$2`, etc.

---

# 16. Script Arguments

## What?

Arguments are values passed to a script while running it.

Example:

```bash
./script.sh Khalid DevOps
```

## Why need it?

Arguments make scripts flexible.

Instead of editing script content every time, we can pass values from the command line.

## How?

```bash
#!/bin/bash

echo "First argument: $1"
echo "Second argument: $2"
```

Run:

```bash
./script.sh Khalid DevOps
```

Output:

```text
First argument: Khalid
Second argument: DevOps
```

Important special variables:

| Variable | Meaning |
|---|---|
| `$0` | Script name |
| `$1` | First argument |
| `$2` | Second argument |
| `$#` | Number of arguments |
| `$@` | All arguments |
| `$?` | Exit status of last command |

## Lab

Create a script that accepts two arguments:

```bash
./student.sh Khalid Bash
```

It should print:

```text
Student name is Khalid
Course name is Bash
```

## Summary

- Arguments are passed when running the script.
- `$1`, `$2`, etc. store argument values.
- `$#` shows number of arguments.

---

# 17. Exit Status

## What?

Every Linux command returns an exit status.

| Exit Code | Meaning |
|---|---|
| `0` | Success |
| Non-zero | Failure |

## Why need it?

We use exit status to check whether a command succeeded or failed.

This is very important in automation and CI/CD.

## How?

```bash
mkdir test-dir

echo $?
```

Use in script:

```bash
#!/bin/bash

mkdir backup

if [ "$?" -eq 0 ]; then
  echo "Directory created successfully"
else
  echo "Failed to create directory"
fi
```

Better way:

```bash
#!/bin/bash

if mkdir backup; then
  echo "Directory created successfully"
else
  echo "Failed to create directory"
fi
```

## Lab

Create a script that creates a directory and checks whether the command succeeded.

## Summary

- Exit status `0` means success.
- Non-zero means failure.
- `$?` stores the exit status of the last command.

---

# 18. Error Handling

## What?

Error handling means managing failures properly.

## Why need it?

Without error handling, scripts may continue even after a command fails.

This can cause:

- Wrong output
- Data loss
- Failed deployments
- Confusing troubleshooting

## How?

```bash
#!/bin/bash

set -e

mkdir backup
cd backup
touch file.txt

echo "Backup folder created"
```

Common options:

| Option | Meaning |
|---|---|
| `set -e` | Stop script if command fails |
| `set -u` | Error if variable is undefined |
| `set -o pipefail` | Fail pipeline if any command fails |

Strong script start:

```bash
#!/bin/bash
set -euo pipefail
```

## Lab

Create a script with `set -e`.

Add one wrong command in the middle and observe what happens.

## Summary

- Error handling makes scripts safer.
- `set -e` stops script on failure.
- `set -euo pipefail` is commonly used in serious scripts.

---

# 19. Redirection

## What?

Redirection sends output somewhere else.

## Why need it?

We use redirection to:

- Save output into files
- Save errors into files
- Append logs
- Hide unwanted output

## How?

Save output:

```bash
echo "Hello" > file.txt
```

Append output:

```bash
echo "New line" >> file.txt
```

Redirect error:

```bash
ls /wrong/path 2> error.log
```

Redirect output and error:

```bash
command > output.log 2>&1
```

Hide output:

```bash
command > /dev/null 2>&1
```

## Lab

Create a script that saves date, hostname, and current user into `system-info.log`.

## Summary

- `>` overwrites a file.
- `>>` appends to a file.
- `2>` redirects errors.
- `/dev/null` hides output.

---

# 20. Pipes

## What?

A pipe sends output of one command as input to another command.

```bash
command1 | command2
```

## Why need it?

Pipes help us filter and process command output.

They are very common in Linux administration.

## How?

```bash
ls -l | grep ".sh"
```

```bash
ps aux | grep nginx
```

```bash
cat /etc/passwd | grep khalid
```

Better:

```bash
grep khalid /etc/passwd
```

## Lab

Use pipes to:

- Find `.sh` files
- Find a running process
- Search a username in `/etc/passwd`

## Summary

- Pipe symbol is `|`.
- It connects commands.
- It helps filter output.

---

# 21. Arrays

## What?

An array stores multiple values in one variable.

## Why need it?

Arrays are useful when we have a list of:

- Users
- Packages
- Services
- Files
- Commands

## How?

```bash
#!/bin/bash

packages=("git" "curl" "vim")

for package in "${packages[@]}"
do
  echo "Installing $package"
done
```

Real example:

```bash
#!/bin/bash

required_commands=("bash" "git" "pwd" "hostname" "df")

for command in "${required_commands[@]}"
do
  if command -v "$command" >/dev/null 2>&1; then
    echo "$command is installed"
  else
    echo "Error: $command is not installed" >&2
    exit 1
  fi
done
```

## Lab

Create an array of five services:

```text
ssh
nginx
docker
cron
apache2
```

Print each service name using a loop.

## Summary

- Arrays store multiple values.
- `"${array[@]}"` means all array values.
- Arrays work very well with loops.

---

# 22. Checking Required Commands

## What?

Checking required commands means verifying if a needed command exists on the system.

## Why need it?

A script may fail if required tools are missing.

For example, a backup script may need:

- `tar`
- `gzip`
- `rsync`
- `date`

## How?

```bash
if command -v git >/dev/null 2>&1; then
  echo "Git is installed"
else
  echo "Git is not installed"
fi
```

Multiple command check:

```bash
#!/bin/bash

required_commands=("bash" "git" "pwd" "hostname" "df")

for command in "${required_commands[@]}"
do
  if command -v "$command" >/dev/null 2>&1; then
    echo "$command is installed"
  else
    echo "Error: $command is not installed" >&2
    exit 1
  fi
done

echo "All required commands are available"
```

## Lab

Create a script that checks if these commands are installed:

```text
git
docker
curl
wget
tar
```

## Summary

- `command -v` checks if a command exists.
- Redirect output to `/dev/null` to hide it.
- This is a professional way to validate script requirements.

---

# 23. Working with Files

## What?

Bash scripts often create, copy, move, read, and delete files.

## Why need it?

File management is one of the most common Linux admin tasks.

Examples:

- Create logs
- Copy backups
- Delete old files
- Read configuration files
- Move reports

## How?

```bash
touch app.log
cp app.log backup.log
mv backup.log logs/
rm app.log
```

Safe script:

```bash
#!/bin/bash

file="app.log"

if [ ! -f "$file" ]; then
  touch "$file"
  echo "$file created"
else
  echo "$file already exists"
fi
```

## Lab

Create a script that:

1. Creates a file named `report.txt`
2. Adds today's date inside it
3. Copies it to `report-backup.txt`

## Summary

- `touch` creates files.
- `cp` copies files.
- `mv` moves or renames files.
- `rm` removes files.
- Always check before deleting important files.

---

# 24. Working with Directories

## What?

Directory operations include creating, checking, moving into, and deleting folders.

## Why need it?

Scripts often need folders for:

- Logs
- Backups
- Reports
- Temporary files
- Project structure

## How?

```bash
mkdir logs
cd logs
pwd
```

Safe script:

```bash
#!/bin/bash

dir="logs"

if [ ! -d "$dir" ]; then
  mkdir "$dir"
  echo "Directory created"
else
  echo "Directory already exists"
fi
```

## Lab

Create a script that creates this structure:

```text
project/
├── logs/
├── backups/
└── scripts/
```

## Summary

- `mkdir` creates directories.
- `mkdir -p` creates parent directories if needed.
- `-d` checks if a directory exists.

---

# 25. Logging

## What?

Logging means saving script output into a file.

## Why need it?

Logs help us troubleshoot later.

Logs are useful for:

- Backup history
- Error tracking
- Automation records
- Server monitoring

## How?

```bash
#!/bin/bash

log_file="script.log"

echo "Script started" >> "$log_file"
date >> "$log_file"
echo "Script completed" >> "$log_file"
```

Better:

```bash
echo "$(date): Backup completed" >> backup.log
```

## Lab

Create a script that logs:

- Script start time
- Current user
- Hostname
- Script completion time

Save it into `activity.log`.

## Summary

- Logs keep history.
- `>>` appends log entries.
- Adding date/time makes logs more useful.

---

# 26. Cron Jobs

## What?

Cron is used to schedule scripts automatically.

## Why need it?

We use cron for:

- Daily backups
- Health checks
- Reports
- Cleanup jobs
- Monitoring tasks

## How?

Open crontab:

```bash
crontab -e
```

Run script every day at 1 AM:

```cron
0 1 * * * /home/khalid/backup.sh
```

Cron format:

```text
minute hour day month weekday command
```

Example:

```cron
*/5 * * * * /home/khalid/check.sh
```

This runs every 5 minutes.

## Lab

Create a script named `daily-report.sh`.

Schedule it with cron to run every day at 9 AM.

## Summary

- Cron schedules scripts.
- `crontab -e` edits cron jobs.
- Cron is important for automation.

---

# 27. Backup Script Project

## What?

A backup script copies important files into a backup folder.

## Why need it?

Backups protect important data.

A backup script is one of the best beginner-to-real-world Bash projects.

## How?

```bash
#!/bin/bash
set -euo pipefail

source_dir="/home/khalid/project"
backup_dir="/home/khalid/backups"
date_now=$(date +%F-%H-%M-%S)

mkdir -p "$backup_dir"

tar -czf "$backup_dir/project-backup-$date_now.tar.gz" "$source_dir"

echo "Backup completed successfully"
```

## Lab

Create a backup script that:

1. Takes source directory as argument
2. Takes backup directory as argument
3. Creates a compressed backup
4. Adds date and time in backup file name
5. Prints success message

Example:

```bash
./backup.sh /home/khalid/project /home/khalid/backups
```

## Summary

- Backup scripts are practical.
- `tar -czf` creates compressed archives.
- Date-based backup names prevent overwriting old backups.

---

# 28. System Health Check Project

## What?

A system health check script checks basic server information.

## Why need it?

Linux admins and DevOps engineers use health checks to monitor servers.

It can show:

- Hostname
- Uptime
- Disk usage
- Memory usage
- Current user
- IP address

## How?

```bash
#!/bin/bash

echo "System Health Check"
echo "==================="

echo
echo "Hostname:"
hostname

echo
echo "Uptime:"
uptime

echo
echo "Disk Usage:"
df -h

echo
echo "Memory Usage:"
free -h

echo
echo "Current User:"
whoami
```

## Lab

Create a health check script that prints:

- Hostname
- Date
- Uptime
- Disk usage
- Memory usage
- Logged-in users

Save output to `health-report.log`.

## Summary

- Health checks are useful for monitoring.
- `df -h` checks disk.
- `free -h` checks memory.
- `uptime` shows system running time.

---

# 29. Service Check Script

## What?

A service check script verifies if a service is running.

## Why need it?

In real jobs, we often need to check services like:

- nginx
- apache2
- docker
- ssh
- cron

## How?

```bash
#!/bin/bash

service_name="nginx"

if systemctl is-active --quiet "$service_name"; then
  echo "$service_name is running"
else
  echo "$service_name is not running"
fi
```

## Lab

Create a script that accepts service name as an argument:

```bash
./check-service.sh nginx
```

If the service is running, print:

```text
nginx is running
```

Otherwise, print:

```text
nginx is not running
```

## Summary

- `systemctl is-active --quiet` checks service status.
- Service checks are common in production.
- Passing service name as an argument makes the script flexible.

---

# 30. Best Practices

## What?

Best practices are rules for writing clean and safe scripts.

## Why need it?

Good scripts are:

- Easier to read
- Easier to debug
- Safer to run
- Easier to maintain
- More professional

## How?

Start serious scripts with:

```bash
#!/bin/bash
set -euo pipefail
```

Always quote variables:

```bash
"$filename"
```

Use meaningful names:

```bash
backup_dir="/backup"
```

Add comments:

```bash
# Create backup directory if it does not exist
```

Check before deleting:

```bash
if [ -f "$file" ]; then
  rm "$file"
fi
```

Avoid hard-coded values when possible:

```bash
backup_dir="$1"
```

## Lab

Review one of your old scripts and improve it using best practices.

Check for:

- Shebang
- Comments
- Quoted variables
- Clear variable names
- Error handling
- Safe file deletion

## Summary

- Best practices make scripts professional.
- Always quote variables.
- Use comments and meaningful names.
- Validate before dangerous actions.

---

# 31. Suggested Teaching Plan

| Day | Topic |
|---|---|
| Day 1 | What is Bash scripting, shebang, echo, comments |
| Day 2 | Variables, user input, command substitution |
| Day 3 | If statements, file tests, string and number comparison |
| Day 4 | Loops: for and while |
| Day 5 | Script arguments and special variables |
| Day 6 | Functions |
| Day 7 | Redirection, pipes, exit status |
| Day 8 | Error handling and debugging |
| Day 9 | Arrays and checking required commands |
| Day 10 | File and directory automation |
| Day 11 | Logging and cron jobs |
| Day 12 | Mini project: backup script |
| Day 13 | Mini project: system health check |
| Day 14 | Mini project: service monitor |
| Day 15 | Final project and review |

---

# Final Teaching Pattern

For every topic, teach using this pattern:

## 1. What?

Explain the concept in simple words.

## 2. Why need it?

Explain where it is used in real Linux, DevOps, or system admin work.

## 3. How?

Show command or script.

## 4. Lab

Give students a small task.

## 5. Summary

End with 3 to 5 key points.

---

# Example Class Format

## Topic: Variables

### What?

Variables store values.

### Why need it?

They help reuse values and make scripts easier to change.

### How?

```bash
#!/bin/bash

name="Khalid"
echo "Hello $name"
```

### Lab

Create a script that stores:

```text
name
course
city
```

Then print them.

### Summary

- Variables store data.
- No spaces around `=`.
- Use `$variable_name` to print the value.

---

# Final Notes for Teacher

Bash scripting should be taught with practical examples.  
Students should not only memorize commands. They should understand:

- What the command does
- Why it is needed
- How it is used in real Linux work
- How to troubleshoot errors
- How to write safe scripts

The best way to teach Bash scripting is:

```text
Explain → Show → Practice → Fix errors → Repeat
```

This guide can be used as a complete preparation document before teaching Bash scripting.
