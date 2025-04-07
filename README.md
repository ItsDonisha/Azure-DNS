<p align="center">
<img src="https://i.imgur.com/CtGfsq8.png" alt="osTicket logo"/>
</p>

<h1>Building Intuition for DNS</h1>
In this lab, we will explore and experiment with the Domain Name System (DNS) to gain a deeper understanding of how it operates and supports network communication. Through practical exercises, we aim to enhance our knowledge of DNS functionality and its critical role in translating domain names into IP addresses.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- DNS

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- A Virtual Machine with Active Directory
- A Client VM joined to your Network 

### Simple Steps to Configure DNS Records  

1. **Start the VMs** – Power on DC-1 and Client1, then RDP into Client1.  
2. **Test Name Resolution** – Open PowerShell as an administrator on Client1 and try to ping "mainframe." It will fail.  
3. **Check DNS Cache** – Run `ipconfig /displaydns` and `nslookup mainframe` to confirm that "mainframe" is not in the DNS cache.  
4. **Create a DNS A-Record** – On DC-1, open **DNS Manager** and navigate to **DC-1 > Forward Lookup Zones > mydomain.com**.  
   - Right-click mydomain.com and select **New Host (A or AAAA)**.  
   - Set the **Name** as **mainframe** and the **IP Address** as **DC-1’s private IP**.  
   - Save the record.  
5. **Verify DNS Resolution** – Return to Client1 and ping "mainframe" again. This time, it should succeed.  
6. **Update the A-Record** – On DC-1, change the **A-record for "mainframe"** to **8.8.8.8**.  
7. **Test the Change** – Back on Client1, ping "mainframe" again. It will still resolve to the old IP.  
8. **Check Cached DNS** – Run `ipconfig /displaydns` on Client1 to confirm that "mainframe" still points to the old IP.  
9. **Flush DNS Cache** – Run `ipconfig /flushdns` to clear the old record.  
10. **Confirm Update** – Ping "mainframe" again. Now, it should resolve to **8.8.8.8**.  
11. **Create a CNAME Record** – On DC-1, open **DNS Manager** and navigate to **mydomain.com**.  
    - Right-click and select **New Alias (CNAME)**.  
    - Set **Alias Name** as **explore** and **FQDN** as **www.google.com**.  
    - Save the record.  
12. **Test CNAME Resolution** – On Client1, ping "explore" to confirm it resolves to **www.google.com**.  
13. **Verify with nslookup** – Run `nslookup explore` on Client1 to confirm the CNAME record is working.  

Now, the DNS setup is complete! 

<h2>Picutre Examples</h2>

![image](https://github.com/user-attachments/assets/4d6f3633-beb6-4910-b732-3ce3eebb7342)

![image](https://github.com/user-attachments/assets/a2449f93-1173-43f9-8dea-3a449ce1d5fa)

![image](https://github.com/user-attachments/assets/9c26279b-e646-4122-872d-23e69ab16d94)

![image](https://github.com/user-attachments/assets/ccb38301-fba6-44d6-87e4-ab7a82d44212)

![image](https://github.com/user-attachments/assets/31e9ccca-93d3-4e88-bb70-74b57fb46af4)

![image](https://github.com/user-attachments/assets/4832ed1c-2862-4aad-bfdc-707fc18b69ec)

![image](https://github.com/user-attachments/assets/7d96a3e3-c633-46ae-8b19-b3ebd8494eae)

![image](https://github.com/user-attachments/assets/1e4408a2-2d57-4cee-b7fa-7795e843e838)

![image](https://github.com/user-attachments/assets/9ce30660-fa78-4d07-90ef-b68c4ed711dd)









