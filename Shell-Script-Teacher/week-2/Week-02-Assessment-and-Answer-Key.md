# Bash Scripting Week 2 Assessment and Answer Key

**Total:** 25 points  
**Suggested time:** 25 minutes written + 20 minutes practical

---

# Student Assessment

## Part A - Multiple Choice - 8 points

### 1. Which assignment is valid?

A. `name = "Ali"`  
B. `name="Ali"`  
C. `$name="Ali"`  
D. `set name = Ali`

### 2. What does `"$name"` normally do?

A. Prints literal `$name`  
B. Expands the value while preserving it as one argument  
C. Deletes spaces  
D. Runs `name` as a command

### 3. What does `'$name'` produce?

A. The variable value  
B. Literal text `$name`  
C. The script name  
D. An exit status

### 4. Why use `${name}_report.txt`?

A. It makes the variable global  
B. It clearly separates the variable name from following text  
C. It disables expansion  
D. It creates the file

### 5. What does `today="$(date +%F)"` do?

A. Stores the command text  
B. Stores the command's standard output  
C. Runs `today`  
D. Creates an environment variable automatically

### 6. What does `$#` contain?

A. The script name  
B. The number of positional arguments  
C. All arguments  
D. The previous exit status

### 7. What does `$1` contain?

A. The first command-line argument  
B. All command-line arguments  
C. The current user  
D. Standard input

### 8. Which form safely preserves all arguments?

A. `$@`  
B. `"$@"`  
C. `$*`  
D. `'${@}'`

## Part B - Short Answer - 7 points

### 9. Explain single quotes versus double quotes.

### 10. Why should a path variable normally be written as `"$path"`?

### 11. Write an argument-count check that requires exactly one argument.

### 12. Write a usage message using `$0` and send it to standard error.

## Part C - Practical Checkpoint - 10 points

Create `week2-checkpoint.sh` that:

1. Requires one name argument.
2. Displays usage and exits `2` when the argument count is wrong.
3. Stores `$1` in `student_name`.
4. Preserves a name containing spaces.
5. Captures current username with command substitution.
6. Captures hostname with command substitution.
7. Displays the student name, Linux username, and hostname.
8. Uses braces in one expansion.
9. Returns `0` on success.
10. Is explained line by line.

---

# Instructor Answer Key

## Part A

| Question | Answer | Explanation |
|---:|:---:|---|
| 1 | B | Assignment syntax has no spaces around `=`. |
| 2 | B | Double quotes allow expansion and prevent splitting/globbing. |
| 3 | B | Single quotes preserve literal text. |
| 4 | B | Braces define the variable-name boundary. |
| 5 | B | Command substitution captures standard output. |
| 6 | B | `$#` is the argument count. |
| 7 | A | `$1` is the first positional argument. |
| 8 | B | `"$@"` preserves every argument separately. |

## Part B Suggested Answers

### 9.

Single quotes preserve literal text and prevent parameter and command substitution. Double quotes allow expansion while protecting the result from word splitting and pathname expansion.

### 10.

Double quoting preserves spaces and wildcard characters as part of one path value instead of allowing Bash to split or expand them.

### 11.

```bash
if [[ $# -ne 1 ]]; then
    exit 2
fi
```

### 12.

```bash
printf 'Usage: %s <name>\n' "$0" >&2
```

## Practical Rubric

| Criterion | Points |
|---|---:|
| Argument validation and usage | 2 |
| Correct variable assignment | 1 |
| Quoting preserves spaces | 2 |
| Command substitution | 2 |
| Clear formatted output | 1 |
| Correct exit status | 1 |
| Line-by-line explanation | 1 |
| **Total** | **10** |

## Milestone Decision

Award **M2 - Input Handler** when the student earns at least 18/25 overall, passes the name-with-spaces test, and explains the purpose of quoting and argument validation.

