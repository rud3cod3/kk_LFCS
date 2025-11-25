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
```bash
# Usually put on the directories
chmod +t dirname
chmod 1777 dirname
```

### Find Command

#### In linux 
1. Modification = create or edit
2. Modified Time = Change time

```bash
# We can make use of this when finding something 
# find by file permission
find . -perm /640          # File with any of 640 permission
find . -prem 640           # Exactly 640 permission
find . -prem -640          # Atleast 640 permission

# Find using name
find . -name filename

# By size 
find . -size +20M

# Casesensitive
find . -iname filename
find . -type f          # only files
find . -type d          # only directories

# Filter by last modified time (in minutes)
find . -mmin 5          # Modified **exactly** 5 minutes ago
find . -mmin -5         # Modified **within the last 5 minutes** (newer than 5 min)
find . -mmin +5         # Modified **more than 5 minutes ago** (older than 5 min)

# Modified Time in Days
find . -mtime 1         # Modified **exactly 1 day ago** (24–48 hrs)
find . -mtime -1        # Modified **within last 24 hours**
find . -mtime +1        # Modified **more than 1 day ago**

# Change Time in Minutes
find . -cmin 10         # Metadata changed **exactly** 10 minutes ago
find . -cmin -10        # Metadata changed **within last 10 minutes**
find . -cmin +10        # Metadata changed **older than 10 minutes**

# To include operators
find -name "f*" -size 512k              # AND operator
find -name "f*" -o -size 512k           # OR operator
find -not -name "f*"                    # NOT operator
find \! -name "f*"                      # NOT alternate
```

### Working with sed
```bash
# Its a streamline editor

# Replace only first match
sed 's/canada/america/'

# Replace word globally in whole file
# s = substitute string
# g = globally
sed 's/canada/america/d' filename       

# Replace word canada to america also change in file aswell
# i = --in-place
sed -i 's/canada/america/d' filename    # replace word canada to america also change in file aswell
```

### Working with cut
```bash
# It can extract what we want from a file
# -d = delimiter / what we are using to seprate like ' ' (Blankspace) or ',' (Comma)
# -f = field / in this case column 1,2 
cut -d ' ' -f 1 filename
cut -d ',' -f 3 filename
```

### uniq and sort
#### country.txt
```bash
# uniq will remove duplicate which are next to each other
# country.txt
canada
america 
palau
america 
america
panama
india 
india
china
```
### Now if we use 
```bash
uniq country.txt
```

### Expected Output
```bash
canada
america
palau
america
panama
india
china
```

### Working with sort
```bash
# Pretty easy to use it will sort everything aplhabetically
uniq country.txt | sort 
```

### Expected Output
```bash 
america
america
canada
china
india
palau
panama
```

### Working with diff
```bash
# Suppose we made some config changes we forget what we changed and we have backup of that one config file in such case we can make use of this command
diff new-conf old-conf

# we can also make use of -c
# -c = context
diff -c new-conf old-conf 

# or we can make use of -y
# -y = side by side
diff -y new-conf old-conf 
```

### Working with grep
```bash
# Multiple Options
# -i = to avoid cases
# -v = to invert of what you want to find | you will get everything except what you specify in the command
# -w = find exactly matching word
# -r = search recursively
# -o = only match words what you specified and then we can use it with wc -l

# Exactly match PASS word
grep '^PASS' /etc/filename

# Exactly match one character between both
# It would match with name cat, cut, etc.
grep -r 'c.t' file
```

```bash
# Using egrep
# Look for 0 which is repeated 3 times next to it we can set max value aswell
egrep -r '0{3,}' /etc/

# for exactly 3 repeatation
egrep -r '0{3}' /etc/

# for max 3 zeros
egrep -r "0{,3}" /etc/

# last optional character
# d in the disabled is optional so it would match all the words with disable wether it is disables or disabled
egrep -r 'disabled?' /etc/

# We can match enabled or disabled
egrep -r 'disabled|enabled' /etc/

# get word start from c and end with t and whatever is specified between the [] will be displayed
egrep -r 'c[au]t' /etc/

# get dev list using grep using mulitple expressions 
egrep -r '/dev/[a-z]*[0-9]?' /etc/
```

### Different version of compression
```bash
# gzip
gzip file1          # Compress
gunzip file1.gz     # Decompress

# bzip2 
bzip2 file2         # Compress
bunzip file2.bz2    # Decompress

# xz 
xz file3            # Compress
unxz file3.xz       # Decompress

# zip
zip file1.zip dir_name/         # Compress
zip -r archive.zip dir_name/    # recursively compress
unzip file1.zip                 # Decompress
```

### Copying file to remote server
```bash
# Use rsync

# Using dd
# Creating backup
sudo dd if=/home/bob/Picture of=diskimage.raw bs=1M status=progress

# Restoring backup
sudo dd if=diskimage.raw of=/dev/vda bs=1M status=progress
```
