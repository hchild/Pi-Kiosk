1.	Copy directory and open readme
a.	CTRL+ALT+T      => Open Terminal
b.	git clone https://github.com/hchild/pi-kiosk
c.	leafpad pi-kiosk/README.md

2.	Run to update Sources
a.	sudo apt-get update

3.	Run to upgrade packages to newest release
a.	sudo apt-get upgrade

4.	Run to set time zone
a.	sudo dpkg-reconfigure tz

5.	Enable SSH
a.	sudo raspi-config
b.	Option 7 then A4 and select yes to enable

6.	Change password
a.	sudo raspi-config
b.	option 2 and enter new password

7.	Set static ip and record for ssh
a.	Right click networking logo in bottom right and select wired & wireless network settings and interface and enter ip address

8.	Hide scroll bars in chromium and in incognito mode
a.	Google Chrome App Store and Search Scrollbar Customizer
b.	Customize and set Height & Width to 0

9.	Disable screen blanking & timeout
a.	https://www.bitpi.co/2015/02/14/prevent-raspberry-pi-from-sleeping/
b.	sudo nano /etc/kbd.config
i.	BLANK_TIME =0
ii.	POWERDOWN_TIME=0
c.	sudo nano /etc/xdg/lxsession/LXDE-pi/autostart
i.	add these lines
1.	@xset s noblank
2.	@xset s off
3.	@xset –dpms
d.	sudo nano /etc/lightdm/lightdm.conf
i.	Add anywhere below the [SeatDefaults] Header
1.	xserver-command=X –s 0 –dpms

10.	Scheule auto reboot
a.	sudo –s
i.	crontab –e
1.	Scroll to bottom and add following line to auto reboot at 10A.M. every day. Can add more times under using 24 hour clock. 
a.	0 10 * * * sudo reboot
b.	CTRL + X and then Y to save

11.	Install script for kiosk
a.	leafpad pi-kiosk/home/pi/start-kiosk.sh
b.	edit last line after incognito with desired URL and then Save and close
c.	cd pi-kiosk
d.	bash install.sh
