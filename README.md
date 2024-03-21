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
We can start by observing ICMP traffic (Internet Control Messaging Protocol), which we'll do by typing "ICMP" into the search bar
</p>
<br />

<p>
<img src=https://github.com/CSanders000/azure-network-protocols/assets/161166823/9050cf44-0320-4eea-a723-587e5bf931dc"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src=https://github.com/CSanders000/azure-network-protocols/assets/161166823/c23e30f6-6d6a-4d9e-a7c7-3ca9381cef79"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src=https://github.com/CSanders000/azure-network-protocols/assets/161166823/c179f8b9-8d9d-482c-a422-c68cf7d53565"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src=https://github.com/CSanders000/azure-network-protocols/assets/161166823/07287040-0b8c-4fdf-800b-9f811a043fe4"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src=https://github.com/CSanders000/azure-network-protocols/assets/161166823/ca1430ef-251e-4429-bc73-00f9b2caf9b9"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src=https://github.com/CSanders000/azure-network-protocols/assets/161166823/a2b39916-1efd-4cc0-a4a1-8338fc7f22da"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src=https://github.com/CSanders000/azure-network-protocols/assets/161166823/45137a9e-fe72-4945-a4b0-b66b98c03127"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src=https://github.com/CSanders000/azure-network-protocols/assets/161166823/55f4b266-a1f9-4553-bf58-e4aef2ebbca9"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src=https://github.com/CSanders000/azure-network-protocols/assets/161166823/c60933f1-53b7-4f40-95d0-e6139035e300"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />



