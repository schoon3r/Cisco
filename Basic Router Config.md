# Basic Router Config
```
 hostname R1
 enable secret class 
 line console 0  
 logging synchronous
 password cisco 
 login 
 exit 
 line vty 0 4 
 password cisco 
 login 
 transport input telnet 
 exit 
 service password-encryption 
 banner motd #
***********************************************
WARNING: Unauthorized access is prohibited!
***********************************************
 #

 ipv6 unicast-routing
 interface gigabitethernet 0/0/0
 description Link to LAN 1
 ip address 10.0.1.1 255.255.255.0 
 ipv6 address 2001:db8:acad:1::1/64 
 ipv6 address fe80::1:a link-local
 no shutdown
 exit
 copy running-config startup-config
```
## Enable SSH
```
security password min-length 10
login block-for 180 attempts 4 within 120
ip domain name span.com
username Bob secret cisco
crypto key generate rsa

line vty 0 15
login local
transport input ssh
exec-timeout 6
exit
```
## Verification Commands
```
show ip interface brief
show running-config interface 'interface-type number'
show interfaces
show ip interface
show ip route
ping
```
## Filter Command Output
| Command | Description | 
| ------- | ----------- |
| **section** | This displays the entire section that starts with the filtering expression. |
| **include** | This includes all output lines that match the filtering expression. |
| **exclude** | This excludes all output lines that match the filtering expression. |
| **begin** | This displays all the output lines from a certain point, starting with the line that matches the filtering expression. |

