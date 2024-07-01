# Part 5: Group Policy Management
## Description:

In this lab, I used GPO to map network drives, set Windows firewall rules, and install software.

## Walk-Through:

### Mapping Network Drives

I had four folders (Finance, IT, HR, and Marketing) that I previously set up on my file Server GW1.

The permissions for each folder were already set up to only allow access from users their corresponding department OU.

I wanted to use GPO to automatically map the folder location when a user logs in on one of the client machines.

On my domain controller (DC1), I opened the Group Policy Management tool.

I created a new Group Policy Object (GPO) named Drive Mapping.

I right clicked on the Drive Mapping GPO and selected Edit to open Group Policy Management Editor tool.

Under User Configuration, I selected Preferences > Windows Settings > Drive Maps.

I right clicked inside the window that appeared and selected New > Mapped Drive.

In the General tab of the New Drive Properties window, I added the location of the shared Finance folder (\\GW1\Finance).

I checked the box next to Reconnect and selected S for the Drive letter.

Next, I selected the Common tab.

I checked the boxes next to “Run in logged-on user’s security context” and “Item-level targeting”, then clicked Targeting.

I clicked New Item > Security Group and added the Finance Department S Drive Access security group.

I repeated the process to add drive maps for the HR, IT, and Marketing shared folders.

After all the drive maps were added to the GPO, I exited the Group Policy Management Editor. I right clicked on the Users OU and selected Link Existing GPO and selected the Drive Mapping GPO.

I went back to the CLIENT1 machine where I was logged on as James Brown, a user in the IT department.

I checked File Explorer and could see that the drive had not yet been mapped despite my newly created GPO.

I opened Command Prompt and entered the command gpupdate /force to update the group policy on CLIENT1.

I checked File Explorer again and could see that the location to the IT shared folder was now mapped.

I logged on to CLIENT1 with users from the other three departments and was able to confirm that the correct folder was mapped for each user.

### Setting Windows Firewall Rules

I was having an issue accessing the client machines from my domain controller using the Computer Management tool. Whenever I tried to connect, I received the message shown in the mage below.

I new the computer was connected to the network, because I was already logged in with a domain user account. This indicated that I needed to configure Windows Firewall rules to allow remote management.

I could have simply enabled the rules locally on the computer itself, but I did not want to have to do that for each of the client machines individually. This led me to the idea of applying the necessary firewall rules using group policy.

On the DC1 machine, I opened the Group Policy Management tool and created a new GPO named Windows Firewall Inbound Rules.

Next, I opened Group Policy Management Editor. Under Computer Configuration, I selected Policies > Windows Settings > Security Settings > Windows Defender Firewall with Advanced Security.

I opened Windows Defender Firewall Properties and updated the settings for the Domain Profile, Private Profile, and Public Profile as follows:

* Firewall state: On
* Inbound connections: Block
* Outbound connections: Allow
* Under the Settings section of each profile, I clicked Customize and set the following options:
   * Display a notification: No
   * Allow unicast response: Yes
   * Apply local firewall rules: Yes
   * Apply local connection security rules: Yes

Next, I selected Inbound Rules to configure the rules I needed for remote management.

I right clicked in the window that opened and selected New rule.

In the New Inbound Rule Wizard, I selected the circle next to Predefined.

From the dropdown box, I selected Remote Event Log Management.

After clicking Next, it showed which rules would be created. I left all the boxes checked and clicked Next again.

I made sure the circle next to Allow the connection was selected and clicked Finish to create the inbound rules.

Back in the Group Policy Management tool, I linked the Windows Firewall Inbound Rules GPO to the Workstations OU.

I restarted the CLIENT4 machine to apply the new group policy. After CLIENT4 rebooted, I was able to successfully connect to it from DC1 using the Computer Management tool.

### Installing Software

In this section, I wanted to test how Group Policy could be used to deploy software.

For this test I created a GPO to install Google Chrome and Microsoft Teams to the client machines on the domain.

First, I downloaded the MIS files for Google Chrome and Microsoft Teams.

Back on GW1 is created a new folder on the shared drive named Software.

I opened properties for the Software folder and selected the Sharing tab.

I clicked Advanced Sharing and selected the box next to Share this folder.

I clicked Permissions and removed Everyone.

Then I added the groups Domain Users and Domain Computers with Read permissions.

Next, I went to the Security tab and added Domain Users and Domain Computers making sure they had read & execute permissions.

I added the MSI files I downloaded to the Software folder.

Next, I logged on to DC1 and opened the Group Policy Management tool.

I created a new GPO named Software Install and opened the Group Policy Management Editor.

Under Computer Configuration, I selected Policies > Software Settings > Software Installation.

I right clicked inside the window and selected New > Package.

I entered the path to the shared Software folder and selected the MSI file for Google Chrome.

In the Deploy Software window that popped up, I selected the circle next to Assigned.

I repeated the process to create another package for Microsoft Teams.

Next, I went back to the Group Policy Management tool and linked the GPO to the Workstations OU.

Now that I had the GPO setup and linked to the Workstations OU, I logged on to CLIENT1.

I opened Command Prompt and entered the command gpupdate /force.

The command returned a message that stated the computer needed to be restarted to apply the settings.

After I rebooted ClIEN1, I could see that both Chrome and Microsoft Teams were installed.
