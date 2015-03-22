# CISSP guide #
This is my learning guide for preparation of the CISSP exam. It covers the essential information on all relevant domains. I aim to keep it as brief as possible leaving out most of the basics, so some previous knowledeg on IT security is mandatory.

## Access Control ##
Subjects ability to communicate with an object is allowed/denied based on security requirements. It is needed to proetct information, computers, networks and all other infrastructure (buildings).

- CIA triad: confidentiality, integrity, availability
- identify relation between resources (which entities need to be protected) and users (identify who needs access), set access control levels
- least privilege/need to know principle: give minimum access needed only for the tasks they need to perform, default to no access
- separation of duties: distribute tasks/rights/privileges between users, deter fraud, split knowledge
- three authentication factors:
	- knowledge factor: something a person knows (e.g. PIN)
	- ownership factor: something a person possesses (e.g. smart card)
	- characteristic factor: something a person is (e.g. fingerprint)
- password types:
	- standard/simple: single words, upper/lowercase
	- numeric: just numbers
	- combination: mix of dictionary words
	- static: same for each login, insecure
	- complex: upper/lowercase, numbers, special characters
	- passphrase: long phrase
	- cognitive: verify identity via asking series of questions
	- one-time: initial login, discraded after use
	- graphical: CAPTCHA
- manage passwords by limiting life (no. of days), history (prevent re-use), period (session time without activity), complexity, length
- ownership factors: synchronous/asynchronous token (handheld device), memory card (swipe card with auth info, data not protected), smart card (ICCs with a chip, usually protected with PIN)
- physiological systems/biometrics:
	- fingerprint, finger scan (less characteristic than fingerprint)
	- hand geometry, hand topography
	- palm or hand scans
	- facial/retina scans (retina blood vassel pattern)
	- iris scans
	- vascular scans (pattern of veins in hand/face, risk of false rejections)
- behavioral characteristics:
	- signature dynamics (strike speed, pen pressure, acceleration)
	- keystroke dynamics (typing pattern, flight/dwell time)
	- voice pattern/print (sound pattern)
- biometric considerations:
	- enrollment time: time to obtain the sample (# of repetitions)
	- feature extraction: approach to obtain information from sample
	- accuracy
	- throughput rate (shouldn't take longer than 5-10 seconds)
	- acceptability (regarding users)
	- FRR: false rejection rate or Type 1 error
	- FAR: false acceptance rate or Type 2 error (more dangerous)
	- CER: crossover error rate (percentage), when FRR=FAR, most important metric
- most effective: iris scan, retina scan, fingerprint
- highest acceptance: voice pattern, keystrok pattern, signature dynamics
- Directory Services: X.500 (DAP), LDAP, X.400 (generally replaced by SMTP)
- SSO: enter credentials once, access all resources throught the network
- simple to administrate, stronge passwords enforceable, faster access to resources, efficient login, only one password to remember
- single vulnerability affects all systems (esp. hackers)
- Kerberos: SSO system with symmeric crypto, default in Windows Server/Linux/MacOS, central Key Distribution Center is repo for all users/keys
- KDC is single point of failure, needs to scale, session keys need to be protected, Kerberos traffic need to be encrypted, all systems need synchronized clocks, susceptile to password-guessing attacks
- SESAME extends Kerberos, also uses asymmetric crypto and a trusted auth server at each host
- federated identity: portable identity across businesses/domains
- cross-certification: each organization certifies all other organizations as trusted (meet standards), due dilligence
- trusted 3rd üarty/bridge model: each organization subscribes to standards of 3rd party
- security domain: set of resources available to subjects over a networks
- auditing monitors user events and also network/system/application events and keystroke activity
- guidelines:
	- audit log mgmt plan needed (control log size, backup process, review plan)
	- deletion of audit log should be two-man control (two admins), otherwise impossible
	- high-privilege accounts need to be monitored (root/admins)
	- audit trail monitors transactions (who, when, whre and success/failure)
- vulnerability assessment: identify areas of weakness in network, asset priorization
	- personal: review standard practices/procedures
	- physical: facility/perimeter protection
	- system/network: review system, network and network topology
- penetration testing simulates an attack to identify threads
- steps:
	- document info on target system/device
	- gather information on attack methods (e.g. via port scan)
	- identify known vulnerabilities
	- execute attacks to gain privileged access
	- document results, report findings
- strategies:
	- blind test: limited knowledge of system, organization knows that test will happen
	- double-blind test: same, but organizations does not know about test
	- target test: maximum info about network and test on both sides
- knowledge levels:
	- zero: attacker knows nothing on organization's network (closed/black box testing)
	- partial: public knowledge on network
	- full: all details are provided
- access control (AC) categories:
	- compensative: mitigate risks, substitute for primary AC (e.g. two keys for two people)
	- corrective: reduce effect of attack, restore entity (e.g. server images, fire extinguishers)
	- detective: detect attack, e.g. IDS, logs, job rotation
	- deterrent: deter/dicourage attacker e.g. authentication,fences, lighting, NDA
	- directive: acceptable practices within an organization, AUP (acceptable use policy)
	- preventive: locks, badges, encryption, guards, training, ...
	- recovery: restore resources, e.g. backups, offsite facilities
- AC types:
	- administrative (mgmt) controls: soft controls, e.g. supervision, personnel controls, security awareness training
	- logical (technical) controls: restrict access to SW/HW components, e.g. firewalls, passwords, IDS
	- physical controls: protect facilities, e.g. badges, guards, dogs, cabling
- AC models:
	- discretionary AC: owner specifies subjects to access the resource (need-to-know)
	- mandatory AC: auth is based on security labels (only admins may modify), more secure than DAC
	- role-based AC: each subject has 1-n roles, not as secure as DAC+MAC
	- rule-based AC: global rules for all users, uses profiles to control access, often used by routers/firewalls
	- content dependent AC: access determined by data contained within the object
	- context dependent AC: access based on subject/object attributes and environment (e.g. login only at specific time of day)
	- ACM: capabilities table that lists subjects/objects and applicable subject actions
	- ACL: objects column from ACM
- AC threads:
	- passwords: dictionary or brute force
	- social engineering: phishing, shoulder surfing, identity theft
	- DoS/DDoS: flood a device with requests to degrade performance
	- buffer overflow: code injection, avoided by inout validation and regular updates
	- mobile code: SW transmitted across network (JS, applets, ActiveX)
	- malicious software: virus, worm, trojan horse, spyware
	- spoofing: communication from attacker appears to come from trusted source, via IP/link spoofing, man-in-the-middle
	- sniffing/eavesdropping: collect all trabsmitted data from medium
	- emanating: emit electromagnetic signals (shielding)
	- backdoor/trapdoor: unlimited access implemented on purpose

## Telecommunications and Network Security ##
Protect data at rest (storage) and in transit (network). Each layer adds new information but makes no modification to the data received from above.

- OSI model: protocol set, breaks communication process into layers
	- Application (7): receives data from app and provides services (HTTP/DNS/FTP)
	- Presentation (6): standardize formatting of info (MIME/XDR)
	- Session (5): enable communication between service/app on source with service/app on destination (NetBIOS/RTP/TLS/SSL)
	- Transport (4): determine transport protocol and port (TCP/UDP)
	- Network (3): route the packet, e.g. via source/destination address (IP/ARP/ICMP)
	- Data Link (2): determine physical destination address (ATM/SLIP/802.2)
	- Physical (1): turn info into bits and send it (DSL/USB/Bluetooth)
- TCP/IP operates on multiple levels of OSI (conceptual model)
- has Application (7,6,5), Transport (4), Internet (3) and Network Access (2,1) layers
- Three-way-handshake: Establish connection state before the actual data transfer 
	1. send packet with SYN flag to create connection
	2. host acknowledges by sending packet with both SYN and ACK
	3. sender completes process by sending packet with ACK flag
- guerantees delivery (resend on failure), sequencing (packets may not arrive in order, therefore sequence number), flow control (receiver may send ACK packets back to trigger slowdown)
- Encapsulation: each layer adds information to header, devices only read the layers they're concerned about
- typical applications, protocols and ports:
	- Telnet: TCP/UDP, 23
	- SMTP: UDP, 25
	- HTTP: TCP, 80
	- SNMP: TCP/UDP, 161/162
	- FTP: TCP/UDP, 20/21
	- POP3: TCP/UDP, 110
	- DNS: TCP/UDP, 53
	- DHCP: UDP, 67/68
	- SSH: TCP, 22
	- LDAP: TCP/UDP, 389
- IP classes represent range of addresses, only A-C used for individual NW devices
	- class A: 0.0.0.0-127.255.255.255, Mask 255.0.0.0
	- class B: 128.0.0.0-191.255.255.255, Mask 255.255.0.0
	- class C: 192.0.0.0-223.255.255.255, Mask 255.255.255.0
	- class D: 224.0.0.0-239.255.255.255, used for multicasting
	- class E: 240.0.0.0-255.255.255.255, reserved for research
- address classes
	- class A: 10.0.0.0-10.255.255.255
	- class B: 172.16.0.0-172.31.255.255
	- class C: 192.168.0.0-192.168.255.255
- network twisted pair cable categories:
	- Cat3: max. 10 Mbps
	- Cat4: max. 16 Mbps
	- Cat5/Cat5e: max. 100 Mbps
	- Cat6: max. 1 Gbps
	- Cat6e: max. 10 Gbps 
- Ethernet implementations:
	- number indicated speed in Mbps, 2/5 indicate Coaxial, T indicated Twisted Pair, X indicated fiber
	- 10Base5: 10 Mbps Coaxial / 100BaseT: 100 Mbps Twisted Pair / 10GBaseT: 10 Gbps Twisted Pair
- CSMA/CD: 802.3 implements Carrier Sense Multiple Access Collision Detection:
	1. Before transmitting, check wire for existing traffic (CS)
	2. when clear, transmit and continue CS
	3. when collision, jam signal for all other devices to NOT transmit, increment retransmission counter
	4. calc random time (random back-off) to wait before retransmit
	5. transmit, repeat
- CSMA/CA: for 802.11 wireless collision can't be detected, so each station must acknowledge each frame has been transmitted
	1. Station A performs CS and continues monitoring for collisions
	2. if transmitting, station A decrements internal countdown (back-off), when it expires it is allowed to send, each station has individual timer
	3. if station A performs CS there is no traffic and timer = 0 it sends the frame
	4. frame goes to AP
	5. AP sends ACK to station A, all other stations are silent
	6. cache queue holds frame and relays it to station B
	7. station B sends ACK to AP, all other stations are silent
- cloud computing: make resources available in web-based data center
	- IaaS: vendor provides hardware/data center, company installs OS/app systems
	- PaaS: vendor also provides software
	- SaaS: vendor provides entire solution (also application)
- WAN technologies differ in capüacity, cost and availability
- T carriers are dedicated/private lines for customer
	- Fractional: 1/24 of T1s, 1 channel, 0.064 Mbps
	- T1: 1 T1, 24 channels, 1544 Mbps
	- T3: 28 T1s, 672 channels, 44736 Mbps
- E carriers are used in Europe, also three levels (E0 64 Kbps, E1 2048 Mbps, E3 8448 Mbps)
- OC lines (SONET) are fiber-based links (OC-9 466.56 Mbps, OC-19 933.12 Mbps, OC-48 2488 Gbps, OC-3072 160 Gbps)
- WLAN standard has been amended a few timesto add features/functionality
- 802.11a: uses OFDM, 5GHz frequency band, up to 54 Mbps
- WPA secures WLAN, Personal (preconfigured password) and Enterprise (requires auth server) profiles
	- WPA Personal: Preshared key for AC, TKIP encryption, Michael Integrity
	- WPA Enterprise: 802.1X for AC, TKIP encryption, Michael Integrity
	- WPA2 Personal: Preshared key for AC, CCMP/AES encryption, CCMP integrity
	- WPA2 Enterprise: 802.1X for AC, CCMP/AES encryption, CCMP integrity