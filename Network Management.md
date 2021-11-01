# CDP

`On by default`

```
Router# show cdp
Router(config)# no cdp run
Router(config)# exit
Router# show cdp
Router# show cdp neighbors
Router# show cdp neighbors detail
Router# show cdp interface

Switch(config)# interface gigabitethernet 0/0/1
Switch(config-if)# cdp enable
```

# LLDP

```
Switch# conf t
Enter configuration commands, one per line.  End with CNTL/Z.
Switch(config)# lldp run
Switch(config)# interface gigabitethernet 0/1
Switch(config-if)# lldp transmit
Switch(config-if)# lldp receive
Switch(config-if)# end
Switch# show lldp
Global LLDP Information:
    Status: ACTIVE
    LLDP advertisements are sent every 30 seconds
    LLDP hold time advertised is 120 seconds
    LLDP interface reinitialisation delay is 2 seconds

S1# show lldp neighbors
S1# show lldp neighbors detail
```

# NTP

### Manual Clock Setting

```
R1# clock set 16:01:00 sept 25 2020
```

### Config and Verify NTP

```
R1# show clock detail
R1(config)# ntp server 209.165.200.225
R1(config)# ntp update-calendar
R1(config)# end
R1# show clock detail
R1# show ntp associations
R1# show ntp status
```

# SysLog

```
R1# configure terminal
R1(config)# logging host 192.168.1.10
R1(config)# service timestamps log datetime msec
R1(config)# logging trap debugging
R1(config)# logging on
```

# Router File System

```
Router# show file systems
Router# dir

Router# cd nvram:
Router# pwd
nvram:/
Router# dir
```

### Use TFTP to Backup Config

```
R1# copy running-config tftp
Remote host []?192.168.10.254
Name of the configuration file to write[R1-config]? R1-Jan-2019
Write file R1-Jan-2019 to 192.168.10.254? [confirm]
Writing R1-Jan-2019 !!!!!! [OK]
```

### Use USB to Backup Config

```
R1# copy running-config usbflash0:
Destination filename [running-config]? R1-Config
5024 bytes copied in 0.736 secs (6826 bytes/sec)
```

### Password Recovery Example

```
Readonly ROMMON initialized

monitor: command "boot" aborted due to user interrupt
rommon 1 >

rommon 1 > confreg 0x2142
rommon 2 > reset
System Bootstrap, Version 15.0(1r)M9, RELEASE SOFTWARE (fc1)
Technical Support: http://www.cisco.com/techsupport
Copyright (c) 2010 by cisco Systems, Inc.
(output omitted)

Router# copy startup-config running-config
Destination filename [running-config]?
1450 bytes copied in 0.156 secs (9295 bytes/sec)
R1#

R1# configure terminal
Enter configuration commands, one per line.  End with CNTL/Z.
R1(config)# enable secret cisco

R1(config)# config-register 0x2102
R1(config)# end
R1# copy running-config startup-config
Destination filename [startup-config]?
Building configuration...
[OK]
R1#

R1# reload
Proceed with reload? [confirm]
*Mar  1 13:04:53.009: %SYS-5-RELOAD: Reload requested by console. Reload Reason: Reload Command.
```

### Copy IOS Image from TFTP Server

```
R1# copy tftp: flash:
Address or name of remote host []?2001:DB8:CAFE:100::99
Source filename []?  isr4200-universalk9_ias.16.09.04.SPA.bin
Destination filename [isr4200-universalk9_ias.16.09.04.SPA.bin]?
Accessing tftp://2001:DB8:CAFE:100::99/ isr4200-
universalk9_ias.16.09.04.SPA.bin...
Loading isr4200-universalk9_ias.16.09.04.SPA.bin
from 2001:DB8:CAFE:100::99 (via
GigabitEthernet0/0/0): !!!!!!!!!!!!!!!!!!!!
[OK - 517153193 bytes]
517153193 bytes copied in 868.128 secs (265652 bytes/sec)
```

### Boot Router with NEW IOS Image

```
R1# configure terminal
R1(config)# boot system flash0:isr4200-universalk9_ias.16.09.04.SPA.bin
R1(config)# exit
R1#
R1# copy running-config startup-config
R1#
R1# reload
Proceed with reload? [confirm]

*Mar  1 12:46:23.808: %SYS-5-RELOAD: Reload requested by console. Reload Reason: Reload Command.
```
