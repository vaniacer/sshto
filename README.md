# sshto

Small bash script that builds a menu (via dialog) from your ~/.ssh/config.</br>
Allow you to connect to your servers or run commands. Availible commands:</br>
</br>
cmdlist=(</br>
    #Command#  #Description#</br>
    "ls  -la"  "List Files."</br>
    "free -m"  "Show free ram."</br>
    "df  -ih"  "Show free inodes."</br>
    "df   -h"  "Show free disk space."</br>
    "top -n1"  "Show summary system information."</br>
    "       "  ""</br>
    "add key"  "Add my ssh key to server."</br>
    "add cls"  "Add my usefull aliases on server."</br>
)</br>
</br>
Your commands can be easialy addad to this list.</br>
</br>
Hosts description neds to be added like this:</br>
</br>
Host 192.168.0.1 #DESCRIPTION</br>
Port 22</br>
User admin</br>
</br>
Horisontal menu delimiters (-------{ description }------) can be added like this:</br>
</br>
#Host DUMMY #DESCRIPTION#
