

# Problems:

## VNC shows "Cannot currently show the desktop".

To solve this problem do these steps: <br>

1. Check VNC Server Status. <br>
Ensure that the VNC server is running on your Raspberry Pi. You can start the VNC server using the following command:
```
sudo systemctl start vncserver-x11-serviced.service
```

2. Configure VNC Server<br>
Make sure the VNC server is configured correctly. You can configure it using the raspi-config tool:<br>
```
sudo raspi-config
```
Navigate to Interfacing Options > VNC and enable it.


3. Resolution Settings<br>
The VNC server may not be able to handle the current resolution settings. You can force a specific resolution by editing the /boot/config.txt file on your Raspberry Pi:<br>
```
sudo nano /boot/config.txt
```
Add or modify the following lines to set a specific resolution (e.g., 1920x1080):<br>
```
hdmi_force_hotplug=1
hdmi_group=2
hdmi_mode=82
```

```
hdmi_mode=16: 1024x768 at 60Hz
hdmi_mode=28: 1280x800 at 60Hz
hdmi_mode=35: 1280x1024 at 60Hz
hdmi_mode=82: 1920x1080 at 60Hz
```

Save the file and reboot your Raspberry Pi:
```
sudo reboot
```

## The screen is too large:

Use the previous steps + go to the raspberrypi icon in the top left side<br>
```
preferences -> Screen Configuration -> right-click on the hdmi-1 image -> choose 1920 X 1080
```

## The screen has a black boundries:


- go to the raspberrypi icon in the top left side:<br>
```
Raspberrypi configuration -> Display -> overscan -> Disable
```

- Add the follow to
```
sudo nano /boot/config.txt
```
```
# Framebuffer settings
framebuffer_width=1920
framebuffer_height=1080
```
- Check the following:<br>
```
# Enable HDMI
hdmi_force_hotplug=1

# Set resolution to 1080p 60Hz in DMT group
hdmi_group=2
hdmi_mode=82

# Disable overscan
disable_overscan=1

# Framebuffer settings
framebuffer_width=1920
framebuffer_height=1080
```

---------------------------------------------------------


