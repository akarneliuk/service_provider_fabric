# Description
- File `sp_underlay.txt` contains the definition of the underlay topology with hostnames, interfaces, IP addresses, BGP ASN and high description of the protocols.
- File `evpn_elan_overaly.txt` contains the design of the customer L2 connectivity over EVPN service.
- File `evpn_elan_customer.txt` shows the emulation of customer sites of EVPN (E-LAN) service.
- File `oob_management.txt` contains information about management topology and IP addresses used for automation.
- File `ip_vpn_overaly.txt` contains the design of the customer IP VPN service including eBGP peering for PE-CE both for IPv4 and IPv6 address families.
- File `ip_vpn_customer.txt` shows the emulation of customer sites of IP VPN service including IPv4/IPv6 subnets, which customer advertizes over eBGP to PEs of Service Provider Fabric.
- File `monitoring_architecture.txt` contains explanation how InfluxData TICK + Grafana are used for monitoring health of Service Provider Fabric.


# VNF
- `SR1`: Nokia VSR (vSIM) 
- `XR1`: Cisco IOS XRv
- `EOS1`, `EOS2`: Arista vEOS-lab
- `VX4`: Cumulus VX
