http://www.cups.org/
https://wiki.debian.org/SystemPrinting

Cups Installation

If you didn't check any option at the Debian network installation, you will need to download and install a few packages.

```sh
 # apt-get build-dep cups
 # apt-get install cups cups-client
```

## Start

```sh
 # service cups start
```

 Allow Users To Print

As the Debian distribution installs a secure Linux system on your computer, most of the permissions involved by installing packages are "opt-in". This means you have to explicitly grant permission to users so that they can print.
This is done by adding them to the lpadmin group:

```
# adduser YOUR_NORMAL_ACCOUNT lpadmin
```

# Download a printer driver

In my case, I used a SL-M4070FR printer. I download the drive on site and install.


