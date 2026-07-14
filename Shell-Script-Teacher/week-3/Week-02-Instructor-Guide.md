# Week 2 Instructor Guide - Variables, Input, and Arguments

## Course Position

Week 1 taught students how Bash executes a script. Week 2 teaches how data enters, moves through, and leaves a script.

```text
Input -> Validate -> Store -> Process -> Display
```

The central safety message is simple:

> Input becomes reliable only after it is validated and quoted correctly.

## Instructor Preparation

- Confirm students completed Milestone M1.
- Create `~/bash-course/week-02`.
- Prepare one file whose name contains spaces.
- Test all four demonstration scripts.
- Prepare examples of empty input and missing arguments.
- Keep the Week 2 lab and assessment files available locally.

---

# Lesson 3 - Variables, Quoting, and Command Substitution

**Duration:** 90 minutes  
**Slides:** 1-7  
**Primary objective:** Students store and expand values without losing spaces or changing meaning.

## Success Criteria

Students can:

- Assign a variable without spaces around `=`.
- Read a variable with `$name` and `${name}`.
- Distinguish single and double quotes.
- Explain why unquoted expansion is risky.
- Capture command output with `$(command)`.
- Build an interactive server greeting.

## Lesson Sequence

| Time | Activity | Evidence |
|---:|---|---|
| 0-10 min | Week 1 retrieval: structure and execution | Student explanation |
| 10-24 min | Variable assignment and expansion | Correct predictions |
| 24-40 min | Quoting comparison | Three-output comparison |
| 40-52 min | Command substitution | Captured command output |
| 52-65 min | Demonstration: variable and quoting script | Observed output |
| 65-78 min | Demonstration: interactive greeting | Validated input |
| 78-87 min | Student Lab 1 | Working greeting script |
| 87-90 min | Exit Ticket A | Individual answers |

## Teaching Notes

### Variable assignment

Correct:

```bash
course_name="Bash Scripting"
```

Incorrect:

```bash
course_name = "Bash Scripting"
```

Bash treats whitespace as a separator, so the incorrect form attempts to run `course_name` as a command.

### Expansion

```bash
name="Khalid"
printf 'Hello, %s\n' "$name"
printf 'File: %s\n' "${name}_report.txt"
```

Use braces when the variable boundary could be unclear.

### Quoting model

| Form | Expansion? | Word splitting/globbing risk? | Example |
|---|---|---|---|
| Unquoted | Yes | Yes | `$name` |
| Double quoted | Yes | Protected | `"$name"` |
| Single quoted | No | Literal text | `'$name'` |

Demonstrate with:

```bash
message="Linux Admin Class"
printf '<%s>\n' $message
printf '<%s>\n' "$message"
printf '%s\n' '$message'
```

### Command substitution

```bash
current_user="$(whoami)"
today="$(date +%F)"
kernel="$(uname -r)"
```

Explain that Bash runs the inner command first and substitutes its standard output.

Prefer `$(command)` over legacy backticks because it is clearer and easier to nest.

## Demonstration 1 - Variables and Quoting

Run:

```bash
bash demo-scripts/variable-quoting-demo.sh
```

Before each section, ask students to predict:

- Whether the variable expands
- Whether spaces remain one argument
- Whether the output is literal

## Demonstration 2 - Interactive Server Greeting

Run:

```bash
bash demo-scripts/interactive-server-greeting.sh
```

Test:

- A normal name
- A name containing spaces
- Empty input

Emphasize `read -r`, validation, and quoting.

## Common Errors

| Error | Cause | Intervention |
|---|---|---|
| `command not found` after assignment | Spaces around `=` | Compare tokenization of correct and incorrect forms |
| Text splits into several pieces | Unquoted variable | Repeat with `"$variable"` |
| `$name` prints literally | Single quotes | Compare single and double quotes |
| Variable name absorbs following text | Missing braces | Use `${name}_report` |
| Backslashes disappear during input | `read` without `-r` | Use `read -r` |

## Exit Ticket A

1. Why are spaces not allowed around `=` in a Bash assignment?
2. What is the difference between `'$name'` and `"$name"`?
3. Why is `"${name}_report"` clearer than `"$name_report"`?

---

# Lesson 4 - User Input and Positional Arguments

**Duration:** 90 minutes  
**Slides:** 8-12  
**Primary objective:** Students accept, validate, and preserve input from users and command-line arguments.

## Success Criteria

Students can:

- Read interactive input with `read -r`.
- Reject empty required input.
- Explain positional parameters.
- Use `"$@"` to preserve all arguments.
- Check argument count with `$#`.
- Display a usage message.
- Safely inspect a path containing spaces.

## Lesson Sequence

| Time | Activity | Evidence |
|---:|---|---|
| 0-10 min | Quoting retrieval | Correct output predictions |
| 10-25 min | Interactive input and validation | Empty-input handling |
| 25-40 min | Positional parameters | Argument map |
| 40-52 min | Usage and argument count | Failure-path test |
| 52-62 min | Demonstration: argument script | Preserved arguments |
| 62-75 min | Demonstration: file inspector | Path-with-spaces test |
| 75-85 min | Student Lab 2 | Working file inspector |
| 85-90 min | Milestone checkpoint | Independent explanation |

## Interactive Input

```bash
read -r -p "Enter your name: " student_name

if [[ -z "$student_name" ]]; then
    printf '%s\n' "Name is required" >&2
    exit 1
fi
```

`-r` prevents backslash interpretation. Quoting preserves the full input as one value.

## Positional Parameters

| Parameter | Meaning |
|---|---|
| `$0` | Script name or invocation path |
| `$1` | First argument |
| `$2` | Second argument |
| `$#` | Number of arguments |
| `"$@"` | All arguments, each preserved separately |

Use this command:

```bash
./argument-demo.sh "Linux Admin" WSL AWS
```

Ask students to identify each resulting parameter.

## Usage Pattern

```bash
if [[ $# -ne 1 ]]; then
    printf 'Usage: %s <path>\n' "$0" >&2
    exit 2
fi
```

Explain that a usage error is different from a missing-file error. Meaningful exit codes help users and automation understand the failure.

## Demonstration 3 - Arguments

Run:

```bash
bash demo-scripts/argument-demo.sh "Linux Admin" WSL AWS
```

Then compare:

```bash
for item in $@; do printf '<%s>\n' "$item"; done
for item in "$@"; do printf '<%s>\n' "$item"; done
```

Use the comparison only for demonstration. Keep `"$@"` as the correct pattern.

## Demonstration 4 - File Inspector

Prepare:

```bash
touch "server report.txt"
```

Test:

```bash
bash demo-scripts/file-inspector.sh "server report.txt"
bash demo-scripts/file-inspector.sh missing.txt
bash demo-scripts/file-inspector.sh
```

## Common Errors

| Error | Isolation question |
|---|---|
| Empty input accepted | Was `-z` checked? |
| Filename with spaces fails | Was `"$1"` quoted every time? |
| Script crashes without arguments | Was `$#` checked before using `$1`? |
| All arguments become one string | Was `"$@"` confused with `"$*"`? |
| Usage appears on normal output | Should guidance/error text go to standard error? |

## Exit Ticket B

1. What does `$#` contain?
2. Why should `"$@"` normally be quoted?
3. What should a script do before using required `$1`?

---

# Milestone M2 - Input Handler

Award M2 when the student independently:

1. Accepts a required path argument.
2. Checks the argument count.
3. Displays usage on incorrect invocation.
4. Quotes the path every time it is used.
5. Handles paths containing spaces.
6. Distinguishes a missing path from a usage error.
7. Returns a meaningful nonzero exit status.
8. Explains every expansion.

## Instructor Recording Grid

| Student | Variables | Quoting | Input | Arguments | Validation | Explanation | M2? |
|---|---|---|---|---|---|---|---|
| | | | | | | | |
| | | | | | | | |
| | | | | | | | |

## Differentiation

### Additional support

- Provide an argument map for `$0`, `$1`, and `$#`.
- Give students a filename containing spaces.
- Use prediction tables before execution.
- Provide a partial usage function.

### Advanced extension

- Add a default value with `${variable:-default}`.
- Accept multiple paths with `"$@"`.
- Add `-h` and `--help` handling.
- Distinguish file, directory, and symbolic link.

