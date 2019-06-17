# sshto

Small bash script that builds a menu (via dialog) from your ~/.ssh/config.</br>
![screeenshot](https://user-images.githubusercontent.com/18072680/50471000-ea8ea380-09c3-11e9-9217-d34a7300ad85.png)
</br>
Allows you to connect to your servers or run commands from menu. Available commands:</br>
![screeenshot](https://user-images.githubusercontent.com/18072680/59601820-d70bfc00-910d-11e9-8e6d-d36622cf8335.png)
</br>
Your commands can be easily added to this list. Just edit this part of the script:</br>
<pre>
cmdlist_renew () { cmdlist=(
    #Command#  #Description#
    "ls  -la"  "List Files."
    "free -h"  "Show free memory."
    "df  -ih"  "Show free inodes."
    "df   -h"  "Show free disk space."
    ""         ""
    "Info"     "Full system info."
    "Copy"     "Copy selected file or dir."
    "Sshkey"   "Add my ssh key to this server."
    "Alias"    "Add my usefull aliases to this server."
    ""         ""
    "Local"    "Change local  port $LOCAL"
    "Remote"   "Change remote port $REMOTE"
    "Tunnel"   "Start portunneling from $target's port $REMOTE to local port $LOCAL"
); }
</pre>
First collumn - command, second - description.</br>
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

Host server1 #First server
HostName 192.168.0.1
Port 22
User admin

Host server2 #Second server
HostName 192.168.0.2
Port 22
User user

Host server3 #Third server
HostName 192.168.0.3
Port 22
User loser

#Host DUMMY #Moscow#

Host server1 #First server
HostName 192.168.1.1
Port 22
User admin

Host server2 #Second server
HostName 192.168.1.2
Port 22
User user

Host server3 #Third server
HostName 192.168.1.3
Port 22
User loser
</pre>
Script greps data from multiple config files via pattername <i>'config*'</i> in <i>~/.ssh</i> dir.<br>
So you can split config to multiple files and use them with <i>Include</i> directive, example:
<pre>
Include config_moscow
Include config_rybinsk
Include config*
</pre>
