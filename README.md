# Knulli scripts

Small service scripts for [Knulli](https://knulli.org/).

## Installation

Copy the scripts you want to `/userdata/system/services` on your Knulli device:

```sh
mkdir -p /userdata/system/services
cp instant_shutdown random_boot_logo openvpn /userdata/system/services/
chmod +x /userdata/system/services/*
```

The scripts will then appear under **Start → System Settings → Services**. Enable or
disable them there and reboot for the change to take effect.

## Services

### `instant_shutdown`

Changes the power button behaviour on Allwinner H700 devices so that a short press
shuts the device down instead of suspending it. The original
`/usr/bin/power-button` is backed up before it is replaced. This service must run as
root.

### `random_boot_logo`

Selects a different boot logo from `/userdata/bootlogos` and copies it to
`/boot/bootlogo.bmp`. Create the directory and add one or more correctly formatted
`.bmp` files:

```sh
mkdir -p /userdata/bootlogos
cp *.bmp /userdata/bootlogos/
```

With two or more images, the script alternates its selection logic so the logo does
not change on every run. Files are selected by shell globbing; avoid spaces and
special characters in filenames.

### `openvpn`

Starts OpenVPN using the first `.ovpn` file found in `/userdata/system/openvpn` and
writes its log to `/userdata/system/logs/openvpn.log`. Install OpenVPN and add a
configuration before enabling the service:

```sh
mkdir -p /userdata/system/openvpn
cp client.ovpn /userdata/system/openvpn/
```

The script accepts `start`, `stop`, `restart`, and `status` arguments. It also
creates `/dev/net/tun` when necessary. If multiple `.ovpn` files are present, only
the first one returned by `find` is used.

## Warning

Use these scripts at your own risk. They modify system behaviour and, in the case
of `random_boot_logo`, write to the boot partition. Test them on your device before
relying on them.
