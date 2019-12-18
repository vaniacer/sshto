# sshto

Small bash script that builds a menu (via dialog) from your ~/.ssh/config.</br>
![screeenshot](https://user-images.githubusercontent.com/18072680/60570513-69e99f00-9d7a-11e9-916d-48b74fa7585a.png)
</br>
Allows you to connect to your servers or run commands from menu. Available commands:</br>
![screeenshot](https://user-images.githubusercontent.com/18072680/71090302-c5d2a380-21b3-11ea-97c8-fc2906c7a0cd.png)
</br>
Your commands can be easily added to this list. Just edit this part of the script:</br>
<pre>
cmdlist_renew () { cmdlist=(
    #Command#  #Description#
    "Username" "Change ssh username to $GUEST"
    ''         ''
    "ls  -la"  "List Files"
    "free -h"  "Show free memory"
    "df  -ih"  "Show free inodes"
    "df   -h"  "Show free disk space"
    ''         ''
    "Info"     "Full system info"
    "Sshkey"   "Add my ssh key to $target"
    "Alias"    "Add my usefull aliases to $target"
    "Copy"     "Copy selected file or dir to $target"
    ''         ''
    "Dest"     "Change destination folder $DEST on $target"
    "Upload"   "Upload   file or folder from $PWD to $target:$DEST"
    "Download" "Download file or folder from $target:$DEST to $PWD"
    ''         ''
    "Local"    "Change local  port $LOCAL"
    "Remote"   "Change remote port $REMOTE"
    "Tunnel"   "Start portunneling from $target port $REMOTE to local port $LOCAL"
); }
</pre>
First collumn - command, second - description.</br>
Simple commands like 'ls -la' can be added as is.</br>
A list of commands or a complicated logic better add via function.</br>
Empty string is used as a delimiter.</br>
You can quick jump to the selected server via <i>CONNECT</i> button.</br>
When you done press ^D it'll bring you back to <i>sshto</i> commands section.</br>
</br>
Hosts description needs to be added like this:</br>
<pre>
Host server1 #DESCRIPTION
HostName 192.168.0.1
Port 22
User admin
</pre>
Start menu delimiters '---{ TEXT }---' can be added like this:</br>
<pre>
#Host DUMMY #TEXT#
</pre>
------
~/.ssh/config example:
<pre>
#Host DUMMY #Rybinsk#

Host rybserver1 #First server
HostName localhost

Host rybserver2 #Second server
HostName localhost

Host rybserver3 #Third server
HostName localhost

#Host DUMMY #Moscow#

Host moserver1 #First server
HostName localhost

Host moserver2 #Second server
HostName localhost

Host moserver3 #Third server
HostName localhost
</pre>
Script greps data from multiple config files via pattername <i>'config*'</i> in <i>~/.ssh</i> dir.<br>
So you can split config to multiple files and use them with <i>Include</i> directive, example:
<pre>
Include config_moscow
Include config_rybinsk
Include config*
</pre>

You can customize dialog colors by creating a config file:
<pre>
dialog --create-rc ~/.dialogrc
</pre>

<a href="https://asciinema.org/a/PQMuRvfmxlHUc4oZMN76LY2V4">See how it works at asciinema</a></br>

