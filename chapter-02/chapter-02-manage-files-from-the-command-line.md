# Manage files from the command line

## Describe Linux file system hierarchy concepts



| Location   | Purpose                                                                                                                                                                                                                                                                                                                   |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| /boot      | Files to start the boot process.                                                                                                                                                                                                                                                                                          |
| /dev       | Special device files that the system uses to access hardware.                                                                                                                                                                                                                                                             |
| /etc       | System-specific configuration files.                                                                                                                                                                                                                                                                                      |
| /home      | Home directory, where regular users store their data and configuration files.                                                                                                                                                                                                                                             |
| /root      | Home directory for the administrative superuser, root.                                                                                                                                                                                                                                                                    |
| /run       | Runtime data for processes that started since the last boot. This data includes process ID files and lock files. The contents of this directory are re-created on reboot. This directory consolidates the /var/run and /var/lock directories from earlier versions of Red Hat Enterprise Linux.                           |
| /tmp       | A world-writable space for temporary files. Files that are not accessed, changed, or modified for 10 days are deleted from this directory automatically. The /var/tmp directory is also a temporary directory, in which files that are not accessed, changed, or modified in more than 30 days are deleted automatically. |
| /usr       | Installed software, shared libraries, including files, and read-only program data. Significant subdirectories in the /usr directory include /bin, /sbin, and /local                                                                                                                                                       |
| /usr/bin   | User commands                                                                                                                                                                                                                                                                                                             |
| /usr/sbin  | System administration commands                                                                                                                                                                                                                                                                                            |
| /usr/local | Locally customized software                                                                                                                                                                                                                                                                                               |
| /var       | System-specific variable data should persist between boots. Files that dynamically change, such as databases, cache directories, log files, printer-spooled documents, and website content, might be found under /var                                                                                                     |
```yaml
tree -L 1
mkdir -pv www.{ansible,openshift,redhat}.com/{html,cgi-bin}/
```


## Make Links Between Files

### Hard links
Hard links have some limitations. First, you can use hard links only with regular files. You cannot use the ln command to create a hard link to a directory or special file.

Second, you can use hard links only if both files are on the same file system. The file-system hierarchy can be composed of multiple storage devices. Depending on the configuration of your system, when you change into a new directory, that directory and its contents might be stored on a different file system.

```bash
ln newfile.txt /tmp/newfile-hlink.txt
ls -il newfile.txt /tmp/newfile-hlink2.txt
```

### Symbolic links
- can link two files on different file systems.
- can point to a directory or special file, not just to a regular file.

```bash
ln -s /home/user/newfile-link2.txt /tmp/newfile-symlink.txt
ls -l newfile-link2.txt /tmp/newfile-symlink.txt

ln -s /etc /home/user/configfiles
```


## Match File Names with Shell Expansions
