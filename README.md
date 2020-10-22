# Raspi 4 Art

#### TErminal Shortcut
```CTRL + ALT + T```

---

#### General Congig Panel
```sudo raspi-config```

#### Force Set Time&Date:  
```sudo date -s "Mon Aug  12 20:14:11 UTC 2014"```

---

#### Network Status: 
```ífconfig```

#### Network Config:  
```sudo nano /etc/dhcpcd.conf```

---

#### Remote Terminal:  
```ssh <RaspiUser>@<RaspiIP>```  

#### SSH transfer PC -> RPi:  
```scp <Url> <RaspiUser>@<RaspiIP>:<RaspiUrl>```

---

#### Run App at startup 1:
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
5. Open "Desktop Session Settings":  
Navigate "Main Menu": Preferences > Desktop Session Settings.  
Check that your application is listed.


#### Run App at startup 2:  
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

#### Shutdown:  
```sudo shutdown -h <now/+mins/hh:mm>```

#### Reboot:  
```sudo shutdown -r <now/+mins/+hh:mm>```
