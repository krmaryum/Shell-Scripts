# Bash Scripting: End-to-End Teaching Curriculum

**Prepared for:** Muhammad Khalid Khan  
**Purpose:** A reusable curriculum for teaching Bash scripting from fundamentals to production-style automation  
**Recommended format:** 10 weeks, 2 lessons per week, 90 minutes per lesson  
**Adaptable formats:** 5-week intensive, 10-week standard, or 20-week extended course

---

## 1. Course Vision

This course teaches students how to think before writing a Bash script. Students progress through the following cycle:

```text
Understand the problem
        |
        v
Define input, processing, and output
        |
        v
Write small testable steps
        |
        v
Validate success and failure paths
        |
        v
Automate safely and document the result
```

The goal is not only to memorize Bash syntax. By the end of the course, students should be able to design, build, test, troubleshoot, and explain practical automation scripts.

---

## 2. Target Audience

This curriculum is designed for:

- Beginners who understand basic Linux commands but have little scripting experience
- Linux administration students
- DevOps and cloud learners
- Junior system administrators
- Professionals preparing for technical interviews

### Recommended prerequisites

Students should know how to:

- Open and use a Linux terminal
- Navigate with `pwd`, `cd`, and `ls`
- Create and inspect files with `touch`, `cat`, `less`, and a text editor
- Understand basic permissions and `sudo`
- Run common commands such as `cp`, `mv`, `rm`, `grep`, and `find`

Do not require programming experience.

---

## 3. Course-Level Learning Outcomes

By the end of the course, students will be able to:

1. Explain what Bash is and when shell scripting is appropriate.
2. Create, execute, and troubleshoot Bash scripts.
3. Use variables, quoting, command substitution, arguments, and user input correctly.
4. Make decisions with tests, exit status, and conditional statements.
5. Repeat work with loops and process collections with arrays.
6. Organize scripts with reusable functions.
7. Process files and command output using pipelines and text-processing tools.
8. Handle failures with validation, logging, traps, and meaningful exit codes.
9. Write safe, readable, idempotent administrative automation.
10. Schedule scripts and verify their execution.
11. Use a structured isolation method to debug scripts.
12. Build and present a documented capstone automation project.

---

## 4. Teaching Model

Use the following sequence in every lesson:

| Stage | Instructor action | Student action |
|---|---|---|
| What? | Define the concept in plain language | Restate the concept |
| Why? | Connect it to a real Linux or DevOps problem | Identify a use case |
| How? | Demonstrate syntax and execution | Follow the demonstration |
| Guided practice | Build one example with the class | Complete each step |
| Independent lab | Provide a problem, requirements, and success criteria | Design and test a solution |
| Review | Discuss errors, alternatives, and safety | Explain the solution |
| Exit ticket | Ask 2-3 short questions | Demonstrate individual understanding |

### Recommended 90-minute lesson pattern

| Time | Activity |
|---:|---|
| 0-10 min | Retrieval practice and review |
| 10-25 min | New concept: What, Why, and How |
| 25-40 min | Instructor demonstration |
| 40-60 min | Guided practice |
| 60-80 min | Independent or pair lab |
| 80-87 min | Troubleshooting discussion |
| 87-90 min | Exit ticket and preview |

---

## 5. Course Sequence at a Glance

| Week | Theme | Main skills | Practical outcome | Milestone |
|---:|---|---|---|---|
| 1 | Bash foundations | Shell, shebang, execution, comments | Run and explain a first script | M1: Script Operator |
| 2 | Data and interaction | Variables, quoting, input, arguments | Build an interactive system-information script | M2: Input Handler |
| 3 | Decisions | Exit status, tests, `if`, `case` | Validate users, files, and services | M3: Decision Builder |
| 4 | Repetition | Loops, lists, arrays | Process users, files, or services safely | M4: Repetition Builder |
| 5 | Reusable design | Functions, scope, return codes | Refactor a script into functions | M5: Script Designer |
| 6 | Text and files | Pipes, `grep`, `sed`, `awk`, `find` | Analyze logs and produce a report | M6: Data Processor |
| 7 | Administration | Users, permissions, processes, disks, services | Create a server health-check tool | M7: Linux Automator |
| 8 | Reliability | Validation, strict mode, traps, logging, debugging | Make an unreliable script safe | M8: Reliability Engineer |
| 9 | Automation | Cron, configuration, idempotency, notifications | Schedule and verify a repeatable job | M9: Automation Operator |
| 10 | Capstone | Planning, testing, documentation, presentation | Deliver production-style automation | M10: Bash Automation Practitioner |

---

# 6. Detailed Lesson Sequence

## Week 1 - Bash Foundations

### Lesson 1: What Bash Is and How Scripts Run

**Key questions**

- What is a shell?
- What is Bash?
- What is the difference between a command and a script?
- When is Bash a good automation choice?

**Topics**

- Shell versus terminal
- Bash interpreter
- Script file structure
- `#!/bin/bash` and `#!/usr/bin/env bash`
- Comments
- `echo` and `printf`
- Running with `bash script.sh`
- Executing with `./script.sh`
- File permissions and `chmod +x`

**Guided lab:** First Script

Create `first-script.sh` that displays:

- Script name
- Current user
- Hostname
- Current directory
- Current date

**Success criteria**

- The script contains a valid shebang.
- It runs with both `bash first-script.sh` and `./first-script.sh`.
- The student can explain why executable permission is required for `./script.sh`.

### Lesson 2: Commands, Output, and Script Readability

**Topics**

- Standard output and standard error
- Command exit status with `$?`
- Command chaining with `&&` and `||`
- Meaningful comments
- Indentation and naming conventions
- ShellCheck as an optional local validation tool

**Independent lab:** Environment Snapshot

Build a script that displays operating system, kernel, uptime, logged-in user, memory summary, and disk usage.

**Assessment:** Five-question foundations quiz and live execution check.

**Milestone M1 - Script Operator**

The student can create, execute, read, and explain a simple Bash script.

---

## Week 2 - Variables, Input, and Arguments

### Lesson 3: Variables and Quoting

**Topics**

- Variable assignment
- Reading variables with `$name` and `${name}`
- Environment variables
- Single quotes versus double quotes
- Whitespace and word splitting
- Command substitution with `$(command)`
- Read-only constants

**Guided lab:** Personalized Server Greeting

Create a script that stores the course name, student name, hostname, and current date in variables and prints a formatted summary.

### Lesson 4: User Input and Positional Arguments

**Topics**

- `read -r`
- Prompts and default values
- `$0`, `$1`, `$2`, `$#`, and `"$@"`
- Required arguments
- Usage messages
- Protecting spaces in input

**Independent lab:** File Inspector

Usage:

```bash
./file-inspector.sh /path/to/file
```

The script must report:

- Whether the path exists
- File type
- Owner and permissions
- Size
- Last modification time

**Negative tests**

- No argument
- Path with spaces
- Missing file

**Milestone M2 - Input Handler**

The student can accept, validate, preserve, and use input safely.

---

## Week 3 - Tests and Decisions

### Lesson 5: Exit Status and Test Expressions

**Topics**

- Success code `0`
- Failure codes
- `test`, `[ ]`, and `[[ ]]`
- String comparisons
- Numeric comparisons
- File tests such as `-e`, `-f`, `-d`, `-r`, and `-w`
- Logical AND, OR, and NOT

**Guided lab:** File and Directory Validator

Accept a path and report whether it is a readable file, writable directory, symbolic link, or missing item.

### Lesson 6: `if`, `elif`, `else`, and `case`

**Topics**

- Conditional flow
- Nested conditions
- Menu selection with `case`
- Guard clauses and early exit
- Returning useful error messages

**Independent lab:** Safe User-Creation Planner

Build the logic for a user-creation script:

```text
Input username
    |
    v
Validate format
    |
    v
Check whether user exists with id
    |
    +-- Yes -> explain and exit 1
    |
    `-- No  -> display planned useradd command
```

Start in dry-run mode. Do not create a real user until the instructor reviews the validation logic.

**Assessment:** Debug three broken conditional scripts.

**Milestone M3 - Decision Builder**

The student can translate requirements into safe decision paths.

---

## Week 4 - Loops and Arrays

### Lesson 7: `for`, `while`, and `until`

**Topics**

- Choosing the correct loop
- Looping over arguments
- Reading files safely with `while IFS= read -r`
- Counters
- `break` and `continue`
- Avoiding infinite loops

**Guided lab:** Multi-Service Status Checker

Check the status of several services and print a consistent result for each one.

### Lesson 8: Arrays and Batch Processing

**Topics**

- Indexed arrays
- Adding and reading elements
- Array length
- Iterating with `"${array[@]}"`
- Recording success and failure counts

**Independent lab:** Batch File Audit

Process a list of paths and classify each as:

- File
- Directory
- Symbolic link
- Missing

Finish with totals for each category.

**Assessment:** Loop trace worksheet plus lab demonstration.

**Milestone M4 - Repetition Builder**

The student can process multiple items without duplicating code.

---

## Week 5 - Functions and Script Design

### Lesson 9: Functions, Parameters, and Return Codes

**Topics**

- Function syntax
- Parameters inside functions
- Local variables
- Output versus return status
- Calling functions
- One responsibility per function

**Guided lab:** Refactor the File Inspector

Create separate functions for:

- Usage
- Input validation
- File classification
- Report formatting
- Main workflow

### Lesson 10: Planning Before Scripting

**Topics**

- Problem statement
- Inputs, processing, and outputs
- Assumptions and constraints
- Pseudocode
- Flowcharts
- Positive and negative test cases
- Main function pattern

**Independent lab:** Design Before Code

Students receive this requirement:

> Create a backup script that accepts a source directory and destination directory, validates both, creates a timestamped archive, and reports success or failure.

Before writing Bash, students must submit:

1. Problem statement
2. Input list
3. Validation rules
4. Pseudocode
5. Test table
6. Cleanup or rollback plan

**Midterm practical:** Build the approved backup script.

**Milestone M5 - Script Designer**

The student can plan and modularize a multi-step script.

---

## Week 6 - Pipelines and Text Processing

### Lesson 11: Redirection and Pipelines

**Topics**

- Standard input, output, and error
- `>`, `>>`, `2>`, `2>&1`, and `/dev/null`
- Pipes
- `tee`
- `cut`, `sort`, `uniq`, `head`, `tail`, and `wc`
- Pipeline exit-status concerns

**Guided lab:** Failed Login Summary

Use a safe sample log file to count and rank repeated failed-login sources.

### Lesson 12: `grep`, `sed`, `awk`, and `find`

**Topics**

- Literal and regular-expression searches
- Field extraction
- Simple substitutions
- Structured text summaries
- Safe use of `find`
- Handling filenames correctly

**Independent lab:** Log Analysis Report

Generate a report containing:

- Total lines
- Error and warning counts
- Top repeated error messages
- First and last event times when available
- Output filename with timestamp

**Assessment:** Students explain every stage of one pipeline.

**Milestone M6 - Data Processor**

The student can transform command output and text into useful evidence.

---

## Week 7 - Linux Administration Automation

### Lesson 13: Processes, Services, Disk, and Memory

**Topics**

- `ps`, `pgrep`, `uptime`, `free`, `df`, `du`, and `ss`
- `systemctl is-active`
- Load average and CPU count
- Thresholds and warnings
- Avoiding false conclusions from one metric

**Guided lab:** Server Health Check

Report:

- Uptime and load average
- CPU count
- Memory availability
- Filesystem usage
- Required service status
- Listening ports

Use `OK`, `WARNING`, and `CRITICAL` result levels.

### Lesson 14: Users, Permissions, and Administrative Safety

**Topics**

- Checking users with `id`
- File ownership and permission validation
- Root checks with `$EUID`
- Least privilege
- Dry-run mode
- Confirmation gates for destructive actions

**Independent lab:** User Onboarding Automation

Required workflow:

1. Validate username.
2. Check whether the user exists.
3. Create the user only when approved.
4. Assign an approved group.
5. Create a home directory.
6. Record actions in a log.
7. Print a final summary.

Use only disposable lab systems.

**Milestone M7 - Linux Automator**

The student can automate common administrative checks without bypassing safety.

---

## Week 8 - Reliability, Errors, and Debugging

### Lesson 15: Defensive Bash

**Topics**

- Input validation
- Meaningful exit codes
- `set -u`
- `set -o pipefail`
- Careful use of `set -e`
- Temporary files with `mktemp`
- Cleanup with `trap`
- Quoting variables
- Dependency checks with `command -v`

**Guided lab:** Harden the Backup Script

Add:

- Dependency checks
- Source/destination validation
- Free-space check
- Temporary-file cleanup
- Failure logging
- Clear exit codes

### Lesson 16: Isolation-Based Debugging

**Debugging sequence**

```text
1. Reproduce the problem
2. Read the exact error
3. Check syntax with bash -n
4. Trace execution with bash -x
5. Verify input and environment
6. Isolate the smallest failing command
7. Fix one cause
8. Retest positive and negative paths
```

**Topics**

- `bash -n script.sh`
- `bash -x script.sh`
- Targeted tracing with `set -x` and `set +x`
- `PS4` trace context
- Logging function name and timestamp
- Syntax, runtime, logic, permission, and environment failures

**Independent lab:** Script Repair Challenge

Students receive a script containing at least eight defects, including:

- Missing quotes
- Incorrect test spacing
- Wrong variable name
- Broken exit-status check
- Unsafe temporary file
- Pipeline failure hidden by the last command
- Missing argument validation
- Incorrect function return logic

**Milestone M8 - Reliability Engineer**

The student can diagnose and harden a failing script systematically.

---

## Week 9 - Scheduling and Repeatable Automation

### Lesson 17: Cron and Non-Interactive Environments

**Topics**

- Crontab structure
- Absolute paths
- Minimal environment and `PATH`
- Working directory assumptions
- Redirecting output and errors
- Locking to prevent overlapping runs
- Testing before scheduling

**Guided lab:** Scheduled Disk Report

Create a disk report script, run it manually, schedule it, and prove execution through a timestamped log.

### Lesson 18: Idempotency, Configuration, and Operational Readiness

**Topics**

- Idempotent behavior
- Configuration variables
- Separating configuration from logic
- Lock files and duplicate prevention
- Log rotation awareness
- Runbooks
- Safe cleanup

**Independent lab:** Idempotent Directory Deployment

The script must create an application directory structure, permissions, configuration file, and log location. Running it repeatedly must not create duplicate or conflicting state.

**Optional DevOps extension**

- Use an EC2 instance role instead of static AWS access keys.
- Run `aws sts get-caller-identity` before AWS CLI work.
- Build a read-only AWS resource inventory or cleanup-check report.
- Keep destructive actions behind an explicit `--execute` option.

**Milestone M9 - Automation Operator**

The student can schedule, verify, and safely rerun an unattended script.

---

## Week 10 - Capstone and Professional Delivery

### Lesson 19: Capstone Build and Review

Students work through:

1. Requirements review
2. Design and pseudocode
3. Function breakdown
4. First implementation
5. Positive tests
6. Negative tests
7. Peer code review
8. Reliability improvements

### Lesson 20: Demonstration, Interview Defense, and Reflection

Each student must:

- Explain the problem and target user.
- Draw or describe the workflow.
- Demonstrate a successful run.
- Demonstrate at least two controlled failures.
- Explain safety controls.
- Show logs and exit codes.
- Describe one improvement for a future version.

**Milestone M10 - Bash Automation Practitioner**

The student can deliver and defend a documented automation solution.

---

# 7. Practical Lab Ladder

The lab sequence intentionally increases in difficulty.

| Level | Lab | Primary concepts | Required evidence |
|---:|---|---|---|
| 1 | First Script | Shebang, execution, output | Two execution methods |
| 2 | Environment Snapshot | Commands, formatting | Expected output |
| 3 | File Inspector | Arguments, tests, quoting | Path-with-spaces test |
| 4 | File Validator | Conditions, exit codes | Missing-path failure |
| 5 | User-Creation Planner | Validation, guard clauses | Dry-run output |
| 6 | Service Checker | Loops, status checks | Success/failure totals |
| 7 | Batch File Audit | Arrays, loops | Category totals |
| 8 | Backup Script | Functions, planning | Archive and restore test |
| 9 | Log Analyzer | Pipes, `grep`, `awk` | Generated report |
| 10 | Health Check | Linux metrics, thresholds | OK/WARNING/CRITICAL result |
| 11 | User Onboarding | Privilege and logging | Disposable-system demo |
| 12 | Script Repair | Debugging and reliability | Defect log and fixes |
| 13 | Scheduled Disk Report | Cron and environment | Timestamped execution log |
| 14 | Idempotent Deployment | Repeatability | Two identical safe runs |
| 15 | Capstone | End-to-end design | Code, tests, README, demo |

---

# 8. Standard Lab Template

Use this structure for every lab handout.

## Lab title

### Scenario

Describe a realistic problem in two or three sentences.

### Objective

State what the student will build.

### Requirements

- Required inputs
- Required processing
- Required output
- Required functions or control structures
- Required safety checks

### Constraints

- Approved commands
- Time limit
- Whether `sudo` is permitted
- Whether the script must run on Ubuntu, RHEL-family systems, or both

### Success criteria

- Expected success behavior
- Expected failure behavior
- Required exit codes
- Required log or report

### Test table

| Test | Input or condition | Expected result | Actual result | Pass? |
|---|---|---|---|---|
| Normal | Valid input | Successful result | | |
| Missing input | No argument | Usage + nonzero exit | | |
| Invalid input | Bad value | Clear error | | |
| Permission failure | Restricted path | Safe failure | | |
| Repeat run | Run twice | No harmful duplication | | |

### Reflection

1. What was the first failure?
2. How did you isolate it?
3. What safety control did you add?
4. What would you improve next?

---

# 9. Assessment Strategy

## Recommended grading distribution

| Assessment | Weight | Purpose |
|---|---:|---|
| Entry diagnostic | 0% | Identify prerequisite gaps |
| Weekly exit tickets | 10% | Check individual understanding |
| Practical labs | 35% | Measure applied skill |
| Quizzes | 15% | Reinforce vocabulary and syntax |
| Midterm practical | 15% | Test planning and modular scripting |
| Capstone project | 20% | Demonstrate end-to-end automation |
| Capstone explanation | 5% | Measure communication and ownership |
| **Total** | **100%** | |

## Assessment rhythm

| Timing | Assessment |
|---|---|
| Every lesson | 2-3 question exit ticket |
| Every week | One practical lab |
| End of Weeks 2, 4, 6, and 8 | Short quiz |
| End of Week 5 | Midterm design + practical |
| Week 8 | Debugging challenge |
| Week 10 | Capstone and presentation |

## Exit-ticket examples

1. What is the difference between `"$@"` and `$@`?
2. Why does exit code `0` mean success?
3. When should you use `[[ ]]`?
4. Why should variables containing paths be quoted?
5. What does `set -o pipefail` change?
6. Why can a cron job fail when the script works manually?

## Practical assessment rules

Students should be evaluated on both the result and the process:

- Did the student define the problem?
- Did the student validate input?
- Did the student test failure paths?
- Did the student use readable structure?
- Did the student collect evidence?
- Can the student explain why the script works?

---

# 10. Lab and Capstone Rubrics

## Standard practical-lab rubric - 20 points

| Category | Excellent | Developing | Missing | Points |
|---|---|---|---|---:|
| Requirements | All requirements work | Some requirements work | Major requirements missing | 4 |
| Input validation | Validates normal and failure inputs | Partial validation | Unsafe or no validation | 3 |
| Logic | Clear and correct control flow | Works with unnecessary complexity | Incorrect logic | 3 |
| Safety | Uses quoting, checks, and controlled actions | Some safeguards | Risky behavior | 3 |
| Readability | Clear names, functions, comments, formatting | Understandable but inconsistent | Difficult to follow | 2 |
| Testing | Positive and negative tests documented | Only success test | No evidence | 3 |
| Explanation | Student clearly explains decisions | Partial explanation | Cannot explain solution | 2 |

## Capstone rubric - 100 points

| Category | Points |
|---|---:|
| Problem definition and requirements | 10 |
| Workflow, pseudocode, and design | 10 |
| Functional correctness | 20 |
| Input validation and error handling | 15 |
| Safety and idempotency | 15 |
| Functions, readability, and maintainability | 10 |
| Test plan and evidence | 10 |
| README and runbook | 5 |
| Demonstration and technical explanation | 5 |
| **Total** | **100** |

### Minimum capstone requirements

- Valid shebang
- Usage/help output
- At least two command-line options or arguments
- Input validation
- At least three functions
- Meaningful exit codes
- Logging
- Cleanup or rollback handling
- Positive and negative tests
- Safe repeat execution
- README with examples

---

# 11. Capstone Project Options

## Option A: Server Health and Alert Report

Check CPU/load, memory, disk, services, and listening ports. Produce a timestamped report with severity levels.

## Option B: Backup, Verification, and Retention Tool

Create timestamped archives, verify the archive, enforce retention, log activity, and support dry-run mode.

## Option C: User Onboarding and Offboarding Tool

Validate user data, create or lock accounts, manage approved groups, log changes, and require confirmation for destructive steps.

## Option D: Log Monitoring and Summary Tool

Analyze an application or system log, summarize errors, track repeated messages, and create a daily report.

## Option E: Service Deployment Validator

Check configuration files, permissions, service status, listening port, and local HTTP response. Produce PASS/FAIL evidence.

## Option F: AWS Resource Inventory Extension

Use the AWS CLI with an IAM role to collect a read-only resource inventory. Validate identity with STS, support multiple regions, log failures, and avoid destructive actions.

---

# 12. Teaching Milestones and Intervention Points

| Milestone | Student demonstration | Instructor decision |
|---|---|---|
| M1: Script Operator | Runs and explains a basic script | Reteach permissions/shebang if execution is unclear |
| M2: Input Handler | Preserves spaces and validates arguments | Add quoting practice if filenames break |
| M3: Decision Builder | Uses exit status and conditions correctly | Review test syntax and logic tracing |
| M4: Repetition Builder | Selects the correct loop and terminates safely | Address infinite loops before arrays |
| M5: Script Designer | Submits pseudocode and functions before code | Require redesign if one block contains all logic |
| M6: Data Processor | Explains every pipeline stage | Reduce pipeline length if understanding is weak |
| M7: Linux Automator | Uses least privilege and dry-run behavior | Stop privileged labs if safety is missing |
| M8: Reliability Engineer | Uses syntax checks, traces, traps, and logs | Repeat repair lab if fixes are guesses |
| M9: Automation Operator | Proves scheduled execution and repeatability | Review environment/PATH and locking |
| M10: Practitioner | Demonstrates, defends, and documents capstone | Assign targeted remediation by rubric category |

---

# 13. Differentiation for Mixed-Skill Classes

## Support for beginners

- Provide command reference cards.
- Give partial pseudocode before code.
- Use small scripts with one new concept at a time.
- Pair students for guided labs, then require individual exit tickets.
- Supply sample input files.
- Use dry-run mode before privileged operations.
- Allow a test checklist during labs.

## Extensions for advanced students

- Add `getopts` or long-option parsing.
- Support Debian/Ubuntu and RHEL-family distributions.
- Add structured CSV or JSON output when appropriate.
- Write Bats tests if available locally.
- Add concurrency protection with `flock`.
- Add configuration-file support.
- Package the script with a man page or installation target.
- Integrate a read-only AWS CLI workflow using an instance role.

## Adaptation by class type

| Class type | Emphasize | Reduce |
|---|---|---|
| Linux beginners | Commands, permissions, tests, loops | Cloud extensions |
| Linux administrators | Users, services, storage, logs, scheduling | Introductory shell theory |
| DevOps learners | Idempotency, CI validation, cloud CLI, configuration | Manual administration detail |
| Interview preparation | Explanation, scenarios, debugging, tradeoffs | Long build time |
| Short workshop | Foundations, decisions, functions, one capstone | Arrays and advanced text processing |

---

# 14. Pacing Alternatives

## Five-week intensive

Teach four lessons per week:

1. Foundations and input
2. Decisions and loops
3. Functions and text processing
4. Administration and reliability
5. Automation and capstone

Recommended homework: one lab after every class.

## Ten-week standard

Teach two 90-minute lessons per week using the sequence in this curriculum.

## Twenty-week extended

Teach one lesson per week and use the second weekly meeting, if available, entirely for labs, review, and student demonstrations.

---

# 15. Instructor Preparation Checklist

## Before the course

- [ ] Confirm each student has a disposable Linux environment.
- [ ] Test commands on the distributions students will use.
- [ ] Prepare sample files and logs without sensitive data.
- [ ] Create starter and completed versions of each demonstration.
- [ ] Define where students submit scripts and evidence.
- [ ] Publish safety rules and the grading rubric.
- [ ] Run every lab from a clean environment.

## Before each lesson

- [ ] Define one primary learning objective.
- [ ] Prepare the What, Why, and How explanation.
- [ ] Test the instructor demonstration.
- [ ] Prepare one intentional error for troubleshooting.
- [ ] Confirm the independent lab has clear success criteria.
- [ ] Prepare the exit ticket.

## After each lesson

- [ ] Record common errors.
- [ ] Identify students needing a small-group review.
- [ ] Update the next lesson's retrieval questions.
- [ ] Save an improved example based on student confusion.
- [ ] Confirm students did not leave scheduled jobs or lab resources running.

---

# 16. Safety Rules for All Classes

1. Use disposable lab systems, not production servers.
2. Read a destructive command aloud before running it.
3. Quote variables that contain user input, paths, or filenames.
4. Validate input before privileged operations.
5. Use dry-run behavior before making changes.
6. Keep backups of important files.
7. Never place passwords or access keys directly in scripts.
8. Prefer roles and temporary credentials for cloud workloads.
9. Require explicit confirmation or `--execute` for destructive operations.
10. Test cleanup and rollback procedures.

---

# 17. Student Script Submission Standard

Every major script should include:

```bash
#!/usr/bin/env bash

# Description:
# Author:
# Usage:
# Requirements:
# Safety notes:
```

Every submission should contain:

- `script-name.sh`
- `README.md`
- `test-results.md`
- Sample configuration or input file when needed
- Sample output without secrets

The README should explain:

1. What problem the script solves
2. Requirements
3. Usage
4. Examples
5. Exit codes
6. Test cases
7. Safety and rollback
8. Known limitations

---

# 18. Final Course Completion Checklist

A student is ready to complete the course when they can independently:

- [ ] Convert a requirement into input, processing, and output.
- [ ] Write pseudocode before a multi-step script.
- [ ] Use variables and quoting safely.
- [ ] Accept arguments and display usage information.
- [ ] Use exit status, tests, and conditions.
- [ ] Select appropriate loops and arrays.
- [ ] Organize logic into functions.
- [ ] Process files and command output.
- [ ] Validate permissions and dependencies.
- [ ] Use meaningful exit codes.
- [ ] Produce useful logs.
- [ ] Clean up temporary state with a trap.
- [ ] Debug with `bash -n` and `bash -x`.
- [ ] Schedule a script and prove it ran.
- [ ] Make repeat execution safe.
- [ ] Test both success and failure paths.
- [ ] Explain the script to another person.
- [ ] Deliver a documented capstone project.

---

## Closing Teaching Principle

Do not measure Bash learning only by whether a script produces output. A successful student should be able to explain the logic, predict failure, isolate errors, protect the system, and improve the script for the next person who must use it.

