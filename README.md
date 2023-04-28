<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<!-- <h2>Video Demonstration</h2>

- ### [YouTube: Azure Virtual Machines, Wireshark, and Network Security Groups](https://www.youtube.com) -->

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDP, DNS, DHCP, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Created a Resoure Group and a Windows 10 & a Linux Virtual Machine
- Using RDP I installed Wireshark on the Win 10 VM
- Observed ICMP Traffic
- Denied/Re-Enabled ICMP Traffic Using NSG
- Observed SSH Traffic
- Observed DHCP Traffic
- Observed DNS Traffic
- Observed RDP Traffic

<h2>Actions and Observations</h2>

<strong><p>Resource Group</p></strong>
<p>  
<img src="https://i.imgur.com/ucAkAQ1.png" height="80%" width="80%" alt="Created Resource Group"/>
</p>
<p>
Created a Resource Group with the name RG-Lab to house the two Virtual Machinces that are needed for this lab
</p>
<br />

<strong><p> Virtual Machine-Windows</p></strong>
<p> 
<img src="https://i.imgur.com/yewFDfJ.png" height="80%" width="80%" alt="Windows VM"/> 
</p>
<br />
<strong><p>Virtual Machine-Linux</p></strong> 
<p> 
<img src="https://i.imgur.com/nyG1LnJ.png" height="80%" width="80%" alt="Windows VM"/> 
</p>
 <br />
 
<strong><p>Network Topology</p></strong>
<p>
<img src="https://i.imgur.com/Lvm1h7W.png" height="80%" width="80%" alt="Network Topology"/> 
</p>
<p>
Within Azure Network Watcher I observed my Network Topology; to make sure that my vm.net was connected to both of the VMs correctly. 
</p>
<br />

<strong><p>RDP to Remote into Windows 10 VM</p></strong>
<p>  
<img src="https://i.imgur.com/jaCF2Sx.png" height="80%" width="80%" alt="RDP into Windows VM"/>
</p>
<p>
Connected via RDP to the Win 10 vm. Logged in with the username and password that was created when the VM was created initally. Installed Wireshark once the VM fished loading. 
</p>
<br />

<strong><p>Monitoring ICMP Traffic</p></strong>
<p>  
<img src="https://i.imgur.com/k0TTEZr.png" height="80%" width="80%" alt="Ping Linux IP"/>
</p>
<p>
Using the Ping Command I observed ICMP traffic in Wireshark on the Win 10 VM using the IP address of the Linux VM
</p>
<br />

<strong><p>Azure Network Security Groups</p></strong>
<p>  
<img src="https://i.imgur.com/I06nuRw.png" height="80%" width="80%" alt="Deny ICMP"/>
</p>
<p>
Denied all incoming ICMP traffic utilizing Azure Network Security Groups 
</p>
<br />

<strong><p>ICMP Traffic</p></strong>
<p>  
<img src="https://i.imgur.com/ZNERKAu.png" height="80%" width="80%" alt="Ping-t Denied ICMP"/>
</p>
<p>  
<img src="https://i.imgur.com/tXg4Mjc.png" height="80%" width="80%" alt="Allowed ICMP Linux IP"/>
</p>
<p>
Using Ping -t command which allows for a continous ping to the selected host. I observed the traffic ICMP traffic timeout as a result of the incoming ICMP traffic being denied. I also observed the traffic continue once the ICMP traffic was allowed through again.
</p>
<br />

<!--<p>Azure Network Security Groups</p>
<p>  
<img src="https://i.imgur.com/I06nuRw.png" height="80%" width="80%" alt="Deny ICMP"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br /> -->

<strong><p>SSH Traffic</p></strong>
<p>  
<img src="https://i.imgur.com/JgobYGg.png" height="80%" width="80%" alt="Deny ICMP"/>
</p>
<p>
Using Wireshark to observe SSH traffic over the network. I used SSH to get into our Linux VM using the login credentials I created for the Win10 VM 
</p>
<br />

<strong><p>DHCP Traffic</p></strong>
<p>  
<img src="https://i.imgur.com/8dne7Yp.png" height="80%" width="80%" alt="Deny ICMP"/>
</p>
<p>
Through Wireshark I filtered traffic for the networking protocol DHCP. We used the ipconfig /renew command to get another IP Address and watch the incoming and outgoing traffic as a result.
</p>
<br />

<strong><p>DNS Traffic</p></strong>
<p>  
<img src="https://i.imgur.com/z84zJdZ.png" height="80%" width="80%" alt="Deny ICMP"/>
</p>
<p>
In Wireshark I filtered for DNS traffic. We used the networking protocol nslookup to see what google.com and disney.com IP addresses were.
</p>
<br />

<strong><p>RDP Traffic</p></strong>
<p>  
<img src="https://i.imgur.com/QOnqtPH.png" height="80%" width="80%" alt="Deny ICMP"/>
</p>
<p>
Through Wireshark I filtered traffic for tcp.port ==3389 which is the RDP port. I see constant traffic going back and forth because the RDP session is open by way of us using it to remote into the Win10 VM. 
</p>
<br />
