# Opalstack Utils

## Shell scripts

### app-control

Allow to control the operation of Python apps.

**Usage:** `app-control APP_NAME ACTION`

**Commands:**

- `kill`: Kill the application if it has hung.
- `restart`: Restart the application (executing stop then start).
- `start`: Start the application.
- `status`: Status the application (values: `running`, `stopped`, `crashed`).
- `stop`: Stop the application.


### app-template-py

**Usage:** `app-template-py APP_NAME`

See [template documentation](templates/python).


## Application templates

- [Python](templates/python)
