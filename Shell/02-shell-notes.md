# Bash

Yifei Yin, November 23, 2018

[YouTube: Beginner's Guide to the Bash Terminal by Joe Collins](https://youtu.be/oxuRxtrO2Ag)

Navigation
----------

- `ls`
    - `-a` all
    - `-l` long, more info
- `cd`
- `pushd` `popd`
- `file filename` tells file's type
- `locate filename` finds the file with (partial) file name
    - To manually update the list: `updatedb`
    - `-i` ignore case
    - on mac, need to run `sudo launchctl load -w /System/Library/LaunchDaemons/com.apple.locate.plist` first and wait until process `find` terminates, can watch it in the activity monitor.
- `which` tells which command is being used
- `history` 


Getting Help
------------
- `whatis`
- `apropos time` search command
- `man` (use for the most of the time)


Files
-----
- `mkdir folder1 folder2`
- `touch file1 file2`
    - Update the file time stamp
    - Creates a new file
- `cp fromDir toDir` copy a file 
- `mv` move or rename
    - move: `mv filename path`
    - rename: `mv filename filename`
    - could potentially overwrite some file
- `rm` remove
    - `rm -r` recursive, to remove folders
- `rmdir` remove empty directory


Text Files
----------
- `cat` concatenate
    - `cat filename` prints file content
    - `cat >> filename` input something to file
    - `cat file1 file2` prints content from file1 and file2
- `more` (very old command)
    - pages through a text file
- `less`
    - better text reader
    - can do search, etc
- `nano` text editor


Redirection
-----------
- `>` write to file
- `>>` append to file
- `|` piping. example: `history | less`


Users
-----
- `sudo` super user do, substitute user do
    - `sudo -s` become super user (root) for a while
- `su` substitute user
    - `su - cindy`: make me cindy (may prompt for cindy's password)
    - `su cindy`: make me cindy but keep me in my home folder
    - leave name empty to log in as root
    - use `exit` to exit
- `user` shows current logged in users
- `id` check user information


Permissions
-----------
- In `ls -l`, we see something like `-rw-rw-r--` It indicates permissions of user, group, everyone, each has 3 letters. `r` for read, `w` for write, `x` for execute.

- `chmod` change mode
    - `chmod +x file` make file executable for everyone
    - `chmod 700 file` make file `rwx`able for me, none for everyone else
    - `r = 4, w = 2, x = 1`
    - for directories, setting `x` bite means visible.


Processes
---------
- `ctrl C` to kill the current process
- `watch command` execute a command every two seconds (linux only)
- `killall processname` find and kill all processes related to the process


Exit
----
- `exit`
- `ctrl D`
- `logout` (not recommended)


Keyboard
--------
- `ctrl L` clear screen
- `ctrl +/-` use shift to get the plus


bin: binary
basics binary files

sbin: system binary
commands for single user mode (safe mode)

boot: boot loaders

dev: where devices live

etc: system-wide configuration 

home: each user has their own home, 

lib, lib32, lib64: libraries

media, mnt: mount, other disks

opt: optional. Contains manually installed softwares

proc: process. Use the process id from the activity manager and go to that folder to access the files

root: root user home folder

run: things that run in memories. The folder is empty when shutdown

snap: self contained applications

srv: server data

sys: system 

tmp: temporary

usr: user applications

var: variables, log, crash information



