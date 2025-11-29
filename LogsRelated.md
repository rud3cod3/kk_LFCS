### Log daemons
Application that collect, organize and store logs.

### rsyslog
```bash
rsyslog - rocker-fast syslog for log processing

# It stores all logs in 
/var/log/

# Most system related logs will be found at
/var/log/syslog 

# We may often find old log file in [*.GZ] files
```

### To get realtime update of logs use
```bash
less -F /var/log/auth.log
```

### journalctl
```bash
# New utility which keeps track of logs
# Use it something like this
# First spot the location of the command than use journalctl

which sudo
journalctl /usr/share/sudo
```
