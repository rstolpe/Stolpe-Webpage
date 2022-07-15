If you want to control a computer with PowerShell for example trough the network it's important that you have enabled WinRM services and also allowed WinRM in the Windows Firewall.  
So I'll go trough how to do that now.  
  
## Enabling WinRM with GPO
You can enable WinRM with GPO:s and to make that GPO to take effect you need to have the GPO in the same OU or above where your computer objects are stored.  
(Insert picture)

### First we need to open Group Policy Management and create the GPO
1. From the start menu, open Control Panel.
2. Select Administrative Tools.
3. Select Group Policy Management.
4. From the menu tree, click Domains > (Your domain).
5. Right-click and select Create a GPO in this domain, and Link it here...
6. Name it for example "Enable WinRM"

<img width="514" alt="1" src="https://user-images.githubusercontent.com/76907327/179216173-ca64f053-3565-4662-9561-84b3f6554a98.png">

### Now we need to allow WinRM
1. Right click on "Enable WinRM" and select Edit
2. Navigate to Computer Configuration > Policies > Administrative Templates: Policy definitions > Windows Components > Windows Remote Management (WinRM) > WinRM Service
3. Right click on "Allow remote server management through WinRM" and click on Edit.
4. Now mark it as Enabled and in every filed you should type *
5. Click Apply and then OK

<img width="685" alt="2" src="https://user-images.githubusercontent.com/76907327/179216210-abbb1105-bf47-43d9-b7b2-44c2680fb621.png">

### Now we need to enable the WinRM service
Make sure that you are still editing our GPO "Enable WinRM"  
1. Navigate to Computer Configuration -> Preferences > Control Panel Settings > Services
2. Right click in the service window _(white window to the right)_ and click New -> Service
3. Change Startup to Automatic
4. As Service Name you enter WinRM
5. Change Service action to Start service
6. Click Apply then OK

<img width="401" alt="3" src="https://user-images.githubusercontent.com/76907327/179216245-1969cb3e-0472-4efc-a57f-83c7cbcde38c.png">

### Now it's time to setup the firewall rules
Make sure that you are still editing our GPO "Enable WinRM"  
1. Now we need to enable Windows Firewall: Allow inbound remote administration exception
2. Navigate to Computer Configuration > Policies > Administrative Templates: Policy definitions > Network > Network Connections > Windows Defender Firewall > Domain Profile
3. Right click on Windows Firewall: Allow inbound remote administration exception and click Edit
4. Mark it as Enabled and in every filed you should write *
5. Click Apply and then OK

(Insert picture)

1. Now we are going to add some firewall rules

### Almost done
Now we have done almost everything we just need to make sure that the computers get the new GPO, we can do that in two ways.
1. Restart the computer
2. Open PowerShell or CMD as Administrator and write gpupdate /force and then press enter