### Story of convenient initial settings in xubuntu 18.04

#### Litteral shorcut notation
These are synonyms

- as root 
	- sudo command ...
	- \# command ...
- as logged in user
	- command (and explaining context that emphasize it is a shell invoked command)
	- $ command

explanations by result, by use of:
 
	function lscat
	{
		ugperm=`ls -l $1 | awk '{ print "perm=",$1,"owner=",$3,"group=",$4 }' `
		echo "$ugperm"
		cat $1 | awk '{ print "    ",$0 }' 
		echo 
	}

### root password

	$ sudo -i
	\# passwd
	\# exit

file ~/.sudo_as_admin_successful is keept to avoid beeing info-ed on every terminal opening.

### getting midnight commander

	# apt-get mc

### [screen resolution](http://ubuntuhandbook.org/index.php/2017/04/custom-screen-resolution-ubuntu-desktop/)
Identify display device name

	$ xrandr

Getting a modeline for wanted resolution - eg. 1280 wide(x) and 1024 high(y)

	$ cvt 1280 1024
	
	$ lscat ~/nonamebin/newvid 
	perm= -rwxrwxr-x owner= bvirk group= bvirk
		 xrandr --newmode  "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
		 xrandr --addmode  VGA1 "1280x1024_60.00"
		 xrandr --output VGA1 --mode "1280x1024_60.00"

Add to Application->settings->sessions and startup

### [ethernet static ip address](https://www.techrepublic.com/article/how-to-configure-a-static-ip-address-in-ubuntu-server-18-04/)

	\# lscat /etc/netplan/01-netcfg.yaml 
	perm= -rw-r--r-- owner= root group= root
		 network:
		   version: 2
		   renderer: networkd
		   ethernets:
		     enp1s0:
		       addresses: [192.168.0.3/24]


	\# netplan apply

### setup files, logged in user

	$ tail ~/.bashrc
	export PATH=/home/bvirk/bin:$PATH
	export EDITOR=jedit
	alias mc='mc -b'
	function lscat
	{
	ugperm=`ls -l $1 | awk '{ print "perm=",$1,"owner=",$3,"group=",$4 }' `
	echo "$ugperm"
	cat $1 | awk '{ print "    ",$0 }' 
	echo 
	}

### [workaround - free console under mc](https://unix.stackexchange.com/questions/182925/dconf-warning-failed-to-commit-changes-to-dconf-the-connection-is-closed)
	
	p$ lscat /usr/local/bin/mousepadWA 
	perm= -rwxr-xr-x owner= root group= root
		 /usr/bin/mousepad $1 >/dev/null 2>&1 &


### setup files, root

	\# tail ~/.bashrc
	export EDITOR=/usr/local/bin/mousepadWA
	alias mc='mc -b'
	function lscat
	{
	ugperm=`ls -l $1 | awk '{ print "perm=",$1,"owner=",$3,"group=",$4 }' `
	echo "$ugperm"
	cat $1 | awk '{ print "    ",$0 }' 
	echo 
	}

### costumize mc 

- left|right->listing mode...
	- user defined: half type name|owner|group|mtime|perm
- option configuration
	- -use internal edit
- option layout
	- -keybar
	- -hintbar
- option panel option
	- +lynx-like motion
- option appearence
	- chose double lines for root
- option save setup
	- IMPORTANT TO KEEP SETTINGS

### hints to identify desktop gui items in Applications

- menues in top of screen
	- settings->panel-items
		- workspace switcher

### [installing apache, mysql, php](https://www.configserverfirewall.com/ubuntu-linux/install-apache-php-mysql-ubuntu-18/)

	...
	# head -n 3 /etc/apache2/apache2.conf 
	## added 20200618
	Include /etc/phpmyadmin/apache.conf 
	ServerName localhost

### [add mysql user](https://alvinalexander.com/blog/post/mysql/add-user-mysql/)
user: 'til' with password 'tilpas' is given database 'tilladt'

- login as mysql user root
	- $ sudo mysql
- create a database
	- mysql> create database tilladt;
- create usr and give access to database
	- mysql> GRANT ALL PRIVILEGES ON tilladt.* TO 'til'@'localhost' IDENTIFIED BY 'tilpas' WITH GRANT OPTION;
- commit
	- flush privileges;
- logout for mysql user root
	- quit






