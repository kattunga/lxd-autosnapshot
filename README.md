# lxd-autosnapshot
LXD Autosnapshot script

Install
-------

download and decompress in any place
```
wget https://github.com/kattunga/lxd-autosnapshot/archive/v0.1.tar.gz
tar -xvf v0.1.tar.gz
sudo mv lxd-autosnapshot /opt/

```

Configure
---------

Create the configuration files for the source and target systems and then edit the configuration files using your preferred text editor.

```
cd /opt/lxd-autosnapshot
sudo ./config
sudo nano lxd-autosnapshot.conf  
```

###lxd-autosnapshot.conf

Please check to ensure DATE points to the GNU date command in the lxd-autosnapshot file.

Minimally, in lxd-autosnapshot.conf you need to specify 
* the email addresses you want to use to email errors/logs from and to 
* the lock path and log file

```
# email settings
mail_from=root@example.com
mail_to=user@example.com
mail_subject=lxd-autosnapshot

#process files/paths
LOCK_PATH=/var/lock
LOG_FILE=/var/log/lxd-autosnapshot.log
```
You may need to change the LOCK_PATH and LOG_FILE location to match the standard locations for your *nix installation.
LOCK_PATH could be set to /var/lock, /var/lock/subsys, or even /tmp

Create the log file with:
```
sudo touch /var/log/lxd-autosnapshot.log
```

Usage
=====

See './lxd-autosnapshot --help'.

Hourly snapshot crontab entry
```
0 * * * *  /opt/lxd-autosnapshot/lxd-autosnapshot --source cn01 --prefix "hour-" --snap-retain "-2 days" 
```



