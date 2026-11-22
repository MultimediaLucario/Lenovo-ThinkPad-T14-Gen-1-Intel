# Lenovo ThinkPad T14 Gen 1 (Intel) OpenCore Configuration

<img width="1112" height="480" alt="repository-open-graph-t14" src="https://github.com/user-attachments/assets/feea50ef-2b7c-48dd-afb6-76f895d6678e" />



[![macOS](https://img.shields.io/badge/macOS-Ventura-orange.svg)](https://developer.apple.com/documentation/macos-release-notes)
[![macOS](https://img.shields.io/badge/macOS-Sequoia-lightblue.svg)](https://www.apple.com/macos/macos-sequoia/) 
[![OpenCore](https://img.shields.io/badge/OpenCore-1.0.8-blue)](https://github.com/acidanthera/OpenCorePkg)
[![License](https://img.shields.io/badge/license-Apache-red)](/LICENSE)

<p align="center">
   <strong>Status: Maintained</strong>
   <br />
   <strong>Version: </strong>1.0
   <br />
   <a href="https://github.com/MultimediaLucario/Lenovo-ThinkPad-T14-Gen-1-Intel/releases"><strong>Download now »</strong></a>
   <br />
   <a 
   <br />
   <a href="https://github.com/MultimediaLucario/Lenovo-ThinkPad-T14-Gen-1-Intel/issues">Report Bug</a>
   <br />  
   <a href="https://github.com/valnoxy/t480-oc/blob/main/CHANGELOG.md">View Changelog (Coming Soon)</a>
   <br />
   <a href="http://linktr.ee/mastertwinsofficial">🥋🎧 Book us to elevate your next event! 🔥😎</a>  
  </p>
</p>
</br>

## ⚠️ Disclaimer ⚠️
This guide is only for the Intel version of the Lenovo ThinkPad T14 Gen 1. I am NOT responsible for any harm you cause to your device. This guide is provided "as-is" and all steps taken are done at your own risk.

## 🎧 Master Twins 🥋
This ThinkPad T14 Gen 1 EFI repo has been brought to you by **Master Twins**! We are an Open Format / Unified style DJ Group that will elevate your next event in order to make said next event an unforgettable experience! We play everything from 80s and 90s classic rock, to Hip-Hop, Recession Pop, House, Trance, Techno, EDM, and more! To book us, click the link above! ⬆️

&nbsp;

## Introduction

### EFI folders

This repo includes multiple EFI configuations for different macOS Versions.

| EFI               | Description                                                               | Type      |
| ----------------- | ------------------------------------------------------------------------- | --------- |
| `EFI - Ventura`     | Supports macOS Ventura (using Airportitlwm)		                | `Stable`  |
| `EFI - Sequoia`   | Supports macOS Sequoia (using Airportitlwm) (Siri & Video Out don't work)	| `Stable`  |         

> **Note** The Sequoia configuration is still a work in progress as both Siri and video output are still not functional. Use ```EFI - Ventura``` instead for a better experience.

<details>
<summary><strong>💻 My Hardware 💻 </strong></summary>
<br>
These are the Hardware component I use. But this OpenCore configuation <strong>should still work</strong> with your device, even if the components are not equal.

> **Note** Check the model of your WiFi & Bluetooth card. Intel cards should be compatible with itlwm (or AirportItlwm). If your card is from another manufacturer, please check if your card supports macOS.

| Category  | Component                            |
| --------- | ------------------------------------ |
| CPU       | Intel Core i5-10310U                 |
| GPU       | Intel UHD Graphics 620               |
| SSD       | Intel 660p 512 GB NVME SSD   		   |
| Memory    | 32 GB DDR4 2667 Mhz                  |
| Camera    | 720p Camera                          |
| WiFi & BT | Intel AX201 (Wifi 6)                 |

</details>  

</details>

<details>  
<summary><strong> 📸 Photos 📸 </strong></summary>
</br>

<img width="3856" height="2169" alt="IMG_0846-Github" src="https://github.com/user-attachments/assets/471cdd77-9246-45bb-9a88-697b5c5c5c12" />
<img width="2560" height="1440" alt="IMG_0393" src="https://github.com/user-attachments/assets/bcabc94d-cbbd-42c3-815b-f37de6f3c86e" />
<img width="8057" height="4532" alt="IMG_0944" src="https://github.com/user-attachments/assets/90c0184f-6e50-47cb-b4c6-3cbd84c8a76f" />
<img width="6666" height="3750" alt="IMG_0186" src="https://github.com/user-attachments/assets/75bf4869-8990-4448-b286-e308ed27e1c1" />
<img width="2560" height="1440" alt="IMG_0979" src="https://github.com/user-attachments/assets/d9b833f3-5015-48f0-a8e8-952008ff0fde" />



</details>  

</details>


&nbsp;

## Installation

<details>  
<summary><strong> ⚠️ Anti-Piracy Warning / Disclaimer ⚠️ </strong></summary>
</br>
	
### ⚠️ PIRACY IS NO PARTY! ⚠️
I do not endorse or condone the use of pre-configured Hackintosh Distros because not only they cause unnecessary harm to your machine but it is considered to be a form of **Software Piracy**. Software Piracy is a serious crime according to copyright law and is punishable for up to 10 years in prison. 
</details>


<details>  
<summary><strong>📝 Requirements 📝 </strong></summary>
</br>

You must have the following items:
- Lenovo ThinkPad T14 Gen 1 (Intel Version only 😁).
- Access to a working Windows machine with Python installed.
- A pendrive with more than 4 GB (Remember that during the preparation we will format the flash drive to create the installation media).
- an Internet connection (recommended via Ethernet).
- 1-2 hours of your time.

</details>

<details>  
<summary><strong>⚙️ Preperation ⚙️ </strong></summary>
</br>

### Create the install media

First of all, you will need the install media of macOS. I will use [macrecovery](https://github.com/acidanthera/OpenCorePkg) to download and create the macOS Install media.

With macrecovery, the process is the following:
- Download [OpenCorePkg](https://github.com/acidanthera/OpenCorePkg) as a ZIP.
- Extract the OpenCorePkg-master.zip file.
- Open ```cmd.exe``` with Administrator privileges and change the directory to OpenCorePkg-master\Utilities\macrecovery.
- Enter the following command to download macOS:
```
# Ventura (13)
python macrecovery.py -b Mac-7BA5B2D9E42DDD94 download

# Sequoia (15)
py macrecovery.py -b Mac-937A206F2EE63C01 -m 00000000000000000 download

```
- After the download succeeded, type ```diskpart``` and wait until you see ```DISKPART>```

- Plug-in your pendrive and type ```list disk``` to see your disk id.

- Select your pendrive by typing ```select disk <diskid>```

- Now we are gonna clean the pendrive and convert it to GPT. First, type ```clean``` and then ```convert gpt```.

>  **Note**: If an error occurred, try to convert again by typing ```convert gpt```.

- After the pendrive is clean and converted, we will create a new partition where we can put our files on. First, type ```create partition primary```, then select the new partition with ```select partition 1``` and format it ```format fs=fat32 quick```.

- Finally, mount your pendrive by typing ```assign```

- Now, close the Command Prompt and create the folder ```com.apple.recovery.boot``` on the pendrive. Copy ```OpenCorePkg-master\Utilities\macrecovery\BaseSystem.dmg``` and ```Basesystem.chunklist``` into that folder.

>  **Note**: If you can't find BaseSystem.dmg, use RecoveryImage.dmg and RecoveryImage.chunklist instead.

After the install media was created, we need to make the USB drive bootable.

### Configure and install OpenCore
Download the EFI folder from this repo, you will find the latest files under the release tab or just download the repo as it is. Move the folder to the root of your pendrive (e.g. J:\) and rename the folder to ```EFI```.

#### GenSMBIOS
We need a script, called [GenSMBIOS](https://github.com/corpnewt/GenSMBIOS), to create fake serial number, UUID and MLB numbers. **This step is essential to have working iMessage, so do not skip it!**

The process is the following:

- Download GenSMBIOS as a ZIP, then extract it.
- Start GenSMBIOS.bat and use option ```1``` to download MacSerial.
- Choose option ```2```, to select the path of the config.plist file. It will be located in ```EFI -> OC``` folder.
- Choose option ```3```, and enter ```MacBookPro15,4``` as the machine type.
- Press ```Q``` to quit. Your config now should contain the requied serials.

#### Enter the proper ROM value
After adding serials to your config.plist, you have to add the computer's MAC address to the config.plist file. **This step is also essential to have a working iMessage, so do not skip it.** We need a Plist editior, to write the MAC address into the config.plist file. I used [ProperTree](https://github.com/corpnewt/ProperTree), since it works on Windows too. You have to change the MAC address value in the config.plist at

```PlatformInfo -> Generic -> ROM```

Delete the generic ```112233445566``` value, and enter your MAC address into the field, without any colons. Save the Plist file, and it is now ready to be written out to the EFI partition of your install media.

#### Default keyboard layout and language
The default keyboard layout and language is ```German```. To change the language, edit the value of ```NVRAM -> Add -> 7C436110-AB2A-4BBB-A880-FE41995C9F82 -> prev-lang:kbd``` to the value of your language. If your value contains an underscore "```_```", replace it with a hyphen "```-```". The value for English would be ```en-US:0```. You can find a list of all language values [here](https://github.com/acidanthera/OpenCorePkg/blob/master/Utilities/AppleKeyboardLayouts/AppleKeyboardLayouts.txt).

### Install OpenCore
After you've finished with the neccesary tweaks, you have to copy the EFI folder to the EFI partition of your pendrive.

</details>

<details>  
<summary><strong>🚚 Installation 🚚 </strong></summary>
</br>

### Prepare BIOS
The bios must be properly configured prior to installing macOS.
In Security menu, set the following settings:

-  `Security > Security Chip`: must be **Disabled**
-  `Memory Protection > Execution Prevention`: must be **Enabled**
-  `Virtualization > Intel Virtualization Technology`: must be **Enabled**
-  `Virtualization > Intel VT-d Feature`: must be **Enabled**
-  `Anti-Theft > Computrace -> Current Setting`: must be **Disabled**
-  `Secure Boot > Secure Boot`: must be **Disabled**
-  `Intel SGX -> Intel SGX Control`: must be **Disabled**
-  `Device Guard`: must be **Disabled**

In Startup menu, set the following options:

-  `UEFI/Legacy Boot`: **UEFI Only**
-  `CSM Support`: **No**

In Thunderbolt menu, set the following options:

-  `Thunderbolt BIOS Assist Mode`: **UEFI Only**
-  `Wake by Thunderbolt(TM) 3`: **No**
-  `Security Level`: **No**
-  `Support in Pre Boot Environment > Thunderbolt(TM) device`: **No**

Now you can go through the install.

### Install macOS
1. Boot from USB, press ```SPACE``` and select the USB drive inside of OpenCore ```"NO NAME (DMG)" or similar```.
>  **Note:** The first boot may take up to 20 minutes.
2. Wait for the macOS Utilities screen.
3. Select Disk Utility, select your disk and click erase. Give a name and choose **APFS** with **GUID Partition Map**.
4. After erasing, go back and select **Reinstall macOS** and follow the steps on your screen. The installation make take up to **2 hours**.
>  **Note:** Your PC will restart multiple times. Just boot from USB and select your disk inside of OpenCore. (named macOS Installer or the disk name).
5. Once you see the `Region selection` screen, you are good to proceed.
6. Create your user accound and everything else.

</details>

## Post-Install Guide

<details>  
<summary><strong>💾 Install OpenCore to your boot drive 💾</strong></summary>
</br>

1. Press `ALT + SPACE` and open terminal. Type `sudo diskutil mountDisk disk0s1` (where disk0s1 corresponds to the EFI partition of the main disk)
2. Open Finder and copy the EFI folder of your USB device to the main disk's EFI partition.
3. Unplug the USB device and reboot your laptop. Now you can boot macOS without your USB device.

</details>


</details>

<details>  
<summary><strong> 💻 Change System Information (GenSMBIOS) 💻  </strong></summary>
</br>

**One of the the most crucial steps in making iMessage and other iServices function properly is to set the SMBIOS and all associated information correctly.**

1. Run the following script in Terminal:

```git clone https://github.com/corpnewt/GenSMBIOS && cd GenSMBIOS && chmod +x GenSMBIOS.command && ./GenSMBIOS.command```

2. Mount your EFI partition using [OpenCore Configurator](https://mackie100projects.altervista.org/download-opencore-configurator/?doing_wp_cron=1741176165.9179310798645019531250).
3. Go to your EFI partition, enter the EFI folder, then the OC folder and then look for the file known as ```Config.plist```.
4. Go back to ```GenSMBIOS``` , type 2 and hit ENTER to then drag your ```Config.Plist``` file into the command line, press ENTER when finished.
5. Type 3 to Generate SMBIOS, then press ENTER. Type ```MacbookPro15,4``` ,(```MacBookPro16,1``` for macOS Sequoia), then press ENTER. Leave this Terminal window open.
6. Type 4 to Generate UUID and press ENTER.
7. Type 5 to Generate ROM and press ENTER.
8. Type Q to Quit and press ENTER.
9. Restart your ThinkPad and enjoy!

**Note**: According to SnowfallMink on Reddit, you'll need to also do the following after the other steps, "You either need to connect to ethernet and start from there or set your wifi card as enO. You also need a supportted wifi card either Broadcomm or Intel via spoofing. You need to configure the serials BEFORE signing in your Apple ID or AFTER wiping any iCloud related keys after siging out. You would then need to have Apple Support help you whitelist your iMessage serial including giving them your customer code found by opening iMessage through terminal. I found that opening a chat and selecting another device like your iPhone helps as they HAVE to report it to the people that actually can whitelist. After chatting they should allow Services and you should receive a notification about iMessage on Mac, etc. You would have to contact support serveral times as most of the time they don't know what to do with the customer code. Hope this helps. Also if you are on a older version they would also push you to upgrade to the lastest version."
</details>

<details>  
<summary><strong>🎧 Fix Audio 🎧 </strong></summary>
</br>
	
**One of macOS's most infamous post-install issues is a glitch with the AUX port. Every time I update the EFI always causes a problem with my audio patch. It is also important to note that the internal microphone needs a special .pkg file to be installed in order to function properly. "Give one a fish you feed them for a day but teach one how to fish and you feed them for a lifetime."  So, here is a guide on how to fix the audio yourself.**

<details>  
<summary><strong>Required Tools</strong></summary>
</br> 

- [OpenCore Configurator](https://mackie100projects.altervista.org/download-opencore-configurator/?doing_wp_cron=1741176165.9179310798645019531250)
- [Hackintool](https://github.com/benbaker76/Hackintool/releases)
- Your macOS USB pendrive with your EFI loaded in case of any errors
- The .zip folder of the repo which houses a crucial .pkg file for the Internal Mic called ```TGLDMic-0.6.0```.

</details>

<details>  
<summary><strong>Instructions</strong></summary>
</br> 

1. Download and install both [OpenCore Configurator](https://mackie100projects.altervista.org/download-opencore-configurator/?doing_wp_cron=1741176165.9179310798645019531250) and [Hackintool](https://github.com/benbaker76/Hackintool/releases). Don't forget to also download and extract the zip folder from this repo.
2. Open Hackintool, navigate to the ```Sound``` section, then go to the bottom half where it says ```Audio Info```. There, you will find a little drop down menu that is labled ```ALC Layout ID```. Click on the drop down menu and you will find a couple different numbers to choose from. These are the potential audio layout ids that can work for your system. Make sure to keep track of them.
3. Open OpenCore Configurator, select ```Tools``` up in the menubar, and then select ```Mount EFI```. Go to the EFI partition for your boot drive, click ```Mount Partition```, and enter your macOS password.
4. Now, go to the menubar, select ```File```, ```Open```, and then Go to the drive that says ```EFI```, open the folder ```EFI```, double click on the ```OC``` folder and the file named ```Config.plist```.
5. Go to ```NVRAM```, the codes listed in this section are the UUIDs. Click on the 3rd one that starts with ```7C``` and navigate to the ```boot-args``` section.
6. In the ```boot-args``` section, go to the part where it says ```Value``` , right click to open the menu and navigate to ```boot-args```, ```AppleALC```, and select ```alcid=layoutid```.
7. Change the layoutid part of ```alcid=layoutid``` to one of the numbers presented in Hackintool (ex: ```alcid=86```), save the config.plist and restart your computer. (Make sure to go through each and every one of those ID numbers until you find the one that works the best with your system.) (**Make sure the ```boot-args``` contains the code, ```-tgldmic```, at the end before rebooting.**
8. Go back to the extracted zip folder and double click on ```TGLDMic-0.6.0.pkg```. The OS will try to block it from opening but click the done button.
9. Open up System Settings, go to Privacy and Security, and scroll down to where it shows that ```TGLDMic-0.6.0.pkg``` could not be opened.
10. From here, click on the button that says **Open Anyway**, enter your password, click the open button, and follow the on-screen prompts.
11. Go to the sound section in System Settings and pick ```Internal Microphone (TGLDmic)``` under input.
12. Congratulations, you've successfully fixed the audio for your T14! 🥳

</details>

</details>

<details>  
<summary><strong>🔋 Power Management (ReYogaSMC) 🔋 </strong></summary>
</br>

### The Power Management kext and software known as ```YogaSMC``` has not been updated since 2022, essentially making it practically deprecated. So, a replacement called ```ReYogaSMC``` surfaced online and it has improved power management on hackintoshed ThinkPads in every single way. However, it does require a couple extra steps. 

1. Go to the extracted repo zip folder and extract the zip file that says ```ReYogaSMC-App-2.2.1-RELEASE.zip```.
2. Select the ```ReYogaSMC``` app and drag it to the applications folder.
3. Go to the applications folder and double click on the ```ReYogaSMC``` app. The OS will try to block it from opening but click the done button.
4. Open up System Settings, go to Privacy and Security, and scroll down to where it shows that ```ReYogaSMC``` could not be opened.
5. From here, click on the button that says **Open Anyway**, enter your password, and enter your password again.
6. The app will open up but we're not done yet. Look for the settings icon on the bottom left corner of the app window and click it.
7. Select the option that says ```Start with macOS```.
8. Go to the section of the ```ReYogaSMC``` app labeled ```Device``` and enable the Accesibility and Input Montitoring settings.
9. Congratulations, you just patched the Power Management on your T14! 🥳

</details> 

</details>

## Status

<details>  
<summary><strong>✅ What's working ✅ </strong></summary>
</br>
 
- [X] Intel WiFi & Bluetooth 
- [X] Brightness / Volume Control
- [X] Battery Information
- [X] Audio (Audio Jack, Speaker, and Microphone) (**Siri does not work on Sequoia yet.**)
- [X] USB Ports & Built-in Camera
- [X] Graphics Acceleration
- [X] Trackpoint / Touchpad
- [X] Power management / Sleep
- [X] FaceTime / iMessage (iServices)
- [X] HDMI (**Ventura Only**)
- [X] Automatic OS updates
- [X] Handoff / Universal Clipboard
- [X] Sidecar (Cable) / AirPlay to Mac
- [X] SIP / FireVault 2
- [X] USB-C

</details>

<details>  
<summary><strong>❌ What's not working ❌ </strong></summary>
</br>

- [ ] Safari DRM ```Use Chromium powered Browser or Firefox to watch Amazon Prime Video, Netflix, Disney+ and others```
- [ ] AirDrop & Continuity 
- [ ] Fingerprint Reader (Disabled with NoTouchID kext)
- [ ] Thunderbolt 3
- [ ] Sidecar Wireless
- [ ] Apple Watch Unlock (**Use the BLEUnlock app as a workaround.**)

</details>

<details>  
<summary><strong>🔄 Not tested 🔄 </strong></summary>
</br>

- [ ] WWAN
- [ ] Dualbooting Windows / Linux (with OpenCore)

</details>

&nbsp;

## ⭐️ Feedback ⭐️
Did you find any bugs or just have some questions? Feel free to provide your feedback using the Discussions tab.
