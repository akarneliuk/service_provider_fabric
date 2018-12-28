# Automated Service Provider Fabric

This part is dedicated for automated deployment of:
1) Underlaying MPLS infrastructure (ISIS, Segment Routing, TI-LFA)
2) Underlaying BGP signaling (VPN-IPV4/VPN-IPV6 UNICAST, EVPN address-families)
3) Overlay services (IP VPN (IPv4/IPv6), EVPN (L2/L3))

# Powered by OpenConfig

Wherever possible, OpenConfig YANG models are used. More preciesly OpenConfig is used:
1) In Arista EOS and Cisco IOS XR for configuration of underlay MPLS fabric running ISIS as IGP with Segment Routing extensions

Exceptions:
1) As of today (27.12.2018) the most current Nokia SR OS release 16.0.R5 doesn't support Segment Routing in OpenConfig YANG models. Nevertheless the common templates `openconfig-interfaces.j2` and `openconfig-network-instance.j2` are prepared and can properly configure ISIS on all NOSes including Nokia SR OS. As soon as Nokia's OpenConfig YANG models will support Segment Routing, the Ansible playbooks will be changed so that Nokia start use OpenConfig as well. Temporary Nokia is using CLI-based configuration using `sros_config` Ansible module.

# How to use

There are several possible options how you can automatically deploy Service Provider Fabric. The prerequisite is copy the initial configuration files called `sp_{{ hostname }}_initial.conf` from `files` folder to the running config of your network functions. Then use the following tags:
1) To deploy undelay routing (ISIS) and MPLS (Segment Routing) use `ansible-playbook --inventory=hosts --tags=underlay_mpls`
2) To deploy undelay BGP signaling use `ansible-playbook --inventory=hosts --tags=underlay_bgp`
3) To deploy the whole underlay infrastructure (ISIS + Segment Routing + BGP) use `ansible-playbook --inventory=hosts --tags=underlay`

# Temporary limitations

Currently only `underlay_mpls` or `underlay` tags are working to build ISIS + Segment Routing fabric. The `underlay_bgp` knob is yet to come.
