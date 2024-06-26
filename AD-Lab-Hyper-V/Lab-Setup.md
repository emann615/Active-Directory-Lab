I used Windows Hyper-V to provision and deploy all the virtual machines needed for the lab.
First, I had to make sure virtualization was enabled on my laptop. 
I opened Task Manager and went to the Performance tab. Next to Virtualization, I made sure it said Enabled. 
If virtualization was disabled, it would have been necessary to go into the BOIS settings to enable it, but fortunately it was already enabled.
Next, I clicked the start icon and typed in “windows features”. I selected “Turn Windows features on and off” from the results.
In the Windows Feature window I made sure the box next to Hyper-V was checked. Originally there was no option to enable Hyper-V because my laptop is running on Windows 11 Home Edition, which does not come with Hyper-V included.
I followed the steps in the video here to install Hyper-V.
After Hyper-V was installed and enabled, I downloaded Microsoft’s lab environment linked here.
Once the lab environment finished downloading, I extracted the files to the Lab folder on my desktop.
Before installing the lab environment, I had to open Hyper-V and create a new virtual network switch.
After creating the virtual network switch, I opened the folder where I downloaded the lab environment and executed the stetup.exe file to install the virtual machines.
Once the installation finished, I could see all the virtual machines were now loaded into Hyper-V.
