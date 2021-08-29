# Port Security
### Config
```
interface fa0/5
switchport mode access
switchport port-security
switchport port-security maximum 3
switchport port-security mac-address aaaa.bbbb.1234
switchport port-security mac-address sticky
```
### Verify 
```
show port-security
show port-security fa0/5
show port-security address
```
# VLAN Attacks Mitigation
### Step 1: Disable trunking by making USED ports access ports.
```
interface range fa0/1 - 16
switchport mode access
exit 
```
### Step 2: Shutdown and disable trunking on UNUSED ports.
```
interface range fa0/17 - 20
switchport mode access
switchport access vlan 1000
shutdown
exit
```
### Step 3: Config trunks manually for trunking and change the default native vlan.
```
interface range fa0/21 - 24
switchport mode trunk
switchport nonegotiate
switchport trunk native vlan 999
end
```
# DHCP Snooping
### Enable ip dhcp snooping (global)
```
ip dhcp snooping
ip dhcp snooping vlan 5,10,50-52
```
### Trusted ports
```ip dhcp snooping trust```
### Untrusted ports
```ip dhcp snooping limit rate 6```

# DAI Attacks (Dynamic ARP Inspection)
### Enable ip dhcp snooping and dai (global)
```
ip dhcp snooping
ip dhcp snooping vlan 10
ip arp inspection vlan 10
```
### Trusted ports
```
ip dhcp snooping trust
ip arp inspection trust
```
### Check both dest and src MAC addresses (can only use one of the 3 options below)
```
ip arp inspection validate src-mac
ip arp inspection validate dst-mac
ip arp inspection validate ip
ip arp inspection validate src-mac dst-mac ip (*for multiple inspection*)
```
# STP Attacks (Spanning Tree)
### Port-fast
```
interface fa0/1
switchport mode access
spanning-tree portfast
spanning-tree portfast default (*global command only*)
```
### BPDU Guard
```
interface fa0/1
spanning-tree bpduguard enable
```
#### Global BPDU config
```spanning-tree portfast bpduguard default```
### Verify
```
show spanning-tree summary
show running-config | begin span
```

