# Campus Network

A1 Switch
```shell
#
sysname A1
#
vlan batch 10 20 60 80 90
#
cluster enable
ntdp enable
ndp enable
#
drop illegal-mac alarm
#
dhcp enable
#
diffserv domain default
#
stp region-configuration
 region-name HCIP
 revision-level 1
 instance 1 vlan 10
 instance 2 vlan 20
 active region-configuration
#
drop-profile default
#
aaa
 authentication-scheme default
 authorization-scheme default
 accounting-scheme default
 domain default
 domain default_admin
 local-user admin password simple admin
 local-user admin service-type http
#
interface Vlanif1
#
interface Vlanif60
 dhcp select global
 dhcp select relay
 dhcp relay server-ip 10.0.100.2
#
interface Vlanif80
 dhcp select global
 dhcp select relay
 dhcp relay server-ip 10.0.100.2
#
interface Vlanif90
 dhcp select global
 dhcp select relay
 dhcp relay server-ip 10.0.100.2
#
interface MEth0/0/1
#
interface Ethernet0/0/1
 port link-type access
 port default vlan 10
#
interface Ethernet0/0/2
 port link-type access
 port default vlan 20
#
interface Ethernet0/0/3
#
interface Ethernet0/0/4
#
interface Ethernet0/0/5
#
interface Ethernet0/0/6
#
interface Ethernet0/0/7
#
interface Ethernet0/0/8
#
interface Ethernet0/0/9
#
interface Ethernet0/0/10
#
interface Ethernet0/0/11
#
interface Ethernet0/0/12
#
interface Ethernet0/0/13
#
interface Ethernet0/0/14
#
interface Ethernet0/0/15
#
interface Ethernet0/0/16
#
interface Ethernet0/0/17
#
interface Ethernet0/0/18
#
interface Ethernet0/0/19
#
interface Ethernet0/0/20
#
interface Ethernet0/0/21
#
interface Ethernet0/0/22
 port link-type trunk
 port trunk pvid vlan 60
 port trunk allow-pass vlan 60 80 90
#
interface GigabitEthernet0/0/1
 port link-type trunk
 port trunk allow-pass vlan 10 20 60 80 90
#
interface GigabitEthernet0/0/2
 port link-type trunk
 port trunk allow-pass vlan 10 20 60 80 90
#
interface NULL0
#
user-interface con 0
user-interface vty 0 4
#
return

```

```shell
```

```shell
```

```shell
```

```shell
```

```shell
```

```shell
```

```shell
```

```shell
```

```shell
```
