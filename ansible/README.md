# Ansible configuration

## Base Pi installation

All Pis run Rasperry Pi OS Lite. Prior to Ansible taking over there are several manual steps required to provision and load an SD card with the base installation.

### Install OS to SD card

1. Download the (Raspberry Pi imager)[https://www.raspberrypi.com/software/].
2. Choose the Raspberry Pi OS Lite (64-bit)
3. Select the Advanced Options cog and select the following options
    - Enable SSH
    - Paste the output of `cat ~/.ssh/id_ed25519.pub` into the set authorized_keys field
    - Disable Set username and password
4. Write to SD card and eject from computer.

### Provision Pi into the network

1. Configure port in Unifi to the desired network.
2. Insert SD card into new Pi.
3. Connect ethernet and power to Pi.
4. Wait for IP to be assigned to device, and reassign to fixed IP if desired.
5. Test `ssh pi@<IP>` (if you're reprovisioning existing hardware you may have to wrangle known_hosts).

### Add new machine to Ansible hosts

```
sudo vim /etc/ansible/hosts
```

Add the new host under the appropriate group. E.g. if the new machine role is a Pi-Hole / DNS server add under the existing `[pihole]` group

### Booting from SSD drive

Some of the Pis have a SSD connected and can be configured to boot from that drive.

#### What I think I need to try

- Flash an SD card with the Bootloader, USB Boot image.
- Put it in the Pi and wait for the green activity light to blink steady.
- Flash the SSD with RPi OS Lite.
- Re-attach the SSD and remove the SD card.
- Power up and watch for successful boot.


## Useful ansible commands

Find out the RPi model of each host
```
ansible all -m shell -a 'cat /proc/cpuinfo | grep Model'
```
