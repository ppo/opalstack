# Node Applications

## Directory Structure

- `app`: Main files of this application.
- `node`: The node version used by this application.
- `node_modules`: Packages installed via `packages.json`.
- `tmp`: Temporary files used by this application.
  - `node.pid`: PID file used by start/stop scripts.

- `.env`: Settings for your app and the management scripts.

- `install-node`: Install the given version of Node (in the `node` directory).
- `start`: Starts this application.
- `stop`: Stops this application.
- `restart`: Executes `stop` then `start`.

_**Note:** There's a crontab executing `start` every 10 minutes._


## Install Procedure

**1. Create a new application**

- Go to the [Opalstack Control Panel](https://my.opalstack.com/apps/).
- Click on "Add Application".
- Fill in the form, chosing `Node.js` as application type.


**2. Remove all files from Opalstack's template**

- Go to your app directory: `cd ~/apps/YOUR_APP_NAME`
- Write down the port number (for step 3): `cat app.js | grep "port ="`
- Disable the cron: `crontab -e`
  - Find the line containing `apps/YOUR_APP_NAME/start`.
  - Add a `#` at the beginning of the line.
  - Save and exit.
- Stop the application: `./stop`
- Delete all files: `rm -fr *`


**3. Clone this template**

_**Note:** `git sparse-checkout` requires Git ≥ 2.25, which is not available on Opalstack._

Execute the following on your computer (not on Opalstack).

- Clone this folder template from GitHub:

```bash
mkdir /tmp/opalstack-template && cd $_
git clone --no-checkout --depth=1 --filter=tree:0 https://github.com/ppo/opalstack/ .
git sparse-checkout set --no-cone templates/node
git checkout
cd templates/node
find . -name .gitkeep -delete
```

- Update the settings in the `.env` file:
    - Set the `PORT` variable using the value from step 2.
    - Update `APP_ENTRYPOINT` according to your needs.
- Copy the files to Opalstack: `rsync -au . YOUR_USER@YOUR_SERVER.opalstack.com:apps/YOUR_APP_NAME/`
- Cleanup these temporary files: `cd; rm -fr /tmp/opalstack-template`


**4. Upload your application files**

Execute the following on your computer (not on Opalstack).

```bash
rsync -au YOUR_APP_DIST/ YOUR_USER@YOUR_SERVER.opalstack.com:apps/YOUR_APP_NAME/app/
```


**5. Configure Opalstack & start your application**

Execute the following on Opalstack.

- Go to your app directory: `cd ~/apps/YOUR_APP_NAME`
- Create a symlink to the logs: `ln -s ~/logs/apps/YOUR_APP_NAME logs`
- Re-enable the cron: `crontab -e`
  - Find the line containing `apps/YOUR_APP_NAME/start`.
  - Remove the `#` at the beginning of the line.
  - Save and exit.
- Start this application: `./start`


## Opalstack Documentation

- [Nodes.js Applications](https://docs.opalstack.com/topic-guides/nodejs/)
