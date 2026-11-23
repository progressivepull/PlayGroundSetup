# Play Ground Setup 
**PRETTY_NAME**="Debian GNU/Linux 13 (trixie)"      
**NAME**="Debian GNU/Linux"    
**VERSION ID**="13"    
**VERSION**="13 (trixie)"    
**VERSION CODENAME**=trixie    
**DEBIAN VERSION FULL**=13.8   

---

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

----
# Permission to access the Docker Socket

```bash
john@debian:~$ docker ps
permission denied while trying to connect to the docker API at unix:///var/run/docker.sock
```
The easiest solution on Debian is to add john to the docker group.

## Step 1. Check whether the Docker group exists

```bash
getent group docker
```

If it exists, continue.

## Step 2. Add john to the Docker group
Run:

```bash
sudo usermod -aG docker john
```

Important: The -aG options add the user to the group without removing existing group memberships.

## Step 3. Activate the new group
Run:

```bash
newgrp docker
```

Alternatively, log out of Debian and log back in.

## Step 4. Test Docker
Run:

```bash
docker ps
```


Also test:

```bash
docker run hello-world
```

Expected result
Docker should now run without the permission-denied error.


## Step 5. Verify permissions
Check your group membership:

```bash
groups
```


You should see docker in the output.

Check the Docker socket:

```bash
ls -l /var/run/docker.sock
```


Expected output resembles:

```
srw-rw---- 1 root docker ... /var/run/docker.sock
```



Security note: Membership in the docker group effectively grants root-level privileges on the machine. Only add trusted users.

If you still get permission denied, send me the output of:

```
groups
ls -l /var/run/docker.sock
sudo systemctl status docker
```

---





