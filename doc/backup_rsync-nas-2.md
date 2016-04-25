## Backup with rsync and NAS - 2: Create Scheduled Tasks to Sync

Finished the server-side mission. Let's turn to client side!


### `crontab` for simple scheduled tasks
Task on the client side is relatively simple. Just need to schedule some commands for automatically synchronizing your data. In a GNU/Linux system, there is a program called `cron`. It is a program that schedule task for us. As for scheduling task, it is also a daemon tool for many routines. To create cron jobs, we use `crontab` command to write down on cron table.

Before we started, let's learn some few options in `crontab`.
- `-u` : specify a user's cron table to use. Must has the permissions.
- `-l` : list a user's cron tabls
- `-r` : remove cron
- `-e` : edit **current** user's cron table if no using `-u`

For example:
- opening and modifying on cron table for user2
    ```bash
    test@server$ sudo crontab -u user2 -e 
    ```

- remove cron tabls for user1
    ```bash
    test@server$ sudo crontab -u user1 -r 
    ```

### 1. write a rsync script
Since crontab can only execute one line command in a task, we should write down our own **Bash Script** for multiple commands. 

First, create a script wherever you want. (maybe at `/home/user/cron_scripts`)
```bash
test@server$ vim ~/crom_scripts/rsync-backup.sh
```

In the `rsync-backup.sh` file, backup using rsync.
```bash
#!/bin/bash
# Modified Time: Sun Apr 24 17:00:00 CST 2016
# Author: john doe (john_doe@example.com)
# Usage: Synchronize data to NAS

echo Start rsync backup at $(date)."

rsync -axvzHSX --numeric-ids --progress --delete --password-file=/etc/rsyncd.cli.secrets /home/ rsync://user@192.168.1.101/server1

echo End rsync backup at $(date)."
```

You may consider why there is anoterh **password file** again. The **password file** contain only a password corresponding to the `rsyncd.secrets` file you created in the NAS server-side before. For instance, if you have a `rsyncd.secrets` file with the contents such as,

```
user:mypassword
root:rootHasItsOwnPassword
```

and you want to login with `user` account, you must create a file containing only the password `mypassword`. Still, this is a plain text file, so you must change its permission to `600` by the `chmod` command as same as what you done to `rsyncd.secrets` before.


### 2. Scheduling your tasks
After write your automated scripts. Open and modify cron tables by `crontab`

```bash
test@server$ sudo crontab -e
```

To create a schedules are easy, just follow its clear syntax and enjoy the amazing automatic tasks.

**Crontab syntax :**
A crontab file has five fields specifying the interval and one field containing the one-line command to be executed.

To define the time you can provide concrete values for minute (m), hour (h), day of month (dom), month (mon), and day of week (dow) or use '\*' in these fields (for **any**).


```bash
*    *    *    *    *    command to be executed
-    -    -    -    -
|    |    |    |    |
|    |    |    |    +----- day of week (0 - 7) (Sunday=0,7)
|    |    |    +------- month (1 - 12)
|    |    +--------- day of month (1 - 31)
|    +----------- hour (0 - 23)
+------------- min (0 - 59)
```

For example, you can run a backup of all your user accounts at 5 a.m every Monday:
```bash
#m   h   dom  mon  dow   command
0    5    *    *    1     tar -zcf /var/backups/home.tgz /home/¬
```

Or you want to repeat the command every four hours:
```bash
#m   h   dom  mon  dow   command
0   */2   *    *    *     sudo apt-get update
```

Finally, set your own cron jobs to your rsync script. Remember, using Absolute path to the script is always better than relative path. This cron will execute at 8:00 A.M every Monday and Thursday.

```bash
#m   h   dom  mon  dow   command
0    8    *    *   1,4    ~/crom_scripts/rsync-backup.sh
```
