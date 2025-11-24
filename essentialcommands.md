### To get virtual terminal
```bash
ctrl + alt + F2
```

### Suppose you forget the command we can make use of apropos
```bash
# Let you see short description of all command
# First in order to use this command we need to either update or create data base
# Use mandb 
# Below given command will try to find all the command which has word director in thei short description
apropos directory

# With example
# 2 is for commands search
apropos -s 2 directory

# Use stat command for deep information
stat file.txt
```

### SGID, SUID, STICKYBIT

#### SUID
```bash
# When this perm is used the execution will happend with users permission without giving creds to someone
# It kinda set permission of execution which allow anyone to execute specific file with user preveledges which letting them having direct account access
# S means no execute permission
# s mean execution is allowed
chmod 4644 filename     # suid setup
```

#### SGID
```bash
# similar to suid but for group
chmod 2664 sgidfile
chmod 2674 sgidfile
```

#### STICKEY BIT


### Find

```bash
# We can make use of this when finding something 
# find by file permission
find . --perm /4000
```
