# Dev
## Git
[Good cheatsheet on useful commands](https://ohshitgit.com/)

## C
- [David R. Hanson - C Interfaces and Implementations](http://www.r-5.org/files/books/computers/languages/c/mod/David_R_Hanson-C_Interfaces_and_Implementations-EN.pdf)
- [Jens Gustedt - Modern C](https://hal.inria.fr/hal-02383654/document)

## Linux
### Files
- [Good reference on the Tar archive format](https://mort.coffee/home/tar/)

### Zsh
- [Good reference on completions](https://github.com/zsh-users/zsh-completions/blob/master/zsh-completions-howto.org)
### System
#### Touchpad not reactive
You probably have the fuzz parameter in libinput set too high! [Libinput docs might help](https://wayland.freedesktop.org/libinput/doc/latest/touchpad-jitter.html) but I suggest you manually edit the hwdb file since the automated command has discarded some other settings on my touchpad, slowing it down considerably.
```
/etc/udev/hwdb.d/99-touchpad-fuzz-override.hwdb
----
evdev:name:SynPS/2 Synaptics TouchPad:dmi:*:svnLENOVO*:pvrThinkPadT490*:
 EVDEV_ABS_00=::44:0
 EVDEV_ABS_01=::52:0
 EVDEV_ABS_35=::44:0
 EVDEV_ABS_36=::52:0
```
#### Disable faulty trackpoint
You need to create a [libinput device quirk](https://wayland.freedesktop.org/libinput/doc/latest/device-quirks.html) for the trackpoint and disable the event codes related to the pointer.
  ```
  /etc/libinput/local-overrides.quirks
  ----
  [Trackpoint wathever]
  MatchName=*name of trackpoint device as found in 'libinput list-devices'*
  AttrEventCodeDisable=REL_X;REL_Y
  # Disabling only one axis will disable the whole trackpoint device for some reason (trackpoint and trackpad buttons are the same device)
  ```
  Tip: use `evtest` to get event names and codes. After changing the quirks you can use `libinput debug-events` to check if the undesired events are still registered by libinput. Keep in mind that `evtest` sits below libinput and will always show all events.

## 3D Printing
### PET bottle pull-struder
- [Forum with some info on pull-struders](https://davehakkens.nl/community/forums/topic/pet-ropes-and-filaments-making-v4/)
- [Video with super cheap pull-struder setup. Got some good links in description](https://www.youtube.com/watch?v=1_BWXhT5Y-I)
- [Tests on printed PET](https://www.cnckitchen.com/blog/how-strong-is-pet-bottle-filament)
- [Recreator 3D: convert a printer into a pull-struder. A bit more expensive but much more polished than the rest](http://recreator3d.com/)
- [Facebook community of the Recreator 3D](https://www.facebook.com/groups/recreator3d)
- [PetBot Facebook community](https://www.facebook.com/groups/petbot/)
- [Cheap but good machine](https://www.youtube.com/watch?v=79gkUiH3ipE)

## CNC Milling
- [SainSmart 3018 Wiki](http://wiki.sainsmart.com/index.php/101-60-280PRO)
- [CNC bits buying guide](https://s3.amazonaws.com/s3.image.smart/download/CNC_Bits_Buying_Guide-20201012.pdf)
- [Good source of random info on 3018s](https://github.com/doug-harriman/3018-Mill)
- [My 3D-printed additions and mods to the 3018 Pro](https://github.com/Bonnee/3d-models/tree/master/CNC_3018_pro)

# Electronics
- [Good reference on **DCF-77** time synchronization signal](https://blog.blinkenlight.net/experiments/dcf77/)

# Keebs
## Model M hacking
### Controllers
-  [Model H PCB](https://modelh.club/)
-  [Model M Type-C board](https://github.com/ashpil/Model-M-Type-C)
-  [Model M USB interface](https://github.com/mschwingen/hardware/tree/master/modelm-usb)
-  [Neat Internal holder for Pro-Micro](https://www.billybuerger.com/pages/20180308_ModelMAdapter/)

# Windows
To boot an unmodified Windows 10 over USB the USB 3.0 support must be enabled at early boot time by setting `BootDriverFlags` to `0x14`. [Link](http://blog.zorinaq.com/boot-win10-over-usb/)

# Misc
- [Best way to find strange UTF8 symbols](https://tell.wtf/)
- Nice reviews of Chinese electronics (https://www.kirich.blog/)
