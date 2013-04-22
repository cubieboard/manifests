manifests
=========

Cubieboard's android source code is maintained by git/repo tools. If you want to build android for cubieboard, you at least need to know how to use git and android repo (just some basic commands will be okay). Also the recommended building environment is ubuntu 12.04(x86_64). You can reference to <a href="http://source.android.com/source/initializing.html">Setting up a Linux build environment</a>

#Instruction to build openbox system for cubieboard  
openbox is based on ics-4.0.4, and with XBMC integrated.

## (1) Get all source code from github/cubieboard
    $curl https://raw.github.com/cubieboard/git-repo/stable/repo > ~/bin/repo
    $chmod +x ~/bin/repo
    $mkdir openbox && cd openbox
    $repo init --no-repo-verify -u git://github.com/cubieboard/manifests -b cb -m openbox.xml  
    $repo sync

## (2) Building
    $source build/envsetup.sh
    $lunch 4 (note: select cubieboard option)
    $make -j4
    $tools/pack-cm.sh (note: this will generate the final image suitable for livesuit tool)

## (3) Write the image to cubieboard
    a)Start livesuit program (linux or windows)
    b)Select the image you make before
    c)Plug in micro USB cable while holding the fex/u-boot key, and keep holding about 3 seconds

#Instruction to build jellybean for cubieboard

## (1) Get all source code from github/jellybean
    $curl https://raw.github.com/cubieboard/git-repo/stable/repo > ~/bin/repo
    $chmod +x ~/bin/repo
    $mkdir openbox && cd openbox
    $repo init --no-repo-verify -u git://github.com/cubieboard/manifests -b cb -m jb.xml  
    $repo sync

## (2) Building
    $source build/envsetup.sh
    $lunch 4 (note: select cubieboard option)
    $make -j4
    $tools/pack-cm.sh (note: this will generate the final image suitable for livesuit tool)

## (3) Write the image to cubieboard
    the same as above


## Known issue
    a)emac is not supported yet
    b)sata is not tested
