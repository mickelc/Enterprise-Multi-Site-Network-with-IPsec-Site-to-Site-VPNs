On each site's firewall the implicit deny feature blocked ICMP traffic from the outside interface to the inside interface


<img width="832" height="282" alt="image" src="https://github.com/user-attachments/assets/541bb166-4197-4f24-960c-d61e8c94431a" />

The above output came from the command "packet-tracer input outside icmp 10.0.2.1 8 0 10.2.10.2 detailed"

This simulates an ICMP echo request entering the outside interface on the ASA from the router (BR2-R2 10.0.2.1) destined for my VLAN 10 PC (10.2.10.2)

So these two commands to allow pings from the PC to the router

1) "access-list OUTSIDE_IN extended permit icmp host 10.0.2.1 10.2.0.0 255.255.0.0"
2) "access-group OUTSIDE_IN in interface outside"
   
This allowed ICMP traffic entering the outside interface from router 10.0.2.1 to my internal 10.2.0.0/16 address space.

Here is a screenshot from the ASA showing the traffic now being allowed

<img width="779" height="294" alt="image" src="https://github.com/user-attachments/assets/22779abc-4dfb-43ac-9327-4b8658140efa" />


Proof from the PC


<img width="472" height="195" alt="image" src="https://github.com/user-attachments/assets/d2624159-036b-4ceb-86c5-ad62ad2d8d77" />

The above screenshot was taken from User 1 who is now able to reach the router connect to their site



<br>
<br>
Now while testing the IPsec tunnel connection in Section 07, I had to enable pings from HQ-LAN to BR1-LAN on both firewalls in each branch
Below is how it was done
<img width="1118" height="193" alt="image" src="https://github.com/user-attachments/assets/a27ba2aa-c0d1-4b00-84aa-6d3a82c30dab" />
<br>
<img width="1066" height="137" alt="image" src="https://github.com/user-attachments/assets/fcfa303a-318b-4cbd-98ce-4218ae98a4ce" />

<br>
Now I can successfully ping USER 5 (10.3.10.2 for this test) from USER 3 
<br>
<img width="471" height="268" alt="image" src="https://github.com/user-attachments/assets/05b4c30a-ae9c-4bdd-bb29-98c345429f11" />


