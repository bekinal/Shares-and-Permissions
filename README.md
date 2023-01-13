<h1>Shares & Permissions</h1>

<h2>Description</h2>
Project consists of using Windows Server 2016 to create a new shared resource within a domain. Then, different permission levels will be granted to users and administrators. This project is completed under the assumption that a Windows 7 client and a Windows 10 client have been added to the domain. 
<br />


<h2>Utilities Used</h2>

- <b>VirtualBox</b> 
- <b>Windows Explorer</b>
- <b>CMD</b>
- <b>Active Directory</b>

<h2>Environments Used </h2>

- <b>Windows Server 2016</b>
- <b>Windows 7</b>
- <b>Windows 10</b>

<h2>Creating a New Shared Resource:</h2>

In the domain controller create a new folder in the Local Disk C: directory, and name it Resource: <br/>
<img src="https://imagizer.imageshack.com/img924/5310/SKtVjS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Create two folders under Resource named Sales and Wokrers. Under Sales, create a text document and name it ForSalesPersonnel. Repeat this process for the Workers folder: <br/>
<img src="https://imagizer.imageshack.com/img924/9095/EvaMBX.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Right click the resource folder and open Properties. Click on Advanced Sharing: <br/>
<img src="https://imagizer.imageshack.com/img922/7182/gPzjuw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Select Share this folder and leave the name as Resource. Click Permissions: <br/>
<img src="https://imagizer.imageshack.com/img922/7128/Nfirmd.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Select Full Control, and click Apply, OK: <br/>
<img src="https://imagizer.imageshack.com/img922/4023/c8SKGZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Verify that the Resource folder was created successfuly and that you can access it via a UNC path. Switch to the Windows 7 client machine and log in with the user Salesperson1: <br/>
<img src="https://imagizer.imageshack.com/img924/8420/hXSv7f.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Open the Run window and type \\\server1: <br/>
<img src="https://imagizer.imageshack.com/img922/3761/TFI96E.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Verify that the Resource folder appears in the window and that you can access it. Click the Resource folder. You should see the Sales and Workers folders: <br/>
<img src="https://imagizer.imageshack.com/img923/4198/0K0tFp.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
On the client, open the cmd. Use the following syntax to map the network drive using a UNC path: <br/>
net use S: \\\server1\resource /persistent:yes<br/>
<img src="https://imagizer.imageshack.com/img923/5594/NIAyLe.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Open This PC and verify that the shared drive appears: <br/>
<img src="https://imagizer.imageshack.com/img924/6254/FT6Y4k.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />



<h2>Grant Permission Levels:</h2>
On the domain controller go back to the Resource folder created in the Local Disk (C:) Directory and right-click it. Select properties, navigate to the security tab, and select advanced: <br/>
<img src="https://imagizer.imageshack.com/img922/4379/z2wlSb.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Disable the inheritence and select the second option. This will remove permissions for users. Then, click Add to add a new principle: <br/>
<img src="https://imagizer.imageshack.com/img924/7180/nW2Uwz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Click Select a principal: <br/>
<img src="https://imagizer.imageshack.com/img922/1523/YI3wuv.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Select Salesperson1: <br/>
<img src="https://imagizer.imageshack.com/img924/4268/NY5Mt5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Allow the user to modify files within the folder: <br/>
<img src="https://imagizer.imageshack.com/img922/6703/RMNxAw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Check the changes made by logging into Salesperson1 on the client machine and trying to access the Resource folder through the shared drive: <br/>
<img src="https://imagizer.imageshack.com/img924/3589/E0fSCM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Switch to the domain controller (admin account) and create a new user within the Users container named Worker1: <br/>
<img src="https://imagizer.imageshack.com/img922/415/JFCRJE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Create a new user named Wokrer1: <br/>
<img src="https://imagizer.imageshack.com/img923/5182/UBtRJo.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Set the password of your choosing and complete the user definition. For convenience purposes, deselect all of the boxes <br/>
<img src="https://imagizer.imageshack.com/img922/7044/WWTVPB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Allow only worker1 to access the Workers shared folder by changing permissions from the Security tab as completed in prior steps. Disable the inheritence and grant read-only and execute permissions: <br/>
<img src="https://imagizer.imageshack.com/img923/7828/KfmCW0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Add a new permission and click "Select a principal" enter "Worker1" and click Check Names, OK: <br/>
<img src="https://imagizer.imageshack.com/img923/6444/Ng4MHB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Check the boxes to grant specific permissions: <br/>
<img src="https://imagizer.imageshack.com/img924/990/vDqjUE.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Verify that the worker1 user has permission to read & execute the Workers folder: <br/>
<img src="https://imagizer.imageshack.com/img922/7128/Bgi8Vp.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Switch to the client machine. log into Salesperson1 and try to access the Workers folder. You should receive a Cannot Access message. However, you should have access to the Sales folder: <br/>
<img src="https://imagizer.imageshack.com/img922/9904/tG4aZt.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Navigate to the directory. right-click it, go to Properties/Security: <br/>
<img src="https://imagizer.imageshack.com/img923/7274/99Lfpq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
On the client, switch users to Worker1. You can do this easily by running "Logoff": <br/>
<img src="https://imagizer.imageshack.com/img922/9646/Sl7Lzi.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Log in as cyber\Worker1: <br/>
<img src="https://imagizer.imageshack.com/img922/4800/7alDPZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Open the Run window and type \\\server1 to access the Resource folder. You should be unable to see Sales but have access to Workers: <br/>
<img src="https://imagizer.imageshack.com/img924/4307/urd5mP.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Error message from trying to access Sales folder: <br/>
<img src="https://imagizer.imageshack.com/img924/8978/bDkwna.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Try to create a new folder in the Workers folder. You should receive an error due to insufficient permissions: <br/>
<img src="https://imagizer.imageshack.com/img922/2914/QZCJxj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Switch back to the domain controller and assign Worker1 full control permissions for the Workers folder.: <br/>
<img src="https://imagizer.imageshack.com/img923/8055/EBgwIA.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Click apply and OK: <br/>
<img src="https://imagizer.imageshack.com/img922/32/IEMJWo.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Test the change under Wokrer1. Notice that you can now add a folder within the Workers directory: <br/>
<img src="https://imagizer.imageshack.com/img922/4366/yFTxUe.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
