# Part 2: Joining the Domain

## Description:
In this section of the lab, I joined CLIENT4 to the corp.contoso.com domain. When a computer joins a domain, it becomes a member of the domain and gains access to shared files, printers, and other network resources. 

## Walk-Through:
To start, I had two VMs running, my domain controller (DC1) running Windows Server 2022 and a client machine (CLIENT4) running Windows 11.

<img src="https://github.com/emann615/Active-Directory-Lab/assets/117882385/54908056-a386-4038-acaf-be3b6b2482b2" height="70%" width="70%" alt="#"/>

After checking Active Directory Users and Computers, I could see the CLIENT4 machine was not joined to the domain and could not access any of the domain resources. I could only log in with a local user account.

<img src="https://github.com/emann615/Active-Directory-Lab/assets/117882385/f593d408-410e-4052-9189-ecb4edf95c47" height="50%" width="50%" alt="#"/>

To join the domain, I logged in to the CLIENT4 machine using admin credentials. Once logged in, I opened the About page of the system settings and clicked Advanced system settings.

<img src="https://github.com/emann615/Active-Directory-Lab/assets/117882385/175688ec-9ee8-44cc-946a-13312b89001b" height="50%" width="50%" alt="#"/>

In the System Properties window that opened, I selected the Computer Name tab and clicked Change.

<img src="https://github.com/emann615/Active-Directory-Lab/assets/117882385/c028e4bd-50b3-4540-971d-7a64a3d5d0ba" height="30%" width="30%" alt="#"/>

Under the Member of section, I selected the circle next to Domain and entered the domain name.

<img src="https://github.com/emann615/Active-Directory-Lab/assets/117882385/59d62f1b-b2b5-480c-99e0-dc4c6e8cf810" height="30%" width="30%" alt="#"/>

After clicking OK, I had to enter the admin credentials. Then a window popped up confirming the CLIENT4 machine successfully joined the domain.

<img src="https://github.com/emann615/Active-Directory-Lab/assets/117882385/e8efa3f5-c2b8-41c9-b784-41fd79cf6dd6" height="30%" width="30%" alt="#"/>

Next, I had to restart the CLIENT4 machine to apply the changes. After the CLIENT4 machine booted back up, I was able to log on with a domain user account.

<img src="https://github.com/emann615/Active-Directory-Lab/assets/117882385/11d439fc-238f-43fe-875e-79aedadaa119" height="30%" width="30%" alt="#"/>

<img src="https://github.com/emann615/Active-Directory-Lab/assets/117882385/1a3974ec-f0db-4c39-82eb-679972b9b835" height="30%" width="30%" alt="#"/>

On the DC1 machine, I could see CLIENT4 was added to Active Directory Users and Computers under the domain.

<img src="https://github.com/emann615/Active-Directory-Lab/assets/117882385/88d4ce47-db81-4d19-8e9d-d656b3e9c432" height="50%" width="50%" alt="#"/>

The computer was also assigned an IP address through DHCP.

<img src="https://github.com/emann615/Active-Directory-Lab/assets/117882385/6e8236fd-6752-45ab-80ef-94e3af029f3c" height="60%" width="60%" alt="#"/>
