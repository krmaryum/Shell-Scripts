# Bash Scripting Week 2 - Student Labs

Create the Week 2 workspace:

```bash
mkdir -p ~/bash-course/week-02
cd ~/bash-course/week-02
```

---

# Lab 1 - Personalized Server Greeting

## Scenario

A training server should display a personalized session summary without hard-coding the student's name.

## Objective

Use variables, interactive input, quoting, and command substitution to create a readable greeting.

## Requirements

Create `server-greeting.sh` that:

1. Uses a valid Bash shebang.
2. Prompts for the student's full name with `read -r`.
3. Rejects empty input.
4. Stores course name in a variable.
5. Captures username, hostname, directory, and date with `$(command)`.
6. Displays a formatted summary.
7. Preserves a full name containing spaces.

## Required Tests

| Test | Input | Expected result | Actual | Pass? |
|---|---|---|---|---|
| Normal | `Ali Khan` | Full name remains intact | | |
| One word | `Ali` | Greeting displays correctly | | |
| Empty | Press Enter | Error + nonzero exit | | |
| Backslash | `Lab\\User` | Backslash remains | | |

## Explanation Check

Explain:

- Why `read -r` is used
- Why `"$student_name"` is quoted
- What happens inside `$(hostname)`
- Why `${student_name}` may be clearer next to other text

---

# Lab 2 - Safe File Inspector

## Scenario

A support engineer needs a script that accepts one path and reports basic information without failing on spaces.

## Objective

Use positional arguments, argument-count validation, quoting, file tests, and usage guidance.

## Required Behavior

Usage:

```bash
./file-inspector.sh <path>
```

The script must:

1. Require exactly one argument.
2. Display usage and exit `2` when invocation is incorrect.
3. Store `$1` in a clearly named variable.
4. Quote the variable every time it is used.
5. Report whether the path exists.
6. Classify it as a regular file, directory, symbolic link, or other item.
7. Display owner, permissions, size, and modification time when possible.
8. Exit `1` when the path does not exist.
9. Exit `0` after a successful report.

## Test Setup

```bash
mkdir -p test-data
touch "test-data/server report.txt"
mkdir -p "test-data/archive folder"
ln -s "server report.txt" "test-data/latest report"
```

## Required Tests

| Test | Command | Expected status | Pass? |
|---|---|---:|---|
| No argument | `./file-inspector.sh` | 2 | |
| Too many | `./file-inspector.sh one two` | 2 | |
| File with spaces | `./file-inspector.sh "test-data/server report.txt"` | 0 | |
| Directory with spaces | `./file-inspector.sh "test-data/archive folder"` | 0 | |
| Symbolic link | `./file-inspector.sh "test-data/latest report"` | 0 | |
| Missing path | `./file-inspector.sh missing.txt` | 1 | |

## Advanced Challenge

Accept multiple paths using `"$@"` and produce one result per path. Keep each argument separate even when it contains spaces.

---

# Week 2 Reflection

1. Why is `name = "Ali"` invalid?
2. When do single quotes prevent expansion?
3. Why should path variables be double quoted?
4. What does `$#` tell a script?
5. What is the difference between `$1` and `"$@"`?
6. What failure did you test before calling the lab complete?

## Submission Checklist

- [ ] `server-greeting.sh`
- [ ] `file-inspector.sh`
- [ ] Completed test tables
- [ ] Week 2 reflection
- [ ] Demonstrated a filename containing spaces
- [ ] Explained every variable expansion

