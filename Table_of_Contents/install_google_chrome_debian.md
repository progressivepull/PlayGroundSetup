# Install Google Chrome on Debian

These instructions work on Debian 12 and Debian 13 on 64-bit Intel/AMD
systems (`amd64`).

## 1. Check your system architecture

Open Terminal and run:

``` bash
dpkg --print-architecture
```

For a typical Intel or AMD computer, the output should be:

``` text
amd64
```

> The download below is for `amd64`. If your system reports a different
> architecture, do not use this package.

## 2. Update Debian

``` bash
sudo apt update
sudo apt upgrade -y
```

## 3. Install `wget`

``` bash
sudo apt install -y wget
```

## 4. Download Google Chrome

Go to your Downloads directory:

``` bash
cd ~/Downloads
```

Download the official Google Chrome Debian package:

``` bash
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
```

## 5. Install Google Chrome

Run:

``` bash
sudo apt install -y ./google-chrome-stable_current_amd64.deb
```

APT will install the package and its required dependencies.

## 6. Verify the installation

``` bash
google-chrome --version
```

The command should display the installed Google Chrome version.

## 7. Launch Google Chrome

Start Chrome from Terminal:

``` bash
google-chrome
```

You can also open Google Chrome from Debian's Applications menu.

## 8. Update Google Chrome

The Debian package configures Google's software repository. To install
available updates, run:

``` bash
sudo apt update
sudo apt upgrade -y
```

## 9. Optional: Delete the downloaded installer

After Chrome is installed, you can remove the downloaded `.deb` file:

``` bash
rm ~/Downloads/google-chrome-stable_current_amd64.deb
```

## Official download

[Download Google Chrome](https://www.google.com/chrome/)

------------------------------------------------------------------------

**Note:** These commands assume you have `sudo` privileges. If you see a
message that your user is not allowed to use `sudo`, sign in as an
administrator or ask your system administrator to grant the required
permissions.

# [README](./../README.md)
