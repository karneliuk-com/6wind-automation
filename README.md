# Automation of 6Wind Turbo Router
This repository contains the Ansible Roles to automate the configuration of 6WINF Turbo Router network function relying on the NETCONF/YANG framework for device configuration and NetBox as a source of truth

## Use Cases
- Creation of VRFs
- Creation of interfaces and mapping them to VRFs
- Creation of IP addresses and mapping them to interfaces
- Creation of BGP configuration

## Environment
The development environment has following components
- Ansible 2.11.*
- Netbox 3.0.*

## Hosts
Options to limite the hosts scope:
- `device_roles_XXX`, where `XXX` is a device role slug from NetBox (e.g., `device_roles_dci`).
- `sites_XXX`, where `XXX` is a site slug slug from NetBox (e.g., `sites_ams3`).

## Need Help?
[Contact us](https://karneliuk.com/contact/) with your request and we will find the most suitable solution for you.

(c)2021, Karneliuk.com