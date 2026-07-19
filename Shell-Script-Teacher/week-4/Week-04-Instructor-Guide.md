# Week 4 Instructor Guide: Loops and Batch Processing

## Position in the Curriculum

Week 3 taught scripts to select one branch. Week 4 repeats that decision process across many items. Students learn that a reliable loop needs a source of items, a continuation condition, safe per-item logic, visible progress, and a guaranteed stopping rule.

## Learning Outcomes

By the end of Week 4, students can:

- explain the lifecycle **initialize → test → process → update → repeat/stop**;
- use `for item in "$@"` to preserve argument boundaries;
- use C-style `for ((...))` for numeric sequences;
- use `while` when repetition depends on a condition or incoming data;
- use `until` when repetition continues until success;
- initialize and increment counters with Bash arithmetic;
- use `continue` to skip the rest of the current iteration;
- use `break` to leave the nearest loop intentionally;
- avoid unsafe `for item in $(command)` parsing;
- test zero-item, one-item, many-item, skipped-item, and stopped-early paths.

## Instructor Preparation

- Use Bash for all demonstrations.
- Make the scripts in `demo-scripts/` executable.
- Prepare files whose names contain spaces and one missing path.
- Explain every loop using the same lifecycle before discussing syntax.
- Keep a maximum-attempt guard in interactive or polling examples.

---

# Lesson 7 — `for` Loops and Counters

**Duration:** 90 minutes  
**Essential question:** How can a script safely repeat one action across a known set of items?

| Time | Teaching move | Evidence of learning |
|---:|---|---|
| 0–10 min | Retrieve Week 3 decision logic | Students identify the per-item validation branch |
| 10–25 min | Model loop lifecycle | Students label initialize, test, process, and update |
| 25–40 min | Demonstrate `for item in "$@"` | Students preserve an argument containing spaces |
| 40–52 min | Compare list and C-style `for` loops | Students choose the clearer form for two scenarios |
| 52–65 min | Add total, success, and failure counters | Students predict counter values |
| 65–82 min | Lab 1: Argument Batch Reporter | Students produce processing-summary evidence |
| 82–90 min | Exit ticket | Students repair an unsafe loop |

## Core Patterns

### Known collection

```bash
for item in "$@"; do
    printf 'Item: %s\n' "$item"
done
```

Quoted `"$@"` expands to one loop item per original argument. Unquoted `$@` can split values and expand wildcards.

### Numeric sequence

```bash
for ((number = 1; number <= 5; number++)); do
    printf '%s\n' "$number"
done
```

### Counters

```bash
total=0
success=0
failed=0

((total++))
```

When `set -e` is introduced later, prefer `((total += 1))`, because the status of `((total++))` can be nonzero when the old value is zero.

## Unsafe Pattern to Challenge

```bash
for file in $(find . -type f); do
    printf '%s\n' "$file"
done
```

Command substitution is split into words, so filenames containing whitespace are damaged. For beginner-safe directory iteration, use a glob such as `for file in ./*`; for robust recursive work, later introduce null-delimited `find` output with `read -d ''`.

## Guided Demonstration

Use `demo-scripts/argument-batch-reporter.sh`. Test zero arguments, one argument, and multiple arguments including `"server report.txt"`.

---

# Lesson 8 — `while`, `until`, `break`, and `continue`

**Duration:** 90 minutes  
**Essential question:** How can a loop skip, retry, or stop without becoming infinite?

| Time | Teaching move | Evidence of learning |
|---:|---|---|
| 0–10 min | Review known collections and counters | Students trace three iterations |
| 10–25 min | Build a condition-controlled `while` loop | Students identify the required update |
| 25–37 min | Contrast `while` and `until` | Students rewrite one form as the other |
| 37–50 min | Demonstrate `continue` | Students show which statements are skipped |
| 50–62 min | Demonstrate `break` and nearest-loop behavior | Students predict the final counter |
| 62–82 min | Lab 2: Safe Batch File Processor | Students test skip and stop paths |
| 82–90 min | Milestone defense | Students explain termination and final status |

## Structure Guide

| Need | Preferred structure |
|---|---|
| Process a known list | `for` |
| Repeat while a condition succeeds | `while` |
| Repeat until a condition succeeds | `until` |
| Skip one bad item, keep batch running | `continue` |
| Stop the batch after a defined condition | `break` |

## `while` Input Pattern

```bash
while IFS= read -r line; do
    printf 'Line: %s\n' "$line"
done < "$input_file"
```

`IFS=` preserves leading and trailing whitespace; `-r` preserves backslashes; redirection keeps the loop in the current shell so counters remain available afterward.

## Guided Demonstration

Use `demo-scripts/retry-until-success.sh`.

- Initialize `attempt=1` and set a maximum.
- Repeat until a file exists or the attempt limit is reached.
- Use `break` on success.
- Update the attempt counter every unsuccessful iteration.
- Avoid long delays in class; accept an optional delay that defaults to zero.

## Common Misconceptions

- “`continue` ends the loop.” It starts the next iteration.
- “`break` exits the script.” It exits the nearest loop; following commands still run.
- “A `while` condition updates itself.” The loop body must change relevant state unless an external event does.
- “Counters automatically start at zero.” Initialize them explicitly.
- “More loops mean more automation.” A loop without termination and evidence is a reliability risk.

---

# Labs and Milestone

## Lab 1 — Argument Batch Reporter

Process quoted positional arguments, number each item, classify empty/nonempty values, and print total/processed/skipped counters.

## Lab 2 — Safe Batch File Processor

Accept paths after an optional `--stop-on-error` flag. For each path:

- increment total;
- report and count missing paths;
- `continue` after recoverable missing-path errors;
- count regular files and directories;
- `break` on the first error when stop mode is enabled;
- print a final summary.

## Milestone M4 Rubric

| Criterion | Points |
|---|---:|
| Chooses an appropriate loop and safe item source | 4 |
| Quotes every item expansion | 3 |
| Initializes and updates accurate counters | 4 |
| Uses `continue` for a documented recoverable condition | 3 |
| Uses `break` for a documented stop condition | 3 |
| Guarantees termination | 3 |
| Prints an accurate summary and returns meaningful status | 3 |
| Tests zero, one, many, skip, and stop paths | 2 |
| **Total** | **25** |

## Readiness for Week 5

Students are ready when they can trace every iteration, prove the stopping condition, and reconcile the final counters with the input set.

## Adaptation Notes

- **Short class:** demonstrate Lab 1 and assign Lab 2.
- **Beginner class:** supply the counter initialization and summary block.
- **Advanced class:** add null-delimited recursive input, traps, or parallelism discussion.
- **No filesystem access:** iterate over service names or simulated status values.

