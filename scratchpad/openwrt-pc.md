# Guide

## Create bootable usb

- Download and flash ubuntu
- Create a new fat32 partition in the remaining usb drive space
- copy openwrt image into that partition

## Flash opwnwrt

- Boot up ubuntu
- use ubuntu's disk utilities to prepare the hard drive if needed
- flash openwrt into the hard drive
- resize the hard drive partitions within ubuntu

## If a single ethernet

You might want to
[set your openwrt to "dumb" access point](https://openwrt.org/docs/guide-user/network/wifi/dumbap),
this process implies to set the interface to dhcp rather than static ip

## Update packages

```bash
opkg update
```

## Install LuCi

[see official page](https://openwrt.org/docs/guide-user/luci/luci.essentials#basic_installation)

```bash

opkg install luci

```

## Identify wireless 

```bash
opkg install pciutils
```

## installing drivers

[see this page for example](https://openwrt.org/docs/guide-user/storage/usb-installing)

```bash
opkg install kmod-usb-net-rtl8152
```