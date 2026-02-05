# Windows 11 Personal Setup
## Installation process | Essential programs | Privacy tweaks with GPEDIT | PowerShell commands to remove Provisioned apps | General tweaks

### 1-Introduction and general information
Applicable to **Windows 11 25H2** (originally made for W11 22H2)
Last update: **2026-05-02**  
Recent changes: Group policies updated, I have modified added policies in W11 24H2 / 25H2; minor QoL updates; repository clean-up

This covers all the steps I personally go though when performing a clean install of Windows 11. My aims are the following:
- As much automation as possible (portable programs, quick import of settings)
- A clean UI/UX (I disable/uninstall most of the bloat that comes with Windows)
- As much privacy as possible (see my Group Policy edits)
- Prioritizing native features (mostly group policies, but also PowerShell) when it comes to customizing Windows, and free and open-source software (FOSS) for features/programs.

Thanks to [Duttyend](https://github.com/duttyend) for the tips and suggestions!

### 2-Installation
- Download the official iso file from [Microsoft](https://www.microsoft.com/software-download/windows11)
- Create bootable USB with [Rufus](https://rufus.ie/en/), leave everything as default (GPT, UEFI, NTFS), and customize the *Windows User Experience* after clicking on `start`. I recommend to tick every box.
  - Benefits: faster than Microsoft's tool, makes the use of a local account easier, skips privacy questions (all will be off)
- Naviagate to /sources in and add the [ei.cfg file](https://github.com/Tom4tot/Windows-11-Personal-Setup/blob/main/Resources/ei.cfg) attached to this repo, so you can bypass your current Windows key and choose the Windows edition you want.
	- In my opinion, Education > Enterprise > Pro > Home. You can find a comparison of all versions [here](https://en.wikipedia.org/wiki/Windows_10_editions#Comparison_chart). Education edition is my favorite as it has all the features from Enterprise but it is available in the multi-edition iso that you can freely download, unlike the enterprise iso that is hard to get. Education and Enterprise editions have a few extra features compared to the Pro edition. The main benefit according to me is that you can completely disable diagnostic data, which is not possible with the Pro edition. Avoid the home edition because it doesn't include the Local Group Policy Editor and it has the least features.
 	- Windows 11 IoT Enterprise LTSC 2024 (or Windows 10 IoT Enterprise LTSC 2021) are also good options if you prefer low maintenance and more legacy Windows programs (it can be relevant if you install it for a relative or for a secondary computer that you don't often use). I however advise in general to install the regular edition of Windows (General Availability Channel), specifically Windows 11 Education, as you're less likely to face incompatibilities (both regarding programs and drivers).
- Reboot and install Windows.
	- Make sure to delete all your partitions (except the data one, if you have one) and to choose the Education/Enterprise/Professional edition.
 	- You can also pick `English (World)` as `the time and currency format` so [most user apps won't be installed](https://www.reddit.com/r/Windows11/comments/15gk07n/english_world_as_time_and_currency_for_debloating/). You can always run `wsreset -i` via CMD (with admin rights) to reset/reinstall Microsoft Store.
  	- Also, don't forget to copy your Wi-Fi drivers on your USB stick (after setting up with Rufus) so you can easily access your network once the Windows installation is complete.

### 3-Applications that I use / install (FOSS / *proprietary*) (alphabetical order)
#### Portable applications
- [ADB/Fastboot - Platform tools](https://developer.android.com/studio/releases/platform-tools) - mandatory to tinker with my Android phones
- [Audacity](https://github.com/audacity/audacity/releases/tag/Audacity-3.0.2) - Tool to analyse/edit audio files (last update that doesn't include telemetry)
- [Calibre](https://calibre-ebook.com/) - Management of my Kindle library
- [chrlauncher](https://github.com/henrypp/chrlauncher/) - Portable Chromium and updater - [macchrome](https://github.com/macchrome/winchrome) and [RobRich999](https://github.com/RobRich999/Chromium_Clang) are both up to date and reliable.
- [Easy Audio Sync](https://github.com/complexlogic/EasyAudioSync) - Synchronization of my main music library with the one for my phone. It automatically mirrors my main folder and transcodes on-the-fly my .flac files to .opus ones. Works great and it's very fast.
- [*Everything*](https://www.voidtools.com/) - Locate files and folders by name instantly
- [*Foobar2000*](https://www.foobar2000.org/download) - My favorite music player by far
- [HandBrake](https://handbrake.fr/) - Favorite video converter
- [JPEGView](https://github.com/sylikc/jpegview) - extremely fast and lightweight image viewer (fork)
- [KeePassXC](https://keepassxc.org/download/#windows) - Cross-Platform Password Manager
- [LameXP](https://lamexp.sourceforge.net/page_3.php) - Multi-format audio file converter
- [LanXchange](https://github.com/tfg13/LanXchange) - Configuration-free, cross-platform file transfers for your local network 
- [*MP3TAG*](https://www.mp3tag.de/en/download.html) - One of my favorite tag editor for music
- [MPC-HC](https://github.com/clsid2/mpc-hc) - One of my favorite video player (fork)
- [MPV](https://sourceforge.net/projects/mpv-player-windows/files/64bit-v3/) - My favorite video player
- [Nicotine+](https://github.com/nicotine-plus/nicotine-plus/) - open source client four Soulseek.
- [Notepad++](https://notepad-plus-plus.org/downloads/) - My favorite text editor
- [OBS](https://obsproject.com) - Best screen recording / broadcasting software
- [*paint.NET*](https://github.com/paintdotnet/release/) - great easy-to-use image editor
- [PDFsam](https://pdfsam.org/en/download-pdfsam-basic/) - nice tool for basic PDF manipulations
- [qBittorrent](https://www.qbittorrent.org/download.php) - Favorite torrent client
- [ShareX](https://getsharex.com/downloads/) - Favorite screen capture tools, many other features
- [simplewall](https://github.com/henrypp/simplewall/) - great firewall
- [Spek](https://github.com/MikeWang000000/spek-X/) - Acoustic spectrum analyser (fork)
- [SumatraPDF](https://www.sumatrapdfreader.org/download-free-pdf-viewer) - My favorite PDF viewer
- [Syncthing](https://syncthing.net/) - Wireless sync of my images, music, etc. in between my computer & Android Phone
- [*TagScanner*](https://www.xdlab.ru/en/) - Another one of my favorite tag editor for music
- [WinCDEmu](https://github.com/sysprogs/WinCDEmu) - CD/DVD/BD emulator
- [yt-dlp](https://github.com/yt-dlp/yt-dlp) - Easily download video/audio files from YouTube (fork)
#### Portable tools
- [BleachBit](https://www.bleachbit.org/download/windows) - Disk space cleaner, privacy manager, and computer system optimizer
- [Caesium Image Compressor](https://github.com/Lymphatus/caesium-image-compressor/) - image compression software, very impressive
- [*HWiNFO*](https://www.hwinfo.com/download/) - System Information
- [Driver Store Explorer [RAPR]](https://github.com/lostindark/DriverStoreExplorer) - Manage drivers
#### Installed applications
##### Automated installation via a package manager
- Package managers (Winget)
    	- see packages [here](https://winstall.app/)
    	- Command to search packages: `winget search XXX` (save the package ID to install programs, it's more accurate and reliable)
     	- Command to install all programs: winget upgrade --all --silent `winget install 7zip.7zip && winget install File-New-Project.EarTrumpet && winget install Mozilla.Firefox && winget install flux.flux && winget install Oracle.JavaRuntimeEnvironment && winget install Nextcloud.NextcloudDesktop&& winget install geeksoftwareGmbH.PDF24Creator && winget install Microsoft.PowerToys && winget install RustDesk.RustDesk && winget install xanderfrangos.twinkletray`
      - Command to update all programs: (you can also download the shortcut I created, [Winget Update.ink](https://github.com/Tom4tot/Windows-11-Personal-Setup/blob/main/Resources/Winget%20Update.lnk)
- [7-zip](https://www.7-zip.org/download.html) - Favorite file archiver
- [EarTrumpet](https://github.com/File-New-Project/EarTrumpet) - Volume Control for Windows (Windows Store) 
- [Firefox](https://www.mozilla.org/fr/firefox/all/#product-desktop-release) - Main browser
  - Add-ons: 
    - [uBlock Origin](https://addons.mozilla.org/en-US/firefox/addon/ublock-origin/)
    - [Bypass Paywalls Clean](https://gitflic.ru/project/magnolia1234/bypass-paywalls-firefox-clean)
    - [SponsorBlock](https://addons.mozilla.org/en-US/firefox/addon/sponsorblock/)
    - [Firefox Multi-Account Containers](https://addons.mozilla.org/en-US/firefox/addon/multi-account-containers/)
    - A working twitch adblocker, see [TwitchAdSolutions](https://github.com/pixeltris/TwitchAdSolutions)
- [*f.lux*](https://justgetflux.com/) - My favorite nightlight software on Windows
- [Java](https://www.java.com/en/) - Needed for some programs
- [NextCloud](https://nextcloud.com/install/) - Cloud Client
- [*PDF24*](https://tools.pdf24.org/fr/creator) - PDF tools
- [PDFsam Basic](https://pdfsam.org/download-pdfsam-basic/) - PDF tools
- [PowerToys](https://github.com/microsoft/PowerToys) - Useful system utilities
- [RustDesk](https://github.com/rustdesk/rustdesk/releases/) - best open source TeamViewer alternative (which has become awful lately by the way)
- [Twinkle Tray](https://github.com/xanderfrangos/twinkle-tray) - Easily manage the brightness of your monitors in Windows from the system tray 
##### Not available on Winget
- [ExplorerPatcher](https://github.com/valinet/ExplorerPatcher) - Enhance the working environment on Windows (available on Winget)
- [FreeFileSync](https://freefilesync.org) - My favorite file synchronization tool
- [*Microsoft Office*](https://massgrave.dev/office_c2r_links) - Office suite (direct link from Microsoft servers)

### 4-Settings & tweaks - Group Policy Editor

#### List of Group Policy changes (screenshots): [Computer Configuration](https://github.com/Tom4tot/Windows-11-Personal-Setup/blob/main/Group%20Policy%20settings/1-Computer%20configuration.png) - [User Configuration](https://github.com/Tom4tot/Windows-11-Personal-Setup/blob/main/Group%20Policy%20settings/2-User%20settings.png)
#### Context
- Sources: [1](https://4sysops.com/archives/windows-10-privacy-all-group-policy-settings/), [2](https://www.autoitconsulting.com/files/autoit-win10-telemetry-gpo/W-Win10-TelemetryEnhancedLockdown.htm), [3](https://www.autoitconsulting.com/files/autoit-win10-telemetry-gpo/W-Win10-TelemetryBasicLockdown.htm)  
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
	- You can also directly import my config that is attached to this repository (WARNING: all my settings are perfectly safe except that I personally disable real-time protection from Windows Security but I can't advise you to do the same: `Computer Configuration > Administrative Templates > Windows Components > Microsoft Defender Antivirus > Real-time protection` → Turn off real-time protection.)
	- If you want to update policies without restarting, run this command in CMD (it's **not** necessary to run it as administrator): `gpupdate /force`
 - Alternatively, you can also use the [LGPO utility](https://www.microsoft.com/en-us/download/details.aspx?id=55319) to backup and restore local group policies.
 - To keep track of new group policies, check this [spreadsheet (25H2)](https://www.microsoft.com/en-us/download/details.aspx?id=108395) and sort the first column.

##### How to get/import the custom group policy configuration for Microsoft Office:
- [Official documentation](https://learn.microsoft.com/en-us/deployoffice/oct/oct-2016-help-overview)
- How to import the policies:
		- Download [templates](https://www.microsoft.com/en-us/download/details.aspx?id=49030)  
		- Execute the .exe and import the policies you want, e.g.  
		- Import `word16.admx` to `C:\Windows\PolicyDefinitions`  
		- Import `word16.adml` to `C:\Windows\PolicyDefinitions\en-US`

##### How to get/import the custom group policy configuration for Microsoft Edge:
- [Official documentation](https://learn.microsoft.com/en-us/deployedge/configure-microsoft-edge))
- How to import the policies:
	- Download [templates](https://www.microsoft.com/en-us/edge/business/download?form=MA13FJ): "Download Windows 64-bit Policy"  
	- Extract the .cab
	- Extract the .zip
	- Import `MicrosoftEdgePolicyTemplates\windows\admx\msedge.admx"` to `C:\Windows\PolicyDefinitions`
	- Import `MicrosoftEdgePolicyTemplates\windows\admx\en-US\msedge.adml` to `C:\Windows\PolicyDefinitions\en-US`

- (oudated) List of entries written down: [Privacy settings](https://github.com/Tom4tot/Windows-11-Personal-Setup/blob/main/Group%20Policy%20settings/Privacy%20settings.md) - [UI/UX settings](https://github.com/Tom4tot/Windows-11-Personal-Setup/blob/main/Group%20Policy%20settings/UI%20UX%20settings.md)


### 5-Settings & tweaks - Others
- [Uninstall all unnecessary preinstalled *provisioned* user apps](https://github.com/Tom4tot/Windows-11-Personal-Setup/blob/main/Resources/PowerShell%20Commands.md)
- Add some essential CLI programs to PATH with CMD (administrator mode) so they are always available when opening CMD or PowerShell:
	- `setx /m PATH ""YourProgramPath";%PATH%"`
	- e.g.: `setx /m PATH ""C:\ffmpeg\bin";%PATH%"`
	- Notes:
		- "/m" = all users
		- "setx" instead of "set" = permanent change
		- adding "" at the beginning and end of path is useful if you have spaces in your path)
		- Programs I add to path: `StreamRip`, `yt-dlp`, `ADB/Fastboot`, `FFmpeg`.
- Local Security Policy 
  - Ask for password for administrator rights: Local Policies → Security Options → User Account Control: Behavior of the elevation prompt for administrators in Admin Approval mode → Prompt for credentials. 
- services.msc: `Connected User Experiences and Telemetry` can be disabled.
- Change default app for different file types
  - Video player: mp4, mov, avi, mkv, webm, flv, html5
  - Music player: mp3, aac, flac, ogg, opus
  - PDF reader: pdf
  - image viewer: png, jpg, jpeg, gif, webp, tiff, bmp, heif, xvg
  - Text viewer: txt
  - Torrent client: .torrent
- Optional features
  - Facial Recognition
  - Math Recognizer
  - Internet Explorer mode
  - Steps recorder
  - WMIC
  - Windows Media Player Legacy
  - Windows PowerShell ISE
  - WordPad
- Most important Windows Settings
  - System → Power
  - System → Multitasking
  - System → Clipboard
  - Bluetooth & devices → Mouse → Additional mouse settings → pointer options → disable enhance pointer precision
  - Bluetooth & devices → Touchpad
  - Network & interent → Wi-Fi / Ethernet → Hardware properties → Edit DNS (e.g. `1.1.1.1` & `1.0.0.1` encrypted)
  - Turn on BitLocker
  - Language & Region → Regional format: English (World) *(allows to use DD/MM/YYYY format and programs will be installed in English instead of your local language)*
 - Performance tips:
   - Settings → Accessiblity → Disable transparency effects
   - Windows Security → Device Security → Disable core isolation (note: weakens security)
  - Firefox:
  	- make sure in about:support that compositing is rendered by `WebRender` (note: and not WebRender (software))
  	- about:config tweaks:
   		- `browser.tabs.loadBookmarksInBackground` → true
   		- `browser.bookmarks.openInTabClosesMenu` → false
   		- `dom.ipc.processPriorityManager.backgroundUsesEcoQoS` → false
   		- `full-screen-api.warning.timeout` → 0
   		- `browser.compactmode.show` → true
   		- `reader.parse-on-load.enabled` → false
		- `browser.cache.disk.enable` → false
       	- `accessibility.force_disabled` → 1
    	- `toolkit.telemetry.unified` → false
     	- `browser.ml.enable` → false (turns off AI, a kill switch should be available with Firefox 148)
- Change "model" name under PC's name: regedit → `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\OEMInformation` → string: Model → data: *model*
