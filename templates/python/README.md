# Python Applications

## Install procedure

1. Create a `Python/uWSGI` application via the Control Panel
   ([Opalstack doc](https://help.opalstack.com/article/60/pythonuwsgi-applications#installing-a-pythonuwsgi-application)).
2. Execute `app-template-py APP_NAME [PY_VERSION]` ([doc](../../README.md#app-template-py)).
3. Copy your application files in the `app` directory.
4. Modify `uwsgi.ini` if/as needed.
5. Start the application: `app-control APP_NAME start`.


## Controlling your application

See [`app-control`](../../README.md#app-control).


## Directory structure

- `app`: Your application.
  - `config`
    - `wsgi.py`: WSGI config for your application (used in `/uwsgi.ini`, cf. below).
- `venv`: Python 3 virtual environment ([Python doc](https://docs.python.org/3/library/venv.html))
- `tmp`: Temporary files used by your application
  - `uwsgi.pid`: PID file
- `opalstack-requirements.txt`: pip requirements related to the Opalstack app.
- `uwsgi.ini`: uWSGI configuration ([uWSGI doc](https://uwsgi-docs.readthedocs.io/)).


## Opalstack documentation

- [Python/uWSGI Applications](https://help.opalstack.com/article/60/pythonuwsgi-applications)
- [Django Applications](https://help.opalstack.com/article/61/installing-django)
