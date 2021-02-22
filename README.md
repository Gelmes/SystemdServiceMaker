# Systemd Service Maker
Sometimes it necessary to run an application from start. If you come from the world of raspberry pi you will run into several different methods on how to run scripts on startup. This methods are going to include but not limited to using `crontab`, `init.d`, `rc.local`.

While all these methods might have their place almost always I just want my application to run after the system is booted and to have some sort of logs. This is where `systemd` comes in.

With `systemd` you can turn your application into a service and even look at logs.

## Install

To check if you have `systemd` installed run:

```
systemctl
```

This will ether give you an error if the command does not exist or list out the status of the system services.

If you have `systemd` you can install then install this application

```
sudo sh install.sh
```

## How to use
```
Usage: servicemaker [OPTION]...
Automatically create and start a systemd unit file from a template.

    -m, --name          Service name
    -a, --application   Application location
    -d, --description   Description of application
    -w, --directory     Working Directory of application (no spaces!)
    -r, --restart       Restart interval in seconds (default: 10)
    -u, --user          User execution level (default: root!)
```

Example:
```
sudo servicemaker -n destroyer -a "/home/destroyer.sh" -d "Builds empty worlds" -w "/home/root" -r 1 -u "$USER"
```
## Good to know commands

Some commands you will want to get familiar with once you run the `SystemdServiceMaker`

```
systemctl status yourservice.service  # Shows the status of your service
systemctl enable yourservice.service  # Enables your service
systemctl disable yourservice.serivce # Disables your service
systemctl start yourservice.service   # Starts your service
systemctl stop yourservice.service    # Stops your service

journalctl -u yourservice    # Shows logs
journalctl -u yourservice -f # Automatically fallows logs
```

## Issues

### Spaces
There is a bug in `systemd` unit files where the working directory cannot have spaces. If you need to have spaces in your working directory create a soft link and pass it as the working directory.

```
ln -s Target Link-Name
```

### Execute permissiions
If you have any issues make sure you have no spaces in the arguments you pass and that the executable you are trying to run has execute permission enabled with `chmod +x you-app`
