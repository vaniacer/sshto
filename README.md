# sshto

Small bash script that builds a menu (via dialog) from your ~/.ssh/config.</br>
![screeenshot](https://user-images.githubusercontent.com/18072680/32890161-ab6ad284-cade-11e7-92c7-f6901cfd0905.png)
</br>
Allows you to connect to your servers or run commands from menu. Available commands:</br>
<pre>
cmdlist=(
    #Command#  #Description#
    "ls  -la"  "List Files."
    "free -m"  "Show free ram."
    "df  -ih"  "Show free inodes."
    "df   -h"  "Show free disk space."
    "top -n1"  "Show summary system information."
    ""         ""
    "info"     "Full system info."
    "copy"     "Copy selected file or dir."
    "sshkey"   "Add my ssh key to this server."
    "alias"    "Add my usefull aliases to this server."
)
</pre>
![screeenshot](https://user-images.githubusercontent.com/18072680/50470807-2aa15680-09c3-11e9-8830-1ababea75860.png)
</br>
Your commands can be easily added to this list.</br>
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

Include directive also supported. But included config files have to be in <i>~/.ssh</i> dir, and start from <i>'config'</i>, example:
<pre>
Include config_*
</pre>
