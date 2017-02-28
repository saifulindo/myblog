---
layout: post
title: IPv6 Basic Link Local 
tags:  [ ipv6, cisco, gns3]
categories: [How To]
author: Muhammad Syaiful
excerpt: ""
---

### Topologi

![Topologi IPv6 Basic Link Local](/myblog/assets/images/ipv6/topologi-ipv6-basic-link-local)

### Config

##### R1

```bash
R1# conf t
R1(config)#ipv6 unicast-routing
R1(config-if)#ipv6 address autoconfig
R2(config-if)#
R1(config-if)#do show ipv6 int fa0/0
FastEthernet0/0 is administratively down, line protocol is down
  IPv6 is enabled, link-local address is FE80::C601:4FF:FE54:0 [TEN]
  No global unicast address is configured
  Joined group address(es):
    FF02::1
    FF02::2
    FF02::1:FF54:0
  MTU is 1500 bytes
  ICMP error messages limited to one every 100 milliseconds
  ICMP redirects are enabled
  ND DAD is enabled, number of DAD attempts: 1
  ND reachable time is 30000 milliseconds
  ND advertised reachable time is 0 milliseconds
  ND advertised retransmit interval is 0 milliseconds
  ND router advertisements are sent every 200 seconds
  ND router advertisements live for 1800 seconds
  Hosts use stateless autoconfig for addresses.
```

##### R2

```bash
R2# conf t
R2(config)#ipv6 unicast-routing
R2(config-if)#ipv6 address autoconfig
R2(config-if)# no sh
R2(config-if)#do show ipv6 int fa0/0
FastEthernet0/0 is administratively down, line protocol is down
  IPv6 is enabled, link-local address is FE80::C602:EFF:FE10:0 [TEN]
  No global unicast address is configured
  Joined group address(es):
    FF02::1
    FF02::2
    FF02::1:FF54:0
  MTU is 1500 bytes
  ICMP error messages limited to one every 100 milliseconds
  ICMP redirects are enabled
  ND DAD is enabled, number of DAD attempts: 1
  ND reachable time is 30000 milliseconds
  ND advertised reachable time is 0 milliseconds
  ND advertised retransmit interval is 0 milliseconds
  ND router advertisements are sent every 200 seconds
  ND router advertisements live for 1800 seconds
  Hosts use stateless autoconfig for addresses.
```

##### Pengujian

R1 to R2

```bash
R1(config-if)#do ping FE80::C602:EFF:FE10:0
Output Interface: FastEthernet0/0
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to FE80::C602:EFF:FE10:0, timeout is 2 seconds:
Packet sent with a source address of FE80::C601:4FF:FE54:0
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 1280/1298/1316 ms

```

R2 to R1

```bash
R2(config-if)#do ping FE80::C601:4FF:FE54:0
Output Interface: FastEthernet0/0
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to FE80::C601:4FF:FE54:0, timeout is 2 seconds:
Packet sent with a source address of FE80::C602:EFF:FE10:0
.!!!!
Success rate is 80 percent (4/5), round-trip min/avg/max = 912/1232/1676 ms
 
```

### Penjelasan

IPv6 Link Local identik dengan FE80::/8. 
