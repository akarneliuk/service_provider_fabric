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

# Monitoring
InfluxData TICK (Telegraf and InfluxDB) + Grafana:
1) Telegraf is using to collect data over SNMPv3 over IPv6 and store it in InfluxDB
2) Grafana polls data out of InfluxDB to build graphs of interfaces' utilization

# Development mode
This repositry is currently being developed, so expect the changes and pull the repository to get the latest version

# To-do list
1) Add automation for EVPNoSR services
2) Add SR policies (static and dynamic using BGP-SR-TE)
3) Add automatic chose of connection method use by device depending on its capabilities (CLI, NETCONF/YANG(native), NETCONF/YANG(OpenConfig))
4) Add GRT routing service (BGP-LU for IPv4/IPv6) for Internet traffic

# Version
The current version of the repository is `0.6.1`

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
4) Currently only underlay IGP (ISIS) and MPLS data plane (Segment Routing) is automated.
5) New file with OOB topology is assed in `topology/oob_management.txt`.

Version `0.4`
1) Added LLDP configuration for `underlay_mpls` role. It's configured automatically on all Ethernet interfaces.
2) Added BGP configuration for `underla_bgp` role to finalize creation of Service Provider Fabric. More details in `ansible/README.md`.
3) Some changes in tasks structure in `underlay_mpls` role to unify and simplify the configuration and provide possibility to extend for new vendors.
4) Added YANG tool `yang_extractor_config.yml` to obtain the configuration/states in particular YANG module from network function. More details in `ansible/README.md`.

Version `0.4.1`
1) New overlay topology for IP VPN (IPv4 and IPv6) is created. It starts with `ip_vpn_` prefixi and located within `topology` folder.
2) Files for EVPN (E-LAN) toplogies are slightly modified.
3) Varios updated in `README.md` files across sub-folders.
4) Underlay topology `sp_underlay.txt` is updated with the metic values of the interfaces.
5) Template for configuration of Nokia for `underlay_mpls` roles is updated to include metric values.
6) File `main_final.yml` from `underlay_mpls/tasks` is updated to apply via `eos_config` on Arista EOS network functions configuration commands not available in OpenConfig YANG modules.

Version `0.4.2`
1) Configuration of Nokia SR OS for `underlay_mpls` role is converted to NETCONF/YANG using Nokia native YANG modules.
2) Configuration of Nokia SR OS for `underlay_bgp` role is converted to NETCONF/YANG using Nokia native YANG modules.

Version `0.5`
1) Automation for IP VPN service creation based on IETF L3VPN SVC (RFC 8299) is added. Check `ansible\README.md` for details how to launch.
2) IETF L3VPN SVC service reqest is located in `ansible\vars` folder and starts with `service_ip_vpn_` prefix.
3) Information about default route target and route distinguishers range allocated for automated services is stored in `ansible\group_vars\all\main.yml`
4) In `ansible\files\ietf` folders there are all IETF YANG models including L3VPN and L2VPN SVC clonned from official GitHub of Yang.
5) To role `underlay_bgp` added configuration of default route policy (action: accept_route) to be used later for customer route fileting.
6) Added customer provisioning for IP VPN using `ansible\customer_equipment.yml`.

Version `0.5.1`
1) Added automated configuration of SNMP version 3. More details in `ansible/README.md`.

Version `0.5.2`
1) Management IP addresses are changed to IPv6, so from now on the communication between management host and all VNFs is over IPv6.
2) File `hosts` with actual state of project's `/etc/hosts` is added to `files` folder.

Version `0.6`
1) Added monitoring using InfluxData TICK and Grafana. Automated installation and operation over `management_cloud.yml` playbook. More details in `ansible\README.md`.
2) OOB topology `topology/oob_management.txt` is updated with containers' network (Docker bridge).
3) Mapping of IP to VNF hostname for OOB is stored in `ansible/vars/etc_hosts.yml`.
4) Added ansible role to update `/etc/hosts` with proper OOB IPv6 addresses of network VNFs. More details in `ansible\README.md`.
5) Added `topology/monitoring_architecture.txt` scheme with explanation how the Service Provider Fabric is monitored.

Version `0.6.1`
1) Added automated generation of self-signed certificate on InfluxDB.
2) Communication between Telegraf and InfluxDB is moved to HTTPS.
3) Communication between Grafana and InfluxDB is moved to HTTPS.
4) Communication between Grafana and user is moved to HTTPS.
