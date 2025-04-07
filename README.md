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

Now, the DNS setup is complete! 🚀

