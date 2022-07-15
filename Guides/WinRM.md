If you want to control a computer with PowerShell for example trough the network it's important that you have enabled WinRM services and also allowed WinRM in the Windows Firewall.  
So I'll go trough how to do that now.  
  
## Enabling WinRM with GPO
You can enable WinRM with GPO:s and to make that GPO to take effect you need to have it in the same OU or above where your computer objects are stored.

### First we need to open Group Policy Management and create the GPO
1. From the start menu, open Control Panel.
2. Select Administrative Tools.
3. Select Group Policy Management.
4. From the menu tree, click Domains > (Your domain).
5. Right-click and select Create a GPO in this domain, and Link it here...
6. Name it for example "Enable WinRM"

(input picture here later)

### Now we need to allow WinRM
1. Right click on "Enable WinRM" and select Edit
2. Navigate to Computer Configuration > Policies > Administrative Templates: Policy definitions > Windows Components > Windows Remote Management (WinRM) > WinRM Service
3. Right click on "Allow remote server management through WinRM" and click on Edit.
4. Now mark it as Enabled and in every filed you should type *
5. Click Apply and then OK

(input picture here later)

### Now we need to enable the WinRM service
Make sure that you are still editing our GPO "Enable WinRM"  
1. Navigate to Computer Configuration -> Preferences > Control Panel Settings > Services
2. Right click in the service window _(white window to the right)_ and click New -> Service
3. Change Startup to Automatic
4. As Service Name you enter WinRM
5. Change Service action to Start service
6. Click Apply then OK

(Insert picture)

### Now it's time to setup the firewall rules
Make sure that you are still editing our GPO "Enable WinRM"  
