## Default Settings
```
IP Addr:  192.168.1.1
Username: Cisco
Password: Cisco
```

# Wireless LAN Controller
### Configure WLAN (WPA2 - Personal - PSK)
```
1. Create WLAN
2. Apply and Enable WLAN
3. Select the Interface (user / management)
4. Secure the WLAN (AES, PSK, PSK Input)
5. Verify the WLAN is operational
6. View wireless client details
```
### Configure WLAN (WPA2 - Enterprise - RADIUS)
```
1. Create a new WLAN (WLAN tab >> Create New > GO)
2. Configure the WLAN name and SSID
3. Enable the WLAN for VLAN 5 (Check ENABLE >> Choose Interface Group >> Apply >> OK)
4. Verify AES and 802.1X defaults (Security Tab >> AES >> 802.1X Enable)
5. Configure WLAN security to use the RADIUS server (AAA Servers Tab >> RADIUS Server IP >> APPLY)
6. Verify the new WLAN is available.
```
### Configure SNMP & RADIUS 
```
SNMP
1. Click MANAGEMENT
2. Click SNMP
3. Click Trap Receivers 
4. Click New..
5. Enter SNMP Community Name and IP address
6. Click Apply
RADIUS Server Information
1. Click SECURITY
2. Click RADIUS
3. Click AUTHENTICATION
4. Click New..
5. Enter IP address of SNMP server and shared secret
6. Click Apply
```
### Configure a New Interface (VLAN)
```
1. Create a new interface (Controller Tab >> Interface >> New)
2. Configure the VLAN name and ID (Enter name and VLAN ID >> Apply)
3. Configure the port and interface address (*Physical Port)
4. Configure the DHCP server address 
5. Apply and Confirm
6. Verify Interfaces
```
### Configure WLC as DHCP Server (for APs ONLY!)
```
1. Create a new DHCP scope (Controller Tab >> Internal DHCP Server >> DHCP Scope >> New...)
2. Name the DHCP scope
3. Verify the new DHCP scope
4. Configure and enable the new DHCP scope (Pool Address >> Default Routers >> Enable)
5. Verify the enable DHCP scope
```
