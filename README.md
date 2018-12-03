# rsync Backup  #

An Ansible Role that creates automatic rsync backup via systemd timers.

## Requirements ##
- systemd
- rsync

## Role Variables ##

Available variables are:
- ``` target: ``` directory to be backed up
- ``` safe_storage: ``` where to store the backup
- ``` day_of_week: ``` Runs the backup on given days.
- ``` hour: ``` hour to run the service
- ``` minute: ```specify hour to run the service

day\_of\_week can be null for everyday backups.
Multiple days must be separated by commas like ```Mon,Tue,Wed```.

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


