# rsync Backup  #

An Ansible Role that creates automatic rsync backup via systemd timers.

## Requirements ##
- systemd
- rsync

## Role Variables ##

Available variables are:
- ` backup: ` list of dictionaries with the targets and configuration.
  - ` - name_of_backup: ` the dictionary name of the backup, it is used for naming the services and timers needed.
	  - ` backup_target: ` directory or file to be backed up.
	  - ` local_safe_path: ` where to store backup locally.
	  - ` local_backup_minute: ` minute to run the local backup_service.
	  - ` local_backup_hour: ` hour to run the local backup service.
	  - ` local_days_of_week: ` days to run the local backup service.
	  - ` remote_safe_path: ` where to store backup on remotely.
	  - ` remote_ssh_port: ` remote ssh port to be used.
	  - ` remote_backup_minute: ` minute to run the remote backup_service. 
	  - ` remote_backup_hour: ` hour to run the remote backup service.
	  - ` remote_days_of_week: ` days to run the remote backup service.
	  - ` backup_now: ` backup when running the role.

The structure of a list of dictionaries allows multiple targets and hosts.

Note that the backups can be both remote and local. The service is only created if either ` remote_safe_path ` or ` local_safe_path ` are set.

` remote_safe_path ` must follow the structure: ` <remote_user>@<remote_host>:<path_to_store> `.
` local_safe_path ` must be an absolute path.

Global candidates variables:

These are the default values when no value is set on backup dictionary.
- `days_of_week` can be null for everyday backups. Multiple days must be separated by commas like ` Mon,Tue,Wed `.
- ` backup_hour: ` 
- ` backup_minute: ` 
- ` remote_ssh_port ` Defaults to 22.

## Usage Notes ##

You can run only the local or remote backup including ` --tags 'now' ` and excluding the one you do not wish to execute with ` --skip-tags <remote|local> `.

## Dependencies ##

None.

## Example Playbook ##

```
- hosts: all
  roles:
    - jpedrodelacerda.rsync-backup
```

## License ##

MIT / BSD


