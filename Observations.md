# Observations

## Issues Found

The following invalid data cases were tested using `invalid_data.sql`:

- Tasks with NULL titles were rejected.
- Duplicate user email addresses were rejected.
- Invalid task priorities outside the range of 1 to 5 were rejected.
- Tasks referencing non-existent projects were rejected.

## Constraints Implemented

The following database constraints were implemented:

- **NOT NULL:** Ensures that every task has a title.
- **UNIQUE:** Ensures that each user's email address is unique.
- **CHECK:** Ensures that task priority is between 1 and 5.
- **FOREIGN KEY:** Ensures that every task references an existing project.

## Result

All four validation tests produced the expected PostgreSQL errors. The database successfully prevented NULL task titles, duplicate email addresses, invalid priorities, and references to non-existent projects.

These database-level constraints help maintain data accuracy, consistency, and integrity, even when invalid data is submitted.