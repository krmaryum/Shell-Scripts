# Bash Scripting Week 1 - Student Labs

## Lab Environment

Use a disposable Linux environment. Create a dedicated directory:

```bash
mkdir -p ~/bash-course/week-01
cd ~/bash-course/week-01
```

Do not copy and paste without reading. Predict the result before each test.

---

# Lab 1 - My First Bash Script

## Scenario

You need a small script that quickly identifies the current system and user before beginning administrative work.

## Objective

Create a script that runs in two ways and displays basic identity information.

## Requirements

Create a file named `first-script.sh` containing:

- A valid Bash shebang
- A description comment
- A welcome heading
- Current username
- Hostname
- Current directory
- Current date and time

Use these commands where appropriate:

```bash
whoami
hostname
pwd
date
```

## Required Tests

### Test 1 - Run through Bash

```bash
bash first-script.sh
echo $?
```

### Test 2 - Run directly

```bash
chmod +x first-script.sh
./first-script.sh
echo $?
```

### Test 3 - Observe a permission failure

```bash
chmod -x first-script.sh
./first-script.sh
```

Record the exact error, explain it, and restore executable permission.

## Test Record

| Test | Expected result | Actual result | Pass? |
|---|---|---|---|
| `bash first-script.sh` | Script displays all information | | |
| `./first-script.sh` before `chmod +x` | Permission failure | | |
| `./first-script.sh` after `chmod +x` | Script displays all information | | |
| `echo $?` after success | `0` | | |

## Explanation Check

Be ready to explain:

1. What the shebang does
2. Why `./` is used
3. Why executable permission matters
4. What exit status `0` means

---

# Lab 2 - Environment Snapshot

## Scenario

A support engineer needs a quick, read-only summary when connecting to a Linux server.

## Objective

Build a readable script that reports essential environment information without changing the system.

## Requirements

Create `environment-snapshot.sh` that displays:

1. Report heading
2. Date and time
3. Current user
4. Hostname
5. Current directory
6. Kernel information
7. System uptime
8. Memory summary
9. Disk usage for `/`
10. Final success message

Suggested commands:

```bash
date
whoami
hostname
pwd
uname -r
uptime
free -h
df -h /
```

## Output Quality

- Use clear section labels.
- Put each section on a new line.
- Add comments for the main sections.
- Do not hide errors.
- Do not use `sudo`.

## Required Tests

```bash
bash -n environment-snapshot.sh
bash environment-snapshot.sh
echo $?
chmod +x environment-snapshot.sh
./environment-snapshot.sh
echo $?
```

## Test Record

| Test | Expected result | Actual result | Pass? |
|---|---|---|---|
| Syntax check | No output and exit status `0` | | |
| Bash execution | Complete report | | |
| Direct execution | Complete report | | |
| Final status | `0` | | |

## Independent Challenge

Add one controlled failure test:

```bash
ls /path-that-does-not-exist
```

Then answer:

1. Where does the error message appear?
2. What exit status is returned?
3. What happens with this command?

```bash
ls /path-that-does-not-exist || echo "The check failed as expected"
```

---

# Week 1 Reflection

1. What is the difference between a terminal and Bash?
2. What is the difference between a command and a script?
3. Why can `bash script.sh` work without executable permission?
4. Why can `./script.sh` fail?
5. What evidence shows whether the last command succeeded?
6. Which error did you encounter, and how did you isolate it?

## Submission Checklist

- [ ] `first-script.sh`
- [ ] `environment-snapshot.sh`
- [ ] Completed test tables
- [ ] Week 1 reflection answers
- [ ] Both scripts run successfully
- [ ] Student can explain every line

