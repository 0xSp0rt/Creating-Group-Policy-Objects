<h1>Creating Group Policy Objects, Shared Data Access, App Restrictions and Remote Desktop Connection</h1>


<h2>Description</h2>
In this lab, we are going to walk through how to create Disk Quota management, Disabling Windows Services, Creating shared folder, Creating Organizational unit and users, Create Group policy Objects <abbr>(GPO)</abbr>, using GPOs to restrict applications and Remote desktop connection. Configuring and running this lab will be done using virtual machines that are run on Hyper-v and this will help develop your understanding of how active directory and GPOs work.
<br />


<h2>Languages and Utilities Used</h2>

- <b>Windows server 2019</b> 
- <b>Windows 10 vm</b>
- <b>Hyper-V</b>
- <b>Remote Desktop Connection </b>


<h2>Disk Quota Management:</h2>
<p>The Disk Quota management allows us to allocate shared storage for all devices connected to the server.</p>


<p align="left">
To enable Disk Quota Management on the Windows Server 2019 VM, go to the file explorer, select the Local C disk, right click on the C drive and select properties. Under properties, I selected the Quota tab, enabled Quota management as shown in the screenshots below. I then proceeded to set the disk space limit to 5gb and warning level to 4gb.. <br/>
<img src="https://res.cloudinary.com/dbglnqdha/image/upload/v1719338334/SS1_brgec1.png" height="80%" width="80%" alt="GPO"/>
<img src="https://res.cloudinary.com/dbglnqdha/image/upload/v1719338338/SS2_tervap.png" height="80%" width="80%" alt="GPO"/>
<br />
<br />

 <h2>Disabling Windows Services</h2>
To disable services like Windows Audio, Telephony, and Print Spooler services, we have to access services. Windows Audio is a service that allows the computer to connect with and use audio devices properly while Telephony allows the device to connect and use communications devices and networks. Print spooler allows the device to be able to connect with, use and detect printers. These services are not required in this lab and this is why we are disabling them.
We did this by using the run command(Win + R) to open run and input “Services.msc” to open Services and individually right click on the services selected such as Windows Audio, Telephony, and Print spooler and click stop if they are currently running as shown in the screenshots below. 
<br />
<br />

After disabling the services mentioned above, we opened task manager to monitor system performance like CPU usage, memory and ethernet. 
<br/>
<img src="https://res.cloudinary.com/dbglnqdha/image/upload/ss2.5_zukoau.png" height="80%" width="80%" alt="GPO"/>
<img src="https://res.cloudinary.com/dbglnqdha/image/upload/ss3_sfhakk.png" height="80%" width="80%" alt="GPO"/>
<img src="https://res.cloudinary.com/dbglnqdha/image/upload/ss4_jogpn8.png" height="80%" width="80%" alt="GPO"/>
<img src="https://res.cloudinary.com/dbglnqdha/image/upload/v1719338339/ss5_fcbqde.png" height="80%" width="80%" alt="GPO"/>
<img src="https://res.cloudinary.com/dbglnqdha/image/upload/v1719338334/ss6_vp7aml.png" height="80%" width="80%" alt="GPO"/>
<img src="https://res.cloudinary.com/dbglnqdha/image/upload/v1719338338/ss7_ffnhoa.png" height="80%" width="80%" alt="GPO"/>

<h2>Creating a Shared Folder</h2>
<p>We then proceed to the local c disk to create a folder called redirect, after creating the folder, we right click on the folder to check folder properties, under properties, we then select sharing tab and click on share, type everyone and click add to share the folder access with everyone and set user permission to read and write in the domain then click done and compress the Redirect folder as shown in the steps in the screenshots below.</p>
<br />
 
<img src="https://res.cloudinary.com/dbglnqdha/image/upload/v1719338340/ss8_b4ymeb.png" height="80%" width="80%" alt="GPO"/>
<img src="https://res.cloudinary.com/dbglnqdha/image/upload/ss9_n2zdvz.png" height="80%" width="80%" alt="GPO"/>
<img src="https://res.cloudinary.com/dbglnqdha/image/upload/v1719338341/ss10_t9ciw3.png" height="80%" width="80%" alt="GPO"/>
<img src="https://res.cloudinary.com/dbglnqdha/image/upload/v1719342178/ss11_u78xoh.png" height="80%" width="80%" alt="GPO"/>
<img src="https://res.cloudinary.com/dbglnqdha/image/upload/v1719342168/ss12_bfjxri.png" height="80%" width="80%" alt="GPO"/>
<img src="https://res.cloudinary.com/dbglnqdha/image/upload/v1719342168/ss13_mvvozn.png" height="80%" width="80%" alt="GPO"/>
<img src="https://res.cloudinary.com/dbglnqdha/image/upload/v1719342169/ss14_xiryn7.png" height="80%" width="80%" alt="GPO"/>
<img src="https://res.cloudinary.com/dbglnqdha/image/upload/v1719342171/ss15_ogrjpb.png" height="80%" width="80%" alt="GPO"/>
<img src="https://res.cloudinary.com/dbglnqdha/image/upload/v1719342172/ss16_xv56e0.png" height="80%" width="80%" alt="GPO"/>

<br />
<br />

<h2>Creating Organizational Unit and Users</h2>
<p>We proceed to create Organizational unit and users in active directory, to do this, under windows server manager dashboard, we click on tools and select active directory users and computers as shown in the screenshot below. In Active directory users and computer, we select our Domain which is “DomainOS.com” and create a new organizational unit named MarketingOS as well as new users named “MarketingUserOS” with password “Secret555” as shown in the screenshots and highlighted.  </p>

<img src="https://res.cloudinary.com/dbglnqdha/image/upload/ss17_ythhxq.png" height="80%" width="80%" alt="GPO"/>
<img src="https://res.cloudinary.com/dbglnqdha/image/upload/ss18_yvwdwm.png" height="80%" width="80%" alt="GPO"/>
<img src="https://res.cloudinary.com/dbglnqdha/image/upload/v1719342176/ss19_dl1dui.png" height="80%" width="80%" alt="GPO"/>
<img src="https://res.cloudinary.com/dbglnqdha/image/upload/v1719342177/ss20_e5umda.png" height="80%" width="80%" alt="GPO"/>
<img src="https://res.cloudinary.com/dbglnqdha/image/upload/v1719343804/ss21_h7qurh.png" height="80%" width="80%" alt="GPO"/>
<img src="https://res.cloudinary.com/dbglnqdha/image/upload/v1719343806/ss22_r2hrt1.png" height="80%" width="80%" alt="GPO"/>
<img src="https://res.cloudinary.com/dbglnqdha/image/upload/v1719343807/ss23_wfk8fm.png" height="80%" width="80%" alt="GPO"/>

<br />
<br />

<h2>Creating Group Policy Objects</h2>
<p>To create Group Policy Objects, we have to go to the server manager dashboard and select Group policy management, in group policy management we select our Domain which is DomainOS.com and drop down the folders under the domain, right click the organizational unit named “MarketingOS” and select the option “Create and link new GPO”. We then named the GPO “OUR GPO” as shown in the screenshots below. </p>

<p>After creating the GPO, we right-click the GPO to edit the group policy object to redirect the documents folder to the redirect folder created in C drive and app restriction to prevent Notepad from running. </p>

<p>To do folder redirection, we click on user configuration under GPO edit, select windows settings and select folder redirection, we right click on the documents folder and select properties, change the target setting to “Basic” and change the target folder location to “Create a folder for each user under root” before selecting the root path to the redirect folder created in the Windows C drive during Quota management, then click yes to the warning prompts and apply as shown in the highlighted screenshots below. </p>
<p>The aim is to redirect every user back to "Redirect" folder wheneevr they select the documents folder on their computers.</p>

<img src="https://res.cloudinary.com/dbglnqdha/image/upload/v1719345503/msd_ihe7ln.png" height="80%" width="80%" alt="GPO"/>
<img src="https://res.cloudinary.com/dbglnqdha/image/upload/v1719343809/SS24_rs4zsd.png" height="80%" width="80%" alt="GPO"/>
<img src="https://res.cloudinary.com/dbglnqdha/image/upload/v1719343810/SS25_qgr8mv.png" height="80%" width="80%" alt="GPO"/>
<img src="https://res.cloudinary.com/dbglnqdha/image/upload/v1719343812/ss26_k3juwi.png" height="80%" width="80%" alt="GPO"/>
<img src="https://res.cloudinary.com/dbglnqdha/image/upload/v1719343814/ss27_t4ajwq.png" height="80%" width="80%" alt="GPO"/>
<img src="https://res.cloudinary.com/dbglnqdha/image/upload/v1719343815/ss28_t9lamp.png" height="80%" width="80%" alt="GPO"/>
<img src="https://res.cloudinary.com/dbglnqdha/image/upload/v1719343800/ss29_bcs1n3.png" height="80%" width="80%" alt="GPO"/>
<img src="https://res.cloudinary.com/dbglnqdha/image/upload/v1719346540/msd2_fhatgx.png" height="80%" width="80%" alt="GPO"/>
<img src="https://res.cloudinary.com/dbglnqdha/image/upload/v1719346537/msd3_gcy6sa.png" height="80%" width="80%" alt="GPO"/>
<img src="https://res.cloudinary.com/dbglnqdha/image/upload/v1719346538/msd4_tthx5r.png" height="80%" width="80%" alt="GPO"/>

<br />
<br />

<h2>App Restriction</h2>
<p>To configure the app restriction, we have to go to User configuration under the created group policy object, select administrative template and select system, under system, we then proceed to click on “don’t run specified windows application” and then click on enable, select “list of disallowed application” and add “Notepad.exe” to select notepad and then click on Ok. This can be done for any application to prevent the user from using or running a particular application and in this case, we are restricting the notepad app.
</p>
<img src="https://res.cloudinary.com/dbglnqdha/image/upload/v1719347819/Picture1_bwy7aa.png" height="80%" width="80%" alt="GPO"/>
<img src="https://res.cloudinary.com/dbglnqdha/image/upload/v1719347819/Picture2_emqqbj.png" height="80%" width="80%" alt="GPO"/>

<br />
<br />

<h2>Testing Folder Redirection and Application Restriction</h2>
<p>To test the folder redirection, we log in the windows 10 VM and first confirm that we can ping the domain controller(Windows server 2019) by running the command "Ipconfig 192.168.1.20" and giving the results as shown below. After confirming the domain controller can be reached, we then proceed to run the command ”gpupdate /force” to update the policy configured on the domain controller to the windows 10 client, running the command will ask for a yes or no confimation to log off the user as shown below. The user is logged off and logged back in as Marketing User. </p> 
<img src="https://res.cloudinary.com/dbglnqdha/image/upload/v1719348750/Picture3_yg77hl.png" height="80%" width="80%" alt="GPO"/>
<img src="https://res.cloudinary.com/dbglnqdha/image/upload/v1719348751/Picture4_vfinzr.png" height="80%" width="80%" alt="GPO"/>
<img src="https://res.cloudinary.com/dbglnqdha/image/upload/v1719348752/Picture5_hcxugj.png" height="80%" width="80%" alt="GPO"/>

<p>After logging back in, we go to the file explorer, click on the documents folder properties and select the location tab to verify the redirection which shows in the location as highlighted below. We also confirmed the app restriction by trying to run the Notepad app multiple times which did not run and this confirms the app restriction using Group policy object was effective as shown in the screenshots below. </p>
<img src="https://res.cloudinary.com/dbglnqdha/image/upload/v1719348953/Picture6_nie3rt.png" height="80%" width="80%" alt="GPO"/>
<img src="https://res.cloudinary.com/dbglnqdha/image/upload/v1719348954/Picture7_dx6etb.png" height="80%" width="80%" alt="GPO"/>

<br />
<br />

<h2>Remote Desktop Connection</h2>
<p>To use remote desktop connection, we must first return to the windows server machine and enable remote desktop. To do this, we proceed to click on local server in the windows server manager dashboard and select remote desktop and enable it as shown in the screenshot below to enable remote access. </p>
<img src="https://res.cloudinary.com/dbglnqdha/image/upload/v1719349991/Picture8_eem7aq.png" height="80%" width="80%" alt="GPO"/>

<p>After remote desktop has been enabled on the windows server, we then proceed to log in on the windows 10 client, search for the remote desktop connection app and then input the Device name which is the device we want to have remote access to and that is the DC01OS as shown in the local server information under windows server manager dashboard and input the username which is “Administrator” and click connect to connect to the windows server 2019 remotely, as shown below and it was successful which is shown in the screenshots below.</p>
<img src="https://res.cloudinary.com/dbglnqdha/image/upload/v1719350022/Picture9_ghi5xj.png" height="80%" width="80%" alt="GPO"/>
<img src="https://res.cloudinary.com/dbglnqdha/image/upload/v1719350041/Picture10_ixjrr8.png" height="80%" width="80%" alt="GPO"/>
<img src="https://res.cloudinary.com/dbglnqdha/image/upload/v1719350042/Picture11_z2ozn2.png" height="80%" width="80%" alt="GPO"/>
<img src="https://res.cloudinary.com/dbglnqdha/image/upload/v1719350044/Picture12_qipsed.png" height="80%" width="80%" alt="GPO"/>

<p>Observing the following steps and procedures above allows for us to create disk quota management, shared file access, create group policy objects, enforcing app restrictions, and remotely connect to the windows server 2019 domain controller using an RDP connection.</p>
<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
