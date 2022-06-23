# Raspberry Pi Configuration

My home Rasperry Pi cluster runs various networking and home automation applications. They are primarily managed by Ansible using the playbooks in this repository.

## Prereqs

- Install anisble
- Install galaxy deps `ansible-galaxy install -r roles/requirements.yml`

## Base Pi installation

All Pis run Rasperry Pi OS Lite. Prior to Ansible taking over there are several manual steps required to provision and load an SD card with the base installation.

### Install OS to SD card

1. Download the (Raspberry Pi imager)[https://www.raspberrypi.com/software/].
2. Choose the Raspberry Pi OS Lite (64-bit)
3. Select the Advanced Options cog and select the following options
    - Enable SSH
    - Paste the output of `cat ~/.ssh/id_ed25519.pub` into the set authorized_keys field
    - Disable Set username and password
4. Write to SD card and eject from PC.

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

## Insta

## Useful ansible commands

Find out the RPi model of each host
```
ansible all -m shell -a 'cat /proc/cpuinfo | grep Model'
```




