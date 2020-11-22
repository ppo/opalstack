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
- `uwsgi.ini`: uWSGI configuration ([uWSGI options](https://uwsgi-docs.readthedocs.io/en/latest/Options.html)).


## Django

To create a Django application, you can start with the following…  
_(replace `APP_NAME`, `MY_PROJECT`, and `your-domain.com` with your values)_

```bash
cd $HOME/apps/APP_NAME/

. venv/bin/activate
pip install django

cd tmp
django-admin startproject MY_PROJECT
mv MY_PROJECT/* ../app/
rmdir MY_PROJECT

cd ..
sed -i "s/ALLOWED_HOSTS = \[\]/ALLOWED_HOSTS = ['your-domain.com']/" app/MY_PROJECT/settings.py
sed -i "/DATABASES =/, /^}/ s/^/# /" app/MY_PROJECT/settings.py
sed -i "s#config/wsgi.\py#MY_PROJECT/wsgi.py#g" uwsgi.ini

app-control APP_NAME restart

# Fine-tuning ;-)
cd venv/bin/
rm django-admin.py
ln -s ../../app/manage.py
cd ../..
```

And you should see the default "The install worked successfully! Congratulations!" page on http://your-domain.com/


## Opalstack documentation

- [Python/uWSGI Applications](https://help.opalstack.com/article/60/pythonuwsgi-applications)
- [Django Applications](https://help.opalstack.com/article/61/installing-django)
