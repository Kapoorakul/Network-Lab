# Network-Lab
Networking Labs for Routing and Switching

I created this lab while I was learning MPLS-VPN technology. I have included the screenshot of the topology as well.

Requirements:
1. GNS3  --> https://gns3.com/software/download
2. Cisco Router - C7200 (used in the lab)
3. IOS Image --> Cisco IOS Software, 7200 Software (C7200-ADVENTERPRISEK9-M), Version 12.4(24)T, RELEASE SOFTWARE (fc1)

Note: When you download GNS3, you do not get the IOS images for the routers. Either, you can pay for it or find it online (Just Google it)

Prerequisite:
Following is a very good Cisco documentation, which get me started. Please read the following
http://www.cisco.com/c/en/us/td/docs/ios-xml/ios/mp_l3_vpns/configuration/15-mt/mp-l3-vpns-15-mt-book/mp-bgp-mpls-vpn.html

After, you have read the documentation, then proceed to lab and start by unzipping the file i have uploaded "mpls-vpn-lab.7z". Open the lab with GNS3 and play around. You can also get the router configurations located under <yourcurrent-working-directory>/mpls-vpn-lab\project-files\dynamips\configs

Goal: The goal of this lab is to make Customer A,B,C & D talk to their respective remote sites located at the other end of the Service Provider's Network. For Instance:
          Customer A -----Service Provider Network ------ Customer A
          
I have used many routing protocols in this lab (Both IGP and EGP) such as RIP, EIGRP, OSPF and BGP. 
The service providers network is running EIGRP (AS 100) as its IGP, and on top of it I am running MPLS on the interfaces which are participating in the MPLS. The service providers network contains PE and P routers (you should be able to learn about P and PE from the cisco docs).  The two PE routers on the edge of the service providers network and IBGP neighbors which converth learned routes (from customers) into vpnv4 routes and then MPLS carries them across the network to the other iBGP peer.
I am using different routing protocols to connect the CE and PE routers, for instance: 
Customer A use RIP to connect to PE
Customer B use EIGRP to connect to PE
Customer C use OSPF to connect to PE
Customer D use BGP to connect to PE

Every customer has end to end connectivity with its remote site. You can verify that by pinging the loopback network of the remote customer site
for instance, for customer B, I will ping 7.7.7.7 from router R1.
