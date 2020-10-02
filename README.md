# RDP

This script makes it easy to connect to older iRDP 6 Controllers and provides a ThinClient experience.

## Requirements

All package required can easily be install by running ```./rdp -i```. But you will need to have a DNS server or edit your ```/etc/hosts``` file. Because the script relies on DNS Queries to identify the host. The host address is built like so : ${USERNAME}${DOMAIN}.

As I initially wrote the script for thinclient use, I wanted to limit the amount of input required for the user while offering secured passwords.

## Usage

```bash
./rdp -?
Invalid option: ?

Usage: rdp [options]

Options:

-v                     => Enable Debug Mode
                          Input commands sent are stored in log/rdp/
-i                     => Install Script as Binary
-r                     => Remove Installation
-u                     => Set Username
-p                     => Set Password
-d                     => Set Domain
-m                     => Enable Multi-Monitor
-a                     => Set Alternate Port
```
