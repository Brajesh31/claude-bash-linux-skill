# claude-bash-linux-skill

A Claude Code skill for using Bash and Linux command-line tools, writing shell scripts, and managing common system workflows.

## Overview

This skill focuses on practical shell usage across Linux and macOS environments. It covers command composition, file operations, text processing, pipelines, scripting, process management, permissions, and reliable error handling.

It is intended for both interactive terminal work and automation scripts.

## Core Topics

### Command Composition

- Sequential execution with `;`.
- Conditional execution with `&&` and `||`.
- Pipelines and redirection.
- Exit status and command substitution.
- Quoting and safe variable expansion.

### File and Text Operations

- Navigating and inspecting directories.
- Finding files and searching content.
- Filtering and transforming text.
- Working with archives and file metadata.
- Safe file creation, copying, moving, and deletion.

### Shell Scripting

- Variables and environment configuration.
- Arguments and option parsing.
- Functions and reusable logic.
- Conditional statements and loops.
- Exit codes and cleanup traps.
- Input validation and defensive scripting.

### Processes and Permissions

- Process inspection and signals.
- Background jobs and job control.
- File permissions and ownership.
- Environment variables and executable paths.
- Basic service and resource diagnostics.

## Installation

```bash
git clone https://github.com/Brajesh31/claude-bash-linux-skill.git ~/.claude/skills/bash-linux
```

## Usage

Invoke the skill for shell commands or Linux scripting tasks:

```text
/bash-linux
```

Describe the operating system, shell, target files, desired outcome, and whether commands should be safe to run repeatedly.

## Safe Command Workflow

1. Inspect the current directory and target files.
2. Understand the effect of each command before execution.
3. Quote paths and variables that may contain spaces.
4. Prefer explicit paths over ambiguous globs.
5. Preview destructive changes before applying them.
6. Check exit codes and command output.
7. Use traps or cleanup logic for temporary resources.
8. Verify the final filesystem or process state.

## Example Script

```bash
#!/usr/bin/env bash
set -Eeuo pipefail

target_dir="${1:?Usage: script.sh <directory>}"

if [[ ! -d "$target_dir" ]]; then
  printf 'Directory not found: %s\n' "$target_dir" >&2
  exit 1
fi

find "$target_dir" -type f -name '*.log' -print
```

This example validates its input and lists matching files without modifying them.

## Best Practices

- Use `#!/usr/bin/env bash` for portable Bash selection.
- Quote variable expansions unless word splitting is intentional.
- Prefer arrays for command arguments.
- Use `read -r` when reading raw input.
- Handle expected failures explicitly.
- Avoid parsing `ls` output.
- Use `find` or shell globs for file selection.
- Do not run privileged commands unless necessary.
- Keep destructive operations separate from inspection.

## Repository Contents

- `SKILL.md`: Main Bash and Linux instructions.
- `README.md`: Command-line concepts and workflow guidance.

## Validation Checklist

- Script handles missing arguments.
- Paths with spaces are supported.
- Expected failures return meaningful exit codes.
- Temporary files and processes are cleaned up.
- Destructive actions require clear scope.
- Script works in the intended shell version.
