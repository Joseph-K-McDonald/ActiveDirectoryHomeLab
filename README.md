<h1>Active Directory Home Lab</h1>

<h2>Description</h2>
This project consists of a creating an Active Directory in a home lab environment. A simple Powershell script is used to populate users into the directory. This project was done to get active and hands-on experience working with Windows Server as well as Active Directory.
<br />


<h2>Languages and Utilities Used</h2>

- <b>PowerShell</b> 
- <b>Virtual Box</b>

<h2>Environments Used </h2>

- <b>Windows 10 Pro</b>
- <b>Server 2019</b>

<h2>Project walk-through:</h2>

<p align="center">
Create the VirtualMachine for the server(Microsoft Server 2019), make sure to apply two Network Adapters(one for connection to the internet and another for connection to the client side): <br/>
<img src="https://imgur.com/QpIER1R.png" height="80%" width="80%" alt="Project walk-through"/>
</br>
</br>
Adjust the internal network adapter IPv4 to reflect the following IP, subnet mask, and DNS: <br/>
<img src="https://imgur.com/9IjI9gv.png" height="30%" width="30%" alt="Project walk-through"/>
</br>
</br>
After opening the server manager, Select "Add roles and features", and check the box for Active Directory Domain Services: <br/>
<img src="https://imgur.com/ZhhOzI2.png" height="50%" width="50%" alt="Project walk-through"/>
</br>
</br>
Promote the newly created Active Directory to a domain controller and add a new forest with any naming convention: <br/>
<img src="https://imgur.com/zkswqoh.png" height="40%" width="40%" alt="Project walk-through"/>
</br>
</br>
Once the Active Directory has been created, manually create an admin organizational unit and admin user: <br/>
<img src="https://imgur.com/asRD2hX.png" height="40%" width="40%" alt="Project walk-through"/>
</br>
</br>
Create the RAS(Remote Access Service): <br/>
<img src="https://imgur.com/zU3G2uX.png" height="40%" width="40%" alt="Project walk-through"/>
</br>
</br>
Make sure to enable routing when creating the RAS to provide support for NAT: <br/>
<img src="https://imgur.com/6i2RF3c.png" height="40%" width="40%" alt="Project walk-through"/>
</br>
</br>
Configure RAS to enable NAT: <br/>
<img src="https://imgur.com/TFYi1GX.png" height="60%" width="60%" alt="Project walk-through"/>
</br>
</br>
Create the DHCP server: <br/>
<img src="https://imgur.com/pGIwirk.png" height="60%" width="60%" alt="Project walk-through"/>
</br>
</br>
Configure DHCP server to add scope(this defines IP addresses for users connecting to the network), also add the IP address for the router(this should be the IP address for the internal NIC defined earlier): <br/>
<img src="https://imgur.com/k2ier5q.png" height="60%" width="60%" alt="Project walk-through"/>
</br>
</br>
Configure DHCP server router(IP address should be the same as the internal NIC): <br/>
<img src="https://imgur.com/vUw5ZUW.png" height="40%" width="40%" alt="Project walk-through"/>
</br>
</br>
Run the Powershell script to generate a list of users, Check the current Active Directory user list to check that the users have been populated correctly: <br/>
<img src="https://imgur.com/FYj6P4W.png" height="70%" width="70%" alt="Project walk-through"/>
</br>
</br>
Create the Windows 10 Pro VM and adjust the network adapter setting to use the Internal Network(this way the client connects to our servers internal NIC): <br/>
<img src="https://imgur.com/otlAS2q.png" height="60%" width="60%" alt="Project walk-through"/>
</br>
</br>
Running ipconfig command shows the current adapter information: <br/>
<img src="https://imgur.com/aEjlDK3.png" height="60%" width="60%" alt="Project walk-through"/>
</br>
</br>
Update the domain used for the computer and login using a user created in the earlier step: <br/>
<img src="https://imgur.com/kcXWUJG.png" height="60%" width="60%" alt="Project walk-through"/>
</br>
</br>
The login screen for the Windows 10 VM displays the sign-in to MYDOMAIN correctly(use one of the generated users from earlier to login): <br/>
<img src="https://imgur.com/6MYtQrI.png" height="40%" width="40%" alt="Project walk-through"/>
</br>
</br>
Finally, check the Active Directory list of users and computers to ensure the client computer has connected successfully. Also, check the DHCP Address lease list to ensure the lease was handled properly: <br/>
<img src="https://imgur.com/IHEL1za.png" height="80%" width="80%" alt="Project walk-through"/>
</br>
</br>

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
