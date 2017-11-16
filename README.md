# sshto

Small bash script that builds a menu (via dialog) from your ~/.ssh/config.</br>
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
Your commands can be easialy addad to this list.</br>
</br>
Hosts description neds to be added like this:</br>
<pre>
Host 192.168.0.1 #DESCRIPTION
Port 22
User admin
</pre>
Horisontal menu delimiters (-------{ description }------) can be added like this:</br>
<pre>
#Host DUMMY #DESCRIPTION#
</pre>
