<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

Step 1: Apply NSGs to Each VM
VM1 (Web server):

Create an NSG and apply it to the NIC of VM1.
Add an inbound rule allowing traffic from VM1’s IP (or its subnet) to VM2 on port 1433.
Add a rule denying all other traffic.
VM2 (Database server):

Create an NSG and apply it to the NIC of VM2.
Add an inbound rule allowing traffic from VM1 on port 1433.
Add a rule denying all other inbound traffic.

Step 2: Use NSG Flow Logs to Inspect Traffic
Enable NSG Flow Logs for both VM1 and VM2’s NSGs.
Monitor traffic between VM1 and VM2 to ensure traffic on port 1433 is allowed.
Verify any traffic from VM3 is being denied.

Step 3: Use Packet Capture to Inspect Specific Traffic
Enable Packet Capture on VM1 to see the network traffic flowing to VM2.
Capture the traffic on port 1433 to verify the communication.

Step 4: Use Traffic Analytics
Use Traffic Analytics to get an overview of traffic patterns between VM1 and VM2, as well as identify any denied traffic.

<h2>Actions and Observations</h2>

<p>
<img src="https://i.imgur.com/LOEJ5JD.jpeg"/>
</p>
<p>
A-Record Exercise
Connect/log into DC-1 as your domain admin account (mydomain.com\jane_admin)
Connect/log into Client-1 as an admin (mydomain\jane_admin)
From Client-1 try to ping “mainframe” notice that it fails
Nslookup “mainframe” notice that it fails (no DNS record)
Create a DNS A-record on DC-1 for “mainframe” and have it point to DC-1’s Private IP address
Go back to Client-1 and try to ping it. Observe that it works


</p>
<br />

<p>
<img src="https://i.imgur.com/6zA1Aij.jpeg"/>
</p>
<p>
Local DNS Cache Exercise
Go back to DC-1 and change mainframe’s record address to 8.8.8.8
Go back to Client-1 and ping “mainframe” again. Observe that it still pings the old address
Observe the local dns cache (ipconfig /displaydns)
Flush the DNS cache (ipconfig /flushdns).
Observe that the cache is empty (ipconfig /displaydns)
Attempt to ping “mainframe” again. Observe the address of the new record is showing up

</p>
<br />

