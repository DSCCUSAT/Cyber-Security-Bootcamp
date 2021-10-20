**#Nmap or Network Mapping**

Nmap is a free open source tool, employed to discover hosts and services on a computer network by sending packets and analyzing the retrieved responses. Nmap offers some features for probing computer networks, including host discovery and service and operating system detection.
Nmap is used by hackers to scan network so that we can find live hosts or find targets to hack, we can also use this tool to find out more information about these targets a process called **enumeration**.
* Nmap can provide further information on targets including reverse DNS names, device types, and MAC addresses.
* Host Discovery - Identifying hosts on a network. For example, listing the hosts that respond to TCP and/or ICMP requests or have a particular port open.
* Port Scanning - Enumerating the open ports on target hosts.
* OS Detection - Determining the operating system and hardware charachteristics of a network devices.
* Version Detection - Interrogating network services on remote devices to determine the application name and version number.
* Scriptable interaction with the target support using the Nmap Scripting Engine (NSE).

**Usage of Nmap**
1. Auditing the security of a device or firewall by identifying the network connections which can be made to or through it.
2. Identifying open ports on a target host in preparation of auditing.
3. Network inventory, network mapping, and maintenance and asset management.
4. Auditing the security of a network by identifying new servers.
5. Finding and exploiting vulnerabilities in a network.
6. DNS queries and subdomain search.
7. Generating traffic to hosts on a network, response analysis and response time measurement.

**Nmap Commands**

Basic scanning Commands:


| Command | Description | Example |
| --- | --- | --- |
| nmap [target] | To scan a single target | nmap 192.168.0.1 |
| nmap [target1, target2,etc] | To Scan multiple targets | nmap 192.168.0.1 192.168.0.2 |
| nmap [range of ip addresses] | To scan a range of hosts | nmap 192.168.0.1-10 |
| nmap [ip address/cdir] | To scan entire subnet | nmap 192.168.0.1/24 |
| nmap -A [target] |  To perform an Aggressive Scan | nmap -A 192.168.0.1 |


Different scan types:


Nmap is able to use various different techniques to identify live hosts, open ports etc. The following are the most popular scan types.
| Command | Description | Example |
| --- | --- | --- |
| nmap -sP [target] | Perform a Ping Only Scan | nmap -sP 192.168.0.1 |
| nmap -PN [target] | Don’t ping the hosts, assume they are up. | nmap -PN 192.168.0.1 |
| nmap -sS [target] | TCP SYN Scan | nmap -sS 192.168.0.1 |
| nmap -sT [target] | TCP Connect Scan | nmap -sT 192.168.0.1 |
| nmap -sU [target] | UDP Scan | nmap -sU 192.168.0.1 |

There are some more scan types supported by nmap but the above listed are the most useful ones. Here is an overview of the most popular scan types:

* -sS: This sends only a TCP SYN packet and waits for a TCP ACK. If it receives an ACK on the specific probed port, it means the port exist on the machine. This is fast and pretty accurate.
* -sT: This creates a full TCP connection with the host (full TCP handshake). This is considered more accurate than SYN scan but slower and noisier.
* -sP: This is for fast checking which hosts reply to ICMP ping packets (useful if you are on the same subnet as the scanned range and want a fast result about how many live hosts are connected).


Identify Versions of Services and Operating systems:


Another important feature of NMAP is to give you a wealth of information about what versions of services and Operating Systems are running on the remote hosts.

| Command | Description | Example |
| --- | --- | --- |
| nmap -sV [target] | Version detection scan of open ports (services) | nmap -sV 10.1.1.1 |
| nmap -O [target] | Identify Operating System version | nmap -O 10.1.1.1 |
| nmap -A [target] | This combines OS detection, service version detection, script scanning and traceroute. | nmap -A 10.1.1.1 |


Scan timings:


These switches have to do with how fast or slow the scan will be performed.

| Command | Description |
| --- | --- |
| nmap -T0 10.1.1.1 | Slowest scan (to avoid IDS) |
| nmap -T1 10.1.1.1 | Sneaky (to avoid IDS) |
| nmap -T2 10.1.1.1 | Polite (10 times slower than T3) |
| nmap -T3 10.1.1.1 | Default scan timer (normal) |
| nmap -T4 10.1.1.1 | Aggressive (fast and fairly accurate) |
| nmap -T5 10.1.1.1 | Very Aggressive (might miss open ports) |


Output types :


For each scan we recommend outputting the results in a file for further evaluation later on. 
Nmap supports 3 main output formats as below:

| Command | Description |
| --- | --- |
| nmap -oN [filename] [IP hosts] | Normal text format |
| nmap -oG [filename] [IP hosts] | Grepable file (useful to search inside file) |
| nmap -oX [filename] [IP hosts] | XML File |
| nmap -oA [filename] [IP hosts] | Output in all 3 formats supported   |


NSE Scripts:


There are hundreds of included scripts that you can use with nmap to scan for all sorts of vulnerabilities, brute force login to services, check for well-known weaknesses on services etc. 
 
| Command | Description |
| --- | --- |
| nmap --script="name of script" 10.1.1.0/24 | Run the specified script towards the targets. |
| nmap --script="name of script" --script-args="argument=arg" 10.1.1.0/24 | Run the script with the specified arguments |
| nmap --script-updatedb | Update script database |


Other useful Commands:


| Command | Description |
| --- | --- |
| nmap -6 [IP hosts] | Scan IPv6 hosts |
| nmap --proxies url1,url2 | Run the scan through proxies |
| nmap --open | Only show open ports |
| nmap -V | Show currently installed version |
| nmap -S [IP address] | spoof source IP |
| nmap -h | Getting help |
| man nmap | Display manual |












