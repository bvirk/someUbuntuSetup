### Achieved 
                          
#### plugin console and errorlist

#### Opening in workspace 1 as the possible only one instance freeing the invoking terminal 

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
	

###### stack
backup supress
spellchecker
importing macroes
invoke cyberkiss
using p
edit git workaround to not deting marked if no git repo