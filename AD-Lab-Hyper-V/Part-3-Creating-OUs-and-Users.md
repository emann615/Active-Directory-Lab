# Part 3: Creating OUs and Users
## Description:
## Walk-Through:
After installing the lab environment, I wanted to create a few Organization Units (OUs) and user accounts to use for the lab.

I booted up the domain controller (DC1) and logged on with the LabAdmin user account.

Once I was logged on, I selected Start > Windows Administrative tools > Active Directory Users and Computers.

With Active Directory Users and Computers open, I clicked the arrow next to the domain corp.contoso.com and saw two OUs, one named CORP and another named Domain Controllers.

I expanded the CORP OU and saw there were four additional OU’s inside it, one of which was named USERS.

Inside the USERS OU there were four test user accounts that came loaded in by default with the lab environment, but I wanted to create some additional user accounts to use for the lab. 

I also wanted to separate the users into different departments, so I decided to create additional OU’s inside the USERS OU.

### Creating OUs
I right clicked on the USERS OU and selected New > Organizational Unit.

I named the OU “HR” and clicked OK.

I repeated the process to create OU’s for the other departments (Finance, IT, and Marketing).

Once I was done creating the OU’s for each department, I could see them all listed under the USERS OU.

### Creating Users

Next, I wanted to create a user in each department’s OU.

I right clicked on the Finance OU and selected New > User.

I filled out the First name, Last name, and User logon name fields and clicked Next.

On the next screen, I entered a password for the user account. 

Since this is just a lab, I unchecked the box next to “User must change password at next logon” and checked the box next to "Password never expires”.

I repeated the process to create a user account in each department’s OU.

After creating the user accounts, I booted up the CLIENT4 machine and was able to successfully log on with one of the newly created users.
