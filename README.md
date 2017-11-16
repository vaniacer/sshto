# sshto

Small bash script that builds a menu (via dialog) from your ~/.ssh/config.
Allow you to connect to your servers or run commands. Availible commands:

cmdlist=(
    #Command#  #Description#
    "ls  -la"  "List Files."
    "free -m"  "Show free ram."
    "df  -ih"  "Show free inodes."
    "df   -h"  "Show free disk space."
    "top -n1"  "Show summary system information."
    "       "  ""
    "add key"  "Add my ssh key to server."
    "add cls"  "Add my usefull aliases on server."
)

Your commands can be easialy addad to this list.

Hosts description neds to be added like this:

Host 192.168.0.1 #DESCRIPTION
Port 22
User admin

Horisontal menu delimiters (-------{ description }------) can be added like this:

#Host DUMMY #DESCRIPTION#
