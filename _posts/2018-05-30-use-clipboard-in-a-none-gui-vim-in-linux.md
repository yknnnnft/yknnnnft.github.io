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
## configure
```
sudo ./configure \
    --with-features=huge \
    --enable-gui=auto \
    --enable-gtk2-check \
    --enable-gnome-check \
    --with-x \
    --enable-multibyte \
    --enable-luainterp=dynamic \
    --enable-gpm \
    --enable-cscope \
    --enable-fontset \
    --enable-fail-if-missing \
    --prefix=/usr/local \
    --enable-pythoninterp=dynamic \
    --enable-python3interp=dynamic \
    --enable-rubyinterp=dynamic
```

succeeded if 
```
#define HAVE_X11 1
```
is shown


## make
```
sudo make clean all
```

## install
```
sudo make install
```

## check
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
| | normal mode | insert mode |
|:---:|:---:|:---:|
| yank | "+y | |
| paste | "+p | S-C-V |
