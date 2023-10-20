# CodeConnectFix-Tips-Troubleshooting
Some tips for MakeCode coding in Minecraft Bedrock for Windows 10 and 11

With the introduction of the bug [MCPE-154405](https://bugs.mojang.com/browse/MCPE-154405) with Minecraft Bedrock version 1.18.30 for Windows as far back in time as April the 19th 2022, the latest [Code Connection App](https://apps.microsoft.com/detail/code-connection-for-minecraft/9PPFPG2FG2QB) version 1.50 could unfortunately no longer connect successfully.

To the rescue came [Laurent Rocher](https://github.com/lrocher) with his great [CodeConnecFix](https://github.com/lrocher/CodeConnectFix).

Here, I present some tips for starting everything up in the correct order quickly and some commong troubleshooting:<br><br>

## Batch script to quickly start everything up in the correct order

### Prerequisites
- Minecraft Bedrock Edition installed on Windows 10 or 11
- [Code Connection UWP App](https://apps.microsoft.com/detail/code-connection-for-minecraft/9PPFPG2FG2QB) installed
- [Check and exempt](https://github.com/Vegz78/CodeConnectFix-Tips-Troubleshooting/edit/main/README.md#:~:text=Sometimes%2C%20often%20on%20Windows%2011%2C) Minecraft from loopback net isolation, especially on Windows 11

### Installation
- Create and download the following files to the folder _C:\Program Files\CodeConnectFix_:
  - [CodeConnectFix.exe](https://github.com/lrocher/CodeConnectFix/releases)
  - [Minecraft_Coding.bat](https://github.com/Vegz78/CodeConnectFix-Tips-Troubleshooting/blob/main/Minecraft_Coding.bat)
  - [images.ico](https://github.com/Vegz78/CodeConnectFix-Tips-Troubleshooting/blob/main/images.ico)
- Make a Windows shortcut(.lnk) to _C:\Program Files\CodeConnectFix\Minecraft_Coding.bat_, add _C:\Program Files\CodeConnectFix\images.ico as icon for the shortcut
- To be able to pin this shortcut to the Start Menu and Taskbar, add "cmd /c " to the beginning of the _Target Path_ in the properties

### Usage
-Execute the above shortcut or _C:\Program Files\CodeConnectFix\Minecraft_Coding.bat_ directly
-Inside a Minecraft world with cheats enabled, press _T_ to open chat, and with the chat box highlighted press _CTRL+V_ to connect
-The first time you connect, you might have to authorize the connection for private networks in the Windows firewall pop-up menu

### Troubleshooting
- The connection string sometimes is not available in the clipboard to paste with _CTRL+V_ when Minecraft starts:
  - Run the _Minecraft_Coding.bat_ script and try _CTRL+V_ again in the Minecraft chat
- CodeConnectFix.exe crashes and closes:
  - Run the _Minecraft_Coding.bat_ script and try _CTRL+V_ again in the Minecraft chat
- CodeConnectFix.exe hangs and does not connect:
  - Close the CodeConnectFix window and run the _Minecraft_Coding.bat_ script again
- Code Connection hangs and does not connect(seldom):
  - Close both Code Connection and the CodeConnectFix window and run the _Minecraft_Coding.bat_ script again
- Sometimes, often on Windows 11, none of the above works and Minecraft does not connect with Makecode through Code Connection:
  - This might be due to UWP local loopback restrictions on the Minecraft app
  - Open PowerShell as administrator and run the following command:<br>
    ```CheckNetIsolation LoopbackExempt -a -n="Microsoft.MinecraftUWP_8wekyb3d8bbwe"```
  - This solution was found here:<br>
    https://www.mysysadmintips.com/windows/clients/912-windows-10-uwp-apps-can-t-connect-to-local-ip-loopback-restriction
