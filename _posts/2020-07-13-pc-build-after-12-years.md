---
layout: post
title:  "PC Build After 12 Years"
date:   2020-07-13 15:00:00
author: Soumil Heble
comments: true
categories: personal computers
---

{% include image.html name="final_build.jpg" alt="My Workstation" width="740px" class="center" caption="My Workstation" %}

Building my PC had been on my mind ever since I came to the US in August 2018 for my Masters but there were several reasons why I decided to hold off until February 2020.
* It was more of a `want` than a `need` at that point in time and an expensive investment.
* There was a high chance that any Job I landed after my Masters would not be in Raleigh, NC. So a PC being a large piece of technology and would incur some additional moving expenses.
* I would not have been doing anything useful with all that power since I planned to build a gaming PC. I was busy with my education/assignments and whatever free time I had was spent sleeping, eating, or watching movies/TV series online. 
* I rarely used to play games back then. I started playing `Dota 2` and `CS:GO` regularly during my last semester.

So, I decided to hold off on purchasing one, until I landed a job at AMD, Inc in the first half of my last semester. As soon as I graduated from NC State, I decided that I'd build a PC with my sign-on bonus.

## What Would I Do With My Machine?
This is the most important question that determines what parts to select for your PC. This question also encompasses the question *What features do I need on my PC?*

**My requirements were:**
* Gaming on a 2K monitor, medium settings with at at least 90Hz refresh rate
* Running design synthesis, PnR tools, and compilation tools quickly
    * Basically, I required multi-threading - at least 4 cores
* Quick OS boot with dual boot setup
    * Nowadays I only use Windows 10 for Gaming, Linux for everything else
    * Needed SSDs as Boot Drives
* A color-accurate display - I like the saturated colors of my phone's AMOLED display and hated the faded colors of my previous laptop's TN panel.
* It should be powerful enough for about 5 years for my tasks

### The Parts
With a budget of $2000 I set-off looking for parts in January 2020, just before the COVID-19 pandemic scare set in.

#### **The CPU and GPU**

{% include image.html name="cpu_gpu.jpg" alt="AMD Ryzen 5 3600 & AMD Radeon RX 5700XT" width="740px" class="center" caption="AMD Ryzen 5 3600 & AMD Radeon RX 5700XT" %}

**CPU**

{% include image.html name="cpu_closeup.jpg" alt="AMD Ryzen 5 3600 Close-up" width="400px" class="left-float" caption="AMD Ryzen 5 3600 Close-up" %}

I decided to go for `AMD "Matisse" Ryzen 5 3600` for the CPU. During that time it was being touted as the best and most economical CPU for ultra-setting 1080p gaming and general applications. It fit my requirements of medium-setting 2K gaming and multi-threading of at least 4 cores (Ryzen 3600 has 6 cores).

My previous experience with an AMD system was not great. I owned an `HP Pavilion g6-1b60us` before an HP Pavilion 15 e038tx and the current Lenovo ThinkPad Carbon X1 6th Generation. It had an `AMD "Llano" Dual-Core A4-3300M APU` which ran hot and had poor battery life. 

Six years later AMD launched processors based on the Zen architecture which had a massive improvement in performance and power efficiency while being economical. When I was an intern at AMD in the summer of 2019, the Ryzen 3000 series of processors were launched. The launch was very successful because of TSMC's 7nm process node, Zen 2 Microarchitecture, and the huge IPC gains and performance efficiency that came with it. Apart from being a great product, as an employee, I get a discount on AMD's products. AMD's commitment to support the AM4 platform for another year was also a huge factor in my decision. Even if I don't plan to upgrade my CPU for at least 4 years having a motherboard with support for the next generation CPUs is a bonus.

**GPU**

NVIDIA has some really good GPUs but I went for Gigabyte Radeon RX 5700XT Gaming OC 8GB card. I got an employee discount and it's a good card for 2K gaming and surpasses the NVIDIA RTX 2060 Super for about the same price. 

#### Parts List

{% include image.html name="pc_parts.jpg" alt="PC Parts Ensemble" width="740px" class="center" caption="PC Parts Ensemble" %}

|Parts|Price| |
|:-:|:-:|:-:|
|<a href="https://www.amd.com/en/products/cpu/amd-ryzen-5-3600" target="_blank">AMD Ryzen 5 3600</a>|$139.45|CPU|
|<a href="https://www.coolermaster.com/catalog/coolers/cpu-air-coolers/hyper-212-black-edition/" target="_blank">Cooler Master Hyper 212 Black 120mm</a>|$31.86|CPU Cooler|
|<a href="https://noctua.at/en/nt-h1-3-5g" target="_blank">Noctua NT-H1 Pro-Grade</a>|$8.39|Thermal Paste|
|<a href="https://www.gigabyte.com/us/Graphics-Card/GV-R57XTGAMING-OC-8GD-rev-10#kf" target="_blank">Gigabyte Radeon RX 5700 XT Gaming OC</a>|$370.27|GPU|
|<a href="https://www.asus.com/Motherboards/TUF-GAMING-X570-PLUS-WI-FI/" target="_blank">ASUS TUF Gaming X570-Plus (WiFi)</a>|$195.49|Motherboard|
|<a href="https://www.newegg.com/g-skill-16gb-288-pin-ddr4-sdram/p/N82E16820232880" target="_blank">G.SKILL Ripjaws V Series 16GB (2 x 8GB) DDR4 3200MHz CL16</a>|$78.61|RAM|
|<a href="https://www.silicon-power.com/web/product-Ace_A55" target="_blank">Silicon Power 256GB SATAIII</a>|$42.49|Windows 10 OS - SSD|
|<a href="https://www.intel.com/content/www/us/en/products/memory-storage/solid-state-drives/consumer-ssds/7-series/ssd-760p-series/760p-series-256gb-m-2-80mm-3d2.html" target="_blank">Intel SSD 760p 256GB NVME</a>|$0 (Salvaged from Laptop)|<a href="https://kubuntu.org/" target="_blank">Kubuntu 20.04 LTS</a> - SSD|
|<a href="https://www.seagate.com/internal-hard-drives/hdd/firecuda/" target="_blank">Seagate FireCuda Gaming (Compute) 2TB</a>|$79.67|Mass Storage - HDD|
|<a href="www.phanteks.com/Eclipse-P400A.html" target="_blank">Phanteks Eclipse P400A</a>|$82.35|Case|
|<a href="https://www.corsair.com/us/en/Categories/Products/Power-Supply-Units/cxm-series-2015-config/p/CP-9020103-NA" target="_blank">Corsair CX Series 650 Watt 80 Plus Bronze</a>|$84.99|PSU|
|<a href="https://noctua.at/en/nf-s12b-redux-1200-pwm" target="_blank">Noctua NF-S12B redux</a>|$44.31|Case Fans|
|<a href="https://www.pixiogaming.com/px7" target="_blank">Pixio PX7 Prime 2K IPS 165Hz</a>|$403.74|Great Features, 95% DCI P3 Color Gamut|
|<a href="https://www.amazon.com/dp/B07C9V1NF1/ref=twister_B07ZNBQKWX?_encoding=UTF8&psc=1" target="_blank">PC RGB LED Strip</a>|$25.49|RGB|
|<a href="https://www.corsair.com/us/en/Categories/Products/Gaming-Keyboards/Mechanical-Gaming-Keyboards/K68-Mechanical-Gaming-Keyboard-%E2%80%94-Red-LED-%E2%80%94-CHERRY%C2%AE-MX-Red/p/CH-9102020-NA" target="_blank">Corsair K68</a>|$74.36|Cherry MX Red Mechanical Keyboard|
|<a href="https://www.amazon.com/Avantree-Aluminum-Headphone-Sennheiser-Accessories/dp/B01A09KCJ4" target="_blank">Avantree Aluminum Metal Headphone Stand</a>|$21.24||
|<a href="https://www.amazon.com/VicTsing-Extended-31-5%C3%9715-75%C3%970-12-Computer-Water-Resistant/dp/B0794WBPHK" target="_blank">Victsing Extended Gaming Mouse Pad</a>|$14.86||
|<a href="https://www.amazon.com/AmazonBasics-8-Outlet-Surge-Protector-6-Foot/dp/B07GFRKSXD" target="_blank">AmazonBasics 8-Outlet Power Strip Surge Protector</a>|$17.61||
|<a href="https://www.amazon.com/Soundcore-Cancelling-Headphones-Wireless-Bluetooth/dp/B07NM3RSRQ" target="_blank">Anker SoundCore Life Q20</a>|$42.5|Bluetooth 5.0 Headset|
|<a href="https://www.amazon.com/atolla-Splitter-Switch-Charging-Adapter/dp/B00W9FLKTY" target="_blank">Powered USB 3.0 HUB</a>|$20.18||
|<a href="https://www.amazon.com/Twisted-Veins-Premium-Ethernet-Supports/dp/B014EV0G3G" target="_blank">HDMI Cables</a>|$8.46||
|<a href="https://www.amazon.com/MillSO-3-5mm-Jack-Adapter-CTIA/dp/B071NDLCGC" target="_blank">Headset Combiner</a>|$7||
|<a href="https://www.newegg.com/steelseries-62352-rival-300-fallout-4-edition-wired/p/N82E16826249211" target="_blank">SteelSeries Rival 300 Fallout 4</a>|$0 (Pre-Owned)|Gaming Mouse|
|<a href="https://www.microsoft.com/en-us/education/products/windows" target="_blank">Windows 10 Education</a>|$0||
|<a href="https://www.g2a.com/en-us/microsoft-office-professional-2019-plus-1-pc-microsoft-key-global-i10000188863004" target="_blank">Microsoft Office Professional 2019 Plus</a>|$24.94||
|=|=|=|
|**Total**|**$1818.26**||

* *All prices are after any rebates and MA sales tax.*

### The Assembly

Before putting all the parts in the case I recommend connecting all the parts on a bench and testing it out. This gives easy access to all the parts and if any one fails or is incompatible you can easily get it replaced.

{% include image.html name="initial_testing.jpg" alt="Initial Testing" width="740px" class="center" caption="Initial Testing" %}

{% include image.html name="case_front.jpg" alt="Case Assembly - Front" width="740px" class="center" caption="Case Assembly - Front" %}

{% include image.html name="case_back.jpg" alt="Case Assembly - Back" width="740px" class="center" caption="Case Assembly - Back" %}