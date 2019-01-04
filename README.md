# Service Provider meets Segment Routing...
This repository covers demo of Service Provider multi-vendor network running Segment Routing with various services on top.

# ... and OpenConfig
Whenever possible OpenConfig YANG modules are used to unify the configuration of Service Provider Fabric. Where it isn't possible (where OpenConfig YANG modules aren't created or not implemented by particular vendor), either vendor-native YANG modules or CLI-based Ansible playbooks are used.

# Currently used network operation systems
1) Arist EOS 4.21.1.1F
2) Cisco IOS XR 6.5.1
3) Nokia SR OS 16.0.R5
4) Cumulus Linux 3.7.1

# Available services
1) IP VPN for IPV4 and IPV6 between all 3 PE
2) EVPN (E-LAN fashion) between all 3 PE

# Development mode
This repositry is currently being developed, so expect the changes and pull the repository to get the latest version

# To-do list
1) Add automation for EVPNoSR services
2) Add automation for IPVPNoSR services automation
3) Add SR policies (static and dynamic using BGP-SR-TE)
4) Add Telemtry using Netflux TICK stack + Grafana
5) Add automatic chose of connection method use by device depending on its capabilities (CLI, NETCONF/YANG(native), NETCONF/YANG(OpenConfig))

# Version
The current version of the repository is `0.4.1`

# Change log
Version `0.1`
1) Initial topology is created.
2) IP VPN is deployed.

Version `0.2`
1) Previous files are stored in `backup` folder in proper version.
2) Underlay topology is updated. It starts with `sp_` prefix.
3) New overlay topology for EVPN (E-LAN) is created. It starts with `evpn_elan_` prefix and located within `topology` folder.
4) Initial configuration files are updated. Now all of them start with `sp_` prefix.
5) New final configuration files for EVPN (E-LAN) are created. Their names start with `evpn_elan_` prefix. 

Version `0.3`
1) Added folder `ansible` with automation of Service Provider Fabric configuration. More details in `ansible/README.md`.
2) Initial configuration files are updated to anticipate minimal requirements for automation.
3) Underlay topology file `topology/sp_underlay.txt` is updated with link prefixes for IPv4 and IPv6.
4) Currently only underlay IGP (ISIS) and MPLS data plane (Segment Routing) is automated 
5) New file with OOB topology is assed in `topology/oob_management.txt`

Version `0.4`
1) Added LLDP configuration for `underlay_mpls` role. It's configured automatically on all Ethernet interfaces.
2) Added BGP configuration for `underla_bgp` role to finalize creation of Service Provider Fabric. More details in `ansible/README.md`.
3) Some changes in tasks structure in `underlay_mpls` role to unify and simplify the configuration and provide possibility to extend for new vendors.
4) Added YANG tool `yang_extractor_config.yml` to obtain the configuration/states in particular YANG module from network function. More details in `ansible/README.md`.

Version `0.4.1`
1) New overlay topology for IP VPN (IPv4 and IPv6) is created. It starts with `ip_vpn_` prefixi and located within `topology` folder.
2) Files for EVPN (E-LAN) toplogies are slightly modified.
3) Varios updated in `README.md` files across sub-folders.
