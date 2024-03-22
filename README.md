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

- Set up our resources in Azure
- Observe ICMP Traffic
- Observe SSH Traffic
- Observe DHCP Traffic
- Observe DNS Traffic
- Observe RDP Traffic

 <h2>Prerequisites </h2>

- Create a virtual machine on Azure running Windows 10 OS (VM1)
- Create a virtual machine running on Linux (Ubuntu). Make sure they are connected to the same virtual network. (VM2)

<h2>Actions and Observations</h2>

<p>
<img src=https://github.com/CSanders000/azure-network-protocols/assets/161166823/f26dd965-2bd8-4d6a-92b9-73b067d5e4ae"/>
</p>
<p>
When we connect into VM1, the first thing we will do is go to Edge to download and install Wireshark. Once it's running, it will ask where it will capture from. We'll click ethernet and click the blue icon under file on the top left. This will take us to the screen pictured above where we are getting a spam of all the background traffic occuring on our network. 
</p>
<br />

<p>
<img src=https://github.com/CSanders000/azure-network-protocols/assets/161166823/6e608195-55a4-4169-ae10-5069e522e844"/>
</p>
<p>
We can start by observing ICMP traffic (Internet Control Messaging Protocol), which we'll do by typing "ICMP" into the search bar. At first we wont see any traffic, but when we open the command prompt ping VM2's private IP address we will see the communication between the servers. We'll see the source of the ICMP packet, it's destination, as well as other information. We can also ping a website such as www.google.com and see that we send the packet out, and then the computer at the destination will send a reply.
</p>
<br />

<p>
<img src=https://github.com/CSanders000/azure-network-protocols/assets/161166823/9050cf44-0320-4eea-a723-587e5bf931dc"/>
</p>
<p>
What we'll do now is initiate a perpetual ping to VM2 from VM1 by typing "ping (VM2 IP address) -t". We will then see a constant stream of traffic in the command prompt and Wireshark. 
</p>
<br />

<p>
<img src=https://github.com/CSanders000/azure-network-protocols/assets/161166823/c23e30f6-6d6a-4d9e-a7c7-3ca9381cef79"/>
</p>
<p>
Now we will disable the incoming pings from VM1 on VM2 using the network security group function in Azure to observe what happens to the traffic. So we'll minimize our remote connection, go to Azure, search for "remote security group", click on VM2, and then go to inbound security rules. From here we can click "Add", then select ICMP under Protocol and deny under Action. We can name it whatever we want but we will press Add.
</p>
<br />

<p>
<img src=https://github.com/CSanders000/azure-network-protocols/assets/161166823/c179f8b9-8d9d-482c-a422-c68cf7d53565"/>
</p>
<p>
Now we can go back into our VM1 connection and oberve that in Wireshark we are only seeing echo requests to VM2, and in the command prompt we will start to see "Request timed out". This confirms that ICMP messages are now being denied by VM2's firewall.
</p>
<br />

<p>
<img src=https://github.com/CSanders000/azure-network-protocols/assets/161166823/07287040-0b8c-4fdf-800b-9f811a043fe4"/>
</p>
<p>
To undo this we can simply go minimize our connection and edit the rule we made. So we'll simply change the action back to allow, or we can delete the rule entirely.
</p>
<br />

<p>
<img src=https://github.com/CSanders000/azure-network-protocols/assets/161166823/ca1430ef-251e-4429-bc73-00f9b2caf9b9"/>
</p>
<p>
Once we save the changed to the rule we can go back to our VM1 connection and observe that the normal request and reply activity in Wireshark has resumed and the command prompt will show we're receiving a reply from VM2. We can then press "Ctrl + C" to stop the ping. 
</p>
<br />

<p>
<img src=https://github.com/CSanders000/azure-network-protocols/assets/161166823/a2b39916-1efd-4cc0-a4a1-8338fc7f22da"/>
</p>
<p>
Next we will observe Secure Shell activity. To start we will type ssh into our search bar, and observe there is no traffic. In the command prompt to "secure shell" into VM2 we will type "ssh (username for VM2)@(VM2's private IP address)" and hit enter. This will initiate the protocol and we will see traffic between our virtual networks. It will ask us if we want to continue which we will say yes. We will then type in the password for VM2. Once connected, everything we type into ssh will show traffic because VM1 is communicating with VM2 to tell it what letters we're typingt. If we type any commands we will see an increased amount of traffic. After observing, we can exit Secure Shell by typing "exit" and pressing enter.
</p>
<br />

<p>
<img src=https://github.com/CSanders000/azure-network-protocols/assets/161166823/45137a9e-fe72-4945-a4b0-b66b98c03127"/>
</p>
<p>
To observe DHCP (Dynamic Host Configuration Protocol) traffic, we will type "DHCP" into our searchbar on wireshark and hit enter. From here, we will go into our command prompt and type "ipconfig /renew". This will ask the DHCP server to renew our lease on our IP address, and as such we will see traffic between our computer and the server.
</p>
<br />

<p>
<img src=https://github.com/CSanders000/azure-network-protocols/assets/161166823/55f4b266-a1f9-4553-bf58-e4aef2ebbca9"/>
</p>
<p>
Next we will be observing DNS (Domain Name Service) traffic. So we can type either "DNS" or "udp.port==53" into the search bar. Then on the command prompt, we can simply search for the ip address of a website by using the nslookup command. So we'll search the IP addresses of a few websites of our choosing by typing "nslookup (website name) and pressing enter. When we do this we will see traffic between our virtual machine and the DNS server asking what the IP addresses are of these websites. 
</p>
<br />

<p>
<img src=https://github.com/CSanders000/azure-network-protocols/assets/161166823/c60933f1-53b7-4f40-95d0-e6139035e300"/>
</p>
<p>
Finally, we will observe RDP (Remote Desktop Protocol) by typing "RDP" or "tcp.port==3389" into our searchbar. When we press enter, we will see a constant stream of traffic due to the fact that we our physical computer is constantly communicating with VM1 to make the connection possible. We can also notice that if we type anything or even move the mouse around it will show an influx of traffic. 
</p>
<br />
