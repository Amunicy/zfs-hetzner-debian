# zfs-hetzner-debian

[![shellcheck](https://github.com/Amunicy/zfs-hetzner-debian/actions/workflows/shellcheck.yml/badge.svg)](https://github.com/Amunicy/zfs-hetzner-debian/actions/workflows/shellcheck.yml)

A script to install Debian 12 with ZFS root filesystem on a Hetzner dedicated server.<br/>
__WARNING:__ all data on the disk will be destroyed.

## How to use:

* Log in to Hetzner Robot self-service portal.
* Select the desired dedicated server.
* Choose "Rescue" menu.
* Select an SSH key.
* Activate the rescue system.
* Reboot the server into a rescue system from either "Reset" menu or via
the ssh.
* Connect to the server via the ssh and run rescue system's command `zfs` to
compile and install latest zfs
* Download and run the script:
````bash
wget -qO- https://raw.githubusercontent.com/Amunicy/zfs-hetzner-debian/master/hetzner-debian12-zfs-setup.sh | bash -
````

Upon successful run, the script will reboot the system. You will be able to log in to it using the same SSH key you have
used to active the rescue system.

***Please note that the drives you intend to format can not be in use!  
You can execute `mdadm --stop --scan` before running the script to halt default software raid operations.***
## Recommendations
To cope with network failures it's highly recommended to run the commands above inside screen console.  
Type `man screen` for more info.

**Example of screen utility usage:**

````bash
export LC_ALL=en_US.UTF-8 && screen -S zfs
````
To detach from screen console, hit Ctrl-d then a
To reattach, type `screen -r zfs`
