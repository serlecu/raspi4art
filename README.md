# Raspi 4 Art

#### Terminal Shortcut
```CTRL + ALT + T```

---

#### General Config Panel
```sudo raspi-config```

#### Force Set Time & Date:  
```sudo date -s "Mon Aug  12 20:14:11 UTC 2014"```

---

#### Network Status: 
```ífconfig```

#### Network Config:  
```sudo nano /etc/dhcpcd.conf```

#### Wireless credentials:  
```sudo nano /etc/wpa_supplicant/wpa_supplicant.conf```  
For Eduroam add and complete at the end:  
```
network={
        ssid="eduroam"
        scan_ssid=1
        key_mgmt=WPA-EAP
        eap=PEAP
        identity="<yourUser>"
        password="<yourPass>"
        phase1="peaplabel=0"
        phase2="auth=MSCHAPV2"
        disabled=1
}
```
---

#### Remote Terminal:  
```ssh <RaspiUser>@<RaspiIP>```  

#### SSH transfer PC -> RPi:  
```scp <Url> <RaspiUser>@<RaspiIP>:<RaspiUrl>```

---

#### Run Script at startup:  
1. Edit rc.local  
```sudo nano /etc/rc.local```  
Add commands to execute the program, preferably using absolute referencing of the file location (complete file path are preferred).  
Be sure to leave the line exit 0 at the end or, if your program runs continuously, fork the process by adding an ampersand (“&”) to the end of the command.  
Save the file and exit.
ej.:  
```sudo python /home/pi/program.py &```  
2. Change permissions:  
```sudo chmod +x /etc/rc.local```  
3. Reboot.  
**If you add a script into /etc/rc.local, it is added to the boot sequence. If your code gets stuck then the boot sequence cannot proceed.**
**Take into consideration that this procedure will not likely work for launching desktop apps or processes that need GUI or interaction.**

#### Run App at startup:
1. Activate "Desktop Session Settings" in Pi-Menu:  
Navigate "Main Menu": Preferences > Main Menu Editor.  
Navigate "Main Menu Editor": Applications > Preferences > Desktop Session Settings.  
Check "Desktop Session Settings".  
Accept.
2. Create .desktop file:
Open Terminal  
```nano ~/.local/share/applications/<AppName>.desktop```
3. Craft .desktopo file: 
```
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Terminal=false
Exec=/path/to/executable
Name=Name of Application
Icon=/path/to/icon
```  
Icon Path is not mandatory.  
4. Save and close:  
```Ctrl+X``` ```Y```   
5. Copy to "Desktop Session Settings'" folder:  
```cp ~/.local/share/applications/<AppName>.desktop ~/.config/autostart/```   
6. Open "Desktop Session Settings":  
Navigate "Main Menu": Preferences > Desktop Session Settings.  
Check that your application is listed.

---

#### Shutdown:  
```sudo shutdown now```  
```sudo shutdown -h +<countdown mins>```  
```sudo shutdown -h <scheduled time hh:mm>```

#### Reboot: 
```sudo reboot```  
```sudo shutdown -r +<countdown mins>```  
```sudo shutdown -r <scheduled time hh:mm>```
