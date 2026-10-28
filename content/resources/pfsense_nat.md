# NAT on pfSense
This assumes that you have a basic knowledge of subnetting and NAT.


## 1:many NAT
This is where you have one public IP and multiple LAN ips.

The WAN interface can be DHCP or static

![pfSense DHCP configuration](/static/images/pfsense_dhcp.png)

Set a static IP on the LAN

![pfSense LAN configuration](/static/images/pfsense_lan.png)


Set Automatic outbound nat

![pfSense automatic outbound NAT](/static/images/pfsense_1/many_nat.png)

Done

----



## 1:1 NAT
You do not have to specify static WAN ip but you really should!

![pfSense static WAN configuration](/static/images/pfsense_static.png)

In this example the pfsense is on the blue team network (10.20.0.0/16) with the static IP 10.20.123.1/16

Set static IP on the LAN

![pfSense LAN configuration](/static/images/pfsense_lan.png)

Go to the NAT settings. Firewall > NAT > Add

![Blank pfSense NAT settings](/static/images/pfsense_nat_blank.png)

Create a new rule mapping the first external address (in this case 10.20.123.1) to the first internal address (192.168.1.1) and use the subnet mask for the internal network (24)

![pfSense 1:1 NAT rule](/static/images/pfsense_1/1_nat_rule.png)


Finally you need to make the pfsense respond to ARP for those IPs.
Firewall > Virtual IPs > Add.

![pfSense proxy ARP configuration](/static/images/pfsense_proxy_arp.png)

Done
