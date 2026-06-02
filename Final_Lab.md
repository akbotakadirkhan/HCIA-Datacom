# HCIA-Datacom
HCIA-Datacom
```

<A1>
dis cu
#
sysname A1
#
vlan batch 43 50 100 to 200
#
interface Ethernet0/0/22
 port link-type trunk
 port trunk pvid vlan 43
 port trunk allow-pass vlan 43 100 200
#
interface GigabitEthernet0/0/1
 port link-type trunk
 port trunk allow-pass vlan 43 50 100 to 200
#
interface GigabitEthernet0/0/2
 port link-type trunk
 port trunk allow-pass vlan 43 50 100 to 200

#
return
<A1>

```

```

<A2>
dis cu
#
sysname A2
#
vlan batch 43 50 100 to 200
#
interface Ethernet0/0/22
 port link-type trunk
 port trunk pvid vlan 43
 port trunk allow-pass vlan 43 100 200
#
interface GigabitEthernet0/0/1
 port link-type trunk
 port trunk allow-pass vlan 43 50 100 to 200
#
interface GigabitEthernet0/0/2
 port link-type trunk
 port trunk allow-pass vlan 43 50 100 to 200
#
interface NULL0
#
user-interface con 0
user-interface vty 0 4
#
return
<A2>

```

```

<D1>
dis cu
#
sysname D1
#
vlan batch 43 50 100 to 200
#
dhcp enable
#
ip pool ap
 gateway-list 10.1.43.254
 network 10.1.43.0 mask 255.255.255.0
 excluded-ip-address 10.1.43.1 10.1.43.100
 excluded-ip-address 10.1.43.201 10.1.43.253
 lease day 5 hour 0 minute 0
 option 43 hex F1 04 0A 01 2B FE
#
ip pool guest
 gateway-list 192.168.200.254
 network 192.168.200.0 mask 255.255.255.0
 excluded-ip-address 192.168.200.1 192.168.200.10
 excluded-ip-address 192.168.200.251 192.168.200.253
 lease day 5 hour 0 minute 0
 dns-list 8.8.8.8
 option 43 sub-option 2 ip-address 10.1.43.254
#
ip pool staff
 gateway-list 192.168.100.254
 network 192.168.100.0 mask 255.255.255.0
 excluded-ip-address 192.168.100.1 192.168.100.10
 excluded-ip-address 192.168.100.251 192.168.100.253
 lease day 5 hour 0 minute 0
 dns-list 8.8.8.8
 option 43 sub-option 2 ip-address 10.1.43.254
#
interface Vlanif100
 ip address 192.168.100.254 255.255.255.0
 dhcp select global
#
interface Vlanif200
 ip address 192.168.200.254 255.255.255.0
 dhcp select global
#
interface Eth-Trunk1
 port link-type trunk
 port trunk allow-pass vlan 43 50 100 to 200
 mode lacp-static
#
interface GigabitEthernet0/0/1
 port link-type trunk
 port trunk allow-pass vlan 43 50 100 to 200
#
interface GigabitEthernet0/0/2
 port link-type trunk
 port trunk allow-pass vlan 43 50 100 to 200
#
interface GigabitEthernet0/0/3
 eth-trunk 1
#
interface GigabitEthernet0/0/4
 eth-trunk 1
#
interface GigabitEthernet0/0/24
 port link-type trunk
 port trunk allow-pass vlan 43 100 200
#
ospf 1 router-id 50.3.3.3
 area 0.0.0.0
  network 50.3.3.3 0.0.0.0
  network 10.1.43.0 0.0.0.255
  network 192.168.100.0 0.0.0.255
  network 192.168.200.0 0.0.0.255
#
return
<D1>

```

```

<D2>
dis cu
#
sysname D2
#
vlan batch 43 50 100 to 200
#
dhcp enable
#
ip pool ap
 gateway-list 10.1.43.254
 network 10.1.43.0 mask 255.255.255.0
 option 43 hex F1 04 0A 01 2B FE
#
ip pool guest
 gateway-list 192.168.200.254
 network 192.168.200.0 mask 255.255.255.0
 excluded-ip-address 192.168.200.1 192.168.200.10
 excluded-ip-address 192.168.200.251 192.168.200.253
 lease day 5 hour 0 minute 0
 dns-list 8.8.8.8
 option 43 sub-option 2 ip-address 10.1.43.254
#
ip pool staff
 gateway-list 192.168.100.254
 network 192.168.100.0 mask 255.255.255.0
 excluded-ip-address 192.168.100.1 192.168.100.10
 excluded-ip-address 192.168.100.251 192.168.100.253
 lease day 5 hour 0 minute 0
 dns-list 8.8.8.8
 option 43 sub-option 2 ip-address 10.1.43.254
#
interface Vlanif100
 ip address 192.168.100.254 255.255.255.0
 dhcp select global
#
interface Vlanif200
 ip address 192.168.200.254 255.255.255.0
 dhcp select global
#
interface Eth-Trunk1
 port link-type trunk
 port trunk allow-pass vlan 43 50 100 to 200
 mode lacp-static
#
interface GigabitEthernet0/0/1
 port link-type trunk
 port trunk allow-pass vlan 43 50 100 to 200
#
interface GigabitEthernet0/0/2
 port link-type trunk
 port trunk allow-pass vlan 43 50 100 to 200
#
interface GigabitEthernet0/0/3
 eth-trunk 1
#
interface GigabitEthernet0/0/4
 eth-trunk 1
#
interface GigabitEthernet0/0/24
 port link-type trunk
 port trunk allow-pass vlan 43 50 100 111 to 112 200
#
interface NULL0
#
interface LoopBack50
 ip address 50.3.3.3 255.255.255.255
#
ospf 1 router-id 50.4.4.4
 area 0.0.0.0
  network 192.168.100.0 0.0.0.255
  network 192.168.200.0 0.0.0.255
  network 50.4.4.4 0.0.0.0
  network 10.1.43.0 0.0.0.255
#
return
<D2>

```

```

<AC1>
dis cu
#
 sysname AC1
#
vlan batch 43 100 200
#
dhcp enable
#
ip pool AP_Pool
 gateway-list 10.1.43.254 
 network 10.1.43.0 mask 255.255.255.0 
 excluded-ip-address 10.1.43.1 10.1.43.100 
#
ip pool Staff_Pool
 gateway-list 192.168.100.254 
 network 192.168.100.0 mask 255.255.255.0 
 dns-list 8.8.8.8 
#
ip pool Guest_Pool
 gateway-list 192.168.200.254 
 network 192.168.200.0 mask 255.255.255.0 
 dns-list 8.8.8.8 
#
interface Vlanif43
 ip address 10.1.43.254 255.255.255.0
 dhcp select global
#
interface Vlanif100
 ip address 192.168.100.254 255.255.255.0
 dhcp select global
#
interface Vlanif200
 ip address 192.168.200.254 255.255.255.0
 dhcp select global
#
interface GigabitEthernet0/0/1
 port link-type trunk
 port trunk allow-pass vlan 43 100 200
#
ospf 1 router-id 43.43.43.43
 area 0.0.0.0
  network 10.1.43.0 0.0.0.255
  network 192.168.100.0 0.0.0.255
  network 192.168.200.0 0.0.0.255
#
capwap source interface vlanif43
#
wlan
 security-profile name WLAN-Guest
  security wpa-wpa2 psk pass-phrase %^%#"KYUUDw:\Hqu5gF[IC19<N+/)q'-_Ok30U3vE}"%
%^%# aes
 security-profile name WLAN-Staff
  security wpa-wpa2 psk pass-phrase %^%#"14eX:i!YFn0D$G^398J~KUD7WuCE6R\YL-6OE<#
%^%# aes
 ssid-profile name WLAN-Guest
  ssid Guest-WiFi
 ssid-profile name WLAN-Staff
  ssid Staff-WiFi
 vap-profile name VAP-Guest
  service-vlan vlan-id 200
  ssid-profile WLAN-Guest
  security-profile WLAN-Guest
 vap-profile name VAP-Staff
  service-vlan vlan-id 100
  ssid-profile WLAN-Staff
  security-profile WLAN-Staff
 regulatory-domain-profile name default
  country-code KZ 
 ap auth-mode no-auth
 ap-group name ap-group1
  radio 0
   vap-profile VAP-Staff wlan 1
   vap-profile VAP-Guest wlan 2
  radio 1
   vap-profile VAP-Staff wlan 1
   vap-profile VAP-Guest wlan 2
  radio 2
   vap-profile VAP-Staff wlan 1
   vap-profile VAP-Guest wlan 2
 ap-id 0 type-id 69 ap-mac 00e0-fc17-3630 
  ap-name AP1
  ap-group ap-group1
 ap-id 1 type-id 69 ap-mac 00e0-fc56-68e0 
  ap-name AP2
  ap-group ap-group1
#
return
<AC1>

```
