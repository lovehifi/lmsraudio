# LMSrAudio [IMG] 64-bit for Pi 3 & Pi 4
You have an affinity for LMS, enjoy the Material Skin interface, and are particularly accustomed to using LMS/Material Skin on mobile devices. However, there are times when you reminisce about the alluring audio experience provided by Archphile or Rune Audio on the Arch Linux platform from many years ago. You can now rekindle that experience with the return of rAudio (Arch Linux).

I have personally created a customized build based on [LMS](https://forums.slimdevices.com/forum/user-forums/logitech-media-server), [Material Skin](https://github.com/CDrummond/lms-material), and Squeezelite build-on for [rAudio](https://github.com/rern/rAudio) to meet my own needs and those of my friends. rAudio, as I understand, is a different branch of Rune Audio.

I've added some features to make it user-friendly for regular users. I want to share it with anyone who wants to use it.

What's special about this build is that it can play YouTube videos on the TV screen and deliver high-quality audio through the DAC. Sometimes, even when I turn off the TV, the Pi 4 DAC continues playing music from YouTube. Importantly, you can use the YouTube app on a mobile device to search and control the Pi 4 playback. I've also included the Tidal Connect Docker from the [GitHub repository](https://github.com/GioF71/tidal-connect) for use with the Tidal app. When you switch the SQ64-rAudio player to off, Tidal Connect will appear.

I did this out of a passion for sound and to enhance user-friendly interaction for audio enthusiasts.

You can use software like Win32 Disk Imager or BalenaEtcher to flash the LMS rAudio OS images to SD cards.

Access the Music Server DAC interface by navigating to http://raudio/ or http://raudio.local/ in your browser. In case you cannot locate it, use the Advanced IP Scanner software to discover the IP address of rAudio. Subsequently, access it via the IP address; for instance: http://192.180.0.2.

In the Material Skin interface, click on the Configuration menu, scroll down to the bottom of the page to update to the LMSrAudio latest version.

>
For the first run, sometimes with certain routers, you might encounter an empty Configuration menu. If you come across this situation, please restart your router, then restart the Pi once again. This will assist LMSrAudio in generating the menu based on your Pi's IP on the first attempt.
>
>
**Download** [LMSrAudio IMG file URL here]:
https://drive.google.com/file/d/1pi3Vy_He6vUO_rfeEYwZQY5uG4Nb1pwS/
>
---------------------
>
SSH credentials: user 'root,' password 'ros.' You can customize these credentials and have full permissions to modify the source code according to your specific requirements.

>
>


---------------
![Screenshot](LMSrAudio-menu.png)

![Screenshot](LMSrAudioUI.png)
>
------------
>
### App Control
Use the app Rune Audio, rAudio or you can use the app for Android: Fully Kiosk Browser & Lockdown, and the app for iOS: Kiosker: Fullscreen Web Kiosk.
>
>
![Screenshot](https://raw.githubusercontent.com/lovehifi/addraudio/main/App_RuneAudio.jpg)
>
----------------
### Play from USB Disk
![Screenshot](https://raw.githubusercontent.com/lovehifi/addraudio/main/playonusb2.png)
>
--------
### Play with BubbleUPnP Server
>
After logging into the BubbleUPnP Server from the Config menu, you'll receive a success message: "Config updated successfully!" Proceed to the LMSBubv9 Server menu. Opt for the Server, select the Folder view option, pick the music album you wish to listen to and click "Add Album" to play it in your LMS.
>
![Screenshot](LMSBubV9.jpg)
>
----------
>
### Parametric EQ (12 band)
>
The Parametric EQ 12-band is a powerful tool for adjusting and optimizing audio with precise control over different frequency ranges. Ideal for fine-tuning your sound experience, it allows users to customize specific aspects of the audio output with simplicity and accuracy.
>
![Screenshot](https://raw.githubusercontent.com/lovehifi/addraudio/main/Eqfa12LMS.png)
>

User Note: You need to select the "Eqfa12p" output from the Config menu for Squeezelite to use. You can switch between Squeezelite outputs to compare sound changes instantly without restarting the Pi.
>
--------
### Play with Tidal Connect
![Screenshot](https://raw.githubusercontent.com/lovehifi/addraudio/main/tidal-connect.jpg)
>
------------
>
### Play Youtube Video
>
![Screenshot](https://raw.githubusercontent.com/lovehifi/addraudio/main/play-ytube.png)

Note:
Youtube on LCD has been turned on for the first time.
- On LCD or TV, tap the settings icon at the bottom.
- Tap 'Link with TV Code' to display the code.
- Next, in the YouTube app on your phone, select the Cast icon, then 'Link with TV code.
- Switch the **SQ64-rAudio player to off** before you play a YouTube video.
- Once completed, you can choose to cast to the TV (Youtube on LCD).
>

Video clip by a user using a phone to **cast YouTube video** from their phone to the Pi 4, displaying the video on the TV via HDMI and the audio to the Pi 4 DAC.
https://youtu.be/cwVGm7qOUq8


------------
>
### HDMI Config
hdmi_group=1 and hdmi_group=2 are two different HDMI mode groups, and they define different standards and configurations for HDMI output. Here is the difference between them:

**HDMI Group 1 (CEA - Consumer Electronics Association):**

- Intended for consumer devices such as TVs, projectors, etc.
- Supports a variety of resolutions and refresh rates common in the consumer electronics industry.


**HDMI Group 2 (DMT - Display Monitor Timings):**

- Intended for computer monitors and computer display devices.
- Supports resolutions and refresh rates suitable for computer monitors.
When you use hdmi_group=1, you are selecting configurations that are more common in the consumer electronics industry. On the other hand, hdmi_group=2 is the choice for computer monitors and computer display devices.

If you are using a TV, typically you would choose hdmi_group=1. If you are connecting Raspberry Pi to a computer monitor, then you might choose hdmi_group=2. Depending on the specific device and use case, you can select the group that is more suitable for your needs
>
>
You can make adjustments to the HDMI configuration in the /boot/config.txt file.

>
Config HDMI port 1 for 65 inch (HDMI port 1):
>
> hdmi_drive=2
>
> hdmi_force_hotplug=1
>
> hdmi_force_mode=1
>
> hdmi_group=1
>
> hdmi_mode=4
>
--------------------
>
### How to change the root password in LMSrAudio?
>
Open Putty (Windows) or Terminal (MAC OS). Login to SSH as root with the password "ros".
>
> ssh root@raudio
>
or
>
> ssh root@raudio.local
>
or
>
> ssh root@your_pi_ip
>
(replace "your_pi_ip" with the actual IP address of your Raspberry Pi).
>
> sudo passwd
>
Enter the new password and press Enter.
>
-------------
>
### How to modify the Configuration menu?
>
You can use software like WinSCP or FileZilla with the credentials user: root, pass: ros to open the file /srv/http/config/unit/startup.sh.
>
Replace WEB="raudio" with WEB="your pi IP" (sample 192.168.1.55). This modification will directly link to your Pi IP instead of using "raudio" for the menu links.
>>
------------------
### Why rAudio-LMS ?
>
https://github.com/lovehifi/raudiolms-32bit/wiki/Why-rAudio%E2%80%90LMS%3F
>


