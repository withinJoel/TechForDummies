Note: These commands are with respect to Linux Ubuntu OS.
## OS
* `lsb_release -a` - To know the version of your ubuntu OS.
* To Update your system to the latest release
```
$ sudo apt install update-manager-core
$ sudo do-release-upgrade
```
To know more visit: `https://jumpcloud.com/blog/how-to-upgrade-ubuntu-20-04-to-ubuntu-22-04`

## Basic
* `sudo --help` - If you need help.
* `ls` - To list all the files in that directory.
* `cd` - To change the directory.
* `uname` - To get the basic OS details.
* `whoami` - To know the user.
* `man` - to see the manual for that command. example: `man echo`
* `rm -r <foldername>` - To delete the folder
* `rm <filename>` - To remove a file.
* `grep -r "<what you want to search>"` - This command allows you to search for a specific keyword within the current directory. For example, if you want to find the name `Joel`, you can use this command to look for that keyword across all the files in the directory.
* `sudo grep -r "keyword" /` - For global search.
* `sudo rm -rf Testing` - To delete a file or a folder here `testing` is the folder name.
* `sudo lsof -c java` - To find something by using its name.
* `sudo touch hello.txt` - To create a new file.
* `sudo mkdir hello` - To create a new directory.
* `tree` - To show all the files with respect to their folders. (You should install this first `sudo apt install tree`)
* `pwd` - To print the current directory.
* `echo hola` - To print something on the terminal.
* `less <filename>` - To open a file to only read its contents alone with no editing (To close just enter `q`)
## Terminal
* `history` - To get the history of all your commands that you typed in the terminal.
* `history -c` - To clear your terminal history.
* `clear` - To clear the terminal.
* `quit` - To close the terminal.

## Application
* To install apps for .gz extenstions
    * Extract it
    * Go to the bin folder
    * Open that folder in the terminal and type `sh filename.sh` (There will be only be one file that ends with .sh)
* `sudo apt install <app name>` - To install an application.
* `apache2 -version` - To get the application version.
* `sudo systemctl start apache2` - To start an application.
* `sudo systemctl status apache2` - To see the application status.
* `sudo systemctl stop apache2` - To stop an application.
* `which apache2` - Tells the installed path of the application.

## Networking
* `ifconfig` or `ip address show` or `ip addr show` - To know your network details.
* `sudo scp registration-oneApp.zip hema@10.0.102.33:/home/hema/Desktop/` - To transfer a file/folder from one machine to another (should be connected over a network)(Recommended: Wired network) (Here `Hema` is the username and `10.0.102.33` is the ip address and `home/hema/Desktop` is the path in which the file should be pasted to. (Install: `sudo apt install openssh-server` Required)
