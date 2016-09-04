# bash-liblog

A Bash library for basic log handling

Install
-------

You can clone this repository or download it as a zip file. To clone:

    git clone https://github.com/david-moreno/bash-liblog.git
    cd bash-liblog
    sudo make install

Uninstall
---------

Using the cloned/unzipped directory:

    cd bash-liblog
    sudo make uninstall

Usage
-----

#### log_get_name
Returns the name of the current log file

#### log_set_name *name*
Sets the name of the current log file

#### log_get_dir
Returns the path of the log file directory
The default is **/var/log**

#### log_set_dir *path*
Sets the path of the log file directory

#### log_get_sep
Returns the level separator character
The default is **:**

#### log_set_sep *separator*
Sets the level separator character

#### log_create
Creates a new log file

#### log_check
Determines if the current log file exists and has write permission
This function returns 1 on success or 0 otherwise

#### log_clear
Clears the current log file

#### log_delete
Deletes the current log file

#### log_write *message*
Writes a message on the current log file

#### log_write_debug *message*
Writes a DEBUG level message on the current log file

#### log_write_info *message*
Writes a INFO level message on the current log file

#### log_write_notice *message*
Writes a NOTICE level message on the current log file

#### log_write_warning *message*
Writes a WARNING level message on the current log file

#### log_write_error *message*
Writes a ERROR level message on the current log file

#### log_write_critical *message*
Writes a CRITICAL level message on the current log file

#### log_get_last
Returns the last line of the current log file

Example
-------

If our script is myscript, we can:

```bash
#!/bin/bash

#Includes the library into the script
source "/usr/lib/bash/liblog"

#Sets log file name
log_set_name "myscript.log"

#Optionally (if we have root access), we can create a directory for the log file,
log_set_dir "/var/log/myscrypt"

log_create

#Checks if all was ok
if (( ! `log_check`)); then
	echo "Cannot create myscript.log"
	exit
fi

#Writes out some stuff to the log
log_write "Starting myscript"
log_write_info "All is fine here"
```

The output on myscript.log is:

    sep 4 03:34:06 Starting myscript
    sep 4 03:34:06 INFO: All is fine here
