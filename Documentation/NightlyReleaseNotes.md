# Beta 3 Nightly (Last updated 2022-07-08)

## Generally
- Moved the Documentation folder to separate repo called Franky-Webpage so I don't need to update the main branch every time I need to change documentation for the webpage
- Renamed Installation Scripts folder to Installation_Scripts
- Renamed Install.ps1 to Host_Install_Script.ps1 as we are going to create more scripts

## Environment
- I have migrated it to work with PowerShell Universal 3.1.0
- Updated PowerShell to 7.2.5
- Updated ImportExcel to 7.6.0
- Updated the code to work with PowerShell 7 as Franky now goes native PowerShell 7.

## Configuration files
- Added missing configuration .ps1 files under .universal folder
- Formatted the .ps1 files after PSU 3.x standard
- Dashboard.ps1 has changed it so it don't re-write the hole $pages and instead following standard
- Moved ActivateLoadBalancing bool from dashboard to variables.ps1

## Bug fixes
- Fixed the error messages that did pop-up if you tried to download the log file when the log was empty

## New functions
Nothing new yet!

## Updates
## All over
- Updated the GUI with icons on some places to make the GUI look better to attract more people to use it.
- Cleaned up the code
- Changed date to YYYY-MM-DD HH:MM
- For data tables I have set pagination location to the top

## Install.ps1
- Checks if the right PowerShell version are installed, if it's not it will download it and prompt to install it
- Added error handling
- Verify so the Franky admin user is existing in the domain
- You can now choose to update or install with the script.
- No need to enter DNSroot manually anymore, collects it automatically
- Showing the SID for Franky.Access group
- Showing the correct LDAP:// path to add to roles.ps1 and Authentication.ps1
- Checks if ActiveDirectory module are installed, if it's not the script will exit as it's needed for the script.
- Checks so the Franky admin user are existing in the AD
- Checks so the OU Path for groups existing
- Downloading latest release of Franky and unzipping it
- Downloading latest supported version of PowerShell Universal
- Integrate InstallEventLog.ps1 to install.ps1 script
- In the end showing a Guide with what value that you need to change in other files.
- For install option it now copy the downloaded latest version of Franky to PSU folder

## Dashboard/pages
## User
- Now you can write the group name, computer name etc. and you will get autosuggestion on computers or groups that exists in your AD in a dropdown list.
- Replaced some text with icons instead to make the GUI to look better
- Added delete button in front of the groups that the user is a member of in the table
- When adding user to a new group it will verify if the user already are a member or not.

### Computer
- Replaced some text with icons instead to make the GUI to look better
- Now you can write the group name, computer name etc. and you will get autosuggestion on computers or groups that exists in your AD in a dropdown list.
- Did rebuild the last logged in user function to speed things up.
- Rebuild so uptime is not showing days if the counter are 0
- Added delete button in front of the groups that the computer is a member of in the table.
- When adding computer to a new group it will verify if the computer already are a member or not.

### Group
- Now you can write the group name, computer name etc. and you will get autosuggestion on computers or groups that exists in your AD in a dropdown list.
- Replaced some text with icons instead to make the GUI to look better
- Added delete button in front och the group members in the table.

## Functions
### Show process on COMPUTERNAME
- Converted it to CIM commands to speed things up!
- Toast message over the action button are showing what process it's stopping
- Added so you can see CommandLine
- Added commandLine and user to include when your searching in the table

### Show network adapters on COMPUTERNAME
- Converted it to CIM commands to speed things up!
- Added so the network adapter name are showing in toast message over the action buttons

### Restart Computer
- Added right order when the command are executed
- Added error message

### Logout current user from COMPUTERNAME
- Has added so it show what user that are logged in on the computer.
- Added error message

### Delete user profile from COMPUTERNAME
- Has been converted to CIM to speed things up!
- Added Not used for to show how many days the profile has not been used for.

### Delete Google Chrome settings
- Has been updated with CIM to speed things up!

### Delete Microsoft Edge settings
- Has been updated with CIM to speed things up!