# AdGuard in OpenWRT

## Dedicated old OpenWRT as ad blocker

The idea is to repurpose an old device able to run OpenWRT as dedicated AdGuard
appliance, for this purpose we need to:

1. install OpenWRT in the device
2. configure the network components such as:
  - configure the device as "dumb AP"
  - disable wireless if needed
  - uninstall `dnsmasq` 
3. install AdGuard
4. configure AdGuard 

As I have installed OpenWRT in an old laptop I use for testing purposes, I'm jumping straight to uninstalling `dnsmasq` 

### Uninstalling `dnsmasq` 

This is required assuming the device is not the primary dns or dhcp server in the network. Since AdGuard will take the role of dns server.
 
There are ways to remove each service individually, however I prefer to remove `dnsmasq` completely

```bash
/etc/init.d/dnsmasq stop
opkg remove dnsmasq
```
If you prefer to -for some reason- keep `dnsmasq` and instead disable each server independently, see following links

- (Disable DHCP Server)[https://openwrt.org/docs/guide-user/network/wifi/dumbap#step_3disable_dhcp_server]

- (Disable DHCPv6 Server)[https://openwrt.org/docs/guide-user/network/wifi/dumbap#step_4disable_dhcpv6_server]


### Install AdGuard

```bash
opkg update
opkg install adguardhome
```
Install `curl` either via the LuCi web interface or using `opkg` example:

```bash
opkg install curl
```


```bash
curl -s -S -L https://raw.githubusercontent.com/AdguardTeam/AdGuardHome/master/scripts/install.sh | sh -s -- -v
```

```bash
/opt/AdGuardHome/AdGuardHome -s start
```



### Static ip

example of how `/etc/config/network` should look like (use your own values)

```
config interface 'lan'
        option type 'bridge'
        option ifname 'eth0.1 eth1'
        option proto 'static'
        option ipaddr '192.168.0.2'
        option netmask '255.255.255.0'
        option gateway '192.168.0.1'
        list dns '192.168.0.100'
```



Learn more:

- (Dnsmasq DHCP server)[https://openwrt.org/docs/guide-user/base-system/dhcp.dnsmasq]
- [AdGuard Home](https://openwrt.org/docs/guide-user/services/dns/adguard-home)
- [DNS and DHCP](https://openwrt.org/docs/guide-user/base-system/dhcp_configuration#providing_custom_dns_with_dhcp)
- (Proper way to disable DHCP and DNS servers
  completely)[https://forum.openwrt.org/t/proper-way-to-disable-dhcp-and-dns-servers-completely/19608/13]
