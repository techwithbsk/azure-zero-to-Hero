MENU ☰


BASIC NETWORKING


Networking Basics
•	Goals:
•	In the Azure Cloud (Or any cloud), we are responsible for virtual network and Physical network with in Azure Hardware is managed by Microsoft
•	Create Virtual Network for your architecture so, creating networks for applications, exposing necessary servers to internet. Deny all the other access
•	Understand and implementing Virtual Private Networks
•	Enabling DNS (Public and Private)
IP Address
•	Unique address given to a system in a network to communicate.
•	There are currently two main versions of IP Address
•	IPv4
•	IPv6
•	IPv4:
•	IPv4 is made up of 32 bits, Because of this , there are 2^32 (4294967296) possible IP Addresses
•	Each IPv4 address is broken down into four sections    
•	Lets look at decimal representation and binary representation of some ip addresses
•	192.168.0.10 => decimal representation
•	11000000.10101000.00000000.00001010 => binary represenation
•	
•	20.25.34.7 => decimal
•	00010100.00011001.00100010.00000111 => binary representation
•	
•	10.0.0.2 => decimal
•	00001010.00000000.00000000.00000010
•	Execute ipconfig on your laptop 
 
•	Observations about IP Addresses
•	What is purpose of Default Gateway and subnet mask?
•	Why are most of our ip addresses starting with 192.168.x.x or 10.x.x.x in our office network
•	IP Address holds
•	network id
•	host id
•	But to determine the network id and host id we need a subnet mask
•	  192.168.0.198
•	  255.255.255.0
•	
•	  network id
•	  192.168.0
•	
•	  host id
•	  198
•	
•	
•	  192.168.0.11
•	  255.255.0.0
•	
•	  network
•	  192.168
•	
•	  host id
•	  0.11
•	
•	  10.0.0.7
•	  255.255.255.0
•	
•	  network id (3 octets)
•	  10.0.0 
•	
•	  host id (1 octet) => 2^8 ~= 256
•	  7 
•	
•	  172.16.0.8
•	  255.255.0.0
•	
•	  network id 
•	  172.16
•	
•	  host id (2 octets => 2^16 ~= 65536)
•	  0.8 

•	Possible subnet mask’s as per what we understood 
SM => 255.255.255.0 => Host (1 Octet) => 2^8 ~= 256
   => 255.255.0.0 => Host (2 octets) => 2^16 ~= 65536
   => 255.0.0.0 => Host (3 Octets) => 2^24 ~= 16777216
•	Lets assume i need a network
•	with 200 devices => SM => 255.255.255.0
•	with 500 devices => SM => 255.255.0.0
•	Now lets look at networks. A network can be regarded as one of the following types
•	Classful networks
•	Classless networks
•	Classful Networks:
•	In terms of classfull networks we have five classes
•	A
•	B
•	C
•	D
•	E
•		Class A	Class B	Class C
Address Range	0.0.0.0-127.255.255.255	128.0.0.0-192.255.255.255	192.0.0.0 – 223.255.255.255
Defult Subnet Mask	255.0.0.0	255.255.0.0	255.255.255.0
Maximum Number of Hosts	16777214	65534	254
private address range	10.0.0.0 – 10.255.255.255	172.16.0.0 – 172.31.255.255	192.168.0.0 – 192.168.255.255
•	Class D compromises of range of IP addresses that are set aside for multicast transmission purpose 224.0.0.0 - 239.255.255.255
•	Class E is set aside for expermimental purposes 240.0.0.0 - 255.255.255.255
•	Classles Inter Domain Routing (CIDR)
•	This was introduced to replace classfull addresses. It uses variable length subnet masks
•	This has introduced a CIDR notation
•	Subnet mask in binary
SM in binary:
   255.255.255.0
   11111111.11111111.11111111.00000000 => 8 zeros => 2^8 -2 => 254

       
   
   11111111.11111111.11111110.00000000 => 9 zeros => 2^ 9 -2 => 512 - 2 => 510
   
   
   100 devices => 2^n ~= 100  => n = 7 i.e 7 zeros
   
   11111111.11111111.11111111.10000000 => 7 zeros => 2^7-2 => 126
   
   1500 devices
   
   11111111.11111111.11111000.00000000 => 2^11 = 2046
•	Possible SM’s in a octect
11111111 => 255
11111110 => 254
11111100 => 252
11111000 => 248
11110000 => 240
11100000 => 224
11000000 => 192
10000000 => 128
•	The CIDR notation denotes subnet mask by /X
192.168.0.0/24
SM => 255.255.255.0
ip range 192.168.0.0 - 192.168.0.255

192.168.0.0/16
SM => 255.255.0.0
ip range => 192.168.0.0 - 192.168.255.255

192.168.0.0/23
SM => 255.255.254.0

192.168.0.0/23

11111111.11111111.11111110.00000000

11000000.10101000.0000000 0.00000000 => 192.168.0.0
11000000.10101000.0000000 1.11111111 => 192.168.1.255

10.10.128.0/22  => 32 -22 => 10 => 2^10 -2 => 1022

SM => 11111111.11111111.11111100.00000000

IP => 00001010.00001010.100000 00.00000000 => 10.10.128.0

      00001010.00001010.100000 11.11111111 => 10.10.131.255

•	Exercise: Try to find the ip ranges for the following CIDR notations
172.16.0.0/12
192.168.0.0/16
10.0.0.0/8

10.100.192.0/20
10.10.0.0/21


•	In any network, We cannot use 2 IP addresses
•	All 0 will be Network Id
•	All 1 (255) will be broadcast id
•	In the case of Azure we cannot 5 IP Addresses
•	All 0 will be Network Id (x.x.x.0)
•	ALL 1 will be broadcast id (x.x.x.255)
•	x.x.x.1 Reserved by Azure for the default gateway
•	x.x.x.2 and x.x.x.3 Reserved by Azure to Map the Azure DNS IPs to VNET Space
•	In Azure the Smallest subnet possible is /29 

