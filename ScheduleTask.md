### Scheduling Tasks
1. at
* Minute
* Hour
* Day
* Other specific time

2. cron
* Day
* Few Days
* Week
* Month
* Year

3. anacron
* Task that only run once

#### crontab file
```bash
# All cronjobs are listed here and we need to modify this file if we want to add or remove cronjobs
# If we edit this one it will be applied to systemwide users
cat /etc/crontab

# To only add for user only
crontab -e

# To list cronjobs
crontab -l
```

### Dir approach
If we create certain directories we can run cron jobs which are described in those directories
this directories are as following

```bash
daily = /etc/cron.daily/
hourly = /etc/cron.hourly/
monthly = /etc/cron.monthly/
weekly = /etc/cron.weekly/
```
