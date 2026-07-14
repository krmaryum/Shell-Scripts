# Bash Scripting Week 1 Assessment and Answer Key

**Total:** 25 points  
**Suggested time:** 25 minutes written + 15 minutes practical

---

# Student Assessment

## Part A - Multiple Choice - 8 points

Choose the best answer.

### 1. What is Bash?

A. A Linux desktop  
B. A command-line shell and scripting language  
C. A file permission  
D. A text editor

### 2. What is the main purpose of a shebang?

A. It creates a comment section  
B. It makes every script secure  
C. It identifies the interpreter for direct execution  
D. It installs Bash

### 3. Which command adds executable permission?

A. `chmod +x script.sh`  
B. `bash +x script.sh`  
C. `execute script.sh`  
D. `chmod +r script.sh`

### 4. What does `./script.sh` mean?

A. Run a file named `script.sh` from the current directory  
B. Delete `script.sh`  
C. Run the script as root  
D. Open the script in Bash documentation

### 5. What normally indicates command success?

A. Exit status `1`  
B. Exit status `0`  
C. No comments  
D. Executable permission

### 6. When does the second command run in `command1 && command2`?

A. Only when `command1` succeeds  
B. Only when `command1` fails  
C. Before `command1`  
D. Always

### 7. When does the second command run in `command1 || command2`?

A. Only when `command1` succeeds  
B. Only when `command1` fails  
C. Before `command1`  
D. Never

### 8. Why should `$?` be checked immediately?

A. It changes after the next command  
B. It deletes the previous command  
C. It works only once per login  
D. It stores the script filename

## Part B - Short Answer - 7 points

### 9. Explain the difference between a terminal and a shell.

### 10. Explain why `bash script.sh` may work when `./script.sh` returns `Permission denied`.

### 11. What is the difference between standard output and standard error?

### 12. Write a command that runs `echo "Backup succeeded"` only when `tar` succeeds.

## Part C - Practical Checkpoint - 10 points

Create `week1-checkpoint.sh` that:

1. Uses a valid Bash shebang.
2. Contains a description comment.
3. Displays a heading.
4. Displays current username.
5. Displays hostname.
6. Displays current directory.
7. Displays current date.
8. Runs with `bash week1-checkpoint.sh`.
9. Runs with `./week1-checkpoint.sh` after permissions are set.
10. Returns exit status `0`.

The student must explain every line.

---

# Instructor Answer Key

## Part A

| Question | Answer | Explanation |
|---:|:---:|---|
| 1 | B | Bash is both a shell and a scripting language. |
| 2 | C | The shebang identifies the interpreter used for direct execution. |
| 3 | A | `chmod +x` adds execute permission. |
| 4 | A | `./` identifies a path in the current directory. |
| 5 | B | Unix-like systems normally use `0` for success. |
| 6 | A | `&&` continues on success. |
| 7 | B | `||` continues on failure. |
| 8 | A | `$?` always represents the most recently completed foreground pipeline. |

## Part B Suggested Answers

### 9.

A terminal is the interface or window used to interact with a command-line environment. A shell is the program that reads and interprets commands. Bash is one shell.

### 10.

`bash script.sh` explicitly starts Bash and asks it to read the file. Direct execution with `./script.sh` requires executable permission and a valid interpreter directive.

### 11.

Standard output carries normal command results. Standard error carries error and diagnostic messages. They are separate streams even when both appear in the terminal.

### 12.

```bash
tar <required-options> && echo "Backup succeeded"
```

Accept a complete valid `tar` example or the logical pattern when no archive requirements were supplied.

## Practical Rubric

| Criterion | Points |
|---|---:|
| Valid shebang and description | 2 |
| Required identity information | 4 |
| Bash execution works | 1 |
| Direct execution works | 1 |
| Exit status is `0` | 1 |
| Student explains every line | 1 |
| **Total** | **10** |

## Milestone Decision

Award **M1 - Script Operator** when the student earns at least 18/25 overall and completes every practical execution requirement. A student who scores well on the written section but cannot execute or explain the script should repeat the practical checkpoint.

