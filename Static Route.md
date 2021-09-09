# Static Routing Configuration

## Standard Static Route 
```
ip route network-address subnet-mask { ip-address | exit-intf [ip-address]} [distance]
or
ipv6 route ipv6-prefix/prefix-length {ipv6-address | exit-intf [ipv6-address]} [distance]
```
## IPv4
```
ip route 172.16.1.0 255.255.255.0 172.16.2.2
ip route 172.16.1.0 255.255.255.0 s0/1/0
```
## IPv6
```
ipv6 unicast-routing
ipv6 route 2001:db8:acad:1::/64 2001:db8:acad:2::2
ipv6 route 2001:db8:acad:1::/64 s0/1/0
```
## Verification Commands
```
show ip route
show ip route static
show running-config | section ip route
```
## IPv4 Fully Specified Static Route
Specify both exit interface and next hop IP
```
ip route 172.16.1.0 255.255.255.0 GigabitEthernet 0/0/1 172.16.2.2
```
## IPv6 Fully Specified Static Route
Specify both exit interface and next hop IP when the next hop IP is the link local address
```
ipv6 route 2001:db8:acad:1::/64 s0/1/0 fe80::2
```
## Default Static Route
```
ip route 0.0.0.0 0.0.0.0 {ip-address | exit-intf}
ip route 0.0.0.0 0.0.0.0 172.16.2.2
```
## Floating Static Route
Uses the AD to determine a backup route
```
ip route 0.0.0.0 0.0.0.0 172.16.2.2 *Standard Static Route
ip route 0.0.0.0 0.0.0.0 10.10.10.2 5 *Floating Static Route
```
## Static Host Route
Uses a 32-bit subnet mask to specify a single host
```
ip route 209.165.200.238 255.255.255.255 198.51.100.2
```
