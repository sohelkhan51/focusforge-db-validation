# Observations

## Issues Found

The following invalid data cases were tested using `constraints_test.sql`:

- Tasks with NULL titles were rejected.
- Duplicate user email addresses were rejected.
- Invalid task priorities outside the range of 1 to 5 were rejected.
- Tasks referencing non-existent projects were rejected.

## Constraints Implemented

The following database constraints were implemented:

- **PRIMARY KEY:** Ensures each user, project, and task has a unique ID.
- **NOT NULL:** Ensures users have names and email addresses, projects have project names, and tasks have titles.
- **UNIQUE:** Ensures each user's email address is unique.
- **CHECK:** Ensures task priority is between 1 and 5.
- **FOREIGN KEY:** Ensures every task references an existing project.

## Result

All four invalid-data tests produced the expected PostgreSQL errors:

1. NOT NULL violation for a task with a NULL title.
2. UNIQUE violation for a duplicate user email.
3. CHECK violation for a task priority outside the allowed range.
4. FOREIGN KEY violation for a non-existent project.

The database successfully prevented invalid data from being inserted.

These database-level constraints help maintain data accuracy, consistency, and integrity.