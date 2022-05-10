### Network  설정

1. ifcfg-enp0s3 수정

```bash
# vi /etc/sysconfig/network-scripts/ifcfg-enp0s3
```

```
TYPE="Ethernet"
BOOTPROTO="static"
DEFROUTE="yes"
IPV4_FAILURE_FATAL="no"
IPV6INIT="yes"
IPV6_AUTOCONF="yes"
IPV6_DEFROUTE="yes"
IPV6_FAILURE_FATAL="no"
IPV6_ADDR_GEN_MODE="stable-privacy"
NAME="enp0s3"
UUID="b0fa6972-9a2d-498b-8f23-1bfb769267c4"
DEVICE="enp0s3"
ONBOOT="yes"
PREFIX="24"
IPV6_PEERDNS="yes"
IPV6_PEERROUTES="yes"
IPV6_PRIVACY="no"

IPADDR="192.168.10.55"
NETMASK="255.255.255.0"
GATEWAY="192.168.10.254"
DNS1="168.126.63.1"
DNS2="168.126.63.2"
```

```bash
# systemctl restart network
```