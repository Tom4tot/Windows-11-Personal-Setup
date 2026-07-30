##### 	How to get/import the custom group policy configuration for Microsoft Office:
- [Official documentation](https://learn.microsoft.com/en-us/deployoffice/oct/oct-2016-help-overview)
- How to import the policies:
		- Download [templates](https://www.microsoft.com/en-us/download/details.aspx?id=49030)  
		- Execute the .exe and import the policies you want, e.g.  
		- Import `word16.admx` to `C:\Windows\PolicyDefinitions`  
		- Import `word16.adml` to `C:\Windows\PolicyDefinitions\en-US`

##### How to get/import the custom group policy configuration for Microsoft Edge:
- [Official documentation](https://learn.microsoft.com/en-us/deployedge/configure-microsoft-edge)
- How to import the policies:
	- Download [templates](https://www.microsoft.com/en-us/edge/business/download?form=MA13FJ): "Download Windows 64-bit Policy"  
	- Extract the .cab
	- Extract the .zip
	- Import `MicrosoftEdgePolicyTemplates\windows\admx\msedge.admx"` to `C:\Windows\PolicyDefinitions`
	- Import `MicrosoftEdgePolicyTemplates\windows\admx\en-US\msedge.adml` to `C:\Windows\PolicyDefinitions\en-US`
