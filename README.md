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
<img src="https://i.imgur.com/43MprWM.png" height="80%" width="80%" alt="Remote Desktop username and password"/>
</p>
<p>
Enter your username and password that you created in Microsoft Azure and click connect, mine is my first name and last initial.
</p>
<br />

<p>
<img src="https://i.imgur.com/fobm1Z9.png" height="80%" width="80%" alt="Windows loading screen"/>
</p>
<p>
<p>After you have entered your credentials successfully, you should see the loading screen on the Windows virtual machine showing your username that you created. In this example, my first name and last initial.</p>
</p>
<br />

<p>
<img src="https://i.imgur.com/PYXDTAH.png" height="80%" width="80%" alt="Wireshark website"/>
</p>
<p>
Now that we are logged in the Windows 10 virtual machine, it's time to download Wireshark. Download and install the "Windows Intel Installer" version in your Windows 10 virtual machine.
</p>
<br />

<p>
<img src="https://i.imgur.com/ITyDstg.png" height="80%" width="80%" alt="private IP address for virtual machine 2"/>
</p>
<p>
After Wireshark has been downloaded and installed, we're going to go back to Microsoft Azure and inside of your Resource Group, click on the second virtual machine that we created earlier, look for the Networking tab, and click on it and take note of the private IP address. In this example, it will be 10.0.0.5. We're going to analyze the traffic inside Wireshark when we ping this address from our first virtual machine (VM1) that we created.
</p>
<br />

<p>
<img src="https://i.imgur.com/TDhxFWt.png" height="80%" width="80%" alt="Wireshark traffic analyzer"/>
</p>
<p>
Next, we will open Wireshark and filter the traffic by ICMP (Internet Control Messaging Protocol) a protocol that devices within a network use to communicate problems with data transmission. I have opened Command Prompt inside of our virtual machine with wireshark installed. If you look carefully, I have set a perpetual ping from VM1 to VM2's private IP address inside of Command Prompt and you can see the requests and replies under the info section inside of Wireshark. This indicates that our virtual machine is receiving the data packets on the network.
</p>
<br />

<p>
<img src="https://i.imgur.com/og8xaPY.png" height="80%" width="80%" alt="Virtual Machine 2 Network settings inside of Azure"/>
</p>
<p>
While our virtual machine (VM1) continues to send pings to VM2's private IP address, we're going to head back into Microsoft Azure and click on VM2, and go to Settings, and click on Network. We are going to add an Inbound Rule, this is where we are going to set up our firewall inside of our NSG (Network Security Group) to block any incoming traffic to VM2's IP address. 
</p>
<br />

<p>
<img src="https://i.imgur.com/4mSBFId.png" height="80%" width="80%" alt="Network Security Rule"/>
</p>
<p>
This is where we are going to set up our Inbound Network Security Rule. This allows for us to customize our firewall settings based on the protocol we choose, in this case, we will set it up based off of the ICMP protocol since that is the protocol we have filtered our traffic by inside of Wireshark so we can actually analyze and view the data. Since we don't want any traffic going to VM2's private IP address, we are going to set our Action to Deny inside of our Inbound Network Security Rule to block any traffic going to that IP address. We are also going to set the priority to 200 so that it's top priority over the other rules, set up a custom name for our inbound rule just so we have a description of what our custom rule entails.
</p>
<br />

<p>
<img src="https://i.imgur.com/JUTu1dG.png" height="80%" width="80%" alt="Inbound Rule Priority"/>
</p>
<p>
After we have successfully set up our custom firewall settings, you can see based on the category what each custom rule is set to based on how we set everything up from our previous example. If we head over to Wireshark, we should now see the traffic being blocked inside of the traffic analyzer and see that there isn't a reply from VM2 in the following example.
</p>
<br />

<p>
<img src="https://i.imgur.com/7leb5fN.png" height="80%" width="80%" alt="Wireshark analyzer showing no response from virtual machine 2"/>
</p>
<p>
As previously discussed, if you take a look at Command Prompt, it says, "Request timed out", and in Wireshark, it says "no response found!". This means that our firewall is active and VM2 is no longer replying back to any pings to its private IP address because our firewall settings that we set up earlier has blocked and denied that traffic. 
</p>
<br />

<p>
<img src="https://i.imgur.com/AODyiJh.png" height="80%" width="80%" alt="Inbound Security Rule settings inside of Azure"/>
</p>
<p>
If we head back to our Inbound Security Rule where we set up our firewall, when we set the action to Allow, VM2 can now start receiving ping requests to its private IP address again.
<img src="https://i.imgur.com/mdkCd5Y.png" height ="80%" width="80%" alt="Wireshark"/>
</p>
<br />
<br />

<p>
<img src="https://i.imgur.com/z5FZSba.png" height="80%" width="80%" alt="Remote Linux Secure Shell"/>
</p>
<p>
In this step, we're going to go over the SSH protocol, port 22. This allows us to login to a remote server to execute commands and data transfer from one machine to another machine. We created a Linux virtual machine using the Ubuntu server inside of our Azure setup. In this example we remotely login to VM2's secure shell and if you remember from our previous setup for this VM, the username that we created was guest123. We're going to go ahead and filter the traffic inside of Wireshark to port 22 so we can analyze the traffic in for this protocol in the next steps.
</p>
<br />

<p>
<img src="" height="80%" width="80%" alt=""/>
</p>
<p>

</p>
<br />

<p>
<img src="" height="80%" width="80%" alt=""/>
</p>
<p>

</p>
<br />

<p>
<img src="" height="80%" width="80%" alt=""/>
</p>
<p>

</p>
<br />

<p>
<img src="" height="80%" width="80%" alt=""/>
</p>
<p>

</p>
<br />
