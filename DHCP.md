# DHCP

## DHCP Client (Router Interface)
```
interface f0/0
  ip address dhcp
  no shutdown
```

## DHCP Server (Router Global)
```
ip dhcp excluded-address 10.10.10.1 10.10.10.10
ip dhcp pool SCHOON3R
  default-router 10.10.10.1
  dns-server 10.10.20.10
  network 10.10.10.0 255.255.255.0
```

## External DHCP (Relay)
```
interface f0/1
  ip helper-address 10.10.20.10
```

## DHCP Verification Commands
```
show dhcp lease

show ip dhcp binding
```
