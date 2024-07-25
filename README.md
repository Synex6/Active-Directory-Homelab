<h1>Active Directory Homelab - Updated 2024</h1>

 ### [YouTube Demonstration From Josh Madakor](https://www.youtube.com/watch?v=MHsI8hJmggI)

<h2>Description</h2>
This homelab project aims to set up a functional Active Directory (AD) environment using Oracle VirtualBox for virtualization and PowerShell for automation. The project will guide you through the process of creating and configuring a virtual network of Windows servers and clients, establishing an AD domain, and using PowerShell scripts to automate administrative tasks.
<br />


<h2>Languages and Utilities Used</h2>

- <b>PowerShell</b> 
- <b>Oracle Virtualbox</b>
- <b>Windows Server 2019</b>
- <b>Windows 10 ISO File</b>

<h2>Environments Used </h2>

- <b>Windows 10</b> (22H2)
- <b>Windows Server 2019</b> 

<h2>Setup walk-through:</h2>

<p align="center">
Review the diagram for the project: <br/>
<img src="https://i.imgur.com/NTSkKds.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Download VirtualBox and the extension pack: <br/>
<img src="https://i.imgur.com/7NwQWrr.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Download Windows 10 ISO: <br/>
<img src="https://i.imgur.com/jOhMPYP.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Download Windows Server 2019: <br/>
<img src="https://i.imgur.com/Htj5Bme.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
I placed both the Windows 10 ISO and the Server Files into a single folder: <br/>
<img src="https://i.imgur.com/6avD6V5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Open up VirtualBox and apply similar settings for our DC Client. Make sure to go into the General settings and go into advanced and change both shared clipboard and drag'n'drop to Bidirectional so we can copy and paste both outside and inside the client environment.: <br/>
<img src="https://i.imgur.com/auC6omc.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Change the first network adapter to NAT: <br/>
<img src="https://i.imgur.com/x9vLCXy.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Change the second network adapter to internal network: <br/>
<img src="https://i.imgur.com/FFI7A2f.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Double-click the DC client and select the Windows 2019 server ISO we downloaded: <br/>
<img src="https://i.imgur.com/6avD6V5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
After selecting the ISO, run it and select this OS Version and make sure to select Custom: Install Windows only (advanced). It will then restart after some time and go ahead and select a password. When you are at the login screen remember to click input and then keyboard at the top to be able to input the Ctrl-Alt-Del Command: <br/>
<img src="https://i.imgur.com/DE51cy8.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Go into the file explorer and run the VboxWindowsAdditions-amd64: <br/>
<img src="https://i.imgur.com/8SuwNDp.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Go into the control panel and change the network connections. Most likely the Internet adapter should be a class C IP starting with 10.0 and the Internal adapter should be a class B IP starting with 169.254: <br/>
<img src="https://i.imgur.com/N5LGULL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Rename the PC: <br/>
<img src="https://i.imgur.com/K1vtxIw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Change the IPv4 IP address in the properties of the internal network adapter: <br/>
<img src="https://i.imgur.com/hg9AHSh.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Open up the server manager and select Add roles and features. Click on the DC Server: <br/>
<img src="https://i.imgur.com/NixccOE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Select Active Directory Domain Services: <br/>
<img src="https://i.imgur.com/gyyKx2q.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Click the flag at the top right and "promote this server to a domain controller": <br/>
<img src="https://i.imgur.com/VNCs7Uw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Change the domain name: <br/>
<img src="https://i.imgur.com/cQidJjd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Set the password: <br/>
<img src="https://i.imgur.com/8CFudmd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Install and re-log into the mydomain/admin account: <br/>
<img src="https://i.imgur.com/N0RhlKA.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Click the windows logo and open up Active Directory Users and Computers. Right click mydomain.com and create a new organizational unit as "_ADMINS" and uncheck the protect container option. Within that new admins organizational unit go ahead and create a new user with your full name and selected username, such as Joseph Github = a-jgithub. Select a password and uncheck everything except for password never expires: <br/>
<img src="https://i.imgur.com/L0BF9vs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Select the user we just created and go into properties. Click the "member of" tab and add a group. Type domain admins and hit "check names". You now made the user an admin for the DC: <br/>
<img src="https://i.imgur.com/oFD757d.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Restart and log into the new admin account you just created: <br/>
<img src="https://i.imgur.com/2kGjMPx.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Open up server manager and add a role for Remote Access: <br/>
<img src="https://i.imgur.com/dfhL3Cc.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Add RAS and Routing options for Remote Access: <br/>
<img src="https://i.imgur.com/HFFP0SX.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Installation complete for Remote Access role: <br/>
<img src="https://i.imgur.com/n4yGEQG.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Select tools at the top right and select "Routing and Remote Access": <br/>
<img src="https://i.imgur.com/K8r1wCn.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Select DC (local) and Configure and Enable Routing and Remote Access: <br/>
<img src="https://i.imgur.com/tHSi7mn.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Select NAT: <br/>
<img src="https://i.imgur.com/qfkslZa.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Select the internet network adapter. You may have to reopen the Routing and Remote Access tab again for it to populate: <br/>
<img src="https://i.imgur.com/0Io1fzD.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Finish the Setup: <br/>
<img src="https://i.imgur.com/UWTgN5c.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
You should now see a green up arrow next to our DC: <br/>
<img src="https://i.imgur.com/hibgtLK.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Add a role for our DHCP Server: <br/>
<img src="https://i.imgur.com/AIYNwo6.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Select DHCP from the tools tab: <br/>
<img src="https://i.imgur.com/w7UY7H3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Select New scope after right-clicking the IPv4 tab: <br/>
<img src="https://i.imgur.com/yVDfl2k.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
For the name write "172.16.0.100-200" and write the following start IP address and End IP address with the Class C IP length and Subnet Mask: <br/>
<img src="https://i.imgur.com/46K1SNT.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
There are no exclusions for the moment so leave this blank: <br/>
<img src="https://i.imgur.com/mNWdDYm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
For the DHCP Lease Duration we can leave it at 8 days unless you would like the IPs to renew quicker or later: <br/>
<img src="https://i.imgur.com/iNGPLX4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Configure DHCP Options: <br/>
<img src="https://i.imgur.com/s0jSiFu.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Type in the Router Default Gateway IP and make sure you click "Add": <br/>
<img src="https://i.imgur.com/7xE1KMf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Write the Parent domain name: <br/>
<img src="https://i.imgur.com/uET67ku.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Ignore WINS Servers: <br/>
<img src="https://i.imgur.com/8UCoTD0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Activate this scope now: <br/>
<img src="https://i.imgur.com/8YT3nP7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Authorize the DHCP server by right-clicking it: <br/>
<img src="https://i.imgur.com/6T8daG7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Refresh and make sure you have up arrows for both the IPv4 and IPv6: <br/>
<img src="https://i.imgur.com/rhIAgrH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Click configure this local server and select the "IE Enhanced Security Configuration" and turn both options off: <br/>
<img src="https://i.imgur.com/SG3IZcc.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Download the PowerShell script to create users from this link by Josh Madakor. https://github.com/joshmadakor1/AD_PS/archive/master.zip . Click save as and put it on the desktop. Make sure to extract the compressed folder back onto the desktop: <br/>
<img src="https://i.imgur.com/hUF7CxZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Open up the names text file and put your full name at the top. This script will go ahead and make user accounts using all the names in this list: <br/>
<img src="https://i.imgur.com/wSln5bU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Run Windows PowerShell ISE as an administrator: <br/>
<img src="https://i.imgur.com/TaBDTXt.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Open the Script by clicking the folder at the top left. Select the Create_Users script: <br/>
<img src="https://i.imgur.com/IOzLeIY.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Type "Set-ExecutionPolicy Unrestricted" to be able to run the script: <br/>
<img src="https://i.imgur.com/HmJgFgd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Change the directory to where the txt file is located for it to parse the data: <br/>
<img src="https://i.imgur.com/IRphiAW.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Run the script by clicking the play button at the top: <br/>
<img src="https://i.imgur.com/QCl0dur.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Open the Active Directory Users and Computers and you can see hundreds of user accounts now populated in the _USERS organizational group: <br/>
<img src="https://i.imgur.com/qrehCfY.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
You can also right-click mydomain.com and find a specific user if needed: <br/>
<img src="https://i.imgur.com/JmQf9fy.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
The last step would be to set up a virtual client to mimic a user's PC: <br/>
<img src="https://i.imgur.com/2MVDKxp.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Go back to the VirtualBox and create a new client using Windows 10 (64-bit): <br/>
<img src="https://i.imgur.com/WG6lmbQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Follow the same steps we did before for the DC client, however, this time we will only change the first network adapter to internal: <br/>
<img src="https://i.imgur.com/1KB1yHt.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Run the new client1 and select the Windows 10 ISO file we downloaded earlier: <br/>
<img src="https://i.imgur.com/MTvIxt0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Click I don't have a product key: <br/>
<img src="https://i.imgur.com/ZQUuBU7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Select Windows 10 Pro and then select custom install: <br/>
<img src="https://i.imgur.com/xwTVUbH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
This setup changes often but if you reach this page go ahead and select offline account: <br/>
<img src="https://i.imgur.com/erqoq3e.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Select limited experience for this: <br/>
<img src="https://i.imgur.com/8Q8D0s8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
After creating your user, go into the command prompt and type "ipconfig" to check our adapter settings. You should see your IPv4 address along with your Subnet Mask Address and Default Gateway: <br/>
<img src="https://i.imgur.com/WnoxKsX.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Diagram for pinging google.com to make sure our DNS server is working: <br/>
<img src="https://i.imgur.com/l0ztGtf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Type "ping google.com" and "ping mydomain.com" to check our DNS and DC and make sure it resolves: <br/>
<img src="https://i.imgur.com/U2nmV5L.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Go into settings to rename this pc: <br/>
<img src="https://i.imgur.com/DNku0mE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Select this option: <br/>
<img src="https://i.imgur.com/RHBHGK4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Write the PC name and make sure to type in the domain name: <br/>
<img src="https://i.imgur.com/cPWnoOS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Log in using a user account such as the one we put into that text file: <br/>
<img src="https://i.imgur.com/Vp7tREx.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Restart once more: <br/>
<img src="https://i.imgur.com/ZGmkBbF.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Go back into the DC client and look into the DHCP Tool and check for the lease from our client computer: <br/>
<img src="https://i.imgur.com/WZuiLKx.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
We can also check for the new client in Active Directory Users and Computers: <br/>
<img src="https://i.imgur.com/HHzwgWV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
After the restart on our client PC, log into a user account such as the one with your name. Don't be confused with this image saying Jadmin as my created user account was "John Admin": <br/>
<img src="https://i.imgur.com/pHODDRt.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<p align="center">
Finally we can go into the command prompt and type the command "whoami" to check our domain name and user name that we are logged in with: <br/>
<img src="https://i.imgur.com/bcb4DmH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />

<h2>Conclusion</h2>
This homelab project provides a comprehensive introduction to setting up and managing an Active Directory environment using Oracle VirtualBox and PowerShell. By following the outlined steps, you will gain valuable hands-on experience in virtualization, AD configuration, and automation. This project not only strengthens your understanding of core IT concepts but also equips you with practical skills that are highly relevant in the field. Whether you are an IT professional seeking to enhance your expertise or an enthusiast looking to explore new technologies, this homelab project offers a structured and rewarding learning experience. 
<br />
Special thanks to Josh Madakor for creating a simple and effective video to follow along with!



<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
