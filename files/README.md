# Description
This folder contains actual router configuration files for network functions:
- Initial configuration called `sp_{{ inventory_hostname }}_initial.conf` contains default configuration with management access with NETCONF enaled configured in accordance with `oob_management.txt` topology.
- Final configuration called `evpn_elan_{{ invnentory_hostname }}_final.conf` contains configuration for EVPN (E-LAN) service.
- Final configuration called `ip_vpn_{{ invnentory_hostname }}_final.conf` contains configuration for IP-VPN (VPNv4/VPNv6) service.

# Important note
This folder is live that's why the content of the files may vary with the time as the project evolve. Read the change log in root directory.
