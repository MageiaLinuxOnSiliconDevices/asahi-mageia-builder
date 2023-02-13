# asahi-mageia-builder

Builds a minimal Mageia image to run on Apple M1/M2 systems

<img src="https://user-images.githubusercontent.com/12903289/200475188-41b1faf1-9b00-4376-ad8c-b9da19ef4d3f.png" width=65%>

## Installing a Prebuilt Image

Make sure to update your macOS to version 12.3 or later, then just pull up a Terminal in macOS and paste in this command:

```sh
curl https://github.com/MageiaLinuxOnSiliconDevices/scripts/mageia.sh | sh
```

## Mageia package install

```dnf install mkosi arch-install-scripts systemd-container zip```

### Notes

- ```qemu-user-static``` is also needed if building the image on a ```non-aarch64``` system  

### Notes

1. The root password is **mageia**
2. On the first boot the ```asahi-firstboot.service``` will run, selinux will be set to enforcing and the system will reboot.   
3. The Asahi Linux-related RPM's (and Source RPM's) used in this image can be found here: <https://leifliddy.com/asahi-linux/37/>  
   All RPM's signed are signed by a GPG key. 
   The repo config can be found here: <https://github.com/MageiaLinuxOnSiliconDevices/asahi-linux/asahi-linux.repo>  

## Setting up WiFi

`NetworkManager` is enabled by default.

To connect to a wireless network, use the following sytanx:
```nmcli dev wifi connect network-ssid```

An actual example:
```nmcli dev wifi connect blacknet-ac password supersecretpassword```

## Wiping Linux

Bring up a Terminal in macOS and run the following Asahi Linux script:  
```sudo curl -L https://alx.sh/wipe-linux | sh```  
You should definitely understand what this script does before running it. You can find more info here:  
<https://github.com/AsahiLinux/docs/wiki/Partitioning-cheatsheet>

## Boot from USB device

Once Linux is installed on an M1 system, you can then boot a compatible usb drive via ```u-boot```.  
This project will create a bootable USB drive for M1 systems.
<https://github.com/MageiaLinuxOnSiliconDevices/asahi-mageia-usb>

## Display and keyboard backlight

The `light` command can be used to adjust the screen and keyboard backlight.

```sh
light -s sysfs/leds/kbd_backlight -S 10
light -s sysfs/backlight/apple-panel-bl -S 50
```
