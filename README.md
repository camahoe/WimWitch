This is an update I made to WimWitchFK as the original developer has apparently abandoned the project.

I am not good at coding/scriping and have never used github before, but I have modified the existing scripts to work with Windows 11 24H2. I have not fully tested all functions, but the following does work:
- Recognize a 24H2 wim file properly
- Download and apply 24H2 updates via OSDSUS/OSDUpdate
- 24H2-specific app removal

Note: New Outlook and Dev Home are not removable via this method.

To remove New Outlook:
- Run the Remove_Outlook_Devhome.reg file on your image or (preferred) inject it into your wim via WimWitch (this will remove Dev Home completely, but not Outlook)
- Run the following commands when logged into your image (unsure if both need to be run, but I'd rather be safe than sorry):

```
Get-AppxProvisionedPackage -Online | ? DisplayName -like '*OutlookForWindows*' | Remove-AppxProvisionedPackage -Online
```
and

```
Get-AppxPackage -AllUsers | Where-Object {$_.Name -Like '*OutlookForWindows*'} | Remove-AppxPackage -AllUsers
```

Instructions:
1. Install the WimWitchFK module via PowerShell
2. Copy the WIMWitchFK.ps1 script to C:\Program Files\WindowsPowerShell\Modules\WIMWitchFK\4.0.1\Public
3. Copy the WWFunctions.ps1 script to C:\Program Files\WindowsPowerShell\Modules\WIMWitchFK\4.0.1\Private
4. Copy the appxWin11_24H2.txt file to C:\Program Files\WindowsPowerShell\Modules\WIMWitchFK\4.0.1\Private\Assets


![image](https://github.com/user-attachments/assets/4020950a-e8d6-47ab-a2d8-541db508b2e3)
![image](https://github.com/user-attachments/assets/d97a2981-414d-4262-b61a-5935bc58420b)
![image](https://github.com/user-attachments/assets/a05b2578-a12e-4494-b165-8ea6ecd2c37c)
