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

Convert an Opalstack Python app (Python/uWsgi or Django) using our app template.

**Usage:** `app-template-py APP_NAME`

See [template documentation](templates/python).


### install-py

Install a version of Python (in `$HOME/opt`).

**Usage:** `install-py VERSION [--force]`

If the script is executed without argument, it lists all the currently available versions found in
`$PATH` and `$HOME/opt/bin`.

If a `X.Y` version is already installed, the requested version will be installed only if `--force`
is specified.

See [Opalstack documentation](https://community.opalstack.com/d/204-howto-install-a-newer-or-older-version-of-python)


## Application templates

- [Python](templates/python)
