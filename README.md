MySQL rotating backup script
============================
mysql_backup provides a way to backup a single mysql database. Old backups are deleted as new ones are created.

Usage
-----
    $ mysql_backup <db_name> [backup_dir]
The current running directory is used if not specified.

This script is most useful when run as a daily cron job.

    0 6 * * * mysql_backup my_db /backups

Alternatively place a script under /etc/cron.daily/

Script Arguments
----------------
The following environment variables can be passed to the script for connecting to mysql.

* MYSQL_HOST: Host to connect to (mysql -h)
* MYSQL_USER: Username to authenticate with (mysql -u)
* MYSQL_PASS: PAssword to authenticate with (mysql -p)

Example:

    $ MYSQL_HOST="localhost" MYSQL_USER="user" MYSQL_PASS="passwd" mysql_backup my_db /backups

Rotation
--------
Daily backups are kept for 7 days, weekly for 4 weeks, and monthly indefinitely. This can be changed by altering the {DAILY,WEEKLY_MONTHLY}_FILES_TO_KEEP variables at the top of the script. 0 corresponds to infinite.
