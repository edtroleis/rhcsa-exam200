# Manage local users and groups
```bash
# show information about the currently logged-in user
id



```


```bash
cat /etc/passwd
...output omitted...
user01:x:1000:1000:User One:/home/user01:/bin/bash
```

| Item         | Description                                                                                                                                             |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| user01       | The username for this user.                                                                                                                             |
| x            | The user's encrypted password was historically stored here; it is now a placeholder.                                                                    |
| 1000         | The UID number for this user account.                                                                                                                   |
| 1000         | The GID number for this user account's primary group.                                                                                                   |
| User One     | A brief comment, description, or the real name for this user.                                                                                           |
| /home/user01 | The user's home directory, and the initial working directory when the login shell starts.                                                               |
| /bin/bash    | The default shell program for this user that runs at login. Some accounts use the /sbin/nologin shell to disallow interactive logins with that account. |


## Describe User and Group Concepts

```bash
```

## Gain Superuser Access
```bash
su - user01
sudo -u devops whoami
sudo -u devops -i
sudo -i
```

## Manage Local User Accounts
```bash
useradd user01
userdel user01
seradd -u 1000 user01
useradd -g users -G wheel,devops user01
passwd user01

id user01
usermod -G wheel user01

userdel -r user01

find / -nouser -o -nogroup 2>/dev/null

# Check the status of a user account
passwd -S user01
```

| UID Range   | Description                                                                                                                                                                        |
| ----------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| UID 0       | The superuser (root) account UID                                                                                                                                                   |
| UID 1-200   | System account UIDs that are statically assigned to system processes                                                                                                               |
| UID 201-999 | UIDs that are assigned to system processes that do not own files on this system. Software that requires an unprivileged UID is dynamically assigned a UID from this available pool |
| UID 1000+   | The UID range to assign to regular, unprivileged users                                                                                                                             |

## Manage Local Group Accounts
```bash

# create a group
groupadd -g 10000 group01
tail /etc/group

# modify a group
groupmod -n group0022 group02
tail /etc/group

# change group membership
usermod -g group01 user01
usermod -aG group01 user01
```

## Manage User Passwords
```bash
```
