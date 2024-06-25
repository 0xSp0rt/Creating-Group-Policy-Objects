<h1>Creating Group Policy Objects and Shared Data Access</h1>


<h2>Description</h2>
In this lab, we are going to walk through how to create Group policy Objects, Shared data access, Organizational Units and Users and using GPOs to restrict applications . Configuring and running this lab on an Hyper-v windows 10 virtual machine will help develop your understanding of how active directory and GPOs work.
<br />


<h2>Languages and Utilities Used</h2>

- <b>Windows server 2019</b> 
- <b>Windows 10 vm</b>
- <b>Hyper-V</b>
- <b>Remote Desktop Connection </b>


<h2>Program walk-through:</h2>


<p align="left">
Create a resource group on Azure: To do this, it's important to create and name the resource group for all the resource to be grouped in, for this demonstration we're using Rgroup-demo. <br/>
<img src="https://imgur.com/XAFCAx9.jpg" height="80%" width="80%" alt="Active Directory Azure homelab"/>
<br />
<br />
 Virtual network steps 1: Setting up a virtual network is important for setting up the Active directory domain server for later, setting up this virtual network allows us to configure our ip address and subnet reservation which could be useful for endpoints or vms trying to connect to the AD-DS server. <br/>
<img src="https://imgur.com/7Auvz4Q.png" height="80%" width="80%" alt="Active Directory Azure homelab"/>
<img src="https://imgur.com/7Auvz4Q.png" height="80%" width="80%" alt="Active Directory Azure homelab"/>
<img src="![ss4](https://github.com/0xSp0rt/Creating-Group-Policy-Objects/assets/145977590/2535fe05-3133-40b0-8b0a-509335defd5d)" height="80%" width="80%" alt="GPO"/>


 
 Virtual network steps 2: Created the virtual network under the Rgroup-demo resource group and named the virtual network "AD-Vnet" <br/>
<img src="https://imgur.com/BqXGNfl.png" height="80%" width="80%" alt="Active Directory Azure homelab"/>
 
 Virtual network steps 3: Configured the virtual network ip address to 172.16.0.0/16 and added a subnet configured with an ip address range of 172.16.0.0/24 <br/>
<img src="https://imgur.com/8Sovenm.png" height="80%" width="80%" alt="Active Directory Azure homelab"/>
 
 Virtual network steps 4: Finalized and created the virtual network <br/>
<img src="https://imgur.com/DLcZoM0.png" height="80%" width="80%" alt="Active Directory Azure homelab"/>
<br />
<br />
Create Windows server 2019 data center Step 1: This windows server will act as our active directory domain controller <br/>
<img src="https://imgur.com/IPP2fgo.png" height="80%" width="80%" alt="Active Directory Azure homelab"/>

Create Windows server 2019 data center Step 2: <br/>
<img src="https://imgur.com/8EnnxBc.png" height="80%" width="80%" alt="Active Directory Azure homelab"/>

Create Windows server 2019 data center Step 3: This server will share the same subnet preconfigured in the Virtual network setup. <br/>
<img src="https://imgur.com/TosE67h.png" height="80%" width="80%" alt="Active Directory Azure homelab"/>

Create Windows server 2019 data center Step 4: It is important to note that the first 3 IPs in azure is always reserved. <br/>
<img src="https://imgur.com/tNLfe21.png" height="80%" width="80%" alt="Active Directory Azure homelab"/>

Windows server 2019 data center: Server overview <br/>
<img src="https://imgur.com/T5X2j86.png" height="80%" width="80%" alt="Active Directory Azure homelab"/>

After setting up the virtual network and the windows server, we would proceed to login to the windows server via the public ip address (172.178.112.148) using a windows remote desktop protocol to further configure the Active Directory Domain server and then setting up a windows 10 virtual machine to add to the active directory.
To configure Active directory, we need Ip address and DNS server of the windows server to be static and the same. If we login to the server, this would not be the same as shown below <br/>

<img src="https://imgur.com/iYGw4pW.png" height="80%" width="80%" alt="Active Directory Azure homelab"/>

To fix this, we have to return to the Windows server (domain controller)  network interface in azure, go to the ipconfigurations and select ipconfig1, then proceed to change the private IP address allocation to static as shown below. <br/>

<img src="https://imgur.com/ceHkmNp.png" height="80%" width="80%" alt="Active Directory Azure homelab"/>

<img src="https://imgur.com/MVGXbW8.png" height="80%" width="80%" alt="Active Directory Azure homelab"/>

<img src="https://imgur.com/JaNH1nN.png" height="80%" width="80%" alt="Active Directory Azure homelab"/>

<img src="https://imgur.com/DmBnRPF.png" height="80%" width="80%" alt="Active Directory Azure homelab"/>

<br />
<br />
After configuring the ip address allocation, proceed to the Virtual Network and select "AD-Vnet" DNS servers then change the server settings to custom and input the Windows server private ip address "172.16.0.5" as the DNS server and "162.63.129.16" as the alternate, click save and go back to the windows server and run the command "IPCONFIG /RENEW" and "IPCONFIG /ALL" to confirm the changes. Observe that the IP address of the Windows server and the DNS servers are now the same.
<br/>

<img src="https://imgur.com/1kDEmA8.png" height="80%" width="80%" alt="Active Directory Azure homelab"/>

<img src="https://imgur.com/zny1zaU.png" height="80%" width="80%" alt="Active Directory Azure homelab"/>

<img src="https://imgur.com/1Kl0oAk.png" height="80%" width="80%" alt="Active Directory Azure homelab"/>

<img src="https://imgur.com/ntDEr6T.png" height="80%" width="80%" alt="Active Directory Azure homelab"/>

<br />
<br />
After configuring the windows server to share the same ip address with the DNS server, we then proceed to the Server manager dashboard, click on roles and features and click next till we get to server roles, here we click on Active directory domain services before clicking next and add features before proceeding with the installation setup, we then confirm the installation setup and wait for it to install, this will take a minute.  <br/>
<img src="https://imgur.com/fZRXB7G.png" height="80%" width="80%" alt="Active Directory Azure homelab"/>

<img src="https://imgur.com/HbGNyQL.png" height="80%" width="80%" alt="Active Directory Azure homelab"/>

<img src="https://imgur.com/6DqDsNZ.png" height="80%" width="80%" alt="Active Directory Azure homelab"/>

<img src="https://imgur.com/ha0ZpJl.png" height="80%" width="80%" alt="Active Directory Azure homelab"/>

<img src="https://imgur.com/edEjYa3.png" height="80%" width="80%" alt="Active Directory Azure homelab"/>

<img src="https://imgur.com/cnC4Hdd.png" height="80%" width="80%" alt="Active Directory Azure homelab"/>

<img src="https://imgur.com/tqKv8hr.png" height="80%" width="80%" alt="Active Directory Azure homelab"/>

<img src="https://imgur.com/3OI4eZm.png" height="80%" width="80%" alt="Active Directory Azure homelab"/>

<img src="https://imgur.com/aCk3I0n.png" height="80%" width="80%" alt="Active Directory Azure homelab"/>

<img src="https://imgur.com/KKqhbqV.png" height="80%" width="80%" alt="Active Directory Azure homelab"/>

<br />
<br />
After this installation, click on the amber alert flag on the server manager dashboard and promote the server to domain controller, the deployment configuration will show up, click on add new forest and generate a root domain name, this can be your organization name but for this demonstration "Sport.com", click next and generate an alternate backup password for directory service restore mode then click next and wait for Netbios to automatically generate name and proceed, click next to prerequisite checks and install, after installation, the Domain controller will restart and show "please wait for group policy client". 
Note that you might have to restart the remote desktop protocol to gain access to the domain controller after restarting: <br/>

<img src="https://imgur.com/8orlGZC.png" height="80%" width="80%" alt="Active Directory Azure homelab"/>

<img src="https://imgur.com/5N7mlZV.png" height="80%" width="80%" alt="Active Directory Azure homelab"/>

<img src="https://imgur.com/bZoiXjC.png" height="80%" width="80%" alt="Active Directory Azure homelab"/>

<img src="https://imgur.com/WfzKeId.png" height="80%" width="80%" alt="Active Directory Azure homelab"/>

<img src="https://imgur.com/n4mFj9A.png" height="80%" width="80%" alt="Active Directory Azure homelab"/>

<img src="https://imgur.com/5Cma0Qs.png" height="80%" width="80%" alt="Active Directory Azure homelab"/>

<img src="https://imgur.com/JNj7jIH.png" height="80%" width="80%" alt="Active Directory Azure homelab"/>

<img src="https://imgur.com/Jvp23uY.png" height="80%" width="80%" alt="Active Directory Azure homelab"/>

<img src="https://imgur.com/id5sjWp.png" height="80%" width="80%" alt="Active Directory Azure homelab"/>

<img src="https://imgur.com/CbMYmUN.png" height="80%" width="80%" alt="Active Directory Azure homelab"/>

<br />
<br />
After logging in, run the command "whoami" to confirm AD-DS is active, you should get your netbiosname\administrator which is "Sport\azureuser" in this demonstration:  <br/>
<img src="https://imgur.com/4RarkOV.png" height="80%" width="80%" alt="Active Directory Azure homelab"/>

<br />
<br />
Create Azure windows 10 vm and set it up with the name Comp1 then login to the virtual machine with a remote desktop protocol using the public ip address, after logging in, proceed to system settings and click on rename this pc (advanced), click on change and switch from workgroup to domain and include the domain name which is "sport.com" in this demonstration, click on OK and enter the Domain controller(Active directory server) username and password to log in to the Active Directory, this should prompt the virtual machine to restart and show up in the Active directory users and computers on the Domain controller:  <br/>
<img src="https://imgur.com/x8Qvbdq.png" height="80%" width="80%" alt="Active Directory Azure homelab"/>

<img src="https://imgur.com/ZObYGZk.png" height="80%" width="80%" alt="Active Directory Azure homelab"/>

<img src="https://imgur.com/zcUtLAu.png" height="80%" width="80%" alt="Active Directory Azure homelab"/>

<img src="https://imgur.com/BmkqJ6N.png" height="80%" width="80%" alt="Active Directory Azure homelab"/>

<img src="https://imgur.com/R9zYMG5.png" height="80%" width="80%" alt="Active Directory Azure homelab"/>

<img src="https://imgur.com/0hMOmke.png" height="80%" width="80%" alt="Active Directory Azure homelab"/>

<img src="https://imgur.com/JsJtp4u.png" height="80%" width="80%" alt="Active Directory Azure homelab"/>

<br />
<br />
Observe the Windows 10 VM named Comp1 has been added to the Active directory users and computers, and this can be done for other VMs deployed that needs to be added to the same Domain  <br/>
<img src="https://imgur.com/JsJtp4u.png" height="80%" width="80%" alt="Active Directory Azure Homelab"/>
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
