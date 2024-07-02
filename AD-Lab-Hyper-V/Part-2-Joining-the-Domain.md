# Part 2: Joining the Domain

## Description:
In this section of the lab, I joined CLIENT4 to the corp.contoso.com domain. When a computer joins a domain, it becomes a member of the domain and gains access to shared files, printers, and other network resources. 

## Walk-Through:
To start, I had two VMs running, my domain controller (DC1) running Windows Server 2022 and a client machine (CLIENT4) running Windows 11.

<img src="https://github.com/emann615/Active-Directory-Lab/assets/117882385/54908056-a386-4038-acaf-be3b6b2482b2" height="70%" width="70%" alt="#"/>

After checking Active Directory Users and Computers, I could see the CLIENT4 machine was not joined to the domain and could not access any of the domain resources. I could only log in with a local user account.

<img src="https://github.com/emann615/Active-Directory-Lab/assets/117882385/f593d408-410e-4052-9189-ecb4edf95c47" height="60%" width="60%" alt="#"/>

To join the domain, I logged in to the CLIENT4 machine using admin credentials. Once logged in, I opened the About page of the system settings and clicked Advanced system settings.

<img src="https://github.com/emann615/Active-Directory-Lab/assets/117882385/175688ec-9ee8-44cc-946a-13312b89001b" height="50%" width="50%" alt="#"/>

In the System Properties window that opened, I selected the Computer Name tab and clicked Change.

Under the Member of section, I selected the circle next to Domain and entered the domain name.

After clicking OK, I had to enter the admin credentials. Then a window popped up confirming the CLIENT4 machine successfully joined the domain.

Next, I had to restart the CLIENT4 machine to apply the changes.

After the CLIENT4 machine booted back up, I was able to log on with a domain user account.

On the DC1 machine, I could see CLIENT4 was added to Active Directory Users and Computers under the domain.

The computer was also assigned an IP address through DHCP.

<img src="" height="70%" width="70%" alt="#"/>
