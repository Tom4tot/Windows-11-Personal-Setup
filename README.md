# Windows 11 Personal Setup
## Installation process | Essential programs | Privacy tweaks with GPEDIT | PowerShell commands to remove Provisioned apps | General tweaks

### Introduction and general information
Made for: Windows 11 22H2  
Last update: 2022-11-14

This covers all the steps I personally go though when performing a clean install of Windows 11. My aims are the following:
- As much automation as possible (portable programs, quick import of settings)
- A clean UI/UX (I disable/uninstall most of the bloat that comes with Windows)
- As much privacy as possible (see my Group Policy edits)
- Prioritizing native software (to break as little things as possible) or FOSS


### Installation
- Download the official iso file from [Microsoft](https://www.microsoft.com/software-download/windows11)
- Create bootable USB with [Rufus](https://rufus.ie/en/), leave everything as default (GPT, UEFI, NTFS), and customize the *Windows User Experience*: tick everything
  - Benefits: faster than Microsoft's tool, makes the use of a local account easier, skips privacy questions (all will be off)
- Naviagate to /sources in and add the ei.cfg attached to this repo.
  - Benefits: it will bypass your current Windows key and allow you to choose Windows Education/Enterprise instead of Windows Home.
  	- Education edition is my favorite as it has all the features from Enterprise but is also included in the multi-edition iso available from Windows without an account, unlike the enterprise iso that is hard to get. You can fin a comparison of all versions [here](https://en.wikipedia.org/wiki/Windows_10_editions#Comparison_chart): 
- Reboot and install Windows. Make sure to delete all your partitions (except the data one, if you have one) and to choose the Education/Enterprise/Professional edition.

### Applications that I use / install (FOSS / *proprietary*) (alphabetic order)
#### Portable applications
- [Platform tools - ADB/Fastboot](https://developer.android.com/studio/releases/platform-tools) - mandatory to tinker with my Android phones
- [Audacity](https://github.com/audacity/audacity/releases/tag/Audacity-3.0.2) - Tool to analyse/edit audio files (last update that doesn't include telemetry)
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
- [Notepad++](https://notepad-plus-plus.org/downloads/) - My favorite text editor
- [qBittorrent](https://www.qbittorrent.org/download.php) - Favorite torrent client
- [ShareX](https://getsharex.com/downloads/) - Favorite screen capture tools, many other features
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
##### Automated installation via a package manager
- Package managers
    - Chocolatey - see packages [here](https://community.chocolatey.org/packages)
        - [Installation](https://chocolatey.org/install) (PowerShell with admin rights)
            - `Set-ExecutionPolicy AllSigned`
            - `Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))`
            - Command to install all programs: `choco install 7zip eartrumpet firefox f.lux  jre8 nextcloud pdf24 powertoys soulseek teamviewer twinkle-tray -y`
            - See installed programs: `choco list --localonly`
    - Winget - see packages [here]([https://community.chocolatey.org/packages](https://winget.run/))
    	- Command to install all programs: `winget install 7zip.7zip && winget install File-New-Project.EarTrumpet && winget install Mozilla.Firefox && winget install flux.flux && winget install Oracle.JavaRuntimeEnvironment && winget install Nextcloud.NextcloudDesktop&& winget install geeksoftwareGmbH.PDF24Creator && winget install Microsoft.PowerToys && winget install Soulseek.SoulseekQt && winget install TeamViewer.TeamViewer && winget install xanderfrangos.twinkletray`
- [7-zip](https://www.7-zip.org/download.html) - Favorite file archiver
- [EarTrumpet](https://github.com/File-New-Project/EarTrumpet) - Volume Control for Windows (Windows Store) 
- [Firefox](https://www.mozilla.org/fr/firefox/all/#product-desktop-release) - Main browser
  - Add-ons: 
    - [uBlock Origin](https://addons.mozilla.org/en-US/firefox/addon/ublock-origin/)
    - [Bypass Paywalls Clean](https://addons.mozilla.org/en-US/firefox/addon/bypass-paywalls-clean/)
    - [SponsorBlock](https://addons.mozilla.org/en-US/firefox/addon/sponsorblock/)
    - [Firefox Multi-Account Containers](https://addons.mozilla.org/en-US/firefox/addon/multi-account-containers/)
    - A working twitch adblocker, see [TwitchAdSolutions](https://github.com/pixeltris/TwitchAdSolutions)
- [*f.lux*](https://justgetflux.com/) - My favorite nightlight software on Windows
- [Java](https://www.java.com/en/) - Needed for some programs
- [NextCloud](https://nextcloud.com/install/) - Cloud Client
- [PDF24](https://tools.pdf24.org/fr/creator) - PDF tools
- [PowerToys](https://github.com/microsoft/PowerToys) - Useful system utilities
- [*Soulseek*](https://www.slsknet.org/news/node/1) - To share and download music files that I legally own
- [*TeamViewer*](https://www.teamviewer.com) - When I need to support a relative with IT stuff
- [Twinkle Tray](https://github.com/xanderfrangos/twinkle-tray) - Easily manage the brightness of your monitors in Windows from the system tray 
##### Only available on Microsoft Store
- [Battery Percentage Icon](https://github.com/soleon/Percentage) - See your battery percentage in the system tray (Windows Store)
##### Not available on Chocolatey or Winget
- [ExplorerPatcher](https://github.com/valinet/ExplorerPatcher) - Enhance the working environment on Windows (available on Winget)
- [FreeFileSync](https://freefilesync.org) - My favorite file synchronization tool
- [*Microsoft Office*](https://www.heidoc.net/joomla/technology-science/microsoft/16-office-2021-direct-download-links) - Office suite (direct link)
- [Sublte](https://github.com/tvdburgt/subtle) - Subtitles downloader

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
	- You can also directly import my config that is attached to this repository
	- If you want to update policies without restarting, run this command in CMD (it's **not** necessary to run it as administrator): `gpupdate /force`

#### [Privacy settings](https://github.com/Tom4tot/Windows-11-Personal-Setup/blob/main/Group%20Policy%20settings/Privacy%20settings.md)
#### [UI/UX settings](https://github.com/Tom4tot/Windows-11-Personal-Setup/blob/main/Group%20Policy%20settings/UI%20UX%20settings.md)
#### [Microsoft Office advanced settings](https://github.com/Tom4tot/Windows-11-Personal-Setup/blob/main/Group%20Policy%20settings/Microsoft%20Office.md)
#### [Microsoft Edge basic and advanced settings](https://github.com/Tom4tot/Windows-11-Personal-Setup/blob/main/Group%20Policy%20settings/Microsoft%20Edge.md)

### Settings & tweaks - Others
- [Uninstall all unnecessary preinstalled *provisioned* user apps](https://github.com/Tom4tot/Windows-11-Personal-Setup/blob/main/PowerShell%20Commands.md)
- Local Security Policy 
  - Ask for password for administrator rights: Local Policies → Security Options → User Account Control: Behavior of the elevation prompt for administrators in Admin Approval mode → Prompt for credentials. 
- services.msc: services to disable
	- Connected User Experiences and Telemetry
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
- Delete OneNote printer through `printmanagement.msc`
- Most important Windows Settings
  - System → Power
  - System → Multitasking
  - System → Clipboard
  - Bluetooth & devices → Mouse → Additional mouse settings → pointer options → disable enhance pointer precision
  - Bluetooth & devices → Touchpad
  - Network & interent → Wi-Fi / Ethernet → Hardware properties → Edit DNS (e.g. 1.1.1.1 & 1.0.0.1 Encrypted)
  - Turn on BitLocker
  - Privacy & security → open Windows Security → disable Tamper Protection
  - Language & Region → Regional format: English (World) *(allows to use DD/MM/YYYY format and programs will be installed in English instead of your local language)*
 - Performance tips:
   - Settings → Accessiblity → Disable transparency effects
   - Windows Security → Device Security → Disable core isolation (note: weakens security)
   - Windows Security → Searching Windows → Find my files: enhanced
   - Device Manager → System Devices → High precision event timer (HPET) → disable device (note: improve performance with most hardware - some people say it's snake oil)
   - Firefox → make sure in about:support that compositing is rendered by WebRender (note: and not WebRender (software))
