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
<img width="495" height="289" alt="image" src="https://github.com/user-attachments/assets/599e21db-b47a-4b91-a981-acab453d6e03" />


