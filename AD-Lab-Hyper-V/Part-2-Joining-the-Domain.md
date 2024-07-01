# Part 1: AD Lab Setup Using Hyper-V

## Description:
In this section of the lab, I joined CLIENT4 to the corp.contoso.com domain. When a computer joins a domain, it becomes a member of the domain and gains access to shared files, printers, and other network resources. 

## Walk-Through:
To start, I had two VMs running, my domain controller (DC1) running Windows Server 2022 and a client machine (CLIENT4) running Windows 11.

The CLIENT4 machine was not joined to the domain and could not access any of the domain resources. I could only log in with a local user account.

To join the domain, I logged in to the CLIENT4 machine using admin credentials.

Once logged in, I opened the About page of the system settings and clicked Advanced system settings.

In the System Properties window that opened, I selected the Computer Name tab and clicked Change.

Under the Member of section, I selected the circle next to Domain and entered the domain name.

After clicking OK, I had to enter the admin credentials. Then a window popped up confirming the CLIENT4 machine successfully joined the domain.

Next, I had to restart the CLIENT4 machine to apply the changes.

After the CLIENT4 machine booted back up, I was able to log on with a domain user account.

On the DC1 machine, I could see CLIENT4 was added to Active Directory Users and Computers under the domain.

The computer was also assigned an IP address through DHCP.
