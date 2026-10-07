# Microsoft-Identity-and-Access-Administrator-In-Azure.
## Step by Step on how to Create and Manage users.

## Part 1: Managing user roles.

  - Navigating to the Microsoft Entra ID dashboard
    
  <img width="980" height="619" alt="Navigating to the dashboard" src="https://github.com/user-attachments/assets/a7724f1f-affb-4d18-8698-20dd319909c5" />

  - Creating a new user; assigning a username and password test their application admin rights
    
  <img width="981" height="553" alt="creating new user" src="https://github.com/user-attachments/assets/c520746c-fea2-4cd2-8d3a-372f1209ea9d" />

### Logging in the User and creating an Enterprise application

  <img width="973" height="559" alt="image" src="https://github.com/user-attachments/assets/3bd29969-603f-4ecc-bbbc-7febbdf91a17" />

  - Updating password
    
  <img width="966" height="564" alt="image" src="https://github.com/user-attachments/assets/9d783352-b4dd-45b4-88f5-8e8059f515e6" />

  - Setting up Multi-Factor Authentication (MFA) during sign-in for better security
 
  <img width="979" height="565" alt="image" src="https://github.com/user-attachments/assets/80e7f02c-f624-430e-9fb4-68f62972f69e" />

  - User dashboard page
    
  <img width="962" height="559" alt="image" src="https://github.com/user-attachments/assets/c5ff0509-4b83-4374-bba1-3c0329f10154" />

  - Navigating to the Enterprise application
    
  <img width="949" height="562" alt="image" src="https://github.com/user-attachments/assets/7427ef78-11f4-4014-8afb-35f7b35a21d6" /><br/>

  > Creating application is unavailable,showing that new user can not yet manage applications, which implies new accounts have no privileged access by default
  
  <img width="958" height="561" alt="image" src="https://github.com/user-attachments/assets/74020180-4ce9-4e64-9de1-c8302bb27532" />
  
  <img width="976" height="560" alt="image" src="https://github.com/user-attachments/assets/32205a80-4414-4f67-8b26-49448b16795b" />

### Assigning the application admin role and creating an application

  > Administrators can assign and change users administrative roles,  resetting user passwords, managing user licenses, and managing domain names.

  - Selecting the user to modify
  
  <img width="964" height="561" alt="image" src="https://github.com/user-attachments/assets/ce066d31-eb8b-40c6-95d9-4d7fab47fd53" />

  - Selecting assigned roles + Add assignments.

        The image below shows that there's no assigned role for the user yet
    <img width="985" height="568" alt="image" src="https://github.com/user-attachments/assets/50a327a1-2a27-42b4-8b66-03513aab179e" />

  - Assigning Application administrator role to the user
    
  <img width="970" height="563" alt="image" src="https://github.com/user-attachments/assets/3a2eae12-1674-4e47-90b7-29efc103b343" />

  - Changing the assignment to active
    
  <img width="951" height="568" alt="image" src="https://github.com/user-attachments/assets/184767bc-a2fe-4901-adaa-5f5a436d847d" />

  - Then Click Assign

  <img width="771" height="415" alt="image" src="https://github.com/user-attachments/assets/03e26092-88d2-4bf0-91f2-518001b99882" />

      Successfully Assigned a role to the user

### Checking application permission

  - Sign in the user
  - In the search box at the top page, search Enterprise application > Select All application + New application

        Notice that "create your own application" is now available 
  - Click on "create your own application"
    
    <img width="786" height="432" alt="image" src="https://github.com/user-attachments/assets/70487227-3529-4eea-9b7b-ab900e9d63d8" />

        After the Application administrator is assigned, this role now has the ability to add application to the tenant

### Remove a role Assignment

- Log in as Admin user, in the search box at the top; search Microsoft Entra Roles and administration
  
  <img width="778" height="413" alt="image" src="https://github.com/user-attachments/assets/4ae108b7-35e8-4bd0-8478-e221c454425a" />

- In All roles, search or select application administrator role
  
  <img width="785" height="419" alt="image" src="https://github.com/user-attachments/assets/4e32687e-5cea-4c9a-9465-c8b1bc20bd47" />
  
      On the page, search or select the user to remove the assignment role

- Scroll all the way to the right on the user, select "Remove" from the options; Answer "Yes"

    <img width="782" height="419" alt="image" src="https://github.com/user-attachments/assets/48ec29c2-9647-464e-bc18-893d5825bbe1" />

      Role Assignment removed successfully

### Bulk Import of Users

> Bulk operations for creating users with a .csv file

- In Microsoft ID Entra menu > Select Users + All users | All users tile, Select Bulk operations + Bulk create

  <img width="773" height="422" alt="image" src="https://github.com/user-attachments/assets/a5036fce-114d-48d8-b7e1-d73a91943e04" />

- On the Bulk create user dialog, select the .csv file to be uploaded

  <img width="776" height="420" alt="image" src="https://github.com/user-attachments/assets/65e1d032-834f-4084-a0d9-79a51d32d866" />

> The .csv file include detailed information about users to be created, the image below shows the sample
  
  <img width="782" height="521" alt="image" src="https://github.com/user-attachments/assets/e20668b6-7a4e-4aa3-9135-c7fd4ce5a412" />

- Click submit to add user

### Bulk addition of users using PowerShell
  - Open PowerShell from the windows start menu
  - Install Microsoft graph PowerShell module, if it has not been used before use:
    
        Install-module Microsoft.Graph -scope CurrentUser -Verbose
        When prompted to confirm press Y

    <img width="830" height="557" alt="image" src="https://github.com/user-attachments/assets/861821ea-c372-4c18-8f44-35aa37fe1173" />

  - Confirm the Microsoft graph is installed:

        Get-InstalledModule Microsoft.Graph

    <img width="766" height="114" alt="image" src="https://github.com/user-attachments/assets/e4d856e7-e8cd-41ac-8667-6148a507fa9b" />

  - Log in to Microsoft graph API by running:

        Connect-MgGraph -Scopes "User.ReadWrite.All"
    
    Note: It would redirect to the browser and promt to Sign-in. Use the Admin log in details

  - To verify its connected and to see existing  users, run:

        Get-MgUser

    <img width="779" height="326" alt="image" src="https://github.com/user-attachments/assets/75b1d548-6da6-4d93-8b8b-cf530f5ef682" />

  - To assign a common temporary password to all new users, run the following command and replace with the password that you would like to provide to your users.

          $PWProfile = @{
          Password = "<Enter a complex password>";
          ForceChangePasswordNextSignIn = $false
          }

  - To create a new user, The following command with the user information would be run. If you have more than one user to add, you can use a notepad txt file to add the user
    information and copy/paste into PowerShell.

        New-MgUser `
        -DisplayName "New PW User" `
        -GivenName "New" -Surname "User" `
        -MailNickname "newuser" `
        -UsageLocation "US" `
        -UserPrincipalName "newuser@<labtenantname.com>" `
        -PasswordProfile $PWProfile -AccountEnabled `
        -Department "Research" -JobTitle "Trainer"


### Remove a user from Microsoft Entra ID

- Remove a User
  
  In Microsoft ID Entra menu > Select Users + All users and then select the check box for the user to be deleted > Select Delete from the menu > Review the confirmation dialog, and then
  select Yes

  <img width="761" height="434" alt="image" src="https://github.com/user-attachments/assets/6494e8bd-2bc9-4dcf-9d15-c452d6fbae97" />

- Restore a deleted user

  On the Users page, select Deleted users from the left navigation menu + Review the list of deleted users, and then select the one to be restored > Review the dialog box and then select OK

      User | Deleted users | All deleted user tiles + Restore user

  <img width="772" height="300" alt="image" src="https://github.com/user-attachments/assets/9d28bea0-413c-45db-8d87-cac25d082221" /><br/>

  > By default, deleted user accounts are permanently removed from Azure Active Directory automatically after 30 days.

  - In the left navigation menu, select All users, Verify the user has been restored.

### Add a Windows 10 license to a user account

  - Find unlicensed user in Azure Active Directory
    
    In Microsoft ID Entra menu > Select Users + All users > Select User,
    
    Review profile and ensure User has a Usage Location set,

    In the left navigation menu, select Licenses,
    
    Ensure that Raul has "No license assignments found."

    <img width="748" height="339" alt="image" src="https://github.com/user-attachments/assets/c85b7c7c-3f75-4469-a87d-89b9f2894775" />

  - Add a Windows license to User

    > Add and remove licenses via the Microsoft 365 admin center, This is a relatively new change.

    In the left navigation menu, select Billing > select Licenses,

    <img width="786" height="504" alt="image" src="https://github.com/user-attachments/assets/82cb2a49-69f0-4e8c-838d-0e4030f61874" />

    Select Windows 10/11 Enterprise E3 license from the list,
    
    Select + Assign licenses from the menu,

    <img width="781" height="474" alt="image" src="https://github.com/user-attachments/assets/afda0eca-723a-46ff-b8b9-9c208ee0668f" />

    After adding the User, select Assign licenses,

    <img width="779" height="427" alt="image" src="https://github.com/user-attachments/assets/de916802-eab2-4a00-959e-b7fb7a7e8495" />

        Licenses assigned successfully
    
    Return to the browser tab with Microsoft Entra admin center open > In the left navigation menu, under Entra ID, select Users, and then select All users > Select User > Select Licenses

    <img width="759" height="350" alt="image" src="https://github.com/user-attachments/assets/91059b95-76be-4df4-828e-936ef398c218" />


## Part 2: Working with tenant properties

### Create a custom subdomains
  > Using the Microsoft 365 admin center

- In the left navigation, select Settings > Domain  > select + Add domain

  <img width="790" height="476" alt="image" src="https://github.com/user-attachments/assets/10d2817b-73d4-4d3d-93f1-5fd1451677d4" />
  
- Create a custom subdomain, The format will look similar to this:

      Sales.TenantName.onmicrosoft.com
  
- Select Use this domain button at the bottom of the screen

### Changing the tenant display name, reviewing other values associated with the tenant
  - Set the tenant name, technical contact

    In Microsoft ID Entra menu > select Overview + then select Properties.

  - Change the Tenant Properties for the Name and Technical contact (Global admin account) in the dialog and Review the Country or region and other values associated with your tenant

    <img width="781" height="359" alt="image" src="https://github.com/user-attachments/assets/a48d5e2e-e5c3-4aac-8efc-345093caa9f8" />

  - Tenant ID is located: In Microsoft ID Entra menu > select Overview

    <img width="576" height="236" alt="image" src="https://github.com/user-attachments/assets/f8a5a2f6-106c-4fa2-a856-d18f79484b8e" />

  - Setting privacy information
    
    The image below shows where to Add privacy info for employees
    
    <img width="728" height="176" alt="image" src="https://github.com/user-attachments/assets/48fc1393-2ae5-4479-ab5a-9ba3b95cf791" />
    
    > This person is also who Microsoft contacts if there's a data breach. If there's no person listed here, Microsoft contacts global administrators.

  - Select Save

## Part 3: Assigning licenses using group membership
  ### Creating a security group and adding a user in Microsoft Entra ID
  
  - In the left navigation, under Entra ID, select Groups > then select All groups > New group

    <img width="776" height="391" alt="image" src="https://github.com/user-attachments/assets/9b5dd4d2-fae0-4116-9b6b-f36e16099dcf" />
    
  - Enter the parameters and Assign the administrator account as the group owner
    
        Group type:	Security
        Group name:	"<Name of the Group>"
        Membership type:	Assigned
  - Click on Members to add a user
  - Then click create

  ### Add an Office license to The group

  > Add and remove licenses via the Microsoft 365 admin center, This is a relatively new change.

  - In the left navigation menu, select Billing > select Licenses > Select Office 365 E3 license + Assign licenses

  - Search for the group and select it from the list

    <img width="781" height="438" alt="image" src="https://github.com/user-attachments/assets/f5723a9c-0e5d-4d68-aebe-1cc7fbd437fd" />

  - Select Assign licenses

  ### Create a Microsoft 365 group in Microsoft Entra ID

  - In the left navigation, under Entra ID, select Groups > then select All groups > New group

    <img width="786" height="357" alt="image" src="https://github.com/user-attachments/assets/341f0184-5cc8-471c-92eb-997f8243b31e" />

  - Enter the parameters and Assign the administrator account as the group owner

        Group type:	Microsoft 365
        Group name:	"<Name of the Group>"
        Membership type:	Assigned
  - Assign the administrator account as the group owner
  - Click on Members to add a user
  - Then click create

### Creating a dynamic group with all users as members
  - In the left navigation, under Entra ID, select Groups > then select All groups > New group

    <img width="789" height="390" alt="image" src="https://github.com/user-attachments/assets/b84cb756-744c-4ba0-a230-ba9229e2f8a7" />

  - Enter the parameters and Assign the administrator account as the group owner

        Group type:	Security
        Group name:	"<Name of the Group>"
        Membership type:	Dynamic User
  - Under Dynamic user members, select Add dynamic query + Edit Rule syntax

    <img width="767" height="342" alt="image" src="https://github.com/user-attachments/assets/22273e0a-7c41-4608-9184-cb412271a2bc" />

  - Select Save + Create

        The new dynamic group will now include B2B guest users as well as member users.
    
  - Verify the members have been added

    In the left navigation, under Entra ID, select Groups > then select All groups + search the group name > Select on Members in the Manage menu
