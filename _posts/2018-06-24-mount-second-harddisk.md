---
layout: post
title: A solution when the secondary disk is not writable in ubuntu
---

# Background  
In a dual-system of Ubuntu(18.04) and windows 10,  the secondary harddisk (Windows 10) becomes read-only so that files cannot be cut or removed.  
When execute
```
$ mount -l
```
the following message is shown 
```
/dev/nvme0n1p4 on /media/user/32DAAB90DAAB4EC3 type fuseblk (__ro__,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096,uhelper=udisks2)
```

# Solution  
1. Remount  
Exeucte the following  
```
$ sudo mount -o remount,rw '/media/user/32DAAB90DAAB4EC3'
```  
1. Confirm  
Exeucte the following  
```
$ mount -l
```  
Succeeded if the following is got  
```
/dev/nvme0n1p4 on /media/user/32DAAB90DAAB4EC3 type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096,uhelper=udisks2)
```  
1. Change the ownership (if necessary)
After remounting, the secondary hard disk is owned by the ROOT user. Thus we need change the ownership.  
```
$ sudo chonw user -R /media/user/32DAAB90DAAB4EC3  
```
Check in the folder in the file system and all files are removable now.  
