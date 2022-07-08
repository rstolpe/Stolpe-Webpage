 # Host Setup
 It's really easy to install Franky as we have provided a installation script for it. Just download the script and run it on the host as admin.  
 It's some settings that you still need to do manually, but we have listed them below and will walk you trough them.  
   
 You can download it trough this link: Coming soon!

## Logging
I have included logging that are stored in Eventlog on the host/s.
Before you activate the logging you need to run the InstallEventLog.ps1 that are located under the folder "Installation Scripts" in this repo so all the sources are created.
As default the LogName is set to Franky but if you want to change that just change the $EventLogName variable in both InstallEventLog.ps1 and in the variables.ps1 file.  
  
When that's done you just need to change [bool]$ActiveEventLog variable from $false to $true in the variables.ps1 file.  
As default it's set to $false

## Load Balancing
It's possible to run this dashboard with multiple hosts and use git for it if you follow the process below.  
It's also working if you have a VIP address and then attach the hosts to the VIP address.  
  
1. In PSU admin on each host create an AppToken. If you set an expiration date on the AppToken remember that date as it will stop working after that date and then the load balancing will also stop working.
    - https://docs.powershelluniversal.com/config/security/app-tokens
2. In the dashboard.ps1 file you should change [bool]$ActivateLoadBalancing to $true
3. Go in to the Component load balancing.psm1 file and change the host1 etc. and also add the AppToken for each host.
4. Change the needed information in variables.ps1 and also in appsettings.json file to your VIP address.  

 # Client Setup