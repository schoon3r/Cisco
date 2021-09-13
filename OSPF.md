## OSPF Options
```
R1(config)# router ospf 10
R1(config-router)# ?
  area                   OSPF area parameters
  auto-cost              Calculate OSPF interface cost according to bandwidth
  default-information    Control distribution of default information
  distance               Define an administrative distance
  exit                   Exit from routing protocol configuration mode
  log-adjacency-changes  Log changes in adjacency state
  neighbor               Specify a neighbor router
  network                Enable routing on an IP network
  no                     Negate a command or set its defaults
  passive-interface      Suppress routing updates on an interface
  redistribute           Redistribute information from another routing protocol
  router-id              router-id for this OSPF process
R1(config-router)#
```
## Sample of a General Config
```
router ospf 10
 router-id 1.1.1.1
 log-adjacency-changes
 passive-interface GigabitEthernet0/1.1
 passive-interface GigabitEthernet0/1.99
 network 10.0.0.0 0.255.255.255 area 0
end
copy run start
```
## Configuring a Loopback Interface as the Router ID
```
interface loopback 1
ip address 1.1.1.1 255.255.255.255
end
```
## Configure OSPF Using the network Command
```
router ospf 10
 network 10.10.1.0 0.0.0.255 area 0
 network 10.1.1.4 0.0.0.3 area 0
 network 10.1.1.12 0.0.0.3 area 0
 exit
```
## Configure OSPF Using the ip ospf Command
```
interface GigabitEthernet 0/0/0
 ip ospf 10 area 0
interface GigabitEthernet 0/0/1 
 ip ospf 10 area 0
interface Loopback 0
 ip ospf 10 area 0
 exit
```
## Configure Passive Interfaces
```
router ospf 10
 passive-interface loopback 0
 end
```
## OSPF Point-to-Point Networks
```
interface GigabitEthernet 0/0/0
 ip ospf network point-to-point
interface GigabitEthernet 0/0/1
 ip ospf network point-to-point
interface Loopback 0
 ip ospf network point-to-point
```
## Configure OSPF Priority
```
interface GigabitEthernet 0/0/0 
 ip ospf priority 255 
 end
clear ip ospf process
```
## Adjust the Reference Bandwidth
```
router ospf 10
 auto-cost reference-bandwidth 10000
```
## Manually Set OSPF Cost Value
```
interface g0/0/1
 ip ospf cost 30
 interface lo0
 ip ospf cost 10
 end
```
## Modify OSPFv2 Hello Packet Intervals
```
interface g0/0/0 
 ip ospf hello-interval 5 
 ip ospf dead-interval 20 
```
## Propagate a Default Static Route in OSPFv2
```
ip route 0.0.0.0 0.0.0.0 loopback 1

router ospf 10
 default-information originate
 end
```
## Verify OSPF Neighbors
```
show ip interface brief
show ip route

show ip ospf neighbor
show ip protocols
show ip ospf
show ip ospf interface
```
