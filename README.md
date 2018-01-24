# vyos-bacsic-config
eth0: WAN
eth1: LAN

NAT inside- src-NAT
edit nat source rule 1
set outbound-interface eth0
set source address 192.168.1.0/24(LAN subnet)
set translation address masquerade

port-forwarding 
edit nat destination rule 1
set inbound-interface any
set destination address IP.WAN
set destination port 80
set translation address LAN.server
#set translation port 80
set protocol tcp

NAT hairpin
edit nat source rule 2
set destination address 192.168.1.0/24(LAN subnet)
set translation address masquerade
set outbound-interface eth1
set description Reflection

----------------------------
