# Bash Scripting Introduction Class

## Class Title

Introduction to Bash Scripting

## Teaching Style

What? → Why need it? → How? → Demo → Lab → Summary

---

## Class Objective

By the end of this class, students should understand:

- What Bash scripting is
- Why Bash scripting is important
- What automation means
- How Bash scripts help in Linux and DevOps
- How to create and run a basic Bash script
- Basic script structure
- Common first commands used in scripts

---

## 1. Opening Introduction

### Teacher Introduction

Today we are starting Bash Scripting.

Bash scripting is one of the most important skills for Linux administrators, DevOps engineers, cloud engineers, and anyone working with servers.

In Linux, we run many commands manually. But when the same commands need to be repeated again and again, we can put them inside a script and run them automatically.

That is the main purpose of Bash scripting.

---

# 2. What is Bash?



Bash stands for:

```text
Bourne Again Shell
```

Bash is a command-line shell used in Linux.

It allows users to interact with the operating system by typing commands.

Examples:

```bash
pwd
ls
cd
mkdir
touch
cp
mv
rm
```

## Why need it?

We need Bash because Linux servers are commonly managed through the command line.

Bash helps us:

- Run Linux commands
- Manage files and directories
- Manage users
- Check system information
- Automate repeated tasks
- Troubleshoot servers



When we open a Linux terminal, we are usually using a shell like Bash.

Example:

```bash
echo $SHELL
```

Output may look like:

```text
/bin/bash
```

This means the current shell is Bash.

---

# 3. What is Bash Scripting?



Bash scripting means writing Linux commands inside a file and running them together.

A Bash script is simply a file that contains commands.

Example script file:

```bash
hello.sh
```

Inside the file:

```bash
#!/bin/bash

echo "Hello, welcome to Bash scripting"
```

## Why need it?

Bash scripting is needed because it helps us automate repeated Linux tasks.

Instead of typing many commands manually every time, we can write them once in a script and run the script whenever needed.



Manual way:

```bash
mkdir logs
cd logs
touch app.log
date
```

Automated way:

```bash
#!/bin/bash

mkdir -p logs
cd logs
touch app.log
date
```

Now all commands can run together.

---

# 4. What is Automation?



Automation means making a manual task run automatically using a script, tool, or system.

Simple definition:

```text
Manual repeated work converted into automatic work = Automation
```

## Why need it?

Automation is important because it:

- Saves time
- Reduces human mistakes
- Makes work faster
- Makes tasks repeatable
- Helps manage servers efficiently
- Helps in DevOps and CI/CD pipelines



Manual work:

```bash
df -h
free -h
uptime
hostname
```

Automated script:

```bash
#!/bin/bash

echo "System Health Check"
df -h
free -h
uptime
hostname
```

Run the script:

```bash
./health-check.sh
```

Now the health check runs automatically.

---

# 5. Real-Life Examples of Bash Automation

## Linux Administration

Create users automatically:

```bash
sudo useradd -m ali
```

Backup files automatically:

```bash
tar -czf backup.tar.gz /home/khalid/project
```

Check disk usage:

```bash
df -h
```

Check services:

```bash
systemctl status nginx
```

## DevOps Examples

Bash scripts can be used for:

- Installing packages
- Running tests
- Building Docker images
- Cleaning old files
- Checking server health
- Starting or stopping services
- Running deployment steps

---

# 6. Why Bash Scripting is Important for DevOps



DevOps is about automation, speed, consistency, and reliability.

Bash scripting helps DevOps engineers automate tasks on Linux servers.

## Why need it?

In DevOps, we often need to:

- Prepare servers
- Install software
- Configure services
- Run CI/CD commands
- Check logs
- Run health checks
- Automate deployment steps

Without scripting, these tasks take more time and can have more mistakes.



Example DevOps workflow:

```text
Code pushed to GitHub
        |
        v
CI/CD pipeline starts
        |
        v
Script installs dependencies
        |
        v
Script runs tests
        |
        v
Script builds application
        |
        v
Script deploys application
```

Bash scripts can be used in many parts of this workflow.

---

# 7. Basic Structure of a Bash Script

A simple Bash script has three basic parts:

```text
Shebang
Comments
Commands
```

Example:

```bash
#!/bin/bash

# This is my first Bash script
echo "Hello Bash"
```

## Shebang

```bash
#!/bin/bash
```

This tells Linux to run the script using Bash.

## Comment

```bash
# This is a comment
```

Comments explain the script. Bash ignores comments.

## Command

```bash
echo "Hello Bash"
```

Commands are the actual instructions that run.

---

# 8. First Bash Script



Our first script will print a simple message.

## Why need it?

This helps students understand:

- How to create a script file
- How to write basic commands
- How to give execute permission
- How to run a script



### Step 1: Create a script file

```bash
nano first-script.sh
```

### Step 2: Add this content

```bash
#!/bin/bash

echo "Welcome to Bash Scripting"
echo "This is my first script"
```

### Step 3: Save the file

In nano:

```text
CTRL + O
Enter
CTRL + X
```

### Step 4: Give execute permission

```bash
chmod +x first-script.sh
```

### Step 5: Run the script

```bash
./first-script.sh
```

Expected output:

```text
Welcome to Bash Scripting
This is my first script
```

---

# 9. Important Commands for First Class

| Command | Purpose |
|---|---|
| `pwd` | Show current directory |
| `ls` | List files and directories |
| `cd` | Change directory |
| `mkdir` | Create directory |
| `touch` | Create empty file |
| `nano` | Edit file |
| `cat` | Show file content |
| `chmod +x` | Give execute permission |
| `./script.sh` | Run script |
| `echo` | Print output |

---

# 10. Script File Permission



A script needs execute permission before it can run directly.

## Why need it?

Linux protects files from being executed accidentally.

Before running a script like this:

```bash
./first-script.sh
```

We need execute permission.



Check permission:

```bash
ls -l first-script.sh
```

Give execute permission:

```bash
chmod +x first-script.sh
```

Run the script:

```bash
./first-script.sh
```

---

# 11. Common Error: Permission Denied

## Error

```text
Permission denied
```

## Why it happens

The script does not have execute permission.

## Fix

```bash
chmod +x first-script.sh
```

Then run again:

```bash
./first-script.sh
```

---

# 12. Common Error: Command Not Found

## Error

```text
command not found
```

## Why it happens

Possible reasons:

- Typo in command
- Script name is wrong
- Script is not in current directory
- Missing `./` before script name

## Fix

Check files:

```bash
ls
```

Run with:

```bash
./script-name.sh
```

---

# 13. Demo Script: System Information



This script prints basic system information.

## Why need it?

It shows how Bash scripting can automate useful Linux commands.



Create file:

```bash
nano system-info.sh
```

Add:

```bash
#!/bin/bash

echo "System Information"
echo "=================="

echo "Current User:"
whoami

echo "Current Directory:"
pwd

echo "Hostname:"
hostname

echo "Today Date:"
date

echo "Disk Usage:"
df -h
```

Give permission:

```bash
chmod +x system-info.sh
```

Run:

```bash
./system-info.sh
```

---

# 14. Class Lab

## Lab Title

Create Your First Bash Script

## Requirements

Create a script named:

```bash
intro.sh
```

The script should print:

1. Your name
2. Your course name
3. Current date
4. Current user
5. Current directory
6. Hostname

## Example Script

```bash
#!/bin/bash

echo "My name is Khalid"
echo "I am learning Bash Scripting"

echo "Today date is:"
date

echo "Current user is:"
whoami

echo "Current directory is:"
pwd

echo "Hostname is:"
hostname
```

## Run Steps

```bash
nano intro.sh
chmod +x intro.sh
./intro.sh
```

---

# 15. Mini Practice Task

Create a script named:

```bash
daily-check.sh
```

The script should run these commands:

```bash
date
whoami
hostname
uptime
df -h
free -h
```

Expected learning:

- Students understand how to place commands inside a script.
- Students understand how to run multiple commands automatically.
- Students understand automation.

---

# 16. Teaching Notes for Instructor

## Explain Like This

Bash scripting is not a new language at the beginning.

At first, it is simply Linux commands written inside a file.

Once students understand this, they will feel more comfortable.

Start with simple commands first:

```bash
echo
date
whoami
pwd
hostname
df -h
```

Then slowly introduce:

- Variables
- User input
- Conditions
- Loops
- Functions

## Important Point

Do not start directly with complex scripts.

First teach students:

```text
Command -> Script -> Permission -> Run -> Output
```

This builds confidence.

---

# 17. Suggested Class Flow

| Time | Topic |
|---|---|
| 5 min | What is Bash? |
| 10 min | What is Bash scripting? |
| 10 min | What is automation? |
| 10 min | Why Bash is important in Linux and DevOps |
| 15 min | First Bash script demo |
| 10 min | Permission and running scripts |
| 15 min | System information script |
| 20 min | Hands-on lab |
| 10 min | Common errors |
| 5 min | Final summary and Q&A |

---

# 18. What Students Should Remember

Students should remember:

- Bash is a Linux shell.
- Bash scripting means writing Linux commands inside a file.
- Automation means making repeated work automatic.
- Scripts usually start with `#!/bin/bash`.
- `echo` prints output.
- `chmod +x` gives execute permission.
- `./script.sh` runs the script.
- Bash scripting is very important for Linux and DevOps.

---

# 19. Practice Questions

1. What is Bash?
2. What is Bash scripting?
3. What is automation?
4. Why do we need Bash scripting?
5. What is the purpose of `#!/bin/bash`?
6. What does `echo` do?
7. Why do we use `chmod +x`?
8. How do we run a script from the current directory?
9. What does `pwd` show?
10. What does `whoami` show?
11. What does `hostname` show?
12. What does `df -h` show?
13. What does `free -h` show?
14. What error appears if execute permission is missing?
15. Why is Bash scripting useful in DevOps?

---

# 20. Final Summary

Bash scripting is the process of writing Linux commands inside a file and running them together.

It helps automate repeated tasks.

Automation saves time, reduces mistakes, and makes Linux administration easier.

In this class, students learned:

- What Bash is
- What Bash scripting is
- What automation means
- Why Bash scripting is important
- How to create a script
- How to give execute permission
- How to run a script
- How to create a basic system information script

The most important idea is:

```text
If you can run Linux commands manually, you can start writing Bash scripts.
```

---

# Homework

Create three scripts:

## 1. welcome.sh

Print your name, course, and goal.

## 2. system-info.sh

Print date, user, hostname, uptime, disk usage, and memory usage.

## 3. folders.sh

Create this folder structure:

```text
bash-practice/
├── scripts/
├── logs/
└── backups/
```

Commands to use:

```bash
mkdir -p bash-practice/scripts
mkdir -p bash-practice/logs
mkdir -p bash-practice/backups
```

---

# Closing Line for Class

Today we learned the foundation of Bash scripting.

From the next class, we can start learning variables, user input, and decision-making using `if` statements.
