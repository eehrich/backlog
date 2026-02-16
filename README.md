# Backlog Tool

A lightweight CLI tool for managing project backlogs in Markdown format. Keep your project tasks organized with epics, tasks, and status tracking - all in a simple, human-readable Markdown file.

This tool was created using Vibe-Coding and meant to be used by Agents/LLMs to track their work and ideas.

It's probably not 100% perfect, but it works well.


## Features

- 📝 **Markdown-based** - Your backlog is stored in a readable `backlog.md` file
- 🏗️ **Epic & Task hierarchy** - Organize tasks under epics
- ✅ **Status tracking** - Track progress with status symbols (☐ open, ✅ done, ⏳ in progress, ❌ failed)
- 📅 **Timestamps** - Automatic tracking of when tasks are added and closed
- 🔍 **Validation** - Ensure your backlog structure is correct
- 🔢 **Auto-ID management** - Automatic 4-digit ID assignment
- 📋 **List & Show** - View your backlog in various formats
- 💾 **Backup** - Create backups before making changes

## Installation

```bash
pip install -e .
```

Or install with development dependencies:

```bash
pip install -e ".[dev,test]"
```

## Quick Start

### Initialize a new backlog

```bash
backlog init
```

This creates a `backlog.md` file with the proper structure.

### Add a task

```bash
backlog add-task --title "Implement user authentication" --status open
```

### Add an epic with tasks

```bash
backlog add-epic --title "User Management System" --status "in progress"
```

### List all items

```bash
backlog list
```

### Show specific item

```bash
backlog show 0001
```

### Validate your backlog

```bash
backlog validate
```

## Backlog Structure

The backlog file follows this structure:

```markdown
# Backlog

## 1. Epics - open

- ☐ Epic 0001: User Management System
  - status: in progress
  - description:
    Complete system for user authentication and authorization
  - added: 2026-02-16
  - closed: —
  - tasks:
    - ☐ Task 0002: Implement login form
      - status: open
      - added: 2026-02-16
      - closed: —
    - ✅ Task 0003: Add password hashing
      - status: done
      - added: 2026-02-15
      - closed: 2026-02-16

## 2. Epics - finished

(Completed epics go here)

## 3. Ideas

(Ideas and proposals for future tasks)
```

## Status Options

- **open** (☐) - Task is not started
- **in progress** (⏳) - Task is currently being worked on
- **done** (✅) - Task is completed
- **failed** (❌) - Task failed or couldn't be completed
- **rejected** - Task was declined or not wanted
- **reverted** - Task was implemented but reverted
- **cancelled** - Task was stopped or superseded

## Commands

### Core Commands

- `backlog init` - Initialize a new backlog file
- `backlog add-task` - Add a new task
- `backlog add-epic` - Add a new epic with optional tasks
- `backlog list` - List all epics and tasks
- `backlog show <id>` - Show details of a specific item
- `backlog validate` - Validate backlog structure
- `backlog backup` - Create a backup of the backlog

### Update Commands

- `backlog update <id> --status <status>` - Update task status
- `backlog update <id> --title <title>` - Update task title
- `backlog update <id> --description <text>` - Update description
- `backlog add-note <id> <note>` - Add a note to a task

### Management Commands

- `backlog close <id>` - Close a task (sets status to done and adds close date)
- `backlog reassign-ids` - Renumber all IDs sequentially
- `backlog prune` - Remove finished epics

## Configuration

Create a `.backlogrc` file in your project root or home directory:

```ini
[backlog]
file = backlog.md
auto_backup = true
id_padding = 4
```

## Development

### Running Tests

```bash
# Install test dependencies
pip install -e ".[test]"

# Run all tests
pytest

# Run with coverage
pytest --cov=backlog_tool

# Run specific test file
pytest tests/backlog/test_backlog_parser.py
```

### Code Quality

```bash
# Install dev dependencies
pip install -e ".[dev]"

# Run linter
ruff check src/

# Run type checker
mypy src/
```

## Requirements

- Python >= 3.11
- No external runtime dependencies (only standard library!)
- Test dependencies: pytest, pytest-timeout, pytest-cov

## License

Apache License 2.0 - See [LICENSE](LICENSE) file for details.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## Author

Enrico Ehrich
