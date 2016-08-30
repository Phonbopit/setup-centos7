# Setup CentOS 7

Setting up CentOS 7 on DigitalOcean

## Fixed locale error

```
-bash: warning: setlocale: LC_CTYPE: cannot change locale (UTF-8): No such file or directory
```

by edit `/etc/environment` , add these line:

```
LANG=en_US.utf-8
LC_ALL=en_US.utf-8
```

## Add new user

```
adduser chai
passwd chai

New password: #password
Retype new password: #password
```

> Note `chai` is just a demo name.

## Root Privileges 
```
gpasswd -a chai wheel
```

By default, on CentOS 7, users who belong to the "wheel" group are allowed to use the sudo command.

## Configure SSH

```
vi /etc/ssh/sshd_config
```

Change from

```
#Port 22
#PermitRootLogin yes
```

To

```
Port xx
PermitRootLogin no
```

Then reload

```
systemctl reload sshd
```

## Connect droplet

```
ssh chai@ip -p PORT_NUMBER
```

Done :smile:


## Extra

Install Oracle DB, Transform CentOS to Oracle Linux (sudo mode)

```
curl -O https://linux.oracle.com/switch/centos2ol.sh 
sh centos2ol.sh

yum install oracle-rdbms-server-11gR2-preinstall
```

## References

- [Initial Server Setup with CentOS 7](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-centos-7)
- [Oracle Linux: A better alternative to CentOS](http://linux.oracle.com/switch/centos/)
