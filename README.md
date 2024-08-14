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

- Create sample file shares with various permissions
- Test file share access as a normal user
- Create a security group, assign permissions and test access

<h2>Actions and Observations</h2>

<p>
<img src="https://i.imgur.com/VSfeQmm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
This image shows the aftermath of making three different file shares, all with different permissions. This is done in the DC-1 database controller. The file shares are listed as: "read-access," "no-access," "write-access," and "accounting." The first three are made just as they sound, with the "read-access" file share being readable by domain users, but not edible. The "write-access" is made with read and write access for domain users. The "no-access" is only available to domain admins, who have read and write access. Accounting will be used later.
</p>
<br />

<p>
<img src="https://i.imgur.com/VOmhcQo.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Here we see the effect of trying to open the "no-access" file share as a regular user. We can't access it unless we're the domain controller. 
</p>
<img src="https://i.imgur.com/g0ZRhXY.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
This image shows us accessing the read-only file share.
<br />

<p>
</p>
<p>
The following screenshots show the creation of the "accountants" security group. The accountants security group is given read/write access to the "accounting" file share. Then, using a regular user, assign this user to the accountants security group. The final screenshot shows the accounting user having access to the accounting file share.
</p>
<img src="https://i.imgur.com/KicYm5N.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/TkB46Pl.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/jW8j9Lx.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
