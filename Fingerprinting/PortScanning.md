# Port Scanning

## Types of TCP Scan

### TCP Connect Scan
- nmap option: `-sT`
- States:
    - open: get SYN-ACK
    - closed: get RST
    - filtered: nothing

### TCP SYN Scan - Half Open Scan
- nmap option: `-sS`
- States:
    - open: get SYN-ACK
    - closed: get RST
    - filtered: nothing
- Example of use: `nmap -sS -p 22,80,443 192.168.1.10`
    - `-p 22,80,443`: scan those ports
    - `192.168.1.10`: target

### TCP FIN/Null/XMAS Tree Scan
- nmap option:
    - FIN: `-sF`
    - Null: `-sN`
    - XMAS: `-sX`
- States:
    - Open|Filtered: no response
    - Close: RST

### TCP Ack Scan
- nmap option: `-sA`
- States: 
    - Filtered: no response
    - Unfiltered: RST

### UDP Scan
- nmap option: `-sU`
- States:
    - Open: UDP + Port Data
    - Open|Filtered: no response
    - Closed: ICMP: port unreachable
    - Filtered

### IDLE Scan
- nmap option: `-Pn -SI <IP_zombie> <IP_victim>`
- States:
    - Open: ID diff = 2
    - Close|Filtered: ID diff = 1
    
## NMAP useful options
- `-sP`: Ping scan (host Discovery only)
- `-sn`: ping sweep
- `-Pn`: do not send ping previous to the scanning
- `-s <type of scan>`: specify the type of scan
- `-p <ports>`: specify the ports to be scanned
- `-sV`: try to obtain the version of the services running in open ports
    - Use banner grabbing, heuristics and protocol specificities
- `-O`: operating system detection
    - TTL, TCP Window size, heuristics based on answers to protocol
misbehaviour
- `-A`: aggressive scan. Complete análisis
- `-T<0-5>`: adjust scan speed (0: slower and more stealthy).