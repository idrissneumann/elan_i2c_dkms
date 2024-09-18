# Elan touchpad driver

## History

Fork of [this fork](https://github.com/pavlepiramida/elan_i2c_dkms) of [this project](https://github.com/Jookia/elan_i2c_dkms) which seems not maintened anymore.

## Getting started

To install, check and replace the values in the [dkms.conf](./dkms.conf) file (follow the comments you'll find there).

Then, run this in a terminal:

```shell
sudo dnf install -y git dkms # on fedora40 but use your own package manager
git clone https://github.com/idrissneumann/elan_i2c_dkms.git
cd elan_i2c_dkms
sudo dkms install . --kernelsourcedir /lib/modules/6.10.9-200.fc40.x86_64/source # check the source dir of your own kernel version (uname -r)
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
