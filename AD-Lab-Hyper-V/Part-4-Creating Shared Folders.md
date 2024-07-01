# Part 3: Creating Shared Folders
## Description:
## Walk-Through:

For this lab I used the GW1 machine as a file server to host the shared folders.

First, I had to set up my drives. GW1 only had a Windows (C:) drive, so I used the Disk Management tool to free up some space and create New Simple Volume to act as my second drive labeled Shared Drive (S:).

Next, I opened Server Manager and selected File and Storage Services. 

To create a share, I had to add the File Server role, so I opened the Add Roles and Features Wizard to install it.

Once the File Server role was installed, I created a New Share on the S volume and labeled it SharedNetworkFolders.

I opened the share in File Explorer and created four separate folders for the Finance, HR, IT, and Marketing departments.

### Configuring Shadow Copies

I also wanted to make sure that the shared folders are backed up, so I decided to configure shadow copies.

I opened the Disk Management tool a created another simple volume labeled Bakup (B:).

Then, I went back to File Explorer, right clicked on Shared Drive (S:) and selected Configure Shadow Copies.

I selected the B volume as the storage location for the shadow copies and adjusted the Schedule settings so that the copies would be created every weekday after business hours at 2 AM.

### Creating Security Groups

Once I had the folders set up, it was time to set the folder permissions for each department.

I only wanted users that belonged to a specific department to have access to the corresponding folder on the shared drive.

I opened Active Directory Users and Computers on my domain controller (DC1) and created a new security group in each department’s OU (Ex. Finance Department S Drive Access).

Next, I added the user in each department to their corresponding security group.

* John Smith > Finance Department S Drive Access
*** Sarah Woods > HR Department S Drive Access
*** James Brown > IT Department S Drive Access
*** Rachel Williams > Marketing Department S Drive Access

### Setting Folder Permissions

Once the security groups were set, I went back to GW1 and opened File Explorer.

I right clicked on Shared Drive (S:) and opened the properties.

On the Security tab I clicked Edit and removed Everyone and GW1\Users from the permissions.

I added the LabAdmin user to the permissions and gave it full control.

Next, I moved on to the individual folders for each department.

I opened properties for the Finance folder and selected the Sharing tab.

I clicked Advanced Sharing and selected the box next to Share this folder.

I clicked Permissions and removed Everyone.

Then I added the security group Finance Department S Drive Access with Read and Change permissions.

Next, I went to the Security tab and added Finance Department S Drive Access with modify, read & execute, List folder contents, read, and write permissions.

After the folder permissions were set, I logged on to the CLIENT4 machine with the user John Smith.

I opened File Explorer and entered the path to the share folder (\\GW1\Finance) to confirm access.

I repeated the process with the HR, IT, and Marketing folders to give access to their department users.

Finally, I created a test text document in each folder and made user users only had access to the folder for their department to confirm the permissions were set correctly.
