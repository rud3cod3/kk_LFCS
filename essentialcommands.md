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
