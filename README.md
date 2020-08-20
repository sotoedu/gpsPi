# gpsPi
gpsPi

https://sj-d.tistory.com/23

https://medium.com/@DefCon_007/using-a-gps-module-neo-7m-with-raspberry-pi-3-45100bc0bb41

https://maker.pro/raspberry-pi/tutorial/how-to-read-gps-data-with-python-on-a-raspberry-pi


# Step1

    sudo nano /boot/cmdline.txt

    dwc_otg.lpm_enable=0 console=tty1 root=/dev/mmcblk0p2 rootfstype=ext4 elevator=deadline fsck.repair=yes rootwait quiet splash plymouth.ignore-serial-consoles

    sudo nano /boot/config.txt

    dtparam=spi=on
    dtoverlay=pi3-disable-bt
    core_freq=250
    enable_uart=1
    force_turbo=1
    init_uart_baud=9600

    sudo reboot now

    sudo stty -F /dev/ttyAMA0 9600
    sudo killall gpsd
    sudo nano /etc/default/gpsd

    DEVICES="/dev/ttyAMA0"


    sudo systemctl enable gpsd.socket
    sudo systemctl start gpsd.socket 
    sudo cgps -s

    cat /dev/ttyAMA0
    or
    cgps -s

     sudo python serial_gps.py




