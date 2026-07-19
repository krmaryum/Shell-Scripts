# Week 4 Assessment: Loops and Batch Processing

**Total: 25 points**

## Part A — Multiple Choice (5 points)

1. Which loop is usually clearest for processing all positional arguments?  
   A. `until`  B. `for item in "$@"`  C. infinite `while`  D. `case`

2. What does `continue` do?  
   A. exits the script  B. exits the loop  C. starts the next iteration  D. repeats the current command

3. What does `break` do by default?  
   A. exits the nearest loop  B. skips one command  C. returns status 2  D. restarts the loop

4. Which form safely reads a text file line by line?  
   A. `for line in $(cat file)`  B. `while IFS= read -r line`  C. `case file`  D. `until cat file`

5. What is the most common cause of an accidental infinite counter loop?  
   A. quoted output  B. missing state update  C. using stderr  D. initializing the counter

## Part B — Short Answer (8 points)

6. Explain why `for file in $(find . -type f)` is unsafe for filenames containing spaces. Give one safer nonrecursive alternative. (2 points)

7. Compare when to use `for`, `while`, and `until`. (2 points)

8. Explain the difference between `break` and `continue`. (2 points)

9. Find the termination bug and repair it. (2 points)

```bash
count=1
while (( count <= 5 )); do
    printf '%s\n' "$count"
done
```

## Part C — Code Reading (4 points)

10. State the printed numbers and final value of `processed`. (4 points)

```bash
processed=0
for number in 1 2 3 4 5; do
    if (( number == 2 )); then
        continue
    fi
    if (( number == 5 )); then
        break
    fi
    printf '%s\n' "$number"
    ((processed += 1))
done
printf 'processed=%s\n' "$processed"
```

## Part D — Practical (8 points)

Write `readable-file-counter.sh <path> [path ...]` that:

- exits `2` when no paths are supplied;
- iterates safely over all paths;
- counts total, readable regular files, and skipped paths;
- uses `continue` after a skipped path;
- stops with `break` when total reaches 10;
- prints a summary and exits `0`.

### Practical Rubric

| Criterion | Points |
|---|---:|
| usage validation | 1 |
| quoted safe loop | 2 |
| accurate counters | 2 |
| correct `continue` | 1 |
| correct limit and `break` | 1 |
| final summary and readable formatting | 1 |

---

# Answer Key

## Part A

1. B
2. C
3. A
4. B
5. B

## Part B

6. Command substitution undergoes word splitting, damaging whitespace-containing filenames. A safer nonrecursive form is:

```bash
for file in ./*; do
    [[ -f "$file" ]] || continue
    printf '%s\n' "$file"
done
```

7. Use `for` for a known collection or numeric sequence, `while` while a condition remains successful, and `until` until a condition becomes successful.

8. `continue` skips the remaining body and begins the next iteration. `break` leaves the nearest loop entirely.

9. The counter never changes:

```bash
count=1
while (( count <= 5 )); do
    printf '%s\n' "$count"
    ((count += 1))
done
```

## Part C

The script prints `1`, `3`, and `4`, then prints `processed=3`. Number `2` is skipped and `5` stops the loop before printing or incrementing.

## Part D — Reference Solution

```bash
#!/usr/bin/env bash

if [[ $# -eq 0 ]]; then
    printf 'Usage: %s <path> [path ...]\n' "$0" >&2
    exit 2
fi

total=0
readable=0
skipped=0

for path in "$@"; do
    ((total += 1))

    if [[ ! -f "$path" || ! -r "$path" ]]; then
        printf 'Skipped: %s\n' "$path" >&2
        ((skipped += 1))
        if (( total >= 10 )); then break; fi
        continue
    fi

    printf 'Readable file: %s\n' "$path"
    ((readable += 1))

    if (( total >= 10 )); then
        break
    fi
done

printf 'Total: %s\nReadable: %s\nSkipped: %s\n' \
    "$total" "$readable" "$skipped"
exit 0
```

