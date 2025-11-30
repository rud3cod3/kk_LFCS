### What is SELinux
* SELinux (Security-Enhanced Linux) is a kernel-level security module that implements Mandatory Access Control (MAC).
* It restricts what processes can do, even if they run as root.

### Why SELinux Exists
* Traditional Linux security (DAC: Discretionary Access Control) allows:
    * Root can do anything
    * File owners control access
* This is not enough for high-security environments.
* SELinux adds:
    * Mandatory rules
    * Kernel-enforced policies that even root cannot bypass


### To see it in a better way use 
```bash
ls -Z
```

### SELinux Modes

| Mode           | Description                                                 |
|----------------|-------------------------------------------------------------|
| **Enforcing**  | SELinux rules are **checked + enforced** (strict).          |
| **Permissive** | SELinux rules are **checked but not enforced** (logs only). |
| **Disabled**   | SELinux is turned off.                                      |


### Checking current mode
```bash
getenforce
```

### Change mode temporarily
```bash
sudo setenforce 0   # permissive
sudo setenforce 1   # enforcing
```
