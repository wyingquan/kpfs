kpfs is a filesystem for accessing kuaipan.cn based on FUSE.
===================
(You can use it in commercial software, but please let me know.)
This application is dedicated to my lovely son (Hean Yu).

How to build kpfs from svn source code?
===================
##download:

	svn checkout http://kpfs.googlecode.com/svn/trunk/ kpfs-read-only
	备注：还是从git下载吧，google被墙了

##prepare before configure
  please install depends, on ubuntu e.g.:
  
  sudo apt-get install gtk-doc-tools libfuse-dev libjson0-dev libcurl4-nss-dev liboauth-dev

  - liboauth will be used for oauth to kuaipan.cn
  - json-c will be used for parse response of request to kuaipan, and load/save kpfs.conf and kpfs_oauth.json
  - glib will be used for hash table

##configure:

    cd kpfs-read-only
    ./autogen.sh
    ./configure
    (run ./configure --help for more options)

##build:
    
    make

##install (need root)

	make install

##prepare before run
  
  please edit kpfs.conf as you wish, e.g.:
  	
    {
        "consumer_key": "xc8D2NfL9c53vkrP",
        "consumer_secret": "p7Lo7Q6XBMipbHBw",
        "mount_point": "/tmp/kpfs",
        "oauth_json_file": "/tmp/kpfs_oauth.json",
        "log_path": "/tmp"
    }
  
  "mount_point" is the mount point which you want mount kuaipan to;
  
  "oauth_json_file" will store the oauth information, then you do not need to input your ID and Password again on webpage.
  
  "log_path" is the path which will be used in debug mode.

##run:

	mkdir /tmp/kpfs
	cd src/
	./kpfs -c ../kpfs.conf

How to build and run kpfs on target board.
=========================================
利用假期改造成了scons编译：

1、安装FUSE for OS X，来源：http://osxfuse.github.io

2、安装libcurl、liboauth、json-c、glib等

3、安装scons

4、然后scons即可

Where can I get more information:
=========================================
DOC:  docs/* 

BLOG: http://blog.csdn.net/mimepp

WIKI: http://code.google.com/p/kpfs/wiki/

Google Group: http://groups.google.com/group/kpfs

Still have problems please send email to yut616@gmail.com
