# Duplicity Utils

This script is useful for managing [Duplicity](http://duplicity.nongnu.org/) backups in a headless environment.
The main advantages provided by this wrapper are better log-file handling, easier cron scheduling, and simpler
command line execution. 

I consider this wrapper to be in Beta until the related ansible role is released.

###Install

####Prerequisites

The following python packages are required:

* duplicity

####Setup

The configuration file `default.conf` is expected to be in /etc/duplicity/. Settings to change include SERVER, GPG_PASSPHRASE, FTP_PASSWORD 
(if you use FTP instead of sftp), and the ssh IdentityFile path in BACKUP_PARAM.

**Logging:** The script currently expects write access to `/var/log/duplicity.log` and the folder `/var/log/duplicity`
for session logs. If you're running as an unprivileged user these log destinations need to be created manually.

###Commands

The main commands are:

* `dup -b` - perform backup (daily, weekly, whenever)
* `dup -u` - cleanup archives (monthly, yearly)


Available commands include:

```
dup - dup[licity] Management Script

  Syntax: dup [command] [options]

  Commands:
    -b       perform backup
    -h       help menu
    -l       list backup files
    -o       output todays log
    -r       restore files (requires: -f -d [-t])
    -s       status of backup
    -u       cleanup backup(s)
    -x       remove backup(s)

        See configuration file for parameters used by `-x`

  Options:
    -c       configuration file

        Unless specified, `/etc/duplicity/default.conf` is used

    -d       destination to put restore
    -f       file(s) to restore
    -t       time to restore

        now
        2002-01-25T07:00:00+02:00
        D=Days, W=Weeks, M=Months, Y=Years
        h=hours, m=minutes, s=seconds
```

###To-Do:

* Update log file handling with improved helper functions
* Add handling for errors related to missing logging path


[![Analytics](https://cjs-beacon.appspot.com/UA-10006093-3/github/cjsheets/duplicity-utils?pixel)](https://github.com/cjsheets/duplicity-utils)
