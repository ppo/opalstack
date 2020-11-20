# Opalstack Utils

## Shell scripts

### [app-control](bin/app-control)

Control the operation of Python applications.

**Usage:** `app-control APP_NAME ACTION`

**Actions:**

- `cron`: Cron job tasks for the application.
- `kill`: Kill the application (in case it has hung).
- `restart`: Gracefully restart the application (uWSGI reload).
- `start`: Start the application.
- `status`: Status of the application (values: `running`, `stopped`, `crashed`).
- `stop`: Stop the application.


### [app-template-py](bin/app-template-py)

Convert a Python application created via the Control Panel using our app template.

**Usage:** `app-template-py APP_NAME [PY_VERSION]`

The Python application can be `Python/uWSGI` or `Django`.

`PY_VERSION` is used to create the virtual environment.  
If `PY_VERSION` is not available, `py-install-version` is used to install it.

See [template documentation](templates/python).


### [py-install-version](bin/py-install-version)

Install a version of Python (in `$HOME/opt`).

**Usage:** `py-install-version VERSION [--force]`

If a `major.minor` version is already installed, the requested version will be installed only if
`--force` is specified.

See [Opalstack documentation](https://community.opalstack.com/d/204-howto-install-a-newer-or-older-version-of-python)


### [py-versions](bin/py-versions)

List available Python versions (in `$PATH` and `$HOME/opt/bin`).

**Usage:** `py-versions [MODE]`

**Modes:**

- Default: Table of real versions and executables.
- `exec`: List all executables.
- `latest`: Latest version available.
- `latest-exec`: Executable of latest version available.
- `raw`: List all real versions.
- `xy`: List "major.minor" version of all executables.


## Application templates

- [Python](templates/python)
