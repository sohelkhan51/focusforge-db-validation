# FocusForge Database Integrity Challenge

## Overview

FocusForge is a productivity application that manages users, projects, and tasks.

The goal of this challenge was to identify database integrity problems and implement SQL constraints to prevent invalid data from being inserted.

## Database Tables

The database contains three tables:

- **users:** Stores user information.
- **projects:** Stores project information.
- **tasks:** Stores task information and project references.

## Constraints Implemented

The following constraints were added to `schema/schema.sql`:

| Constraint | Table and Column | Purpose |
|---|---|---|
| PRIMARY KEY | All tables: `id` | Ensures every record has a unique identifier. |
| NOT NULL | `users.name` | Requires a user name. |
| NOT NULL | `users.email` | Requires an email address. |
| UNIQUE | `users.email` | Prevents duplicate email addresses. |
| NOT NULL | `projects.project_name` | Requires a project name. |
| NOT NULL | `tasks.title` | Prevents tasks without titles. |
| CHECK | `tasks.priority` | Restricts priority values to 1 through 5. |
| FOREIGN KEY | `tasks.project_id` | Ensures each task references an existing project. |

## Project Structure

```text
DB Level Validation/
├── README.md
├── Observations.md
├── schema/
│   ├── schema.sql
│   ├── sample_data.sql
│   └── invalid_data.sql
└── screenshots/
    ├── 01-not-null.png
    ├── 02-unique.png
    ├── 03-check.png
    └── 04-foreign-key.png
```

## How to Run the Project

1. Open PostgreSQL.
2. Connect to the `focusforge_db` database.
3. Run the schema file:

```sql
\i 'schema/schema.sql'
```

4. Insert the sample data:

```sql
\i 'schema/sample_data.sql'
```

5. Test invalid data:

```sql
\i 'schema/invalid_data.sql'
```

The invalid data script should produce constraint violation errors.

## Validation Results

All four invalid data tests were successfully rejected by PostgreSQL:

1. **NOT NULL:** Rejected a task with a NULL title.
2. **UNIQUE:** Rejected a duplicate user email.
3. **CHECK:** Rejected a task with priority 10.
4. **FOREIGN KEY:** Rejected a task referencing a non-existent project.

## Screenshots

The `screenshots/` folder contains evidence of all four database validation errors.

## Observations

See [Observations.md](Observations.md) for details about the problems found, constraints implemented, and final results.

## Conclusion

The database now uses constraints to protect data integrity and prevent invalid records from being inserted.

This challenge demonstrated how database-level validation helps maintain accurate, consistent, and reliable data.