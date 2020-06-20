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

###### stack
edit git workaround to not deting marked if no git repo