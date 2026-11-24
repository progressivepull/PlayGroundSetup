# Set Password for John Account

**Error Message**

```
john@debian:~$ sudo apt update
[sudo] password for john: 
john is not in the sudoers file.
```

## Step 1. Switch to the root account
At the terminal, run:

```bash
su -
```

Enter your **root password** (not your john password).

## Step 2. Add john to the sudo group
Run:

```bash
usermod -aG sudo john
```


This adds **john** to the sudo group without removing other group memberships.

## Step 3. Verify group membership
Run:

```bash
groups john
```


You should see something similar to:

```bash
john : john sudo
```

Great! Your output confirms that john is already a member of the sudo group.

```
john : john cdrom floppy sudo audio dip video plugdev users netdev scanner bluetooth lpadmin
```

**Refresh your group membership**

```bash
newgrp sudo
```


## Step 4. Restart your session
Log out of Debian completely and log back in.

Alternatively, reboot:

```bash
reboot
```

## Step 5. Test sudo
Open a terminal and run:

```bash
sudo apt update
```

Enter john's password when prompted.

# [README](./README.md)
