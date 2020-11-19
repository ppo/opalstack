# Python Applications

## Install procedure

1. Create a `Python/uWSGI` application as explained [here](https://help.opalstack.com/article/60/pythonuwsgi-applications#installing-a-pythonuwsgi-application).
2. Execute `app-template-py APP_NAME` (see [README](../../README.md)).
3. Copy your application files in the `app` directory.


## Controlling your application

`app-control APP_NAME ACTION`

See [README](../../README.md)


## Directory structure

- `app`: Your application.
  - `config`
    - `wsgi.py`: WSGI config for your application (used in `/uwsgi.ini`, cf. below).
- `env`: Python 3 virtual environment ([doc](https://docs.python.org/3/library/venv.html))
- `tmp`: Temporary files used by your application
  - `uwsgi.pid`: PID file
- `opalstack-requirements.txt`: pip requirements related to the Opalstack app.
- `uwsgi.ini`: Configuration for the Opalstack app.


## Opalstack documentation

- [Python/uWSGI Applications](https://help.opalstack.com/article/60/pythonuwsgi-applications)
- [Django Applications](https://help.opalstack.com/article/61/installing-django)
