# Service Provider meets Segment Routing...
This repository covers demo of Service Provider multi-vendor network running Segment Routing with various services on top.

# ... and OpenConfig
Whenever possible OpenConfig YANG modules are used to unify the configuration of Service Provider Fabric.

# Currently used network operation systems
1) Arist EOS 4.21.1.1F
2) Cisco IOS XR 6.5.1
3) Nokia SR OS 16.0.R5
4) Cumulus Linux 3.7.1

# Available services
1) IP VPN between all 3 PE
2) EVPN (E-LAN fashion) between all 3 PE

# Development mode
This repositry is currently being developed, so expect the changes and pull the repository to get the latest version

# To-do list
1) Add SR/EVPN service
2) Add Ansible automation

# Version
The current version of the repository is `0.3`

# Change log
Version `0.1`
1) Initial topology is created.
2) IP VPN is deployed.

Version `0.2`
1) Previous files are stored in `backup` folder in proper version.
2) Underlay topology is updated. It starts with `sp_` prefix.
3) New overlay topology for EVPN (E-LAN) is created. It starts with `evpn_elan_` prefix.
4) Initial configuration files are updated. Now all of them start with `sp_` prefix.
5) New final configuration files for EVPN (E-LAN) are created. Their names start with `evpn_elan_` prefix. 

Version `0.3`
1) Added folder `ansible` with automation of Service Provider Fabric configuration. More details in `ansible/README.md`.
2) Initial configuration files are updated to anticipate minimal requirements for automation.
3) Underlay topology file `topology/sp_underlay.txt` is updated with link prefixes for IPv4 and IPv6.
4) Currently only underlay IGP (ISIS) and MPLS data plane (Segment Routing) is automated 
