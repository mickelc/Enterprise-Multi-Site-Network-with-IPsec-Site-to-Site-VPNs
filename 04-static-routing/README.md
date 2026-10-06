
Created a default static route from each branch's firewall to point to the connected routers

<img width="640" height="402" alt="image" src="https://github.com/user-attachments/assets/09fff912-c099-4629-add9-f0a405ff5235" />


Created a default route from the router to the vlans in each site and also advertised this default route into the OSPF area that was configured for each site


<img width="661" height="398" alt="image" src="https://github.com/user-attachments/assets/1aed739c-b4eb-492c-8985-a88a7fa4d546" />


<img width="451" height="60" alt="image" src="https://github.com/user-attachments/assets/6b00d054-6014-4378-a806-bbcebd82cf92" />


Verified that each site's core switch can now see that default route


<img width="552" height="241" alt="image" src="https://github.com/user-attachments/assets/1a314308-bc7a-483b-ba50-2d94b812c165" />


