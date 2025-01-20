<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png"/>
</p>

<h1>osTicket: Prerequisites and Installation</h1>


<h2>Description</h2>
Project consists of setting up all the prerequisites and installing osTicket from scratch. This was done on a Windows 10 Virtual Machine I created in Azure. osTicket is a widely used and trusted open source Help Desk ticketing system. <br/>
<br/>

You can find all the necessary installation files used in this project [here.](https://drive.google.com/drive/u/1/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6)
<br />


<h2>Environments and Utilities Used</h2>

- <b>Microsoft Azure</b>
- <b>Virtual Machines</b>
- <b>Remote Desktop Connection</b>
- <b>Internet Information Services</b>
- <b>MySQL</b>


<h2>Operating Systems Used </h2>

- <b>Windows 10</b>

<h2>Project Walk-through:</h2>


Navigate to Microsoft Azure and create a resource group:
</p>
<img src="https://i.imgur.com/YkM3v7l.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Once my resource group is created, next I'll create the virtual machine:
</p>
<img src="https://i.imgur.com/cg8gJqi.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<img src="https://i.imgur.com/rM0gShm.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
I'll leave all other settings to default and create this VM. Once it has been created I'll use Remote Desktop Connection to connect to the VM:
</p>
<img src="https://i.imgur.com/lqwBE4C.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Once I've connected to the VM I will install and enable IIS (Internet Information Servies) by going to Control Panel> Programs> Turn Windows Features On or Off> Internet Information Services and enable it then World Wide Web Services> Application Development Features and enable CGI:
</p>
<img src="https://i.imgur.com/ZeVHYjx.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Then go to Common HTTP Features dropdown and enable all features. Then apply the changes: 
</p>
<img src="https://i.imgur.com/ZrwkjIi.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
I can test that the web server installed correctly by typing in the loopback IP (127.0.0.1) in the internet browser and this page should load: 
</p>
<img src="https://i.imgur.com/yCZNnGP.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Now I need to install PHP manager for IIS Setup: 
</p>
<img src="https://i.imgur.com/sdu7Mnt.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Install IIS URL Rewrite Module: 
</p>
<img src="https://i.imgur.com/MpwdBq9.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Once those have installed I will create a PHP directory on the C drive: 
</p>
<img src="https://i.imgur.com/YPgQ2s3.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Now I'll download PHP and extract the zip file in the PHP directory I just made:  
</p>
<img src="https://i.imgur.com/0bbWvOC.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Download Microsoft Visual C++: 
</p>
<img src="https://i.imgur.com/ncDfUqE.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Download MySQL:  
</p>
<img src="https://i.imgur.com/mQglSms.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Next, I have to setup the login credentials and I'll write them down just so I remember, since this is only a project. Do not write passwords down in real life:  
</p>
<img src="https://i.imgur.com/Q8P7J4Q.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Open IIS as an admin:  <br/>
<img src="https://i.imgur.com/oL76kzb.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Next go to PHP Manager> Register new PHP version and then select the file shown: 
</p>
<img src="https://i.imgur.com/F65LgAj.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Go back to osticketVM Home and hit Restart under Manage Server on the right side:  
</p>
<img src="https://i.imgur.com/M14MaC6.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Next I'll download osTicket and copy the upload file to the wwwroot file in the inetpub directory: 
</p>
<img src="https://i.imgur.com/Uqw7jq0.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Rename upload file to osTicket: 
</p>
<img src="https://i.imgur.com/JbxATQk.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Reload IIS and restart the server as I did before, then click Browse *80 (http) on the right side:  
</p>
<img src="https://i.imgur.com/aiedsUJ.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
This page should open:  
</p>
<img src="https://i.imgur.com/gERSJOV.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Notice some extensions are not enabled. I'll enable a few of those in IIS. Go to Sites> Default Web Site> osTicket Click PHP Manager> Enable or disable an extension. Enable php_imap.dll, php_intl.dll, and php_opcache.dll:  
</p>
<img src="https://i.imgur.com/GyIF089.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Note the changes here:  
</p>
<img src="https://i.imgur.com/yIXmoUK.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Next browse in file explorer to C drive> osTicket> include> ost-sampleconfig.php and remove the "sample" from the name:
</p>
<img src="https://i.imgur.com/XR2i88I.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Right-click on ost-config.php> Properties> Security> Advanced> Disable Inheritance> Remove all inherited permissions from this object:  
</p>
<img src="https://i.imgur.com/hNpM3rI.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Click on the add buton to add permissions to the file> Select a principle> type "everyone"> Check> OK> check all permissions> OK> apply> OK:  
</p>
<img src="https://i.imgur.com/VoPQTV9.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Hit continue on the osTicket web page in the browser and fill out the set up page: 
</p>
<img src="https://i.imgur.com/vDxzura.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Before database set up we'll have to connect the database using HeidiSQL. Install HeidiSQL from setup links: 
</p>
<img src="https://i.imgur.com/Yv6XTWq.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
In HeidiSQL click New> Username = root> Password = mySQL password from mySQL setup> Open:  
</p>
<img src="https://i.imgur.com/DC8UtRj.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
In HeidiSQL right click Unnamed> Create> New Database> Name it osTicket> OK. Then continue to fill out the database portion of osTicket setup with the correct database name "osTicket," and your MySQL username and password. 
</p>
<img src="https://i.imgur.com/4YuHjzT.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
Click “Install Now!”
</p>
Congratulations, hopefully it is installed with no errors!
</p>
<img src="https://i.imgur.com/HMRvmc1.png" height="80%" width="80%" alt="Setting Up in Azure"/>
<br />
<br />
  
<h2>osTicket Installed!</h2>

<b>osTicket is now installed and ready for use! In the next project I will walk you through how to configure agents, their permissions and access, users, and more!  </b>
<br />
<br />
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
