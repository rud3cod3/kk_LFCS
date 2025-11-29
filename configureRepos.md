### Debian 
```bash
Types : deb
URIs : http://us.archive.ubuntu.com/ubuntu/
Suites : noble noble-updates noble-backports
Components : main restricted universe multiverse
Signed-By : /usr/share/keyrings/ubuntu-archive-keyring.gpg
```

**Types** : *wehter deb or rpm repo*

**URIs** : *Universal resource identifier*

**Suites** : *noble means core ubuntu packages*

**Components** : *Categories of packages based on their licensing and other criterias* 
                 *main - supported and licenced by ubuntu, Free and opensource also officially supported by ubuntu*, 
                 *restricted - free and opensource but may have restriction for redestribution*, 
                 *universe - free and opersource but not officially supported by ubuntu*, 
                 *multiverse - may note be free and opensource and also might have licensing issues*


### Adding Third Party repo
```bash
# First add key
curl "https://download.docker.com/linux/ubuntu/gpg" -o docker.key

# Dearmor the key (convert it into the binary)
gpg --dearmor docker.key (Now we have got docker.key.gpg)

# Add this new file to keyrings (A place where digital keys are stored)
sudo mv docker.key.gpg /etc/apt/keyrings/

# Now create a list file at /etc/apt/sources.list.d/
sudo vim /etc/apt/sources.list.d/docker.list

# Now add repo content in my case it is this one 
# Also remember this one is old way new syntax is described above
deb [signed-by=/etc/apt/keyrings/docker.key.gpg] https://download.docker.com/linux/ubuntu noble stable 

# Now update apt database
sudo apt update
```

### PPA - Personal Package Archive

```bash
# To add repo also upload all the packages you want in this ppa
sudo add-apt-repository ppa:john/mylatestapp        # john username and mylatestapp is reponame

# To get list of all the ppa
sudo add-apt-repository --list

# To remove ppa
sudo add-apt-repository --remove ppa:john/mylatestapp 
``` 
