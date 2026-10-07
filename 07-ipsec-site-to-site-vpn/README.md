# For creating the IPsec VPN tunnel, the first step I did was configure IKE Phase 1 on HQ-R1
<br>
<img width="524" height="235" alt="image" src="https://github.com/user-attachments/assets/ddea2be4-493c-4e74-b656-31d025c69441" />
<br>
<br>

# The below image shows that policy 10 was created 
<br>
<img width="668" height="177" alt="image" src="https://github.com/user-attachments/assets/21a1223c-1919-40d0-bae2-8419eb8e8840" />
<br>
<br>


# Next was to create the transform set on the HQ router
<br>
<img width="552" height="60" alt="image" src="https://github.com/user-attachments/assets/fab1e1a4-e6b0-466b-a297-412f10d8661c" />
<br>
<br>


# I then defined what traffic should enter the VPN using the below ACL rule
<br>
<img width="612" height="59" alt="image" src="https://github.com/user-attachments/assets/6db436d6-0bcf-4c25-b1d4-72bfbc0caaa1" />
<br>
<br>


# Next a crypto map was created as a blueprint to glues all the different pieces of an IPsec policy together
<br>
<img width="506" height="133" alt="image" src="https://github.com/user-attachments/assets/3f41ccff-5e52-497b-a9fc-d3d6a60efdac" />
<br>
<br>

# Then that map was applied to the WAN interface of HQ-R1
<br>
<img width="799" height="167" alt="image" src="https://github.com/user-attachments/assets/ebb764c3-2b41-4092-b3e5-780f6c2e8a1d" />
<br>
<br>

# After completing the configurations on the HQ branch, it was time to do the same on Branch 1
<br>
## IKE Phase 1 on BR1-R1
<br>
<br>
<img width="495" height="289" alt="image" src="https://github.com/user-attachments/assets/599e21db-b47a-4b91-a981-acab453d6e03" />

<br>
## Created a transform set on BR1-R1 router
<br>
<img width="574" height="76" alt="image" src="https://github.com/user-attachments/assets/20b4cd3d-06be-4969-a2b0-45146b4a41bd" />

## Interesting traffic ACL
<br>
<img width="609" height="57" alt="image" src="https://github.com/user-attachments/assets/e00584d3-50c8-44de-bb06-24e04ac63fea" />

## Then finally the crypto map being created and applied to the WAN interface of BR1-R1
<img width="776" height="403" alt="image" src="https://github.com/user-attachments/assets/280ce0b2-d76c-4da2-9824-e406c8444c6c" />

<br>
<br>
Pings from USER 3 in HQ to USER 5 in Branch 1 are successful
<br>
<img width="479" height="293" alt="image" src="https://github.com/user-attachments/assets/9d149a2c-67e9-444e-b0d3-d7e24fd9f761" />
<br>
<br>

## Now as you can see from the output below the pkts encaps and decaps counters are going up, showing that the VPN tunnel is working 
<br>

<img width="551" height="313" alt="image" src="https://github.com/user-attachments/assets/6cce42df-4920-4186-be54-2c87d9a57583" />

<br>

To create the IPsec connection between HQ and BR-2 the above steps where repeated but the respective changes were made
<br>
<br>
Here is a look at the crypto map on HQ router after BR2's network was added
<br>
<img width="736" height="553" alt="image" src="https://github.com/user-attachments/assets/d76f445b-b0fa-493f-9c53-73225bcc2b3a" />

<br>
<br>
And to verify connectivity USER 3 on HQ can ping USER 1 on BR2 through the established hub and spoke setup
<img width="476" height="221" alt="image" src="https://github.com/user-attachments/assets/1fca0947-3fe5-49c9-8187-f209cdd9924f" />
<br>
<br>
<img width="579" height="227" alt="image" src="https://github.com/user-attachments/assets/08ce9f87-4619-4243-8021-4c5418b8bec5" />

