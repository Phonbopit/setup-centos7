# setup-centos7
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
