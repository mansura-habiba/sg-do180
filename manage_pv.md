Host Directory
---
/var/lib/mysql

Set Selinux
---
Help
```
sudo semanage -f
```

```
sudo semanage fcontext -a 0t container_file_t '/home/student/local/mysql(/.*)'?'
```
Apply the SeLinux just created

```
sudo restorecon -Rv <host directory>
```
