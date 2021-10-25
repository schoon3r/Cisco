# **Network Address Translation (NAT)**

## Private IPv4 Addresses

```
10.0.0.0 - 10.255.255.255 (10.0.0.0/8)
172.16.0.0 - 172.31.255.255	(172.16.0.0/12)
192.168.0.0 - 192.168.255.255 (192.168.0.0/16)
```

## Static NAT

`Map inside local to inside global`

```
R2(config)# ip nat inside source static 192.168.10.254 209.165.201.5
```

`Inside/Outside interfaces`

```
R2(config)# interface serial 0/1/0
R2(config-if)# ip address 192.168.1.2 255.255.255.252
R2(config-if)# ip nat inside
R2(config-if)# exit
R2(config)# interface serial 0/1/1
R2(config-if)# ip address 209.165.200.1 255.255.255.252
R2(config-if)# ip nat outside
```

`Verify NAT`

```
R2# show ip nat translations
R2# clear ip nat statistics
R2# show ip nat statistics
```

<BR />

## Dynamic NAT

`Map inside local to inside global`

```
R2(config)# ip nat pool NAT-POOL1 209.165.200.226 209.165.200.240 netmask 255.255.255.224
```

`ACL to permit only those 'inside local' to be translated`

```
R2(config)# access-list 1 permit 192.168.0.0 0.0.255.255
```

`Bind the ACL to the pool`

```
R2(config)# ip nat inside source list 1 pool NAT-POOL1
```

`Inside/Outside interfaces`

```
R2(config)# interface serial 0/1/0
R2(config-if)# ip nat inside

R2(config)# interface serial 0/1/1
R2(config-if)# ip nat outside
```

<BR />

## PAT (NAT Overload)

`Single IPv4 address`

```
R2(config)# ip nat inside source list 1 interface serial 0/1/1 overload
R2(config)# access-list 1 permit 192.168.0.0 0.0.255.255
R2(config)# interface serial0/1/0
R2(config-if)# ip nat inside
R2(config-if)# exit
R2(config)# interface Serial0/1/1
R2(config-if)# ip nat outside
```

`IPv4 Address Pool`

```
R2(config)# ip nat pool NAT-POOL2 209.165.200.226 209.165.200.240 netmask 255.255.255.224
R2(config)# access-list 1 permit 192.168.0.0 0.0.255.255
R2(config)# ip nat inside source list 1 pool NAT-POOL2 overload
R2(config)#
R2(config)# interface serial0/1/0
R2(config-if)# ip nat inside
R2(config-if)# exit
R2(config)# interface serial0/1/1
R2(config-if)# ip nat outside
R2(config-if)# end
R2#
```
