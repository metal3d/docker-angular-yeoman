# Dockerized boilerplate using yeoman and angular

To be able to use angular with yeoman, we need to install node, yeoman and some dependencies. This docker image has the defaults.

# Usage

The default working directory is "/project", exposed port are 9000 (http service) and "35729" for livereload websocket.

The default command is "grunt serve".

**Important:** you need to set "user" option (working with docker-compose also) to be able to read/write sources.

To startup:

```bash

mkdir ~/myapp
cd ~/myapp
docker run -it --rm            \
    --user="$(id -u):$(id -g)" \
    -v $(pwd):/project         \
    metal3d/angular-yeoman yo angular app
```

Answer questions and let "yeoman" prepare the project. **Do not say yes to use gulp**, I will manage it later, at this time please keep grunt as default.

To serve:

```bash
cd ~/myapp
docker run -it --rm -v $(pwd):/project \
    --user="$(id -u):$(id -g)"         \
    metal3d/angular-yeoman
```

To create controller, directives, and so on, simply call "yo" command, eg. To create MyCtrl controller:

```bash

cd ~/myapp
docker run -it --rm -v $(pwd):/project/app \
    --user="$(id -u):$(id -g)"             \
    metal3d/angular-yeoman yo angular:controller MyCtrl
```
