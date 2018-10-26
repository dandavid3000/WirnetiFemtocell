# WirnetiFemtocell
Guide to install Wirnet iFemtocell to work with The Things Network.

### Wirnet iFemtocell Wik access
Please contact support@kerlink.fr to open an account to access the wiki

### Configuration

#### Preparation
1. Connect the gateway to your LAN network, and prepare an empty USB key (FAT-32 formatted).
2. There are 2 ways to access the gateway configuration.
    * `Web interface`: Access through gateway IP address  
        ```
        To connect to the web interface, enter the IP address of your gateway into your browser’s URL bar (Make sure your computer is on the same local network). The default login/password are:
        Login:admin
        Password:pwd4admin
        
        For firmware version before v3.4.3, the default login/password are: 
        Login:admin
        Password:admin
        ```
    * SSH connection
        ```
        Login:admin
        Password:pdmk-$serialno
        
        For example, if an iFemtoCell has 704BEc1234AB as board ID, then the root password will be pdmk-1234AB (case sensitive).
        ```
#### Firmware upgrade
1. Prepare a USB key with the following files:
    * `liveburner_X.X.X_klk-wifc-signed.ipk` (Liveburner firmware): Can be found [Here]( http://wikikerlink.fr/wirnet-ifemtocell/doku.php?id=wirnet-ifemtocell:resources)
    * `usb.autorun` [Here](usb.autorun)
    * `usbkey.txt` [Here](usbkey.txt)
2. Plug the USB key on the iFemtoCell, the power LED is lit solid red.
3. Wait for the power LED fast blinking from green to red.
4. Unplug the USB key.
5. Wait for CPU reboot (Power LED is lit solid green).

#### Connect to The Things Network
1. Prepare a USB key with the following files:
    * `spf_3.1.0-klk18_4.1.3-klk11_klk_wifc.ipk` [Semtech Packet Forwarder v3.1.0-klk18]( http://wikikerlink.fr/wirnet-ifemtocell/doku.php?id=wirnet-ifemtocell:resources)
    * `usb.autorun` [Here](usb.autorun)
    * `usbkey.txt` [Here](usbkey.txt)
2. Plug the USB key on the iFemtoCell, the power LED is lit solid red.
3. Wait for the power LED fast blinking from green to red.
4. Unplug the USB key.
5. Wait for CPU reboot (Power LED is lit solid green).
6. Connect to the gateway using `SSH connection`.
7. Open the file: `/user/spf/etc/global_conf.json` Fill in the details below. Check this link for the right server_address. The UDP ports 1700 are used, both for outgoing and incoming traffic. You can set this UDP port in the lines serv_port_up and serv_port_down. (In some cases, firewalls block these UDP ports. Please contact your network administrator if you’re in doubt).
    ```
    "gateway_conf": {
    "server_address": "router.eu.thethings.network",
    "serv_port_up": 1700,                                               
    "serv_port_down": 1700,
    ```
8. Register the gateway in the [Developer Console](https://console.thethingsnetwork.org/). You can find more information on how to register your gateway in the Console [here](https://www.thethingsnetwork.org/docs/gateways/registration.html).
9. How to find the Gateway EUI: Open the file on your gateway `/user/spf/etc/local_conf.json`.

#### References
1. [The Things network](https://www.thethingsnetwork.org/docs/gateways/kerlink-ifemtocell/)
2. [Wirnet wiki](http://wikikerlink.fr/)
