# Windows 11 Personal Setup - privacy tweaks with GPEDIT

### Introduction and general information
Made for: Windows 11 22H2  
Last update: 2022-10-20  

This covers all  the steps I personally go though when performing a clean install of Windows 11. My aims are the following:
- As much automation as possible (portable programs, quick import of settings)
- A clean UI/UX (I disable/uninstall most of the bloat that comes with Windows)
- As much privacy as possible (see my Group Policy edits)
- Prioritizing native software (to break as little things as possible) or FOSS


### Installation
- Download the official iso file from [Microsoft](https://www.microsoft.com/software-download/windows11)
- Create bootable USB with [Rufus](https://rufus.ie/en/), leave everything as default (GPT, UEFI, NTFS), and customize the *Windows User Experience*: tick everything
  - Benefits: faster than Microsoft's tool, makes the use of a local account easier, skips privacy questions (all will be off)
- Naviagate to /sources in and add the ei.cfg attached to this repo.
  - Benefits: it will bypass your current Windows key and allow you to choose Windows Pro instead of Windows Home.
- Reboot and install Windows. Make sure to delete all your partitions (except the data one, if you have one) and to choose the professional edition.

### Applications that I use / install (FOSS / *proprietary*) (alphabetic order)
#### Portable applications
- [Platform tools - ADB/Fastboot](https://developer.android.com/studio/releases/platform-tools) - mandatory to tinker with my Android phones
- [Audacity](https://github.com/audacity/audacity/releases/tag/Audacity-3.0.2) - Tool to analyse/edit audio files (last update that doesn't include telemetry)
- [*Everything*](https://www.voidtools.com/) - Locate files and folders by name instantly
- [*Foobar2000*](https://www.foobar2000.org/download) - My favorite music player by far
- [HandBrake](https://handbrake.fr/) - Best video converter
- [JPEGView](https://github.com/sylikc/jpegview) - extremely fast and lightweight image viewer (fork)
- [KeePassXC](https://keepassxc.org/download/#windows) - Cross-Platform Password Manager
- [LameXP](https://lamexp.sourceforge.net/page_3.php) - Multi-format audio file converter
- [LanXchange](https://github.com/tfg13/LanXchange) - Configuration-free, cross-platform file transfers for your local network 
- [*MP3TAG*](https://www.mp3tag.de/en/download.html) - One of my favorite tag editor for music
- [MPC-HC](https://github.com/clsid2/mpc-hc) - One of my favorite video player (fork)
- [MPV](https://sourceforge.net/projects/mpv-player-windows/files/64bit-v3/) - My favorite video player
- [Notepad++](https://notepad-plus-plus.org/downloads/) - My favorite text editor
- [qBittorrent](https://www.qbittorrent.org/download.php) - Best torrent client
- [ShareX](https://getsharex.com/downloads/) - Best screen capture tools, many other features
- [simplewall](https://github.com/henrypp/simplewall/) - great firewall
- [Spek](https://github.com/MikeWang000000/spek-X/) - Acoustic spectrum analyser (fork)
- [SumatraPDF](https://www.sumatrapdfreader.org/download-free-pdf-viewer) - My favorite PDF viewer
- [*TagScanner*](https://www.xdlab.ru/en/) - Another one of my favorite tag editor for music
- [WinCDEmu](https://github.com/sysprogs/WinCDEmu) - CD/DVD/BD emulator
- [yt-dlp](https://github.com/yt-dlp/yt-dlp) - Easily download video/audio files from YouTube (fork)

#### Portable tools
- [BleachBit](https://www.bleachbit.org/download/windows) - Disk space cleaner, privacy manager, and computer system optimizer
- [*HWiNFO*](https://www.hwinfo.com/download/) - System Information
- [Driver Store Explorer [RAPR]](https://github.com/lostindark/DriverStoreExplorer) - Manage drivers

#### Installed applications
- [7-zip](https://www.7-zip.org/download.html) - best file archiver
- [Battery Percentage Icon](https://github.com/soleon/Percentage) - See your battery percentage in the system tray (Windows Store)
- [EarTrumpet](https://github.com/File-New-Project/EarTrumpet) - Volume Control for Windows (Windows Store) 
- [ExplorerPatcher](https://github.com/valinet/ExplorerPatcher) - Enhance the working environment on Windows
- [Firefox](https://www.mozilla.org/fr/firefox/all/#product-desktop-release) - Main browser
  - Add-ons: 
    - [uBlock Origin](https://addons.mozilla.org/en-US/firefox/addon/ublock-origin/)
    - [Bypass Paywalls Clean](https://addons.mozilla.org/en-US/firefox/addon/bypass-paywalls-clean/)
    - [SponsorBlock](https://addons.mozilla.org/en-US/firefox/addon/sponsorblock/)
    - [Firefox Multi-Account Containers](https://addons.mozilla.org/en-US/firefox/addon/multi-account-containers/)
    - A working twitch adblocker, see [TwitchAdSolutions](https://github.com/pixeltris/TwitchAdSolutions)
- [*f.lux*](https://justgetflux.com/) - My favorite nightlight software on Windows
- [*Microsoft Office*](https://www.heidoc.net/joomla/technology-science/microsoft/16-office-2021-direct-download-links) - Office suite (direct link)
- [NextCloud](https://nextcloud.com/install/) - Cloud Client
- [PowerToys](https://github.com/microsoft/PowerToys) - Useful system utilities
- [*Soulseek*](https://www.slsknet.org/news/node/1) - To share and download music files that I legally own
- [Sublte](https://github.com/tvdburgt/subtle) - Subtitles downloader
- [*TeamViewer*](https://www.teamviewer.com) - When I need to support a relative with IT stuff
- [Twinkle Tray](https://github.com/xanderfrangos/twinkle-tray) - Easily manage the brightness of your monitors in Windows from the system tray 

### Settings & tweaks - Group Policy Editor
#### Context
- Sources: [1](https://4sysops.com/archives/windows-10-privacy-all-group-policy-settings/), [2](https://www.autoitconsulting.com/files/autoit-win10-telemetry-gpo/W-Win10-TelemetryEnhancedLockdown.htm), [3](https://www.autoitconsulting.com/files/autoit-win10-telemetry-gpo/W-Win10-TelemetryBasicLockdown.htm)  
- Abbreviations:  
	- (D) = disabled  
	- (E) = enabled  
	- (E+C) = enabled, configuration is necessary
- Benefits of using GPE instead of third-party programs or regedit
	- Easier to setup after a clean install (no need to tick all boxes one by one).
	- All GP edits are up to date, so there's no risk to mess with regedit by adding unnecessary keys.
	- Changes are easier to track than on regedit.
	- No third-party software = more reliable, more secure, more private.
	- GPE includes meaningful descriptions, wheras regedit doesn't offer any. Third-party softwares' are usually not very accurate or up to date.

#### How to Backup / Restore group policies
- Backup: copy all files/folders from `C:\Windows\System32\GroupPolicy`
- Restore/import: 
	- Paste these files to your new installation in the same folder
	- You can also directly import [my config](https://github.com/Tom4tot/Windows-11-Personal-Setup/blob/main/GroupPolicy.7z) that is attached to this repository
	- If you want to update policies without restarting, run this command in CMD (it's **not** necessary to run it as administrator): `gpupdate /force`

#### Privacy edits  
- `Computer Configuration > Administrative Templates > Control Panel > Regional and Language Options > Handwriting personalization` → Turn off automatic learning (E)  
- `Computer Configuration > Administrative Templates > System > Internet Communication Management > Internet Communication settings`
	- Turn off Windows Customer Experience Improvement Program (E) 
	- Turn off Windows Error Reporting (E) 
	- Turn off the Windows Messenger Customer Experience Improvement Program (E)  
- `Computer Configuration > Administrative Templates > System > OS Policies`
	- Allow Clipboard History (D) 
	- Enables Activity Feed (D) 
	- Allow publising of User Activities (D) 
	- Allow upload of User Activities (D)
- `Computer Configuration > Administrative Templates > System > User Profiles` → Turn off the advertising ID (E)
- `Computer Configuration > Administrative Templates > Windows Components > Application Compatibility`
	- Turn off Application Telemetry (E) 
	- Turn off Inventory Collector (E) 
	- Turn off Steps Recorder (E)
- `Computer Configuration > Administrative Templates > Windows Components > Cloud Content​`
	- Do not show Windows tips (E) 
	- Turn off Microsoft consumer experiences (E)
- `Computer Configuration > Administrative Templates > Windows Components > Data Collection and Preview Builds`
	- Allow Desktop Analytics Processing (D) 
	- Allow device name to be sent in Windows diagnostic data (D) 
	- Allow Diagnostic data (E+C) + Configure Authenticated Proxy usage for the Connected User Experience and Telemetry service (E+C) 
	- Disable OneSettings Downloads (E) 
	- Enable OneSettings Auditing (D)
	- Limit Diagnostic Log Collection (E) 
	- Limit Dump Collection (E) 
	- Limit optional diagnostic data for Desktop Analytics (D)
	- Do not show feedback notifications (E) 
	- Configure collection of browsing data for Desktop Analytics (E+C) 
- `Computer Configuration > Administrative Templates > Windows Components > File Explorer` → Configure Windows Defender SmartScreen (D)
- `Computer Configuration > Administrative Templates > Windows Components > Find My Device` → Turn On/Off Find My Device (D)
- `Computer Configuration > Administrative Templates > Windows Components > Location and Sensors`
	- Turn off location (E) 
	- Turn off location scripting (E)
- `Computer Configuration > Administrative Templates > Windows Components > Maps`
	- Turn off unsolicited network traffic on the Offline Maps settings page (E)
	- Turn off Automatic Download and Update of Map Data (E) 
- `Computer Configuration > Administrative Templates > Windows Components > OneDrive`
	- Prevent the usage of OneDrive for file storage (E) 
	- Save documents to OneDrive by default (D)
- `Computer Configuration > Administrative Templates > Windows Components > Search` 
	- Allow Cloud Search (D)
	- Allow Cortana (D)
	- Do not allow web search (E) 
	- Don't search the web or display web results in Search (E) 
	- Set what information is shared in Search (E+C)
- `Computer Configuration > Administrative Templates > Windows Components > Speach` → Allow automatic Update of Speech Data (D)
- `Computer Configuration > Administrative Templates > Windows Components > Sync` your settings → Do not sync (E)
- `Computer Configuration > Administrative Templates > Windows Components > Text Input` → Improve inking and typing recognition (D)
- `Computer Configuration > Administrative Templates > Windows Components > Windows Error Reporting` → Disable Windows Error Reporting (E)

- `User Configuration > Administrative Templates > Start Menu and Taskbar`
	- Remove the People Bar from the taskbar (E)
	- Turn off feature advertisement balloon notifications (E)
- `User Configuration > Administrative Templates > System > lnternet Communication Management > lnternet Communication settings`
	- Turn off Help Ratings (E)
	- Turn off Help Experience Improvement Program (E)
	- Turn off Windows Online (E)
	- Turn off the Windows Messenger Customer Experience Improvement Program (E)
- `User Configuration > Administrative Templates > Windows Components > Cloud Content`​
	- Turn Off Spotlight collection on Desktop (E) 
	- Do not use diagnostic data for tailored experiences (E) 
	- Do not suggest third-party content in Windows spotlight (E) 
	- Turn off all Windows spotlight features (E) 
	- Turn off Windows Spotlight on Action Center (E) 
	- Turn off Windows Spotlight on Settings (E) 
	- Turn off the Windows Welcome Experience (E)
- `User Configuration > Administrative Templates > Windows Components > Edge UI`
	- Disable help tips (E) 
	- Turn off tracking of app usage (E)
- `User Configuration > Administrative Templates > Windows Components > File Explorer` → Turn off display of recent search entries in the File Explorer search box (E)
- `Computer Configuration > Administrative Templates > Windows Components > Text Input` → Improve inking and typing recognition (D)
- `User Configuration > Administrative Templates > Windows Components > Search` → Turn off storage and display of search history (E)

#### UI/UX edits
- Disable chat: `Computer Configuration > Administrative Templates > Windows Components > Chat` → Configures the Chat icon on the taskbar (E+C)
- Disable Widgets: `Computer Configuration > Administrative Templates > Windows Components > Widgets` → Allow widgets (D)
- Disable Connected Modern Standby: `Computer Configuration > Administrative Templates > System > Power Management > Sleep Settings` → Allow network connectivity during connected-standby (on battery) (D)
- Microsoft Defender
	- `Computer Configuration > Administrative Templates > Windows Components > Microsoft Defender Antivirus > Real-time protection` → Turn off real-time protection (E)
		- `Computer Configuration > Administrative Templates > Windows Components > Microsoft Defender Antivirus` → Configure detection for potentially unwanted applications (D)
	- `Computer Configuration > Administrative Templates > Windows Components > Windows Defender SmartScreen > Enhanced Phising Protection` → Service Enabled (D)
	- `Computer Configuration > Administrative Templates > Windows Components > Windows Defender SmartScreen > Explorer` → Configure Windows Defender SmartScreen(D)
- Microsoft Edge: 
	- Basic tweaks: `Computer Configuration > Administrative Templates > Windows Components > Microsoft Edge`
		- Allow extended telemetry for the Books tab (D)
		- Allow web content on New Tab page (D)
		- Allow Microsoft Edge to pre-launch at Windows Startup, when the system is idle, and each time Microsoft Edge is closed (E+C)
		- ALlow Microsoft Edge to start and load the start and New Tab pag at Windows startup and each time Microsoft Edge is closed (E+C)
	- Advanced tweaks: ([official documentation](https://learn.microsoft.com/en-us/deployedge/configure-microsoft-edge))
		- Policy import:
			- Download [templates](https://www.microsoft.com/en-us/edge/business/download?form=MA13FJ)
			- Extract the .cab
			- Import `MicrosoftEdgePolicyTemplates\windows\admx\msedge.admx"` to `C:\Windows\PolicyDefinitions`
			- Import `MicrosoftEdgePolicyTemplates\msedge.adml` to `C:\Windows\PolicyDefinitions\en-US`
		- `Computer Configuration > Administrative Templates > Microsoft Edge > SmartScreen settings`
			- Configure Microsoft Defender SmartScreen (D)
			- Configure Microsoft Defender Smartscreen to block potentially unwanted apps (D)
		- `Computer Configuration > Administrative Templates > Microsoft Edge - Default Settings (users can override)`
			- Enable AUtoFill for adresses (D)
			- Enable AutoFill for adresses (D)
			- Configure Automatic HTTPS (E+C)
			- Continue running background apps after Microsoft Edge closes (D)
			- Allow download restrictions (E+C)
			- Shopping in Microsoft Edge Enabled (D)
			- Enable favorites bar (D)
			- Show the Reload in Internet Explorer mode button in the toolbar (D)
			- Enable Widnows to search local Microsoft Edge browsing data (D)
			- Allow suggestions from local providers (E)
			- Allow single sign-on for Microsoft personal sites using this profile (D)
			- Manage Search Engines (E+C) (`[{"allow_search_engine_discovery":true},{"is_default":true,"search_url":"https://www.google.com/search?q={searchTerms}","name":"Google","keyword":"google.com"}]`)
			- Enable Microsoft Edge mini menu (D)
			- Enable resolution of navigation errors using a web service (D)
			- Enable search suggestions (D)
			- Show Microsoft Rewards experiences (D)
			- Disable syncrhonization of data using Microsoft sync services (E)
			- Enable travel assistance (D)
			- Visual search enabled (D)			
		- `Computer Configuration > Administrative Templates > Microsoft Edge - Default Settings (users can override) > Default search provider` → (E+C) (Adress bar)
		- `Computer Configuration > Administrative Templates > Microsoft Edge - Default Settings (users can override) > Startup, home page and new tabe page`
			- Set the new tab page as the home page (E)
			- Action to take on startup (E+C)
			- Show Home button on toolbar (E)
- Microsoft Office: 
	- Policy import:
		- Download [templates](https://www.microsoft.com/en-us/download/details.aspx)
		- Execute the .exe and import the policies you want, e.g.
		- Import `MicrosoftEdgePolicyTemplates\windows\admx\msedge.admx"` to `C:\Windows\PolicyDefinitions`
		- Import `MicrosoftEdgePolicyTemplates\msedge.adml` to `C:\Windows\PolicyDefinitions\en-US`
	- Policies
		- `Computer Configuration > Administrative Templates > Microsoft Office 2016 (Machine) > Global Options` → Default Office theme (E+C)
		- `Computer Configuration > Administrative Templates > Microsoft Office 2016 (Machine) > Updates` → Don't install Microsoft Teams with new installations or updates of Office (E)
		
		- `User Configuration > Administrative Templates > Microsoft Office 2016 > AutoSave`
		- `User Configuration > Administrative Templates > Microsoft Office 2016 > Improved Error Reporting`
		- `User Configuration > Administrative Templates > Microsoft Office 2016 > Miscellaneous` 
			- Show LinkedIn Features in Office applications (D)
			- Show OneDrive Sign In (D)
			- Show Screen Tips (E+C)
		- `User Configuration > Administrative Templates > Microsoft Office 2016 > Privacy > Trust Center`
			- Allow the use of connected experiences in Office (D)
			- Allow Microsoft to follow up on feedback submitted by users (D)
			- Enable Customer Experience Improvement Program (D)
			- Allow users to include log files and content samples when they submit feedback to Microsoft (D)
			- Allow the use of connected experiences in Office that analyze content (D)
			- Allow the use of connected experiences in Office that download online content
			- Allow the use of additional optional connected experiences in Office
			- Allow users to include screenshots and attachments when they submit feedback to Microsoft
			- Allow users to submit feedback to Microsoft
			- Allow users to receive and respond to in-product surveys from Microsoft
			- Send personal information (D)
			- Automatically receive small updates to improve reliability (D)
			Disable Opt-in Wizard on first run (D)
			Configure the level of client software diagnostic data sent by Office to Microsoft (E+C)
		- `User Configuration > Administrative Templates > Microsoft Office 2016 > Telemetry Dashboard`
			- Turn on telemetry data collection (D)
			- Turn on data uploading for Office Telemetry Agent (D)
			- Turn on privacy settings in Office Telemetry Agent (E)
			- Office applications to exclude from Office Telemetry Agent reporting (E+C)
			- Office solutions to exclude from Office Telemetry Agent reporting (E+C)
		- `User Configuration > Administrative Templates > Microsoft Office 2016 > Tools I Options I General I Web Options...` → Display Developer tab in the Ribbon (E)
		- `User Configuration > Administrative Templates > Microsoft Office 2016 > Tools | Options | Spelling` → Allow accented uppercase in French (E)
		- `User Configuration > Administrative Templates > Microsoft Office 2016 > Tools | Options | Spelling \Proofing Data Collection` → Improve Proofing Tools (D)
		- `User Configuration > Administrative Templates > Microsoft Word 2016 > Advanced > File Locations` → (E+C)
		- `User Configuration > Administrative Templates > Microsoft Word 2016 > Customize Ribbon` → Display Developer tab in the Ribbon (E)
		- `User Configuration > Administrative Templates > Microsoft Word 2016 > Proofing > AutoCorrect`
			- Correct TWO INitial CApitals (E)
			- Correct accidental usage of CAPS LOCK key (E)

### Settings & tweaks - Others
- Uninstall all unnecessary user UWP apps
- Windows Settings
  - System → Power
  - System → Multitasking
  - System → Clipboard
  - Bluetooth & devices → Mouse → Additional mouse settings → pointer options → disable enhance pointer precision
  - Bluetooth & devices → Touchpad
  - Turn on BitLocker
  - Privacy & security → open Windows Security → disable Tamper Protection 
  - Windows Security → import this [task](https://github.com/Tom4tot/Microsoft-Defender-RTP-stop/) in Task Scheduler
- PowerShell commands
  - Remove YourPhone `Get-AppxPackage Microsoft.YourPhone -AllUsers | Remove-AppxPackage`
- Local Security Policy 
  - Ask for password for administrator rights: Local Policies → Security Options → User Account Control: Behavior of the elevation prompt for administrators in Admin Approval mode → Prompt for credentials. 
- services.msc: services to disable
	- Connected User Experiences and Telemetry
	- Microsoft Account Sign-In Assistant
- Disable telemetry in Microsoft Office
