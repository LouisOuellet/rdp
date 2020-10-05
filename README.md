# RDP

This script makes it easy to connect to older iRDP 6 Controllers and provides a ThinClient experience.

## Requirements

All package required can easily be install by running ```./rdp -i```. The script relies on DNS Queries to identify the host. The host address is built like so : ${USERNAME}${DOMAIN}. Otherwise you can specify a host using ```-h```.

As I initially wrote the script for thinclient use, I wanted to limit the amount of input required for the user while offering secured passwords.

## Usage

```bash
./rdp -?
Invalid option: ?

Usage: rdp [options]

Options:

-u                     => Set Username
-p                     => Set Password
-d                     => Set Domain
-h                     => Set Host
-k                     => Enable Persist Mode which relaunches the prompt whenever you close your connection
-l                     => Enable Drives Redirection
-v                     => Enable Debug Mode
                          Input commands sent are stored in log/rdp/
-i                     => Install Script as Binary
-r                     => Remove Installation
-m                     => Enable Multi-Monitor
-a                     => Set Alternate Port
```

## How To
### Update the script

First update the local repository using:
```bash
git pull origin main
```

And update the bin file using

```bash
./rdp -r && ./rdp -i
```
### Add a desktop shorcut

From the repository directory execute:
```bash
cp Remote\ Desktop\ Connection.desktop ~/Desktop/Remote\ Desktop\ Connection.desktop
```

Then you can edit the parameters (```Exec=rdp -mkl```) of the command using nano.

### Run the script when a X session is started

Create a script in ```/etc/X11/Xsession.d```.

/etc/X11/Xsession.d/startup-local
```bash
#!/bin/sh
rdp -mkld domain.fqdn
```

And make it executable.

```bash
chmod 755 /etc/X11/Xsession.d/startup-local
```

*To run only when a specific user login, you will need to check the desktop environment documentation.

## Changlelog

 * [2020-10-01] - Added a persist switch that will specify the script to run in a loop. So whenever a session is closed, the script prompts the GUI again and launches the connection. If the host port is closed, the script will output an error in a dialog box. The OK button will continue the loop while the close button will stop it.
 * [2020-10-01] - Added a host switch if you want to specify a host.
 * [2020-10-01] - Added a some tutorials to setup your thinclient to use the script.
 * [2020-10-01] - Added a drive redirection switch to enable drive redirections such as USB drives.
 * [2020-10-01] - Added the output of xfreerdp whenever ```-v``` is used
 * [2020-10-01] - Added a desktop file to copy on the client's Desktop
