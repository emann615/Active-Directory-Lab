# AD Lab Setup Using Hyper-V

## Description
Active Directory (AD) is a directory service created by Microsoft that runs on Windows Servers. It allows administrators to control what access and permissions users and computers have on a domain network. In this tutorial, I will show you how to set up an Active Directory home lab using Oracle VM VirtualBox and Windows Server 2022.
<br />

## Walk-Through:
I used Windows Hyper-V to provision and deploy all the virtual machines needed for the lab.
First, I had to make sure virtualization was enabled on my laptop. I opened Task Manager and went to the Performance tab. Next to Virtualization, I made sure it said Enabled. 

<img src="https://github.com/emann615/Active-Directory-Lab/assets/117882385/09c84ac1-a43a-4809-a920-c024137e1324" height="20%" width="20%" alt="#"/>

If virtualization was disabled, it would have been necessary to go into the BOIS settings to enable it, but fortunately it was already enabled.

Next, I clicked the start icon and typed in “windows features”. I selected “Turn Windows features on and off” from the results.

<img src="https://github.com/emann615/Active-Directory-Lab/assets/117882385/2a38176e-21bc-4131-880a-fa246d70b093" height="30%" width="30%" alt="#"/>

In the Windows Feature window I made sure the box next to Hyper-V was checked. 

<img src="https://github.com/emann615/Active-Directory-Lab/assets/117882385/78119afe-310d-4d02-976e-20f807c928da" height="30%" width="30%" alt="#"/>

Originally there was no option to enable Hyper-V because my laptop is running on Windows 11 Home Edition, which does not come with Hyper-V included. I followed the steps in the video here to install Hyper-V.

After Hyper-V was installed and enabled, I downloaded Microsoft’s lab environment linked here. Once the lab environment finished downloading, I extracted the files to the Lab folder on my desktop.

<img src="" height="80%" width="80%" alt="#"/>

Before installing the lab environment, I had to open Hyper-V and create a new virtual network switch.

<img src="" height="80%" width="80%" alt="#"/>

After creating the virtual network switch, I opened the folder where I downloaded the lab environment and executed the stetup.exe file to install the virtual machines.

<img src="" height="80%" width="80%" alt="#"/>

Once the installation finished, I could see all the virtual machines were now loaded into Hyper-V.

<img src="" height="80%" width="80%" alt="#"/>
