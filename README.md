# Network-Mapper

Network Mapper commonly known as Nmap is one of the best tool to gather network information about a target or even about a whole subnet. Nmap is a information gathering tool which can gather nearly every information about the target. It is mostly used to gather information about open ports and the services on them on the target. It is a CLI based tool which come pre-packaged with most of the Linux distribution such as Kali Linux, parrot OS and also ubuntu. Nmap is written in Lua language which is very easy to learn and understand. Nmap also comes with many scripts to gather extensive information related to the configuration of a particular protocol on the target.

# Features

1. It has a GUI based version called ZenMap which has a beginner friendly interface.
2. It has easy to use commands and the syntax is very easy.
3. It can easily show the results in the way we want to see.
4. It has verbose option which can help us to monitor the status of the scan.
5. The large database of Nmap help us to easily fingerprint information not only about Windows, Linux, Mac but also about various IOT devices.
6. We can easily write scripts and customise existing Nmap scripts to works it in way we want.
7. The larger database of scripts help us to deeply enumerate the target related to a particular point.
8. Along with network it can also be used to gather information related to HTTP(web).
9. It can also be used to deted Eternal Blue , HeartBleed and many other CVE's target is vulnerable to.
10. The time support of Nmap help us to increase or decrease the speed of enumeration according to the version and capacity of the target server.

# Basic Syntax:

    nmap  <filter/s> (IP/subnet)

- Note: The Flags used below are to be putted between in <filter> tag while doing scanning.
  
# Basic usage of Nmap

#  1. To gather information about open ports
  
-  -p = Used to scan ports we specify
-  -p 22 = Only scan port 22
-  -p- = Scan all the ports (65535)
-  -p-23 = Scan from port 1 to 23
-  -F = Scan only well known port
-  -sS = Do a SYN scan(don't complete handshake)
-  -sT = Only scan TCP ports
-  -sU = Only scan UDP ports
-  -O = Try to detect OS of the target
-  -Pn = Do not ping the target(Mostly used for windows target)
-  -A = Perform a Aggressive scan
-  -sV = Try to detect service version of open ports

#  2. Getting desired information
  
- -oA result = Creatae 3 output file of the scan. result.txt, result.xml, result.gnmap
- -oA result.xml = Only create a XML file
- -v = Verbose output
- -vv = Double verbose output
- -vvv = Triple verbose output
  
# 3. Firewall detection and Bypassing
  
- -sA = ACK probing, check if firewall is present
- -D 12.32.23.43 = Perform scan with the specific IP as source. Used to hide our IP. Technique is called as Decoy.
- -D RND:4 = Perform scan with any 4 random IP as source.
- -f = Break the packets in fragments to bypass firewall.Technique is called as fragmentation.
- --mtu 24 = Make each packet of 24 bytes to evade the firewall.
 
 ## If these techniques do not work you may need to add --send-eth flag after the filter.
For example: nmap -sT -D 12.33.22.64 --send-eth (target IP/subnet)

   ## Above technique may not work on modern firewall due to their extensive functionally of reassembling packets on destination : (
  
#  4. Time Performance

- -T0 = Paranoid 
- -T1 = Sneaky
- -T2 = Polite
- -T3 = Normal
- -T4 = Aggressive
- -T5 = Extreme Aggressive

## The scans are listed on their increasing speed. We sometimes may have to use -T0 or -T1 when we are dealing with old machine and server as if they receive large amounts of packets in less time they may crash.

## You may use T5 flag when dealing with modern servers and machines as they can handle large amount of packet at same time and they will not crash and we will also get our results faster.


## These were some of the basic filters which you can use to scan your target and see the desired results you want .
  
- Now we will move to some advance Nmap filters and to the NSE.
  
# Nmap Scripting Engine (NSE)
  
  The NSE has a huge database to scripts which can be used to enumerate the target.
NSE has scripts to enumerate SSH, FTP, HTTP, SQL, SMB, DOMAIN and many other CVE and Services and Vulnerability.

- The Nmap scripts are stored in the
    
       /usr/share/nmap/scripts/ directory.

- Syntax: --script=<name of scripts>
  
## Some of the most common used scripts are:
  
1. ftp-anon.nse = To see anon login is enabled
2. ssh-brute.nse = brute force SSH
3. ftp-brute.nse = brute force FTP
4. smb-enum.nse = enumerate SMB
5. mysql-enum.nse = enumerate MySQL
  
- There are many other scripts and it is impossible to remember the name of all the scripts : )

# Advance Options: 
  
  1. --min-parlellism 20 = Scan minimum 20 ports parlelly
  
  2. --max-parlellism 20 = Scan maximum 20 ports parlelly
  
  3. --min-hostgroups 34 = Scan minimum 34 hosts parlelly; when scanning whole subnet
  
  4. --max-hostgroups 34 = Scan maximum 34 hosts parlelly; when scanning whole subnet
  
  5. --scan-delay 10 = Wait for 10 second after scanning each host;when scanning whole subnet
  
  6. --host-timeout 20 = Skip the host if it don't reapond to the scan in 20 seconds;when scanning whole subnet
  
  7. --min-rate 20 = send minimum 20 packets in a second
  
  8. --max-rate 20 = send maximum 20 packets in a second
  
- Note: Nmap is a very vast tool and it is impossible to tell you whole Nmap as it is very difficult. So I would like to end here.
The above blog gives you a detailed overview of Nmap and I hope that now you will be able to use Nmap with your requirements and would be able to take most of out of it.
  
