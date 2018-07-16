---
layout: post
title: Use clipboard in a none-gui vim in linux(ubuntu)
---
# Get source code (version 8.1)  
```
git clone https://github.com/vim/vim.git
```

# Install lib necessary for X11 support in ubuntu  
```
sudo apt-get install libx11-dev libxtst-dev libxt-dev libsm-dev libxpm-dev
```

# compile vim  
- clear cached files by previous execution of configure
```
~ $ cd git/vim
~/git/vim $ sudo rm src/auto/config.cache
```
- configure  
```
sudo ./configure \
    --with-features=huge \
    --enable-gui=auto \
    --enable-gtk2-check \
    --enable-gnome-check \
    --with-x \
    --enable-multibyte \
    --enable-gpm \
    --enable-cscope \
    --enable-fontset \
    --enable-fail-if-missing \
    --prefix=/usr/local \
    --enable-luainterp=dynamic \
    --enable-pythoninterp=dynamic \
    --enable-python3interp=dynamic \
    --enable-perlinterp=dynamic \
    --enable-rubyinterp=dynamic \
    --enable-tclinterp=dynamic
```  
succeeded if  
```
#define HAVE_X11 1
```
is shown when executing  
```
grep X11 src/auto/config.h
```  
- make  
```
sudo make clean all
```  
- install  
```
sudo make install
```  
- check  
check by executing
```
vim version | grep clipboard
```

# configure .vimrc  
add
```
set clipboard=unnamedplus
```

# practical use
<table align="center">
  <tr><th align="center"></th><th align="center">normal mode</th><th align="center">insert mode</th></tr>
  <tr><td>yank</td><td>"+y</td><td></td></tr>
  <tr><td>paste</td><td>"+p</td><td>S-C-V</td></tr>
</table>
