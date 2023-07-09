# azure-network-protocols

<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Video Demonstration</h2>

- ### [YouTube: Azure Virtual Machines, Wireshark, and Network Security Groups](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDP, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Step 1
- Step 2
- Step 3
- Step 4

<h2>Actions and Observations</h2>

<p>
<img src="https://i.imgur.com/ONhk5Gl.png" height="80%" width="80%" alt="Resource Group"/>
</p>
<p>
First, we create our first Resource Group called AZ-Compute-Network where all of our resources will be stored.
</p>
<br />

<p>
<img src="https://i.imgur.com/ywrHP61.png" height="80%" width="80%" alt="Virtual Machine"/>
</p>
<p>
Here we are going to create our first virtual machine within Azure. Our first virtual machine is going to be a Windows 10 VM called VM1, and the username is going to be my first name and last initial, "NicholasV".
</p>
<br />

<p>
<img src="https://i.imgur.com/zLY0QZJ.png" height="80%" width="80%" alt="Linux Virtual Machine"/>
</p>
<p>
Next, we are going to create a Linux Virtual Machine using the Ubuntu Server, and make sure we are on the sane virtual network as VM1 in the following step.
</p>
<br />

<p>
<img src="https://i.imgur.com/nb4LZmG.png" height="80%" width="80%" alt="VM1 vnet"/>
</p>
<p>
Virtual Network VM1, make sure VM2 is on the same network as VM1 by selecting, "VM1-vnet/default". This step is important as we will be able to analyze the traffic on the same network when we ping VM2's private IP Address and view it through <a href=https://www.wireshark.org/download.html>Wireshark</a> the traffic analyzer tool which we will download in a future step.
</p>
<br />

<p>
<img src="https://i.imgur.com/yqwKQqO.png" height="80%" width="80%" alt="VM1 Public IP Address"/>
</p>
<p>
Now that we have created our virtual machines, we can go ahead inside Microsoft Azure and click on VM1's virtual machine, and look for VM1's public IP address. We're going to need this to remotely log into VM1's virtual machine using Microsoft Remote Desktop on Mac which you can download for free inside the App Store. After Microsoft Remote Desktop has finished downloading, we will now open it, copy and paste the public IP address into the "PC name" section in the following step.
</p>
<br />

<p>
<img src="https://i.imgur.com/ygwJjhw.png" height="80%" width="80%" alt="Microsoft Remote Desktop settings"/>
</p>
<p>
While we still have Microsoft Remote Desktop open, we want to make sure everything is set up as is inside the screenshot and click add. Double check that you have the correct public IP address so that we can connect to our Windows virtual machine.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

</p>
<br />
