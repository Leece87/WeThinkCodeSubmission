TASK MANAGER - README

PROJECT OVERVIEW
Task Manager is a command-line application for creating, managing, and tracking tasks with support for priorities, due dates, tags, and status tracking. Designed for developers who need simple, efficient task organization.

KEY FEATURES
- Create tasks with title, description, and optional metadata
- Priority levels: LOW, MEDIUM, HIGH, URGENT
- Status tracking: TODO, IN_PROGRESS, REVIEW, DONE
- Due date management and overdue detection
- Tag system for task categorization
- Task filtering by status, priority, and tags
- Task statistics dashboard
- JSON persistent storage
- Full task details viewing

TECHNOLOGIES USED
- Python 3.x
- argparse (command-line interface)
- json (data persistence)
- datetime (date/time handling)
- uuid (unique task identification)

INSTALLATION

Prerequisites:
- Python 3.7 or higher
- pip package manager

Quick Start:
1. Navigate to project directory
2. Install dependencies:
   pip install -r requirements.txt
3. Run first command:
   python cli.py --help

PROJECT STRUCTURE
- cli.py: Command-line interface and user interactions
- task_manager.py: Core business logic and task operations
- models.py: Task, TaskPriority, TaskStatus classes
- storage.py: JSON file persistence and retrieval
- tasks.json: Persistent task storage
- tests/: Unit test suite
- README.txt: This file

BASIC USAGE

Create Task:
  python cli.py create "Task title" -d "Description" -p 2 -u 2024-12-31 -t "tag1,tag2"

List Tasks:
  python cli.py list                          # All tasks
  python cli.py list -s todo                  # Filter by status
  python cli.py list -p 3                     # Filter by priority (1-4)
  python cli.py list -o                       # Show overdue only

Update Task:
  python cli.py status <task_id> todo         # Change status
  python cli.py priority <task_id> 3          # Change priority (1-4)
  python cli.py due <task_id> 2024-12-31      # Set due date

Manage Tags:
  python cli.py tag <task_id> <tag_name>      # Add tag
  python cli.py untag <task_id> <tag_name>    # Remove tag

View Details:
  python cli.py show <task_id>                # Display full task details

Delete Task:
  python cli.py delete <task_id>

Statistics:
  python cli.py stats                         # Show task overview

CONFIGURATION

Date Format: Use YYYY-MM-DD for all date inputs
Priority Values: 1=LOW, 2=MEDIUM, 3=HIGH, 4=URGENT
Status Values: todo, in_progress, review, done
Storage Location: tasks.json in project root

FEATURES IN DETAIL

Task Metadata
Each task stores: ID (UUID), title, description, priority, status, creation timestamp, update timestamp, due date, completion timestamp, and tags.

Status Workflow
- TODO: Initial state for new tasks
- IN_PROGRESS: Task actively worked on
- REVIEW: Task waiting for review
- DONE: Completed task with timestamp

Priority System
- LOW (1): Non-urgent tasks
- MEDIUM (2): Standard priority (default)
- HIGH (3): Important tasks
- URGENT (4): Critical tasks

Overdue Detection
Automatically identifies incomplete tasks past their due date. Use "list -o" to view.

TROUBLESHOOTING

"Invalid date format" error:
- Ensure dates follow YYYY-MM-DD format
- Example: 2024-12-25 for December 25, 2024

Task ID not found:
- Use "list" command to view all task IDs (first 8 characters shown)
- Full UUID stored internally

File corruption or errors:
- Backup tasks.json
- Delete tasks.json to start fresh
- Data will regenerate on next save

Priority mismatch:
- Use integer values 1-4 only
- 1=LOW, 2=MEDIUM, 3=HIGH, 4=URGENT

CONTRIBUTING
Modify core business logic in task_manager.py. Add CLI commands in cli.py. Extend models for new features. Update tests/ suite with new test cases. Follow existing code structure and naming conventions.

LICENSE
This project is provided as-is for educational and development purposes.

SUPPORT
Test suite: python -m pytest tests/
Debug output: Check tasks.json formatting
Error messages: Review command syntax with --help flag
