### Achieved
                        
#### plugins

- console options
	- general
		- -show startup message
	
- errorlist

#### Opening in workspace 1 as the limitted to one instance freeing the invoking terminal 

	# tail -n 2 /usr/share/jedit/jedit.sh 
	wmctrl -s0
	run_java org.gjt.sp.jedit.jEdit -reuseview "$@" &

#### jedit as default editor 
	
	$ cat .bashrc|grep jedit
	export EDITOR=jedit

#### list of global options changes

- backup and save
	- -confirm on save all buffers
	- -autosave
	- max numbers of backup: 0
- shotcut key
	- F9			spell check selection
	- A+s			open scratchpad
	- S+BACKSPACE	actionsdialog
	- C+TAB			goto recent buffer
	- CONTEXT_MENU	cyberkiss
	- C+s			gitcommit-a-mSelected

#### macro costumation
	- cyberkiss
		- jedit api which wasn't part of apt jedit installation
			- copied using scp to /usr/share/doc/jedit/api/
		- in function OSUrl(String key) 
			- 	String [] linux = { "rt=https://docs.oracle.com/javase/8/docs/api/", "jedit=file:///usr/share/doc/jedit/api/"};
		- requirement for bash script jimport
			- gettting rt.jar
				- sudo apt-get install openjdk-8-jre
			- put jimport in path

#### bash script jimport for use with macro cyberkiss

	#!/bin/bash
	if [ -z $1 ]; then
		exit 2
	fi
	echoImport() { 
		if [ -f $2 ];then
			class=`jar -tf $2|grep /${1}.class`
			if [ -n "${class}" ];then
				jarFile=${2##*/}
				echo ${jarFile%.*}:${class}
			fi
				return 0
		fi
	}
	echoImport $1 /usr/lib/jvm/java-8-openjdk-i386/jre/lib/rt.jar 
	echoImport $1 /usr/share/jedit/jedit.jar

		
