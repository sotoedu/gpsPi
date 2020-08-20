# gpsPi
gpsPi

![gps](https://user-images.githubusercontent.com/17608995/90718424-db710d80-e2ec-11ea-9164-b149eae8c072.jpeg) 

https://sj-d.tistory.com/23

https://medium.com/@DefCon_007/using-a-gps-module-neo-7m-with-raspberry-pi-3-45100bc0bb41

https://maker.pro/raspberry-pi/tutorial/how-to-read-gps-data-with-python-on-a-raspberry-pi

    VCC — 5v(pin 2)
    GND — Pi’s ground(pin 6)
    RX — Pi’s TX
    TX — Pi’s RX


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




