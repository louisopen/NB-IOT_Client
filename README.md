### NB-IOT_Client 

> SIM7000C of NB-IOT module client on Raspberry Pi applications, SIM7000C 運行在樹莓派上的應用
> SIM card(大卡) 採用中華電信CAT. M1 門市申請即可

#### 1. Close power-saving of the display on Raspberry Pi
#### 先關閉視窗下螢幕休眠功能(當然也可以不用關閉)

sudo nano /etc/lightdm/lightdm.conf 
* [SeatDefaults]
* ...
* #xserver-command=X	    #Change to as below
* xserver-command=X -s 0 –dpms
* ...

#### 2. How to login command line mode to run application in the X-windows mode? 
#### 視窗模式開機自動開啟一個終端機模式, 並運行應用程序

sudo nano /home/pi/.config/autostart/autoboot.desktop 
* ...
* [Desktop Entry]
* Type=Application
* Name=MyApplicationRun
* #Exec = lxterminal -e /home/pi/autorun.sh               #運行掛機 applivcation close aftern run 5day 
* Exec = lxterminal -e "bash -c /home/pi/autorun.sh;bash" #運行測試(Stay Bash)
* Icon=pictur.png
* ...
or

* [Desktop Entry]
* Encoding=UTF-8
* Type=Application
* Name=myprogram
* Exec=lxterminal -e bash -c '/home/pi/autorun.sh;$SHELL' #bash run autorun.sh
* Terminal=true
* ...

* sudo nano /home/pi/autorun.sh
* ...
* python3 SIM7000iot.cht.py
* ...

#### 3. SIM7000Ciot.cht.py


