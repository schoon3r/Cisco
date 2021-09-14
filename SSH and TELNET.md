## Quick SSH Config
```
ip domain-name cisco.com
crypto key generate rsa
  How many bits in the modulus [512]: 1024
username admin secret ccna
line vty 0 15
  transport input ssh
  login local
  exit
ip ssh version 2
```

## Verify SSH
```
show ip ssh
show ssh
```
*If the switch does not support cryptographic features, this command is unrecognized.*

## Telnet Config
```
!Sets up an SVI on a Switch
int vlan 1
  ip address 192.168.1.2 255.255.255.0
  no shut
  exit

line vty 0 15
  transport input telnet
  password password
  login
```
*SSH is preferred than TELNET*
