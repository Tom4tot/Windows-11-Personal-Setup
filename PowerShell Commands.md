## Introduction
- All apps listed are "provisioned apps", i.e. preinstalled user apps. Unlike "system apps", they can be uninstalled without any risk. They can also be reinstalled from Windows Store, since they are UWP apps.
  - [About provisioned apps](https://learn.microsoft.com/en-us/windows/application-management/provisioned-apps-windows-client-os)
  - [About system apps](https://learn.microsoft.com/en-us/windows/application-management/system-apps-windows-client-os)
  - [Overview of apps on Windows client devices](https://learn.microsoft.com/en-us/windows/application-management/overview-windows-apps)
 - The purpose of these commands is to make the processs way faster than manually uninstalling apps from the start menu or from the "add or remove programs" setting page. It will also be applied to all users as long as you keep the two `-AllUsers` argument.
 - You can simply copy and paste all the lines mentioned below in one go, it will work perfectly. Of course, you're encouraged to edit the list to your liking.


## Basic commands
- List of installed apps: `Get-AppxProvisionedPackage -Online | Format-Table DisplayName, PackageName`
- List of all system apps: `Get-AppxPackage -PackageTypeFilter Main | ? { $_.SignatureKind -eq "System" } | Sort Name | Format-Table Name, InstallLocation` or `Get-AppxPackage -AllUsers -PackageTypeFilter Bundle | Select-Object Name, PackageFullName`
- Uninstall command: `Get-AppxPackage -AllUsers PACKAGENAME | Remove-AppxPackage -AllUsers`
    - e.g. `Get-AppxPackage -AllUsers Clipchamp.Clipchamp | Remove-AppxPackage -AllUsers`
## Personal user apps
- W11 24H2 Pro/Education: 
    - Clipchamp.Clipchamp
    - Microsoft.549981C3F5F10 *(Cortana)*
    - Microsoft.BingNews
    - Microsoft.BingSearch
    - Microsoft.BingWeather
    - Microsoft.GamingApp
    - Microsoft.GetHelp
    - Microsoft.Getstarted *(can't be easily removed)*
    - Microsoft.MicrosoftOfficeHub
    - Microsoft.MicrosoftSolitaireCollection
    - Microsoft.MicrosoftStickyNotes
    - Microsoft.People
    - Microsoft.PowerAutomateDesktop
    - Microsoft.ScreenSketch
    - Microsoft.Todos
    - Microsoft.WindowsAlarms
    - microsoft.windowscommunicationsapps
    - Microsoft.WindowsFeedbackHub
    - Microsoft.WindowsMaps
    - Microsoft.WindowsSoundRecorder
    - Microsoft.Xbox.TCUI
    - Microsoft.XboxGameOverlay
    - Microsoft.XboxGamingOverlay
    - Microsoft.XboxIdentityProvider
    - Microsoft.XboxSpeechToTextOverlay
    - Microsoft.ZuneMusic
    - Microsoft.ZuneVideo
    - MicrosoftCorporationII.QuickAssist
    - MSTeams

**PowerShell Commmand to delete them all:**  
Get-AppxPackage -AllUsers Clipchamp.Clipchamp | Remove-AppxPackage -AllUsers  
Get-AppxPackage -AllUsers Microsoft.549981C3F5F10 | Remove-AppxPackage -AllUsers  
Get-AppxPackage -AllUsers Microsoft.BingNews | Remove-AppxPackage -AllUsers  
Get-AppxPackage -AllUsers Microsoft.BingSearch | Remove-AppxPackage -AllUsers  
Get-AppxPackage -AllUsers Microsoft.BingWeather | Remove-AppxPackage -AllUsers  
Get-AppxPackage -AllUsers Microsoft.GamingApp | Remove-AppxPackage -AllUsers  
Get-AppxPackage -AllUsers Microsoft.GetHelp | Remove-AppxPackage -AllUsers  
Get-AppxPackage -AllUsers Microsoft.Getstarted | Remove-AppxPackage -AllUsers  
Get-AppxPackage -AllUsers Microsoft.MicrosoftOfficeHub | Remove-AppxPackage -AllUsers  
Get-AppxPackage -AllUsers Microsoft.MicrosoftSolitaireCollection | Remove-AppxPackage -AllUsers  
Get-AppxPackage -AllUsers Microsoft.MicrosoftStickyNotes | Remove-AppxPackage -AllUsers  
Get-AppxPackage -AllUsers Microsoft.People | Remove-AppxPackage -AllUsers  
Get-AppxPackage -AllUsers Microsoft.PowerAutomateDesktop | Remove-AppxPackage -AllUsers  
Get-AppxPackage -AllUsers Microsoft.ScreenSketch | Remove-AppxPackage -AllUsers  
Get-AppxPackage -AllUsers Microsoft.Todos | Remove-AppxPackage -AllUsers  
Get-AppxPackage -AllUsers Microsoft.WindowsAlarms | Remove-AppxPackage -AllUsers  
Get-AppxPackage -AllUsers microsoft.windowscommunicationsapps | Remove-AppxPackage -AllUsers  
Get-AppxPackage -AllUsers microsoft.windowscommunicationsapp | Remove-AppxPackage -AllUsers  
Get-AppxPackage -AllUsers Microsoft.WindowsFeedbackHub | Remove-AppxPackage -AllUsers  
Get-AppxPackage -AllUsers Microsoft.WindowsMaps | Remove-AppxPackage -AllUsers  
Get-AppxPackage -AllUsers Microsoft.WindowsSoundRecorder | Remove-AppxPackage -AllUsers  
Get-AppxPackage -AllUsers Microsoft.Xbox.TCUI | Remove-AppxPackage -AllUsers  
Get-AppxPackage -AllUsers Microsoft.XboxGameOverlay | Remove-AppxPackage -AllUsers  
Get-AppxPackage -AllUsers Microsoft.XboxGamingOverlay | Remove-AppxPackage -AllUsers  
Get-AppxPackage -AllUsers Microsoft.XboxIdentityProvider | Remove-AppxPackage -AllUsers  
Get-AppxPackage -AllUsers Microsoft.XboxSpeechToTextOverlay | Remove-AppxPackage -AllUsers  
Get-AppxPackage -AllUsers Microsoft.YourPhone  | Remove-AppxPackage -AllUsers  
Get-AppxPackage -AllUsers Microsoft.ZuneMusic | Remove-AppxPackage -AllUsers  
Get-AppxPackage -AllUsers Microsoft.ZuneVideo | Remove-AppxPackage -AllUsers  
Get-AppxPackage -AllUsers MicrosoftCorporationII.QuickAssist  | Remove-AppxPackage -AllUsers  
Get-AppxPackage -AllUsers MSTeams | Remove-AppxPackage -AllUsers  

## System apps (that are safe to uninstall)
 - [System apps](https://learn.microsoft.com/en-us/windows/application-management/system-apps-windows-client-os)
    - Microsoft.Windows.Cortana (command: `Get-AppxPackage -AllUsers Microsoft.Windows.Cortana | Remove-AppxPackage`)
    - Microsoft.Windows.DevHome (command: `Get-AppxPackage -AllUsers Microsoft.Windows.DevHome | Remove-AppxPackage`)
    - Microsoft.Windows.DevHomeGitHubExtension (command: `Get-AppxPackage -AllUsers Microsoft.Windows.DevHomeGitHubExtension | Remove-AppxPackage`)
