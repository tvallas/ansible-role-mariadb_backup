Ansible role mariadb_backup
=========

A simple role that configures MariaDB backups using mysqldump command and cron to take backups on local server. Another cron task is created for removing old backups.

Requirements
------------

Ansible role mariadb (as this is for local backups). A mysql user account that has necessary privileges for backup is also naturally required.

Role Variables
--------------
##### `mariadb_backup_mysqldump_user` (required)

 mariadb user account name for backups

##### `mariadb_backup_mysqldump_password` (required)
 mariadb user account password


##### `mariadb_backup_days_to_keep` (required)
 how many days old backups are removed (int).

##### `mariadb_backup_cron_entries` (required)

 for example
```
- database: mydatabase
       minute: 0
       hour: 23
       day: "*"
       mysqldump_options: "--single-transaction"
```

##### `mariadb_backup_dir` (optional)

 destination folder for backups

##### `mariadb_backup_mysqldump_path` (optional)
path for mysqldump binary

##### `mariadb_backup_create_system_user` (optional)
 Defines if dedicated system user is created (boolean)

##### `mariadb_backup_system_user` (optional)
 name of the system user

##### `mariadb_backup_system_group` (optional)
 group for system user

##### `mariadb_backup_cron_file` (optional)
 name of the cron file

##### `mariadb_backup_permission` (optional)
  privileges that are used for backup folder



Dependencies
------------
Mariadb ansible role (not strictly required but in practise it is necessary)

Example Playbook
----------------

    - hosts: servers
      roles:
         - { role, mariadb, tags: mariadb }
         - { role: mariadb_backup, tags: mariadb_backup }

License
-------
Propriertary

Author Information
------------------
Tuomas Vallaskangas
