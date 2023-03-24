## Microsoft Edge basic settings
- `Computer Configuration > Administrative Templates > Windows Components > Microsoft Edge`
	- Allow extended telemetry for the Books tab (D)
	- Allow web content on New Tab page (D)
	- Allow Microsoft Edge to pre-launch at Windows Startup, when the system is idle, and each time Microsoft Edge is closed (E+C)
	- ALlow Microsoft Edge to start and load the start and New Tab pag at Windows startup and each time Microsoft Edge is closed (E+C)

## Microsoft Edge advanced group policy config (ADMX/ADML templates)
### How to get/import the custom group policy configuration for Microsft Edge:
- [Official documentation](https://learn.microsoft.com/en-us/deployedge/configure-microsoft-edge))
- How to import the policies:
	- Download [templates](https://www.microsoft.com/en-us/edge/business/download?form=MA13FJ)
	- Extract the .cab
	- Extract the .zip
	- Import `MicrosoftEdgePolicyTemplates\windows\admx\msedge.admx"` to `C:\Windows\PolicyDefinitions`
	- Import `MicrosoftEdgePolicyTemplates\windows\admx\en-US\msedge.adml` to `C:\Windows\PolicyDefinitions\en-US`
### Configuration
![Administrative Templates - Microsoft Edge - all subfolders](https://github.com/Tom4tot/Windows-11-Personal-Setup/blob/main/Group%20Policy%20settings/Administrative%20Templates%20-%20Microsoft%20Edge%20-%20all%20subfolders%20(Custom).png)
