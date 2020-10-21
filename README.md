# Raspi 4 Art

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

#### Run at startup:  
1. Edit rc.local  
´´´sudo nano /etc/rc.local´´´  
Add commands to execute the program, preferably using absolute referencing of the file location (complete file path are preferred).  
Be sure to leave the line exit 0 at the end or, if your program runs continuously, fork the process by adding an ampersand (“&”) to the end of the command.  
Save the file and exit.
2. Reboot.  
**If you add a script into /etc/rc.local, it is added to the boot sequence. If your code gets stuck then the boot sequence cannot proceed.**

#### Shutdown:  
´´´sudo shutdown -h <now/+mins/hh:mm>´´´

#### Reboot:  
´´´sudo shutdown -r <now/+mins/+hh:mm>´´´
