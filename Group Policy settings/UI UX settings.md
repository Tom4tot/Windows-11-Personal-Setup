## UI/UX-related group policy settings
- Disable chat: `Computer Configuration > Administrative Templates > Windows Components > Chat` → Configures the Chat icon on the taskbar (E+C)
- Disable Widgets: `Computer Configuration > Administrative Templates > Windows Components > Widgets` → Allow widgets (D)
- Disable Connected Modern Standby: `Computer Configuration > Administrative Templates > System > Power Management > Sleep Settings` → Allow network connectivity during connected-standby (on battery) (D)
- Disable Copilot: `User Configuration > Administrative Templates > Windows Components > Windows Copilot` → Turn Off Windows Copilot (E)
- Microsoft Defender
	- `Computer Configuration > Administrative Templates > Windows Components > Microsoft Defender Antivirus > Real-time protection` → Turn off real-time protection (E)
		- `Computer Configuration > Administrative Templates > Windows Components > Microsoft Defender Antivirus` → Configure detection for potentially unwanted applications (D)
	- `Computer Configuration > Administrative Templates > Windows Components > Windows Defender SmartScreen > Enhanced Phising Protection` → Service Enabled (D)
	- `Computer Configuration > Administrative Templates > Windows Components > Windows Defender SmartScreen > Explorer` → Configure Windows Defender SmartScreen (D)
- Control Panel (lock screen, language)
    - `Computer Configuration > Administrative Templates > Control Panel` → Allow Online Tips (D)
    - `Computer Configuration > Administrative Templates > Control Panel > Personalization` → Do not display the lock screen (E)
    - `Computer Configuration > Administrative Templates > Control Panel > Regional and Language Options`
        - Restricts the UI language Windows uses for all logged users (E)
        - Force selected system UI language to overwrite the user UI language (E+C)
