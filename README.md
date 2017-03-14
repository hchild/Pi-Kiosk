Each task below is done through terminal which can be opened using CTRL+ALT+T

1.	Copy directory and open readme

		a. CTRL+ALT+T      => Open Terminal
		b. git clone https://github.com/hchild/pi-kiosk
 		c. leafpad pi-kiosk/README.md &

2.	Run to update Sources

		a. sudo apt-get update

3.	Run to upgrade packages to newest release

		a. sudo apt-get upgrade

4.	Run to set time zone

		a. sudo dpkg-reconfigure tzdata

5.	Enable SSH

		a. sudo raspi-config
		b. Option 5 then P2 and select yes to enable

6.	Change password

		a. sudo raspi-config
		b. option 1 and enter new password

7.	Set static ip and record for ssh

		a. Right click networking logo in bottom right and select wired & wireless 
          network settings and interface and enter ip address

8.	Hide scroll bars in chromium and in incognito mode

		a. https://chrome.google.com/webstore/detail/scrollbar-customizer/flffekjijpabhjgpoapooggncnmcjopa?utm_source=chrome-ntp-icon
		b. Google Chrome App Store and Search Scrollbar Customizer
		c. Customize and set Height & Width to 0

9.	Disable screen blanking & timeout

		a. https://www.bitpi.co/2015/02/14/prevent-raspberry-pi-from-sleeping/
		b. sudo nano /etc/kbd.config
			i. Set the following to the values shown below
                 		1. BLANK_TIME =0
                 		2. POWERDOWN_TIME=0
                		3. CTRL+X and then Y to Save
		c. sudo nano /etc/xdg/lxsession/LXDE-pi/autostart
			i. add these lines
                 		1. @xset s noblank
                 		2. @xset s off
                 		3. @xset –dpms
                		4. CTRL+X and then Y to Save
		d. sudo nano /etc/lightdm/lightdm.conf
			i. Add anywhere below the [SeatDefaults] Header
                	 	1. xserver-command=X –s 0 –dpms

11.	Schedule Auto Reboot 

		a. sudo -s
        b. crontab -e
            i. Add the following lines to the bottom.The first line restarts the pi everyday at 9:10 A.M
               You can add as many times as needed just remember to use 24 hour clock.
                  1. 10 9 * * * sudo reboot  
                  2. 0 20 * * * sudo reboot

11.	Install script for kiosk

		a. leafpad pi-kiosk/home/pi/start-kiosk.sh
            i. edit last line after incognito with desired URL and then Save and close
        b. cd pi-kiosk
        c. bash install.sh
