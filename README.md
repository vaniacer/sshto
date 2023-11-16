# sshto

Small bash script that builds a menu (via dialog) from your ~/.ssh/config.</br>
![screeenshot](https://user-images.githubusercontent.com/18072680/60570513-69e99f00-9d7a-11e9-916d-48b74fa7585a.png)
</br>
Allows you to connect to your servers or run commands from menu. Available commands:</br>
![cmds](https://user-images.githubusercontent.com/18072680/211161226-1c5eec5a-634b-4902-90cd-5947dd95083e.png)
</br>
Your commands can be easily added to this list. Just edit this part of the script:
<pre>
cmdlist=(
    #Command#    #Description#
    "${slct[@]}" #De/Select command
    "Username"   "Change ssh username to \Z1$GUEST\Z0"
    "Add tab"    "Add terminal tab with \Z1sshto\Z0 for \Z4$target\Z0"
    "Ssh tab"    "Add terminal tab with \Z1ssh\Z0 to \Z4$target\Z0"
    ''           ''
    "ls -lah"    "List Files"
    "free -h"    "Show free memory"
    "df  -ih"    "Show free inodes"
    "df   -h"    "Show free disk space"
    "Custom"     "Run custom command on \Z4$target\Z0"
    "Script"     "Run custom script on \Z4$target\Z0"
    ''           ''
    'Yes'        "Say 'yes' to SSH"
    "Info"       "Full system info"
    'Fix_id'     "Update host in known_hosts"
    "Sshkey"     "Add my ssh key to \Z4$target\Z0"
    "Alias"      "Add my useful aliases to \Z4$target\Z0"
    "Copy"       "Copy selected file or dir to \Z4$target\Z0"
    ''           ''
    "Home"       "Change home folder \Z4$home\Z0 on local server"
    "Dest"       "Change destination folder \Z4$DEST\Z0 on \Z4$target\Z0"
    "Upload"     "Upload file or folder from \Z4$home\Z0 to \Z4$target:${DEST}\Z0"
    "Download"   "Download file or folder from \Z4$target:${DEST}\Z0 to \Z4$home\Z0"
    "Mount"      "Mount remote folder \Z4$target:$DEST\Z0 to \Z4$home\Z0"
    "Unmount"    "Unmount remote folder \Z4$target:$DEST\Z0 from \Z4$home\Z0"
    ''           ''
    "Local"      "Change local  port \Z1$LOCAL\Z0"
    "Remote"     "Change remote port \Z1$REMOTE\Z0"
    "Tunnel"     "Start portunneling from \Z4$target:$REMOTE\Z0 to \Z4localhost:$LOCAL\Z0"
    ''           ''
    "ShowConf"   "Show ssh config for this host"
    "EditConf"   "Edit ssh config for this host"
)
</pre>
First collumn - command, second - description.</br>
Simple commands like `ls -la` could be added as is.</br>
A list of commands or a complicated logic should be added via function.</br>
Empty values(`''`) could be used as a delimiter.</br>
You can quick jump to the selected server via <i>CONNECT</i> button.</br>
To close <i>ssh</i> session press <kbd>CTRL</kbd>+<kbd>D</kbd> or run `exit` command, it'll bring you back to <i>sshto</i> commands section.</br>
</br>
Optional hosts description could be added like this:</br>
<pre>
Host server1 #Description, it could be more than one word
HostName 192.168.0.1
Port 22
User admin
</pre>
Optional start menu delimiters '---{ Group Name }---' could be added like this:</br>
<pre>
#Host DUMMY #Group Name#
</pre>
If you are unhappy with this 'DUMMY' group name template, or you actually have a host named 'dummy',
you can change this template by ajusting this variable `group_id=dummy`. </br>
All these additions won't break your *ssh configs* coz they are considered as comments.  

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
Script greps data from multiple config files via pattername `config*` in `~/.ssh` dir.</br>
So you can split config to multiple files and use them with <i>Include</i> directive, example:
<pre>
Include config_moscow
Include config_rybinsk
Include config*
</pre>
All preset variables and functions could be tweaked via `~/.sshtorc` config file:
<pre>
echo "REMOTE=9000  # Remote port for tunneling." >> ~/.sshtorc
</pre>

You can customize dialog itself a bit by creating and editing its config file:
<pre>
dialog --create-rc ~/.dialogrc
nano ~/.dialogrc
</pre>

If you don't have dialog and don't want(or can't) to install it, there is a dialog-less version of sshto
in my new project [bashui](https://github.com/vaniacer/bashui) here is how it looks:
![bashui-hosts](https://habrastorage.org/getpro/habr/upload_files/024/c74/38e/024c7438e6429f5e37a8a71d98bf7edb.png)

![bashui-commands](https://habrastorage.org/getpro/habr/upload_files/495/2cc/526/4952cc52616db16acfa7b2fd9e8d366f.png)

Try it [bashui-sshto](https://github.com/vaniacer/bashui/blob/master/demo_sshto)!

# How to install
Clone\download this project, go to it's folder and run:
<pre>sudo cp sshto /usr/bin/

#and to unistall
sudo rm /usr/bin/sshto
</pre>

<a href="https://asciinema.org/a/PQMuRvfmxlHUc4oZMN76LY2V4">See how it works at asciinema</a></br>

<a href="http://www.youtube.com/watch?feature=player_embedded&v=FhnsVH8t96Q
" target="_blank"><img src="http://img.youtube.com/vi/FhnsVH8t96Q/0.jpg" 
alt="ssh config guide" width="240" height="180" border="10"/></a></br>
Tom Lawrens video guide about ssh config and sshto

[![paypal](https://img.shields.io/badge/Donate-PayPal-green.svg)](https://paypal.me/sshto?locale.x=en_US) <sup>Feel free to support the project!)</sup></br>

~~Twitter~~ DOGE: D7qJBRU3UpXES9EwtvE8YZSNAVgFEmz3py</br>
![dodge](https://user-images.githubusercontent.com/18072680/229992296-f415eadb-645b-4229-81c7-e269485c635d.png)

BTC: 1LxRxsyXP389YW3Ezw9YzNetE5VYj1RaJf</br>
![btc](https://user-images.githubusercontent.com/18072680/106382955-f2f00e80-63d3-11eb-9316-b6653225820c.png)

BCH: qqnssal30x6acrga6zt4pd4q2s2t8um3cyqvd37qs7</br>
![bch](https://user-images.githubusercontent.com/18072680/108552897-fd326800-7302-11eb-8ae7-97eb0cc81d5e.png)

ETH: 0xd7e17A37DD936B211790ba70Aa985448277030E8</br>
![eth](https://user-images.githubusercontent.com/18072680/106382951-f2577800-63d3-11eb-8c01-f7ade514fb58.png)

XMR: 484z9YpiD4VBd4BfsaG7jKGYGuJ84tYJyCJBX4ZnAPqQXsUWgTY14TKRH3JLosFSAsKsv75nyt9yWPkFMUJhryxi7zccHNB</br>
![mon](https://user-images.githubusercontent.com/18072680/106383275-15832700-63d6-11eb-87d5-8b9f4ba08c40.png)

LTC: LRVPYR7dvRVdNET23gg3fvTwDM9hotQkZw</br>
![ltc](https://user-images.githubusercontent.com/18072680/106383361-7a3e8180-63d6-11eb-9239-48b6d80c3c4b.png)

DASH: Xtz7P6GasicE9yS8zXkH3PH2qAF2qWJADG</br>
![dash](https://user-images.githubusercontent.com/18072680/108553387-a11c1380-7303-11eb-9560-81f0deec2fbc.png)

ZEC: t1ZDgHci8yDVkoGvUFG7QtxUNRuzsF1Qtse</br>
![zec](https://user-images.githubusercontent.com/18072680/108553595-f7895200-7303-11eb-9ca8-17d1c81df7eb.png)

MKR: 0xd7e17A37DD936B211790ba70Aa985448277030E8</br>
![mkr](https://user-images.githubusercontent.com/18072680/108553822-4505bf00-7304-11eb-9db9-0833141e36c9.png)
