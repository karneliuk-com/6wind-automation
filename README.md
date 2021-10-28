# Automation of 6WIND Turbo Router
This repository contains the Ansible Roles to automate the configuration of 6WINF Turbo Router network function relying on the NETCONF/YANG framework for device configuration and NetBox as a source of truth

## Use Cases
- Creation of VRFs
- Creation of interfaces and mapping them to VRFs
- Creation of IP addresses and mapping them to interfaces
- Creation of BGP configuration

## Environment
The development environment has following components
- Ansible Core 2.11.*
- Netbox 3.0.*

## Hosts
Options to limite the hosts scope:
- `device_roles_XXX`, where `XXX` is a device role slug from NetBox (e.g., `device_roles_dci`).
- `sites_XXX`, where `XXX` is a site slug slug from NetBox (e.g., `sites_ams3`).

## Usage
There are two main use cases:
- Data collection, which you can write then in your target system (e.g., NetBox or Monitoring system).
- Change of network function's state, which is based on the information from NetBox in our case.

### Preparing
1. Create the environment file `.env` out of `sample_env`:
```
cp sample_env .env
```
2. Fill in `.env` with information per setup.
3. Make th file execuable
```
chmod 775 .env
```
4. Run it:
```
/.env
```

### Collecting Data
To collect YANG modules from 6WIND network devices:
```
ansible-playbook collector.yaml -t yang
```

To collect the operational data from 6WIND network devices:
```
ansible-playbook collector.yaml -t state
```

To collect the configuration from 6WIND network devices:
```
ansible-playbook collector.yaml -t config
```

To configure the non-customer part (main VRF, base system, etc ) in 6WIND network devices:
```
ansible-playbook configurator.yaml -t infrastructure
```

To configure the customer part (main VRF, interfaces, VRRP, BGP, etc) in 6WIND network devices:
```
ansible-playbook configurator.yaml -t customer -e "target_vrf=XXX"
```
where XXX is the name of customer's VRF in NetBox

## Need Help?
[Contact us](https://karneliuk.com/contact/) with your request and we will find the most suitable solution for you.

(c)2021, Karneliuk.com