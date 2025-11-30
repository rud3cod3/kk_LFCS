### Security Modules
By default there is something called SELinux which is a security module is enabled in redhat based system and in ubuntu based systems there is something called apparmor

### To disable apparmor
```bash
sudo systemctl stop apparmor.service
sudo systemctl disable apparmor.service
```

### SELinux Installation Help
```bash
# Install this two pakacge selinux and audit daemon
sudo apt install selinux-basics auditd

# Use command to check status of selinux
sestatus

# Activate selinux
sudo selinux-activate

# To check mode of enforcing
getenforce
```
