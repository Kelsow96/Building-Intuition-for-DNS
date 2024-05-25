<h1> Building Intuition for DNS </h1>

<img src="https://github.com/Kelsow96/Building-Intuition-for-DNS/assets/169297569/6bfbaa31-0873-4da5-b0fd-0b950082a531" width="400" />

<h2> What is Active DNS? </h2>

DNS stands for Domain Name System. It's like the internet's address book. When you type a website's domain name (like google.com) into your browser, your computer uses DNS to look up the IP address associated with that domain. This process lets your computer connect to the correct server and load the website. DNS also plays a crucial role in email delivery, network communication, and other internet services by translating human-readable domain names into machine-readable IP addresses.
<br>
<br/>

<h2> Overview </h2>

In this tutorial we'll demonstrate and practice DNS (Domain Name System) management and troubleshooting tasks within a Windows environment by doing a few exercises.

A-Record Exercise:

- Establishing connectivity between machines using DNS. Creating an A-record to map a hostname ("mainframe") to an IP address. Verifying successful DNS resolution after creating the A-record.

Local DNS Cache Exercise:

- Understanding and observing local DNS caching on client machines. Modifying DNS records and observing the impact on DNS caching. Flushing DNS cache to clear outdated entries and force DNS resolution.

CNAME Record Exercise:

- Creating a CNAME (Canonical Name) record to alias one hostname to another. Testing DNS resolution using CNAME records. Verify the CNAME resolution using the ping and nslookup commands.

These exercises cover essential concepts such as DNS record types (A-record, CNAME), DNS resolution, local DNS caching, and troubleshooting DNS issues. They are valuable for IT professionals to understand and manage DNS infrastructure effectively.

<h2> Environments and Technologies Used: </h2>

- Microsoft Azure (Virtual Machines/Compute)
- DNS (Domain Name System) for managing hostname-to-IP address mappings
- Remote Desktop
- PowerShell
- Commands like nslookup, ping, ipconfig, and flushdns for DNS troubleshooting and management

<h2> Operating Systems Used: </h2>

- Windows 10
- Windows Server 2022

<h2> List of Prerequisites: </h2>

- Azure Account/Subscription
- Virtual Machines ([DC-1 and Client-1](https://github.com/Kelsow96/-Implementing-Active-Directory-On-Premises-in-Azure)) from previous tutorial and have Client-1 joined to the domain.

<h2> High-Level Steps: </h2>

- A-Record Exercise:
1. Log into DC-1 as your domain admin account.
2. Log into Client-1 as an admin.
3. Attempt to ping "mainframe" from Client-1 (it should fail).
4. Nslookup "mainframe" to confirm there's no DNS record.
5. Create a DNS A-record on DC-1 for "mainframe" pointing to DC-1’s Private IP address.
6. Ping "mainframe" from Client-1 again to verify it works.
 
- Local DNS Cache Exercise:
1. Change the mainframe's record address on DC-1 to 8.8.8.8.
2. Ping "mainframe" from Client-1 (it should still ping the old address).
3. Observe the local DNS cache on Client-1 (ipconfig /displaydns).
4. Flush the DNS cache (ipconfig /flushdns) and verify it's empty.
5. Ping "mainframe" again from Client-1 to see the new address.

- CNAME Record Exercise:
1. Create a CNAME record on DC-1 pointing "search" to "www.google.com."
2. Ping "search" from Client-1 and observe the CNAME record results.
3. Use nslookup on Client-1 to verify the CNAME record for "search."

<h2> Steps: </h2> 

- A-Record Exercise:

1. Log into DC-1 as your domain admin account.
  -

2. Log into Client-1 as an admin.
3. Attempt to ping "mainframe" from Client-1 (it should fail).
4. Nslookup "mainframe" to confirm there's no DNS record.
5. Create a DNS A-record on DC-1 for "mainframe" pointing to DC-1’s Private IP address.
6. Ping "mainframe" from Client-1 again to verify it works.
