# sshto

Small bash script that builds a menu (via dialog) from your ~/.ssh/config.</br>
![screeenshot](https://user-images.githubusercontent.com/18072680/32890161-ab6ad284-cade-11e7-92c7-f6901cfd0905.png)
Allow you to connect to your servers or run commands. Availible commands:</br>
<pre>
cmdlist=(
    #Command#  #Description#
    "ls  -la"  "List Files."
    "free -m"  "Show free ram."
    "df  -ih"  "Show free inodes."
    "df   -h"  "Show free disk space."
    "top -n1"  "Show summary system information."
    "       "  ""
    "add key"  "Add my ssh key to server."</br>
    "add cls"  "Add my usefull aliases on server."
)
</pre>
![screeenshot](https://user-images.githubusercontent.com/18072680/32890160-ab43f696-cade-11e7-8c80-c51089354e37.png)
Your commands can be easialy added to this list.</br>
First collumn - command, second - description.</br>
</br>
Hosts description neds to be added like this:</br>
<pre>
Host server1 #DESCRIPTION
HostName 192.168.0.1
Port 22
User admin
</pre>
Horisontal menu delimiters (-------{ description }------) can be added like this:</br>
<pre>
#Host DUMMY #DESCRIPTION#
</pre>
