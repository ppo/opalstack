# Opalstack Utils

## Shell scripts

### [app-control](bin/app-control)

Allow to control the operation of Python apps.

**Usage:** `app-control APP_NAME ACTION`

**Commands:**

- `kill`: Kill the application if it has hung.
- `restart`: Restart the application (executing stop then start).
- `start`: Start the application.
- `status`: Status of the application (values: `running`, `stopped`, `crashed`).
- `stop`: Stop the application.


### [app-template-py](bin/app-template-py)

Convert an Opalstack Python app (Python/uWsgi or Django) using our app template.

**Usage:** `app-template-py APP_NAME`

See [template documentation](templates/python).


### [py-install-version](bin/py-install-version)

Install a version of Python (in `$HOME/opt`).

**Usage:** `py-install-version VERSION [--force]`

If a `X.Y` version is already installed, the requested version will be installed only if `--force`
is specified.

See [Opalstack documentation](https://community.opalstack.com/d/204-howto-install-a-newer-or-older-version-of-python)


### [py-versions](bin/py-versions)

List available Python versions (in `$PATH` and `$HOME/opt/bin`).

**Usage:** `py-versions [mode]`

**Modes:**

- `default`: Table of real versions and executables.
- `exec`: List all executables.
- `latest`: Latest version available.
- `latest-exec`: Executable of latest version available.
- `raw`: List all real versions.
- `xy`: List "major.minor" version of all executables.


## Application templates

- [Python](templates/python)
