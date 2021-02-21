# Systemd Service Maker
Sometimes it necessary to run an application from start. If you come from the world of raspberry pi you will run into several different methods on how to run scripts on startup. This methods are going to include but not limited to using `crontab`, `init.d`, `rc.local`.

While all these methods might have their place almost always I just want my application to run after the system is booted and to have some sort of logs. This is where `systemd` comes in.

With `systemd` you can turn your application into a service and even look at logs.

## Install
sudo sh install.sh

## How to use

sudo servicemaker [-n=name] [-a="app-executable-location"] [-d="description"] [-w=working-directory] [-r=reset-time] 

## Issues

If you have any issues make sure you have no spaces in the arguments you pass and that the executable you are trying to run has exeute permission enabled with `chmod +x you-app`

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