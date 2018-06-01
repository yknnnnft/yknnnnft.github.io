---
layout: post
title: access git using local ssh key
---

# Generate RSA key
```
$ ssh-keygen -t rsa
```  

# Add key to github  
- get key generated  
```
$ cat ~/.ssh/id_rsa.pub
```
- add the key to the Github

# Configure local ssh  
```
$ vim ~/.ssh/config
```  
add the following to the config file
```
Host github.com
  HostName github.com
  IdentityFile ~/.ssh/id_rsa
  User git
```

# setup local repository
- get the repository  
```
$ git clone https://github.com/sample.git
```  
- setup remote url  
```
$ git remote set-url origin git+ssh://github.com/sample.git
```

# access github with local ssh key
```
git pull
```
