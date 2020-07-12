---
layout: post
title:  "Jailbreaking My Kindle Paperwhite 3"
date:   2020-07-12 12:00:00
author: Soumil Heble
comments: true
categories: kindle hacking
---

{% include image.html name="kindle_post_banner.jpg" alt="PC from the 2000's" width="700px" class="center" caption="<a href=\"https://www.flickr.com/photos/matt_gibson/21693789403\" target=\"_blank\">Amazon Kindle Paperwhite</a> by <a href=\"https://www.flickr.com/photos/matt_gibson/\" target=\"_blank\">Matt Gibson</a> is licensed under <a href=\"https://creativecommons.org/licenses/by-nc/2.0/\" target=\"_blank\">CC BY-NC 2.0</a>" %}

<a href="https://en.wikipedia.org/wiki/Amazon_Kindle#Kindle_Paperwhite_(third_generation)" target="_blank">Amazon Kindle Paperwhite 3</a> is an excellent book reader. Amazon makes one of the best and affordable eBook readers. E-ink displays have improved a lot over the years and reading on one of these devices is visually close to reading material books. Apart from the visual experience eBook readers are environmentally friendly and compact (You can easily read a few hundred books while carrying only a few grams of weight).

**This jailbreak is heavily based on <a href="https://www.mobileread.com/forums/member.php?u=266535" target="_blank">grant2</a> <a href="https://www.mobileread.com/forums/showthread.php?t=267541" target="_blank">post</a> on <a href="https://www.mobileread.com/" target="_blank">mobileread.com </a>**

`The last section of this article titled References might be helpful if you have a different model of Kindle.`

### Why I Jailbroke my Kindle?

These days I read more research papers and white papers than books. It's easy to purchase eBooks from Amazon and read them but a lot of the literature I tend to read is in PDF. Even though Amazon offers a <a href="https://www.amazon.com/gp/sendtokindle/email" target="_blank">Mail to Kindle</a> service for PDF's it does not render some aspects of PDFs properly like figures, tables, etc. Jailbreaking your Kindle gives you additional features like applying custom screensavers, loading custom fonts, installing apps for reading comic books better, support for popular eBook extensions like <a href="https://en.wikipedia.org/wiki/EPUB" target="_blank">EPUB</a> and <a href="https://en.wikipedia.org/wiki/Mobipocket" target="_blank">Mobipocket (Mobi)</a> and the most important of all is using <a href="https://github.com/koreader/koreader" target="_blank">KOreader</a> which handles PDF formatting better on Kindle.

{% include image.html name="kindle_jb_intro.jpg" alt="Kindle with Front Panel Removed" width="600px" class="center" %}

### My Kindle Configuration Before Jailbreak

| Kindle PaperWhite 3 (2015) WiFi ||
|:-:|:-:|
| Serial Number | G090 G1 |
| Firmware Version | Kindle 5.12.4 (3602730042) |

### Jailbreaking Requirements

There are two methods to jailbreak your kindle:
1. Software Jailbreak - `(Firmware Version >= 5.6.x)`
2. Serial Jailbreak - `(Other Firmware Versions)`

Since my Kindle has the latest Firmware as of July 2020, I could only use the serial jailbreak method.

I am not going to explain how to solder or how to establish a serial connection with the USB to Serial converter. Please use Google or refer the following pages:
* <a href="https://youtu.be/QKbJxytERvg" target="_blank">Soldering</a>
* <a href="https://pbxbook.com/voip/sputty.html" target="_blank">Using Putty</a>

#### Tools Used
This is the exact list of tools that I used. You can make do with less and also find alternatives that suit you.

* <a href="https://www.ifixit.com/Store/Tools/Prying-and-Opening-Tool-Assortment/IF145-364?o=1" target="_blank">iFixit Prying Tools</a>
* <a href="https://www.hakkousa.com/products/soldering/hakko-fx-888d-digital-soldering-station-10148.html" target="_blank">Soldering Equipment</a>
* 30AWG Tinned Copper Wire
* Kapton Tape
* Electrical Tape
* <a href="https://www.sparkfun.com/products/12009" target="_blank">Sparkfun Bi-directional Logic Level Converter</a>
* <a href="https://robotdyn.com/usb-ttl-serial-adapter-cp2102-5v-3-3v-usb-a.html" target="_blank">CP2102 USB to Serial Converter</a>
* Breadboard
* Spare Jumper Cables
* Linux/Windows PC
* <a href="https://hackaday.com/2017/08/20/dps5005-makes-digital-power-supply-a-snap/" target="_blank">A Variable DC-DC Power Supply</a>

### Preparing your Kindle for Jailbreak

`Backup` all your `Kindle content` and `Device Info` from the setting menu. Take note of your Firmware Version, Wi-Fi MAC, Serial#. Calibre is a great piece of software to manage your Kindle content, find book covers, and metadata among other things. `Factory Reset` your Kindle and make sure your Kindle is in `Airplane mode` and `all wireless connections are forgotten.`

Power off your kindle by holding the button on the bottom for `10 seconds` and select `SCREEN OFF`.

### Getting Access to Kindle's Serial Port

> <p style="color:red">DISCLAIMER: I am not an expert in jailbreaking Kindle, my experience is limited to online guides and tutorials. If your Kindle gets bricked <b>I AM NOT RESPONSIBLE</b>. Google for solutions or refer the Help/FAQ Section at the end of this article.</P>

Follow <a href="https://www.ifixit.com/" target="_blank">iFixit's</a> Guide on <a href="https://www.ifixit.com/Guide/Kindle+Paperwhite+3+(7th+Generation)+Battery+Replacement/61550" target="_blank">Battery Replacement</a> up to `Step 5` to get access to the back of the PCB. Remove 3 screws and remove the battery for the next step.

### Setting Up a Serial Connection between Kindle and your PC
As almost every tablet/cellular/multimedia device runs on some form of Linux, no surprise here, Kindle also runs on one and the hardware designers have a serial port exposed on the PCB for debugging and maintenance. You'll need to `solder` some wires to the pads on the PCB to access the port.

Refer to the image below for the pads with which we can access the serial port. If you need access to a `1.8 V` supply use the `GND` pad and probe other pads to locate one.

{% include image.html name="kindle_serial_port.jpg" alt="Kindle PW3 Serial Port PCB Pads" width="600px" class="center" caption="Close-up of Serial Port in Kindle PW3" %}

{% include image.html name="kindle_solder_closeup.jpg" alt="Kindle PW3 Serial Pads Soldered" width="600px" class="center" caption="Kindle PW3 Serial Pads Soldered with Precision"%}

Ther serial port on Kindle is 1.8V and the module I used is compatible with a `3.3V` serial port hence I used a Bi-directional Logic Level converter to make the USB to Serial converter work with Kindle. Instead of using the Kindle for a `1.8V` supply, I used a DC-DC variable power supply to power the logic converter. Below is a block diagram of the setup.

{% include image.html name="setup_block_diagram.jpg" alt="Setup Block Diagram" width="600px" class="center" caption="Setup Block Diagram"%}

| USB to UART | Kindle |
|:-:|:-:|
| TX | RX |
| RX | TX |
| GND | GND |

You'll need access to the screen for the next steps so pop in the battery you removed for soldering wires to the serial port.

### Getting Root Access to Your Kindle
**Overview**
1. Getting Kindle's Password
1. Setting Up Your COM Port
1. Getting Into Diagnostics Boot
1. Removing Password for `root` User
1. Jailbreak

#### Getting your Kindle's Password
You should have Python installed on your system to generate the password to access Kindle as a `root` user. Run the following commands in Python to get your root password specific to your Kindle's Serial Number. Do not forget to substitute your Kindle's serial# in the command.
{% highlight python %}import hashlib
print("fiona%s"%hashlib.md5("<your kindle serial number with no spaces and all capital letters>\n".encode('utf-8')).hexdigest()[13:16]) {% endhighlight %}

Post running these commands you should get your root password. It should have the following format `fionaxxx`. The `xxx` will be three characters specific to your device.

#### Setting Up Your COM Port
Use the following settings in PuTTy to connect to your Kindle.

| Speed (Baud Rate) | 115200 |
| Data Bits | 8 |
| Stop Bits | 1 |
| Parity | None |
| Flow Control | None |

#### Getting Into Diagnostics Boot
Turn on your Kindle and you should see some text on the serial terminal (PuTTy). When you see something hit any key to stop autoboot press any key to interrupt the process or better yet keep pressing any key after you see text appear. You should be left with a prompt something like this:
{% highlight shell %}uboot>{% endhighlight %}

Type the following command to boot into the diagnostics menu:
{% highlight shell %}uboot> bootm 0xE41000{% endhighlight %}

You should see a menu on your Kindle's screen. Refer to the two images below to gain access to the login prompt on PuTTy.

{% highlight shell %}kindle login:{% endhighlight %}

{% include image.html name="kindle_diag_1.jpg" alt="System Diagnostics Menu" width="600px" class="center" caption="Screen 1: System Diagnostics Menu"%}

{% include image.html name="kindle_diag_2.jpg" alt="Reboot or Disable Diags Menu" width="600px" class="center" caption="Screen 2: Reboot or Disable Diags Menu"%}

{% include image.html name="kindle_diag_3.jpg" alt="Kindle Screen After Login Prompt" width="600px" class="center" caption="Screen 3: Kindle Screen After Login Prompt on PuTTy"%}

Enter the following details to get the root prompt `[root@kindle root]#`. As Kindle is using linux you won't see the password being typed on PuTTy:
{% highlight shell %}kindle login: root
password: fionaxxx (The one you generated above using Python) {% endhighlight %}

#### Removing Password for root User
This section removes the need for entering password for the main root account.

Mount the system partition to access the linux `passwd` file. Run the following commands:
{% highlight shell %}mkdir /tmp/main
mount /dev/mmcblk0p1 /tmp/main
vi /tmp/main/etc/passwd {% endhighlight %}

This will open the linux `passwd` file in vi editor. Make the following edits to this file. At the top of the file you should see {% highlight shell %}root:x:0:0:root:/tmp/root:/bin/sh{% endhighlight %} after it there might be some other lines. You need to remove the first `x` after `root` on the first line to get {% highlight shell %}root::0:0:root:/tmp/root:/bin/sh{% endhighlight %} and save the file.

**Steps to Follow after `vi` is opened:**
* Move the cursor to the colon before the `x`
* Press `i` then the `Delete` Key
* Press `Esc` Key
* Press `:` Key then type `wq` and press `Enter` to save the file

Type `reboot` on the prompt after saving the file and press `Enter`, you should see your Kindle reboot and see some text your Kindle as well as PuTTy.

### Jailbreak
`All the tools/files you require for following sections can be found at the` <a href="https://www.mobileread.com/forums/showthread.php?t=225030" target="_blank">Tool Snapshots Page</a> and look for the tools under the sections **Packages targeting the Kindle 5 (Touch/PW1/PW2/KT2/KV/PW3/KOA/KT3/KOA2/PW4/KT4)** and **KUAL & KUAL extensions**. 

For this section you will need the `K5 JailBreak (5.0.x - 5.4.4.2)` tar.xz file.

1. Unzip the tar.xz
1. Connect your Kindle to PC
1. Copy the following files from `kindle-5.4-jailbreak` inside the extracted directory to Kindle's root directory
    * bridge.conf
    * bridge.sh
    * developer.keystore
    * gandalf
    * jb.sh
    * json_simple-1.1.jar
    * Update_jb_$(cd mnt && cd us && sh jb.sh).bin
1. Eject Kindle Drive

Type the following commands on PuTTy:
{% highlight shell %}cd /mnt/us
sh jb.sh{% endhighlight %}

The jailbreak script will do its magic and you should see the word `JAILBREAK` at the bottom of your Kindle.

{% include image.html name="kindle_jb.jpg" alt="Kindle Jailbreak Message" width="600px" class="center" caption="Kindle Jailbreak Message"%}

Reboot Kindle by typing the `reboot` command on PuTTy. If the jailbreak is a success you should see the following directories in your Kindle's root directory.
* mkk
* rp

### Jailbreak Hotfix
> If you've just successfully ran any iteration of a Factory JailBreak, this is your next step - <a href="https://www.mobileread.com/forums/showpost.php?p=3004892&postcount=1597" target="_blank">JB Hotfix Page</a>

For this section you will need the `K5 JailBreak Hotfix` zip file.
1. Unzip the tar.xz
1. Connect your Kindle to PC
1. Copy the `Update_jailbreak_hotfix_1.16.N_install.bin` file from the extracted directory to Kindle's root directory
1. Eject Kindle Drive
1. On your Kindle, Go To: Settings -> All Settings -> Device Options -> Advanced Options -> Update Your Kindle
1. This will execute the `.bin` you copied above and install the hotfix. 

### Installing MRPI or MobileRead Package Installer
> This is a KUAL extension, that will plug into the Helper menu a single Install MR Packages button. - <a href="https://www.mobileread.com/forums/showthread.php?t=251143" target="_blank">MRPI Page</a>

I do not know what it does but from some forum post on <a href="www.mobileread.com" target="_blank">mobileread.com</a> said that this allows one to install KUAL which allows the running of 3rd Party apps and hence KOReader which was my aim.

For this section you will need the `MR Package Installer` tar.xz file.
1. Unzip the tar.xz
1. Connect your Kindle to PC
1. Copy the following directories from the extracted directory to Kindle's root directory
    * extensions
    * mrpackages

### Installing KUAL
> KUAL - Kindle Unified Application Launcher. This is a Launcher application, in which anybody can plug into to provide new buttons and menus through extensions. - <a href="https://www.mobileread.com/forums/showthread.php?t=203326" target="_blank">KUAL Page</a>

For this section you will need the `KUAL` and `Helper` tar.xz files.

1. Unzip the `KUAL` tar.xz
1. Connect your Kindle to PC
1. Copy the `Update_KUALBooklet_hotfix_v2.7.24_install.bin` file from the extracted directory to Kindle's root directory
1. Eject Kindle Drive
1. On your Kindle, Go To: Settings -> All Settings -> Device Options -> Advanced Options -> Update Your Kindle
1. This will execute the `.bin` you copied above and install the hotfix.
1. You should see a book named `KUAL` in your Kindle Library.

{% include image.html name="kindle_kual.jpg" alt="KUAL in Kindle Library" width="600px" class="center" caption="KUAL in Kindle Library"%}

1. Unzip the `Helper` tar.xz
1. Connect your Kindle to PC
1. Copy the contents of `extensions` directory from the extracted directory to the `extension` directory in Kindle's root directory
1. Restart your Kindle

### Installing KOReader
> KOReader is a document viewer primarily aimed at e-ink readers. - <a href="https://github.com/koreader/koreader" target="_blank">KOReader Github</a>

1. Download <a href="https://github.com/koreader/koreader/releases/download/v2020.06/koreader-kindlepw2-v2020.06.zip" target="_blank">koreader-kindlepw2-v2020.06.zip</a> from <a href="https://github.com/koreader/koreader/releases" target="_blank">KOReader GitHub Download Page</a>. The release might change so keep that in mind but the file prefix will be `koreader-kindlepw2`.
1. Unzip the whole archive into the Kindle's USB root directory
1. Restart your Kindle

There's an excellent <a href="https://github.com/koreader/koreader/wiki/Installation-on-Kindle-devices" target="_blank">tutorial on GitHub</a> to install KOReader, written by the developers.

{% include image.html name="kindle_kual_menu.jpg" alt="KOReader in KUAL Menu" width="600px" class="center" caption="KOReader in KUAL Menu"%}

{% include image.html name="kindle_koreader_paper.jpg" alt="2 Column Research Paper Reflow in KOReader" width="600px" class="center" caption="2 Column Research Paper Reflow in KOReader"%}

### Protecting Your Jailbreak from Amazon's Updates
I probably won't connect my Kindle to Wi-Fi and manage documents using <a href="https://calibre-ebook.com/" target="_blank">Calibre</a>, but if you want to, make an empty directory named `update.bin.tmp.partial` in your Kindle's root directory. This will confuse Kindle from updating automatically.

### Installing Screensaver Hack [Optional]
If you want custom/personalized screensavers on your Kindle you can do so.

For this section you will need the `ScreenSavers Hack` and `Python 2.7 & Python 3.8` tar.xz files.

1. Unzip the `ScreenSavers Hack` and `Python 2.7 & Python 3.8` tar.xz
1. Connect your Kindle to PC
1. Copy the `Update_python_0.15.N_install_pw2_kt2_kv_pw3_koa_kt3_koa2_pw4_kt4.bin` file from the extracted `Python` directory to the `mrpackages` directory in Kindle's root directory.
1. Copy the `Update_linkss_0.25.N_install_pw2_kt2_kv_pw3_koa_kt3_koa2_pw4_kt4.bin` file from the extracted `ScreenSavers` directory to the `mrpackages` directory in Kindle's root directory.
1. Eject Kindle Drive
1. Run KUAL -> Helper -> Install MR Packages

You should see the Image below while Python is being installed. After the packages are installed your Kindle will reboot and you should see the second image below as your screensaver. Not getting the screensaver after hack? Check the README section in the `ScreenSavers` directory or the `references` section.

{% include image.html name="kindle_screensaver_python.jpg" alt="Python Installing on Kindle" width="600px" class="center" caption="Python Installing on Kindle"%}

{% include image.html name="kindle_screensaver_success.jpg" alt="Kindle Screensaver Hack Successful" width="600px" class="center" caption="Kindle Screensaver Hack Successful"%}

There are several options that the screensaver hack provides refer the `README` file in the `ScreenSavers` directory. I'll explain what mode I'm using:

> One the KV/PW3/KOA: PNG files, 1072x1448. Grayscale if possible, but color works too (you can even play with an alpha channel if you like). You *NEED* to follow these directives: non-PNG files will be discarded by the hack, and broken files or files in the wrong resolution will confuse the framework and trigger weird issues. - `ScreenSavers README File`

1. Copy any of your PNG screensavers (compliant to the above specification) to the Kindle's Root Directory/linkss/screensavers
1. On your Kindle, Go To KUAL -> Screen Savers -> Screen Savers Behavior -> Image Cycle (Default)
1. KUAL -> Screen Savers -> Screen Savers Tools -> Clear cover cache
1. KUAL -> Screen Savers -> Screen Savers Tools -> Clear personal info cache
1. KUAL -> Screen Savers -> Screen Savers Tools -> Restart framework now

Your Kindle should restart the screensaver framework and the custom screensavers you added should be displayed on screen from now. 

{% include image.html name="kindle_my_screensaver.jpg" alt="KUAL in Kindle Library" width="600px" class="center" caption="My Kindle's Screensaver"%}

### Help/FAQ
`There are no issues with my jailbreak yet. I'll update this section if I find any.`

## References
* The <a href="https://www.mobileread.com/forums/showthread.php?t=267541" target="_blank">Main Reference</a> article for this hack
* The <a href="https://www.mobileread.com/forums/showthread.php?p=3137590&postcount=1" target="_blank">Linux Specific Reference</a> article for this hack
* <a href="http://www.mobileread.mobi/forums/showthread.php?t=325971" target="_blank">Reference Post</a> for installing MRPI first before KUAL in newer firmwares
* <a href="https://www.mobileread.com/forums/showthread.php?t=225030" target="_blank">Reference Post</a> for the current Tool Snapshots