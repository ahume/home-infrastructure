# Pi-hole DNS and ad-blocking

[Pi-hole)[https://pi-hole.net/] runs on two dedicated rpi machines, `10.10.10.10` (primary) and `10.10.10.11` (secondary, failover).


## Instance metadata

### pihole1

| IP address              | 10.10.10.10               |
| Console                 | https://pihole1/admin     |
| Application Logs        |                    |
| Machines metrics        | [Node Exporter - pihole1](https://grafana.hunet.uk/d/rYdddlPWk/node-exporter-full?var-node=pihole1:9100)    |

### pihole2

| IP address              | 10.10.10.11               |
| Console                 | https://pihole2/admin     |
| Application Logs        | [Query Logs](https://app-uk.logz.io/#/dashboard/kibana/discover/cb4a2720-f758-11ec-8925-61c7cd875b25?_g=(filters:!())&accountIds=true&switchToAccountId=514054)                   |
| Machines metrics        | [Node Exporter - pihole2](https://grafana.hunet.uk/d/rYdddlPWk/node-exporter-full?var-node=pihole2:9100)    |

## Adding local DNS records

NB: Do not do this via the console.

Edit the [custom.list](../pihole/templates/custom.list) file.

## Adding domain to block list

NB: Do not do this via the console.

## Adding domain to allow list

NB: Do not do this via the console.

## Bootstraping a new Pi-hole machine

- Follow the runbook to provision a new base Raspberry Pi SD card.
- Configure a Unifi port profile to access the DNS VLAN.
- Plug in the machine to the newly configured port and connect to power.
- Wait for the machine to appear on the network and assign the desired IP address.
- Test SSH
    - `ssh pi@10.10.10.x`.
- Add the new machine to the Ansible inventory file
    - `sudo vim /etc/ansible/hosts`
- Run the install-pihole Ansible playbook.
    - `ansible-playbook install-pihole.yaml --vault-password-file .vault-password`

## Problems and known workarounds

| Problem | Workaround |
| ------- | ---------- |
| Query logging is enabled in config but nothing is logged to pihole.log | Disable and re-enable query logging in the console of both pihole machines |


