<h1>Active Directory Home Lab</h1>

 ### [YouTube Demonstration](https://youtu.be/7eJexJVCqJo)

<h2>Description</h2>
Active Directory (AD) is a directory service created by Microsoft that runs on Windows Servers. It allows administrators to control what access and permissions users and computers have on a domain network. In this lab, I will show you how to set up an Active Directory home lab using Oracle VM VirtualBox.
<br />


<h2>Languages and Utilities Used</h2>

- <b>VirtualBox</b> 
- <b>Active Directory</b>
- <b>PowerShell</b>

<h2>Environments Used </h2>

- <b>Windows 10</b> (21H2)
- <b>Windows Server 2022</b>

<h2>Program walk-through:</h2>

<h3>Part 1: Install VirtualBox</h3>

1. Download **VirtualBox** by going to the following link: https://www.virtualbox.org/wiki/Downloads
   - Download the version for whatever OS you are using.

<img src="https://user-images.githubusercontent.com/117882385/224390278-d7e4222c-6e2c-4eb8-8d43-ec41a3b8ec11.jpg" height="80%" width="80%" alt="VirtualBox Download"/>

2. Download the **VirtualBox Extension Pack** from the same page.

<img src="https://user-images.githubusercontent.com/117882385/224393765-d360956a-1bce-4199-830a-830e4551c8f8.jpg" height="80%" width="80%" alt="VirtualBox Extension Pack Download"/>

4. Open the files you downloaded to install **VirtualBox** and the **VirtualBox Extension Pack**.

<h3>Part 2: Download Windows 10 and Windows Server 2022 ISO Files</h3>

1. Download the **media creation tool** from the following link: https://www.microsoft.com/en-us/software-download/windows10

<img src="https://user-images.githubusercontent.com/117882385/224394320-fdba0899-5d7d-4051-9fc0-6e535e95f445.jpg" height="80%" width="80%" alt="Media Tool Download"/>

2. Run the tool and follow the steps to download the **Windows 10 ISO**.
   * There are instructions on the download page for how to use the tool to download the ISO file.

<img src="https://user-images.githubusercontent.com/117882385/224397663-9602b21e-1542-43bf-8f6e-ea403caa68d5.jpg" height="80%" width="80%" alt="Media Tool Download"/>

3. Download the **Windows Server 2022 ISO** from the following link: https://info.microsoft.com/ww-landing-windows-server-2022.html
   * You will have to fill out your information to register for the 180 day free trial in order to download the ISO file.

<img src="https://user-images.githubusercontent.com/117882385/224398317-e1b9868f-5b2f-49a5-8e75-3574c2115523.jpg" height="80%" width="80%" alt="Windows Server 2022 Download"/>

<img src="https://user-images.githubusercontent.com/117882385/224398502-2423adc9-b7a8-4e1a-ad06-e3c34503effd.jpg" height="80%" width="80%" alt="Windows Server 2022 Download"/>

<h3>Part 3: Create Domain Controller Virtual Machine</h3>

1. Open **VirtualBox**.
2. Click **New** from the top menu bar to set up a new machine.

<img src="https://user-images.githubusercontent.com/117882385/224441280-8631c621-ded8-4810-ba97-c778ac5b2bbb.jpg" height="80%" width="80%" alt="DC Virtual Machine Creation"/>

3. Name the machine '**DC**' for Domain Controller.
4. From the dropdown next to **Version**, select **Other Windows (64 bit)**, and click **Next**.

<img src="https://user-images.githubusercontent.com/117882385/224441366-df922c98-ad0d-4d63-a20a-5287583c4c86.jpg" height="80%" width="80%" alt="DC Virtual Machine Creation"/>

5. On the next screen set the amount of **RAM** and the number of **CPUs** you want to use.
   * If you have at least 8GB of RAM on your host computer, setting the RAM to 2048MB works pretty well.

<img src="https://user-images.githubusercontent.com/117882385/224441587-15a6e9d6-e613-40f2-96b8-027ab11f0d0c.jpg" height="80%" width="80%" alt="DC Virtual Machine Creation"/>

6. Click **Next** through the rest of the screens, and click **Finish** on the last screen.

<img src="https://user-images.githubusercontent.com/117882385/224441678-48b2e4cc-54c6-4e31-96e2-2cf707c133da.jpg" height="80%" width="80%" alt="DC Virtual Machine Creation"/>

7. Select **Settings** from the top menu to edit the settings of the virtual machine you just created.

<img src="https://user-images.githubusercontent.com/117882385/224441749-08b26115-ba8b-4787-b4e7-1e3bda9c980f.jpg" height="80%" width="80%" alt="DC Virtual Machine Creation"/>

8. Go to the **Advanced** tab and set both the dropdowns next to **Shared Clipboard** and **Drag ‘n Drop** to **Bidirectional**.
   * Shared clipboard allows you to copy/paste between your host computer and the virtual machine.
   * Drag ‘n Drop allows you to drag/drop files between your host computer and the virtual machine.

<img src="https://user-images.githubusercontent.com/117882385/224433773-2a570a20-36cb-4f7b-aa43-a10cf459f4ee.jpg" height="80%" width="80%" alt="DC Virtual Machine Creation"/>

9. Select **Network** from the left menu.
   * The first network adapter is already enabled and set to **NAT**. It connects to our home internet. You need to enable a second network adapter that will connect to our internal VirtualBox network.

<img src="https://user-images.githubusercontent.com/117882385/224433868-7205d48f-e381-44ee-a966-d8b14c2f7d90.jpg" height="80%" width="80%" alt="DC Virtual Machine Creation"/>

10. Select **Adapter 2**.
11. Select the checkbox next to **Enable Network Adapter**.
12. From the dropdown next to **Attached to** select **Internal Network**.
13. Click **OK** in the bottom right corner to close the settings.

<img src="https://user-images.githubusercontent.com/117882385/224434172-88a61379-77cd-4b1e-96e8-795f8d84a963.jpg" height="80%" width="80%" alt="DC Virtual Machine Creation"/>

<h3>Part 4: Install and Set Up Windows Server 2022 on the DC Virtual Machine</h3>

1. Double click the **DC** virtual machine, and it will start in a new window that appears.
   * Once it has loaded a box will appear that says your virtual machine failed to boot. This is because you have not installed the actual operating system yet.

<img src="https://user-images.githubusercontent.com/117882385/224505813-ebc2b305-c5c8-475a-bb90-082940bf36c5.jpg" height="80%" width="80%" alt="Windows Server 2022 Installation"/>

2. Click the dropdown arrow in the box next to **DVD** and navigate to the folder where you downloaded the **Windows Server 2022 ISO**.

<img src="https://user-images.githubusercontent.com/117882385/224505534-f4f08ad3-c33e-47a2-b615-8ec8e0cb0891.jpg" height="80%" width="80%" alt="Windows Server 2022 Installation"/>

<img src="https://user-images.githubusercontent.com/117882385/224506425-5b203898-0eb8-4336-9573-b4649dc786c0.jpg" height="80%" width="80%" alt="Windows Server 2022 Installation"/>

3. Select the **Windows Server 2022 ISO** file, and click **Open**.

<img src="https://user-images.githubusercontent.com/117882385/224506302-b6dd876a-95bd-49f8-9cf3-f22734d63eb6.jpg" height="80%" width="80%" alt="Windows Server 2022 Installation"/>

4. Click **Mount and Retry Boot** to restart your virtual machine.

<img src="https://user-images.githubusercontent.com/117882385/224515231-0783677c-2897-4623-b6a1-4e0d813ed48b.jpg" height="80%" width="80%" alt="Windows Server 2022 Installation"/>

5. Once your VM restarts, the Microsoft Server Operating System Setup tool will appear. Click **Next** and **Install** now.

<img src="https://user-images.githubusercontent.com/117882385/224515262-fa5c0d30-c3a5-4cd4-8882-5fde0ec7bb06.jpg" height="80%" width="80%" alt="Windows Server 2022 Installation"/>

<img src="https://user-images.githubusercontent.com/117882385/224515265-8b60f1bc-e646-4138-8137-2e14debbdcd3.jpg" height="80%" width="80%" alt="Windows Server 2022 Installation"/>

6. On the next screen select **Windows Server 2022 Standard Evaluation (Desktop Experience)**, and click **Next**.
   * If you select an option that does not say ‘Desktop Experience’ you won’t have a GUI.

<img src="https://user-images.githubusercontent.com/117882385/224515309-d6d192f9-7875-4c7a-8b89-151ef646b95c.jpg" height="80%" width="80%" alt="Windows Server 2022 Installation"/>

7. Click the checkbox next to **I accept the license terms**, and click **Next**.

<img src="https://user-images.githubusercontent.com/117882385/224515313-639c5eaf-3246-4daa-8f47-bb2d205c84d3.jpg" height="80%" width="80%" alt="Windows Server 2022 Installation"/>

8. Select **Custom: Install Windows only (advanced)** since this is the first time you are installing Windows on this machine.

<img src="https://user-images.githubusercontent.com/117882385/224515516-dd14c013-cc96-4101-bd0d-9233e0c9008a.jpg" height="80%" width="80%" alt="Windows Server 2022 Installation"/>

9. Click **Next**, and the tool will install Windows 10 on your machine.
   * During installation your virtual machine will restart several times. You will see a black screen that says '**Press any key to boot from CD or DVD**'. Just do not press any buttons until your machine has booted into Windows.

<img src="https://user-images.githubusercontent.com/117882385/224515654-5fe9ae14-75f8-4ddb-8956-9fb73feb4e2b.jpg" height="80%" width="80%" alt="Windows Server 2022 Installation"/>

<img src="https://user-images.githubusercontent.com/117882385/224515660-034307be-b95b-484c-903d-96a88050ce16.jpg" height="80%" width="80%" alt="Windows Server 2022 Installation"/>

<img src="https://user-images.githubusercontent.com/117882385/224515688-e98f76a8-2d81-44ad-9afc-a963f0668c3c.jpg" height="80%" width="80%" alt="Windows Server 2022 Installation"/>

10. Once your virtual machine has booted into Windows you will need to set a password for your Administrator account.
    * Your password can be anything but I just use something simple like '**Password1**' if you are just using it for a lab environment.

<img src="https://user-images.githubusercontent.com/117882385/224515746-90d207cf-51ff-4c6c-85e4-8384ce739d30.jpg" height="80%" width="80%" alt="Windows Server 2022 Installation"/>

11. Once you are at the Windows lock screen, select **Input** from the top menu of your VM, and select the **Keyboard** to see the keystroke you need to press to unlock your machine. 

12. Select **Insert Ctrl-Alt-Delete**, or press the keystroke you see next to it to unlock your machine.

<img src="https://user-images.githubusercontent.com/117882385/224515748-aa7e4963-4dcd-414f-9d6f-7accd1c90b1e.jpg" height="80%" width="80%" alt="Windows Server 2022 Installation"/>

13. Enter the password you created for the Administrator account to log in to your Windows Server.

<img src="https://user-images.githubusercontent.com/117882385/224515808-99425407-ef21-477f-ac70-7e5f301f2c4a.jpg" height="80%" width="80%" alt="Windows Server 2022 Installation"/>

<h3>Part 5: Install VirtualBox Guest Additions</h3>

1. Select **Devices** from the top menu of your VM, and click **Insert Guest Additions CD Image**.

<img src="https://user-images.githubusercontent.com/117882385/224579642-ab19a399-921f-4dfe-bf35-0b424f67b3d3.jpg" height="80%" width="80%" alt="VirtualBox Guest Additions Installation"/>

2. Open **File Explorer** from the bottom menu bar, and click **This PC**.

<img src="https://user-images.githubusercontent.com/117882385/224599787-12a3d080-b57d-49ba-a5ad-eb4cd176699d.jpg" height="80%" width="80%" alt="VirtualBox Guest Additions Installation"/>

3. Under **Devices and drives**, double click **CD Drive (D:) VirtualBox Guest Additions**.

<img src="https://user-images.githubusercontent.com/117882385/224600571-f40154f4-660e-44e9-8abe-5b481f94d896.jpg" height="80%" width="80%" alt="VirtualBox Guest Additions Installation"/>

4. Run the file named **VBoxWindowsAdditions-amd64**.

<img src="https://user-images.githubusercontent.com/117882385/224600590-e00958af-4c72-41a6-9e87-aee6f0960784.jpg" height="80%" width="80%" alt="VirtualBox Guest Additions Installation"/>

5. Click **Next** through the next couple screens, and click **Install**.

<img src="https://user-images.githubusercontent.com/117882385/224599923-60712666-fbb4-41d1-bca3-bb2d93def2e4.jpg" height="80%" width="80%" alt="VirtualBox Guest Additions Installation"/>

<img src="https://user-images.githubusercontent.com/117882385/224599969-641bef50-b0d1-4822-b1e1-487994a99468.jpg" height="80%" width="80%" alt="VirtualBox Guest Additions Installation"/>

<img src="https://user-images.githubusercontent.com/117882385/224599987-0f7f89e7-8969-4412-8b9e-35c0a9e01595.jpg" height="80%" width="80%" alt="VirtualBox Guest Additions Installation"/>

6. After Guest Additions has finished installing, select **I want to manually reboot later**, and click **Finish**.

<img src="https://user-images.githubusercontent.com/117882385/224600149-db9db64f-0c5b-4b48-af8b-9a3dd478f49b.jpg" height="80%" width="80%" alt="VirtualBox Guest Additions Installation"/>

7. Manually shut down the VM by clicking **Start**, clicking the power icon, and clicking **Shut down**.

<img src="https://user-images.githubusercontent.com/117882385/224600165-d37f4417-0652-4765-a3f9-5411c786a269.jpg" height="80%" width="80%" alt="VirtualBox Guest Additions Installation"/>

8. In the little popup that appears, click **Continue**.

<img src="https://user-images.githubusercontent.com/117882385/224600177-debb994c-799f-4bd1-b01e-2825b16a1019.jpg" height="80%" width="80%" alt="VirtualBox Guest Additions Installation"/>

<h3>Part 6: Set Up IP Addressing and Rename the PC</h3>

1. Double click the **DC** machine to start it up again.

<img src="https://user-images.githubusercontent.com/117882385/224601921-dc83c6c3-f572-4221-be3c-99e27f9599d3.jpg" height="80%" width="80%" alt="IP Addressing Setup"/>

2. Log in to the Administrator account.

<img src="https://user-images.githubusercontent.com/117882385/224601940-7696049b-15ea-4ec7-99e1-d5ce28ebb8f1.jpg" height="80%" width="80%" alt="IP Addressing Setup"/>

<img src="https://user-images.githubusercontent.com/117882385/224601976-bc8881a4-d424-4235-b0d9-57bc4aa3f648.jpg" height="80%" width="80%" alt="IP Addressing Setup"/>

3. Click the Network icon on the right side of the bottom menu bar, and click **Network** to open the network setting.

<img src="https://user-images.githubusercontent.com/117882385/224601999-f4b16ffc-c96b-4c0c-9e31-e91cbe8ab364.jpg" height="80%" width="80%" alt="IP Addressing Setup"/>

<img src="https://user-images.githubusercontent.com/117882385/224602016-f0f8914e-3c01-4fbe-902e-f6f460e325d6.jpg" height="80%" width="80%" alt="IP Addressing Setup"/>

4. Click **Change adapter options**.
   * You should see two network adapters in the window that pops up. You need to figure out which one connects to your home internet and which one will connect to your internal **VirtualBox** network.

<img src="https://user-images.githubusercontent.com/117882385/224602050-2a5beca9-9b9a-40a7-9a3b-f45cc9f13bb5.jpg" height="80%" width="80%" alt="IP Addressing Setup"/>

<img src="https://user-images.githubusercontent.com/117882385/224602069-7d41457f-7963-4a38-9b87-917e54154242.jpg" height="80%" width="80%" alt="IP Addressing Setup"/>

5. Right click the first network adapter, and select **Status**.

<img src="https://user-images.githubusercontent.com/117882385/224602111-2241d92b-04e4-440b-ae03-c4d1b1fff77c.jpg" height="80%" width="80%" alt="IP Addressing Setup"/>

6. In the window that pops up, click **Details**.

<img src="https://user-images.githubusercontent.com/117882385/224603586-4f6f5f1b-515c-4ec8-8de5-888d4b965d11.jpg" height="80%" width="80%" alt="IP Addressing Setup"/>

7. Check what IP address appears next to **IPv4 Address**.
   * If the IP address looks something like **10.0.2.15** it is probably connected to your home internet.
   * If the IP address looks something like **169.254.196.79**  it connects to the internal network.

<img src="https://user-images.githubusercontent.com/117882385/224603590-f087a3c6-a200-4795-a2ff-c8f6471d93dd.jpg" height="80%" width="80%" alt="IP Addressing Setup"/>

8. Close the **Details** window and the **Status** window.

<img src="https://user-images.githubusercontent.com/117882385/224603591-a15ce8c8-3991-46d4-b343-6d627688f358.jpg" height="80%" width="80%" alt="IP Addressing Setup"/>

9. Repeat **steps 5-8** for the second network adapter.

<img src="https://user-images.githubusercontent.com/117882385/224603799-9ba45ef0-4c28-49b4-805a-895d794281a7.jpg" height="80%" width="80%" alt="IP Addressing Setup"/>

<img src="https://user-images.githubusercontent.com/117882385/224603803-49b9fd83-1c69-4e65-88f5-76ac349713c3.jpg" height="80%" width="80%" alt="IP Addressing Setup"/>

<img src="https://user-images.githubusercontent.com/117882385/224603808-f59022d4-5d12-4b4f-8f3d-6949405c7e8e.jpg" height="80%" width="80%" alt="IP Addressing Setup"/>

10. Right click on the adapter connected to your home internet, and select **Rename**.

<img src="https://user-images.githubusercontent.com/117882385/224604032-fbc49fff-a391-47f6-9e57-23306d7884ef.jpg" height="80%" width="80%" alt="IP Addressing Setup"/>

11. Rename it to something like '**INTERNET**'.

<img src="https://user-images.githubusercontent.com/117882385/224604028-e15874c9-4912-4a94-9f61-dc3e6747e71d.jpg" height="80%" width="80%" alt="IP Addressing Setup"/>

12. Right click on the adapter that connects to the internal network, and select **Rename**.

<img src="https://user-images.githubusercontent.com/117882385/224604031-b01e529c-7e91-414f-96ff-1b41e00c72bb.jpg" height="80%" width="80%" alt="IP Addressing Setup"/>

13. Rename it to something like '**INTERNAL**'.

<img src="https://user-images.githubusercontent.com/117882385/224604814-8e099bf9-15a1-4677-8bb3-4938f396409f.jpg" height="80%" width="80%" alt="IP Addressing Setup"/>

14. Right click on the internal network adapter again, and select **Properties**.

<img src="https://user-images.githubusercontent.com/117882385/224604816-0fde3450-f8a2-4024-b2a1-65e1f9c43b87.jpg" height="80%" width="80%" alt="IP Addressing Setup"/>

15. Click Internet **Protocol Version 4 (TCP/IPv4)**.

<img src="https://user-images.githubusercontent.com/117882385/224604817-b945bf6d-1ae7-4e5f-be68-c1ac075b61c7.jpg" height="80%" width="80%" alt="IP Addressing Setup"/>

16. Select **Use the following IP address**, and add the following information.
    * **IP address:** 172.16.0.1
    * **Subnet mask:** 255.255.255.0
    * **Default gateway:** (leave blank)
       * You do not need to add a default gateway because the domain controller itself will act as the default gateway.
    * **Preferred DNS server:** 127.0.0.1
       * 127.0.0.1 is a loopback address that refers to your IP address, so you can also use your IP address (172.16.0.1) as the DNS instead.

<img src="https://user-images.githubusercontent.com/117882385/224605123-062fe7c2-7116-4ce2-ab7f-05dc5eb3f21e.jpg" height="80%" width="80%" alt="IP Addressing Setup"/>

17. Click **OK** to save your settings.

<img src="https://user-images.githubusercontent.com/117882385/224605125-773fffa7-2e5a-4dd4-ba30-93d4751d88e3.jpg" height="80%" width="80%" alt="IP Addressing Setup"/>

18. Click **OK** again to close the Properties window.

<img src="https://user-images.githubusercontent.com/117882385/224605126-4dcc22d6-9b14-4041-98e2-1785c2659a86.jpg" height="80%" width="80%" alt="IP Addressing Setup"/>

19. Right click **Start**, and select **System**.

<img src="https://user-images.githubusercontent.com/117882385/224605241-d6fe3703-172d-41bb-bac9-bd9bbc67f94e.jpg" height="80%" width="80%" alt="Renaming the PC"/>

20. Click **Rename this PC**.

<img src="https://user-images.githubusercontent.com/117882385/224605242-8742927a-aa86-4705-9604-3f5f6a6c6e00.jpg" height="80%" width="80%" alt="Renaming the PC"/>

21. Rename it something like '**DC**' for Domain Controller, and click **Next**.

<img src="#" height="80%" width="80%" alt="Renaming the PC"/>

22. Click **Restart now**.

<img src="#" height="80%" width="80%" alt="Renaming the PC"/>

23. In the little popup that appears, click **Continue**.

<img src="#" height="80%" width="80%" alt="Renaming the PC"/>

<h3>Part 7: Install Active Directory Domain Services and Create Your Domain</h3>

1. Double click the **DC** machine to start it up again.
2. Log in to the Administrator account.
3. Once you are logged in, the **Server Manager Dashboard** will automatically load up, and you need to click **Add roles and features** to open the Add Roles and Features Wizard.
4. In the window that appears, click **Next** until you get to the page titled Select destination server
5. You should see the server you created named **DC**. Select it, and click **Next**.
6. On the next page titled Select server roles, click the box next to **Active Directory Domain Services**.
7. In the popup that appears, click **Add Features**.
8. Click **Next** through the next few pages, and click **Install**.
9. Click **Close** to exit the Add Roles and Features Wizard.
10. On the top right side of the **Server Manager Dashboard** you should see a flag icon with a yellow warning icon next to it. Click it.
10. From the menu that drops down, click **Promote this server to a domain controller**. This will open the Active Directory Domain Services Configuration Wizard.
11. Select **Add a new forest**.
12. In the box next to **Root domain name**, add your domain name, and click **Next**.
    * You can name the domain anything you want, but for the purposes of this lab  just use '**mydomain.com**'.
13. Type in a password and click **Next**. 
14. I suggest using '**Password1**' again if you are only using this for the lab.
15. Click **Next** through the next few pages, and click **Install**.
16. Once it has finished installing, you will see a popup that says '**You are about to be signed out**'. Click **Close**, and your VM will automatically restart.
17. Once your VM has loaded back up, log in to the Administrator account again.
    * You will notice your account name now says '**MYDOMAIN\Administrator**'.
 
<h3>Part 8: Create Dedicate Domain Admin Account</h3>

1. Click **Start**, and select **Windows Administrative Tools**.
2. From the options that drop down click **Active Directory Users and Computers**.
3. In the window that appears, right click **mydomain.com**.
4. Hover over **New**, and select **Organizational Unit**.
5. In the box under Name, put it something like '**ADMINS**'. 
6. [OPTIONAL] Uncheck the box next to **Protect container from accidental deletion**, and click **OK**.
   * This just makes it easier to delete later.
8. Right click the Organization Unit you just created named **ADMINS**.
9. Hover over **New**, and select **User**.
10. Fill out the name information using your name.
11. In the box under **User logon name**, add a user name for your admin account, and click **Next**.
12. Create a password. Again you can use '**Password1**'.
13. Uncheck the box next to **User must change password at next logon**, and check the box next to **Password never expires**.
14. Click **Next**, and click **Finish**.
15. The user you just created will now appear in the Active Directory Users and Computers window. Right click the user, and select **Properties**.
16. In the properties window, select the **Member of tab**, and click **Add**.
17. In the box under **Enter the object names to select** type '**domain admins**'.
18. Click **Check Names**, and click **OK**.
19. In the Properties window click **Apply** and **OK**.
20. Click **Start** and sign out.
21. On the login screen, click **Other user** in the bottom left corner.
22. Log in with the new admin user account info you created in **steps 10 and 11**.

<h3>Part 9: Install RAS / NAT</h3>

1. Click **Add roles and features** on the Server Manager Dashboard to open the Add Roles and Features Wizard.
2. Click **Next** until you reach the Select server roles page.
3. Check the box next to **Remote Access**.
4. Click **Next** until you reach the Select role services page.
5. Click the box next to **Routing**.
6. In the window that pops up click **Add Features**.
7. Click **Next** through the next few pages, and click **Install**.
8. Close the Add Roles and Features Wizard.
9. Select **Tools** from the top right side of the Server Manager Dashboard, and click **Routing and Remote Access** from the dropdown menu. 
10. In the Routing and Remote Access window, right click **DC (local)**, and select **Configure and Enable Routing and Remote Access** to open the Routing and Remote Access Setup Wizard.
11. Select **Network address translation (NAT)**, and click **Next**.
12. Make sure **Use this public interface to connect to the internet** is selected.
13. Under Network interfaces, select the one you named '**INTERNET**', and click **Next**.
14. Click **Finish** to complete setup.
15. In the Routing and Remote Access window you should now see a little icon with a green arrow pointing up next to **DC (local)**.

<h3>Part 10: Set Up a DHCP Server On Your Domain Controller</h3>

1. Click **Add roles and features** on the Server Manager Dashboard to open the Add Roles and Features Wizard
2. Click **Next** until you reach the Select server roles page.
3. Check the box next to **DHCP Server**.
4. In the window that pops up click **Add Features**.
5. Click **Next** through the next few pages and click **Install**.
6. Close the Add Roles and Features Wizard.
7. Select **Tools** from the top right side of the Server Manager Dashboard and click **DHCP** from the dropdown menu.
8. In the DHCP window select your DHCP server by clicking **dc.mydomain.com**. 
9. Right click **IPv4** and select **New Scope**. 
10. In the New Scope Wizard window that appears click **Next**.
11. On the Name Scope page enter the name of the scope in the box next to **Name**, and click **Next**.
    * You can name the scope after what the IP range is (**172.16.0.100-200**)
12. On the IP Address Range page enter the following information:
    * **Start IP address:** 172.16.0.100
    * **End IP address:** 172.16.0.200
    * **Length:** 24
    * **Subnet mask:** 255.255.255.0
13. Click **Next** to get to the Add Exclusions and Delay page.
    * This page allows you to add any IP addresses you don’t want to give out, but you can leave it blank for this lab.
14. Click **Next** to get to the Lease Duration Page.
    * This page allows you to set how long a computer can have an IP address before it needs to be refreshed. You can leave it at 8 days for this lab.
15. Click **Next** to reach the Configure DHCP Options page, and make sure **Yes, I want to configure these options now** is selected.
16. Click **Next** to reach the Router(Default Gateway) page.
17. In the box under IP address enter the Domain Controllers IP address (**172.16.0.1**), and click **Add**.
18. Click **Next** through the next few pages, and click **Finish**.
19. In the DHCP window right click your server (**dc.mydomain.com**) and select **Authorize**.
20. Right click the server again, and select **Refresh**.
    * Next to **IPv4** you should now see an icon with a green check mark indicating it is online now.
    * If you click the dropdown arrow next to **IPv4** you should also see the scope you just created.

<h3>Part 11: Use PowerShell Script to Create Users</h3>

1. From the Server Manager Dashboard, click **Configure this local server**.
2. Next to **IE Enhanced Security Configuration**, click **On**.
3. Select **Off** under Administrators and Users. 
4. Open **Internet Explorer**, and download the PowerShell script using the following link: https://github.com/joshmadakor1/AD_PS 
5. Click **Save as**, and save it to the **Desktop** folder.
6. Right click the **AD_PS-master.zip** file you just downloaded, and select **Extract all**.
7. Open the extracted folder. You will see a PowerShell script file named **1_CREATE_USERS**, and a text file named **names**.
8. Open the **names** file and add your name at the top of the file.
    * This file contains about 1000 randomized users that will be added to Active Directory once you run the PowerShell script.
9. Click **Start**, and select **Windows PowerShell**.
10. Right click **PowerShell ISE**, hover over **More**, and click **Run as administrator**.
11. Click **Yes** when asked '**Do you want to allow this app to make changes to your device?**'.
12. Click the open scripts icon from the top menu bar, navigate the **1_CREATE_USERS** script, and open it.
13. Enter the following command in PowerShell:
    * PS C:\Windows\system32> **Set-ExecutionPolicy unrestricted**
14. Click **Yes to All** in the popup that appears.
15. Enter the following commands in PowerShell:
    * C:\Windows\system32> **cd c:\users\a-emann\desktop\AD_PS-master** 
     * Replace a-emann with your own username.
16. Click the play button to run the script.
17. In the popup that appears, click **Run once**.
    * To confirm that the script worked, you can go back to Active Directory Users and Computers. You should now see a **USERS** folder under your domain with all the users the script just created.
    * You may need to right click your domain and select **Refresh** to see all the new users.
18. Minimize your Domain Controller virtual machine.

<h3>Part 12: Create Client Virtual Machine</h3>

1. Go back to **VirtualBox**.
2. Click **New** from the top menu bar to set up a new machine.
3. Name the machine '**CLIENT1**'.
4. From the dropdown next to **Version**, select **Windows 10 (64 bit)**, and click **Next**.
5. On the next screen set the amount of **RAM** and the number of **CPUs** you want to use.
   * If you have at least 8GB of RAM on your host computer, setting the ram to 2048MB works pretty well.
   * I suggest setting the Processors to at least 2 CPUs.
6. You can click **Next** through the rest of the screens, and click **Finish** on the last screen.
7. Select **Settings** from the top menu to edit the settings of the virtual machine you just created.
8. Go to the **Advanced** tab and set both the dropdowns next to **Shared Clipboard** and **Drag ‘n Drop** to **Bidirectional**.
    * Shared clipboard allows you to copy/paste between your host computer and the virtual machine.
    * Drag ‘n Drop allows you to drag/drop files between your host computer and the virtual machine.
9. Select **Network** from the left menu and make sure **Adapter 1** is selected.
10. From the dropdown next to **Attached to**, select **Internal Network**.
11. Click **OK** in the bottom right corner to close the settings.







<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
