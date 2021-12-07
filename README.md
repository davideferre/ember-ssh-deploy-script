# ember-ssh-deploy-script
Deploy bash script for ember applications using an SSH connection to a remote server.

## Configurations
You need to specify the SSH connection parameters inside the `.env.deploy.example` file and put this script into an [Ember.js](https://emberjs.com/) application root folder.

## Running
This script has **4 actions**: `deploy`, `activate`, `list` and `remove`.

### Available commands
- `./deploy.sh deploy`: this command runs the `ember build --environment production` command, creates a tar.gz file of the resulting dist folder after the build has finished, copies it to the ssh destination folder, extracts it to the `ssh_dest_folder/releases/app_version+app_commit` and cleanup the remote and the local folders
- `./deploy.sh activate APP_VERSION+APP_COMMIT`: Removes previously created symbolic links and creates a new symbolic link from the deployed folder and the `ssh_dest_folder/current` link. You can point this symbolic link inside your webserver exposed folder config
- `./deploy.sh list`: shows a list of all the deployed folder and the current symbolic link value
- `./deploy.sh remove APP_VERSION+APP_COMMIT`: Removes a deployed folder if this one is not the current released version
