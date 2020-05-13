# m93p-tiny-hackintosh
a Repository containing files for turning a Lenovo M93p tiny into a shiny hackintosh
# Introduction
Setting up Hackintoshes can be a pain and there is a lot to consider. In this Repo I want to document my journey of turning a Lenovo M93p Tiny PC into a Hackintosh running Catalina with the Opencore Bootloader.

 ## My Configuration

 M93p tiny PCs come in many different configurations and here's mine:

 - Intel i5 4570T CPU
 - Intel HD 4600 integrated GPU
 - Q87 Chipset
 - 8GB DDR3 RAM
 - some SSD I had lying around
 - Intel Wifi Card (replaced with a Broadcom BCM94352)

 As far as I'm aware there are M93p out there that don't have any Wifi preinstalled, which would make upgrading the antennas and Wifi card a bit more cumbersome later, though if you don't plan to use Wifi you could save some money here.

 Also there's quadcore configurations out there, which would give you a bit more power, so if you can get one of these, go for it. I found that the most crucial component is the integrated GPU though. My model uses the natively supported HD4600 variant. If yours uses a mobile iGPU like HD4400, prepare for some more fiddling.

 ## What Works

 - Catalina 10.15.4
 - iMessage
 - Airdrop
 - (almost) 4K60 through DP
 - Audio Out
 - Energy Management
 - FileVault
 - App Store
 - Wifi and Bluetooth

 ## What Doesn't Work

 This build is still a bit away from being golden. Here are my current issues:

 - no 4k60
 - no fan readout
 - no sleep
 - still a bit shaky energy management (though it could be that the CPU is just busy most of the time since it clocks up and don just fine)


# Useful Links
https://dortania.github.io/OpenCore-Desktop-Guide/ - The OpenCore Desktop Guide is the most important bit of info for this build.
# Tools To Download
https://github.com/corpnewt/gibMacOS - gibMacOS lets you download MacOS recovery images directly from Apple.

https://github.com/corpnewt/ProperTree - ProperTree is a nice plist editor. It's cross platform, so you can use it both when preparing the files in Windows and later in MacOS.

https://github.com/corpnewt/GenSMBIOS - GenSMBIOS is used to create a valid serial number for your hackintosh so you can use iMessage and other iCloud services later.
# Creating the Hackintosh
## Preparation
First you should clone or download this repo and the tools I recommended. If you have the same system config as my Lenovo tiny PC there's only one thing you have to set in the config.plist located under EFI/OC/

As you can see in https://github.com/lumpi2k/m93p-tiny-hackintosh/blob/caf13bc817f28be0f482b7b1a78febe9a7ae8a4b/EFI/OC/config.plist#L769 I blanked my own serial info in the config.plist. This means you'll have to create your very own set of serials.

The OpenCore Desktop Guide shows this in it's chapter  [Fixing iServices][1]. **Don't skip this step, it is very important!** I've left the model iMac15,1 in the config, but you can also use iMac14,1 or iMac14,2 (these should technically work a little better since they're the exact CPU generation. I found no difference though.)

After yo've created the SMBIOS with GenSMBIOS put in the values as described [here in the Desktop Guide][2].



[1]:https://dortania.github.io/OpenCore-Desktop-Guide/post-install/iservices.html
[2]: https://dortania.github.io/OpenCore-Desktop-Guide/config.plist/haswell.html#platforminfo