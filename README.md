# Elan touchpad driver

## History

Fork of [this fork](https://github.com/pavlepiramida/elan_i2c_dkms) of [this project](https://github.com/Jookia/elan_i2c_dkms) which seems not maintened anymore.

## Getting started

To install, run this in a terminal:

```shell
sudo dnf install -y dkms # on fedora40 but use your own package manager
cd elan_i2c_dkms
sudo dkms install .
```

Then reboot your machine.

## How to update this driver

If it still not working, here's how I updated this driver on Fedora 40:

```shell
sudo dnf install -y acpidump # on fedora40 but use your own package manager
sudo acpidump | grep -C3 -i elan
```

Pick the value you'll find here:

![acpidump](./img/acpidump.png)

And add it [here](./elan_i2c_core.c#1269)
