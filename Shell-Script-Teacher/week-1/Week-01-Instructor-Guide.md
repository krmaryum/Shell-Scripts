# Week 1 Instructor Guide - Bash Foundations

## Course Position

Week 1 establishes the operating model students will use throughout the Bash course:

```text
Understand -> Predict -> Run -> Observe -> Explain -> Improve
```

Avoid introducing complex automation too early. The Week 1 objective is confidence with script structure, execution, output, and basic failure evidence.

## Instructor Preparation

Before class:

- Confirm students have Bash available.
- Create a working directory such as `~/bash-course/week-01`.
- Test all three demonstration scripts.
- Confirm students can edit files with their preferred editor.
- Prepare one script without executable permission for troubleshooting.
- Prepare one script with an invalid interpreter path.
- Keep the student lab and assessment files available locally.

## Required Commands

```bash
bash --version
pwd
ls -l
chmod +x script.sh
bash script.sh
./script.sh
echo $?
command -v bash
```

---

# Lesson 1 - What Bash Is and How Scripts Run

**Duration:** 90 minutes  
**Slides:** 1-7  
**Primary objective:** Students create and execute a valid first script.

## Lesson 1 Success Criteria

By the end of the lesson, students can:

- Explain terminal versus shell.
- Explain command versus script.
- Identify the shebang.
- Run a script with `bash`.
- Make a script executable.
- Run a script with `./`.
- Explain one execution error.

## Lesson 1 Sequence

| Time | Activity | Instructor focus | Evidence |
|---:|---|---|---|
| 0-10 min | Welcome and retrieval | Ask what happens after typing `ls` | Student predictions |
| 10-22 min | Terminal, shell, and Bash | Use Slides 1-3 | Students restate the relationship |
| 22-35 min | How a script runs | Use Slide 4 | Students trace editor -> file -> Bash -> output |
| 35-47 min | Script anatomy | Use Slide 5 | Students label each line |
| 47-60 min | Two execution methods | Use Slide 6 | Students predict permission behavior |
| 60-70 min | Instructor demonstration | Run `first-script.sh` | Visible command and output |
| 70-84 min | Student Lab 1 | Observe without taking control | Completed script and tests |
| 84-90 min | Exit Ticket A | Check individual understanding | Three written answers |

## Teaching Notes

### Terminal, shell, and Bash

Use this explanation:

- The **terminal** is the window or interface.
- The **shell** reads commands and requests work from the operating system.
- **Bash** is one type of shell.
- A **script** stores a sequence of commands in a file.

Analogy:

```text
Terminal = classroom microphone
Shell/Bash = interpreter receiving the instruction
Command = one instruction
Script = prepared list of instructions
```

Clarify that a terminal is not Bash itself. A terminal can run different shells.

### Shebang

Explain:

```bash
#!/usr/bin/env bash
```

- `#!` begins the interpreter directive.
- `/usr/bin/env bash` locates Bash through the environment.
- The shebang matters when the script is executed directly with `./script.sh`.
- Running `bash script.sh` explicitly selects Bash, so Bash reads the file directly.

### Two execution methods

Method 1:

```bash
bash first-script.sh
```

Method 2:

```bash
chmod +x first-script.sh
./first-script.sh
```

Emphasize:

- `bash script.sh` requires read permission for the user.
- `./script.sh` requires executable permission and a usable interpreter directive.
- `./` means the file is in the current directory.

## Demonstration 1 - First Script

Open `demo-scripts/first-script.sh` and ask students to predict each output line before running it.

Run:

```bash
ls -l demo-scripts/first-script.sh
bash demo-scripts/first-script.sh
echo $?
chmod +x demo-scripts/first-script.sh
./demo-scripts/first-script.sh
echo $?
```

### Intentional error demonstration

Remove executable permission:

```bash
chmod -x demo-scripts/first-script.sh
./demo-scripts/first-script.sh
```

Ask students to isolate the problem from the exact error. Restore permission afterward.

## Common Misconceptions and Interventions

| Misconception | Instructor response |
|---|---|
| The terminal and Bash are the same | Ask which shell `echo "$SHELL"` reports and explain the terminal hosts it |
| `.sh` makes a file executable | Show `ls -l`; permissions control execution |
| The shebang is a comment | Explain that the kernel treats the first `#!` line specially during direct execution |
| `./` is part of the filename | Use `pwd` and explain current-directory path notation |
| No output means success | Introduce exit status as separate evidence |

## Exit Ticket A

1. What is the difference between a terminal and Bash?
2. Why can `bash script.sh` work when `./script.sh` fails?
3. What does the shebang tell the system?

---

# Lesson 2 - Output, Errors, Exit Status, and Readability

**Duration:** 90 minutes  
**Slides:** 8-12  
**Primary objective:** Students observe command results and build an environment-snapshot script.

## Lesson 2 Success Criteria

By the end of the lesson, students can:

- Distinguish standard output and standard error.
- Check the most recent exit status.
- Explain exit code `0` and nonzero exit codes.
- Use `&&` for success flow.
- Use `||` for failure flow.
- Create readable output with `printf`.
- Build and test a system-information script.

## Lesson 2 Sequence

| Time | Activity | Instructor focus | Evidence |
|---:|---|---|---|
| 0-10 min | Retrieval practice | Rebuild a four-line script from memory | Student script |
| 10-25 min | Output, error, and status | Use Slide 8 | Students classify evidence |
| 25-38 min | `&&` and `||` | Use Slide 9 | Students predict flow |
| 38-50 min | Demonstration | Run `exit-status-demo.sh` | Predictions versus output |
| 50-62 min | Readable reporting | Use Slide 10 | Students identify report sections |
| 62-76 min | Student Lab 2 | Environment Snapshot | Working script |
| 76-84 min | Pair explanation | Each student explains two lines | Oral evidence |
| 84-90 min | Assessment launch | Slides 11-12 | Individual checkpoint |

## Teaching Notes

### Three different kinds of evidence

```text
Standard output  -> normal information
Standard error   -> error information
Exit status      -> numeric success or failure result
```

Use:

```bash
pwd
echo $?
ls /missing-path
echo $?
```

Important: `$?` changes after every command. Check it immediately.

### Success and failure chaining

```bash
command && echo "Command succeeded"
command || echo "Command failed"
```

Explain:

- The right side of `&&` runs only when the left side succeeds.
- The right side of `||` runs only when the left side fails.
- These operators do not replace thoughtful `if` statements in complex scripts.

## Demonstration 2 - Exit Status

Run:

```bash
bash demo-scripts/exit-status-demo.sh
```

Pause before each example and ask:

1. Will this command succeed?
2. Which message will run?
3. What exit status should appear?

## Demonstration 3 - Environment Snapshot

Run:

```bash
bash demo-scripts/environment-snapshot.sh
```

Ask students to identify:

- Static labels
- Commands
- Command substitution
- Quoted variables
- Formatting choices

Do not formally teach variables in depth yet; preview them as named containers for Week 2.

## Common Errors and Isolation Questions

| Error | Isolation question |
|---|---|
| `Permission denied` | Does the chosen execution method require execute permission? |
| `bad interpreter` | Does the shebang point to an available interpreter? |
| `command not found` | Is the command installed and spelled correctly? |
| Wrong exit status | Was another command run before checking `$?`? |
| Text appears on one line | Was `printf` or a newline used correctly? |
| Script works only from one directory | Does it assume a relative path? |

## Exit Ticket B

1. What does exit status `0` mean?
2. When does the right side of `&&` run?
3. Why must `$?` be checked immediately?

---

# Week 1 Milestone Check

Award **M1 - Script Operator** when the student can complete this without step-by-step help:

1. Create `milestone.sh`.
2. Add a valid Bash shebang.
3. Display username, hostname, and current directory.
4. Run it with `bash milestone.sh`.
5. Make it executable.
6. Run it with `./milestone.sh`.
7. Check exit status.
8. Explain every line.

## Instructor Recording Grid

| Student | Structure | Execution | Permission | Exit status | Explanation | M1 achieved? |
|---|---|---|---|---|---|---|
| | | | | | | |
| | | | | | | |
| | | | | | | |

## Differentiation

### Additional support

- Provide a partially completed shebang and output template.
- Pair command names with their purpose.
- Allow a command reference card.
- Require the student to type the final version independently.

### Advanced extension

- Add `set -u` and discuss what it protects.
- Compare `#!/bin/bash` with `#!/usr/bin/env bash`.
- Send one message to standard error with `>&2`.
- Add a deliberate failure and return a chosen exit code.

