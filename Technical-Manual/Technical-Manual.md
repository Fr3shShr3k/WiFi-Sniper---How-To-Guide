# WiFi Sniper Technical Manual 


## Bill of Materials
+ 1/4 8ft Lumber - $3
+ Tupavco TP513 Yagi WiFi Antenna - $38
+ ALFA AWUS036ACH - $59
+ N Type Male to RP-SMA Male Adapter - $3
+ Rasberry Pi 5
+ UUQ 3-9x40 Rifle Scope - $30
+ 17 Slot MLock Adluminum Picatinny Rails - $15
+ Velcro Tape 

In order to cut out the wooden stock an electric saw is required as well as a polishing sandpaper tool (for a smoother finished product). 

## Technical Diagram

![Diagram](https://github.com/Fr3shShr3k/WiFi-Sniper---How-To-Guide/blob/1f50a49ccd2e0ca56c4c5e3fd2158f88cb9bfdbb/assets/images/WifiSniperDiagram.drawio%20(1).png)
## Directional Antenna 
### Tupavco TP513 Yagi Wireless Antenna
![Yagi](https://github.com/Fr3shShr3k/WiFi-Sniper---How-To-Guide/blob/ebd481694265777bed3a50f01a09e7634009a165/assets/images/TupavcoYagi.jpg)

Although not the highest quality Yagi antenna, it gets the job done for long-distance scanning of WiFi networks. The antenna is rated for 2.4GHz at 17dBi and uses a RP-SMA male connector, meaning that an adapter is neaded in order to plug the antenna into the ALFA wireless adapter card. 


## Single-Board Computer (SBC) 
### Raspberry Pi 5
![Pi5](https://github.com/Fr3shShr3k/WiFi-Sniper---How-To-Guide/blob/9f59b038df7b430eb68764c86c08dc3283c858b5/assets/images/Pi5.jpg)

Using a Pi5 provides some of the best hardware availalbe for a SBC at the time of writing this on top of support for WiFi 802.11ac, Bluetooth 5.0, and BLE. Theoretically the Yagi antenna would be able to transieve data over Bluetooth at 2.4GHz as well as it can over WiFi. 
## Assembly 

### Creating Stock
First, you want to start with making a stock that will hold all of the components the WiFi sniper will use. Although not completely necessary to have a functioning system, the coolness factor of having a "gun" that you can hold and point at where you want to scan WiFi networks as well as the looks you get from people more than makes it worth it. 


I recommend basing the design of the stock off a prexisting gun stock and tracing out the outline on the 1x4 of where you want to cut out/shape. (I traced out an airsoft AK47 I happened to have and it ended up working great).

![StockDesign](https://github.com/Fr3shShr3k/WiFi-Sniper---How-To-Guide/blob/ace5553f0f41e2b0164581cd79f412cfcd706c30/assets/images/AkStockDesign.jpg)

Also important not to forget to plan out where you want to place all the components. I ended up attaching a laser sight I also happened to have laying around because why not.  

![PlanningComponentPlacement](https://github.com/Fr3shShr3k/WiFi-Sniper---How-To-Guide/blob/1f409d3b568f9adaa2a256e2a30852c40965386a/assets/images/WifiSniper_Components.jpg)
### Attaching components
Now we move onto mounting components, this part is pretty straight-forward as all we need to do is screw the yagi antenna onto the end of the stock we made and secure it with the washers and screws that came with the antenna. I recommend using velcro tape to hold the Alfa Card and Pi 5 this way they can be detatched at convienence. Also be sure to use the N Type to RP-SMA adapter to connect the ALFA card and Yagi. I ended up drilling a small hole into part of the end of the Yagi so that I could attach a ziptie to hold down the coax cable. 

![ZiptieholdingCable](https://github.com/Fr3shShr3k/WiFi-Sniper---How-To-Guide/blob/64c0674c36f1408faa104cc21f8c53182b26df36/assets/images/20250414_004224.jpg)

We also mount the picatinny railing on the top of the stock in order to attach the scope, again not necessary but for aesthetics. I picked up a cheap camera stand from a thrift store as well which ended up being a nice stand for the Wifi Sniper. This is what the finished product should look like after assembly. The Pi5 has been mounted on the other side of the rifle not shown.

![WifiRifleComplete](https://github.com/Fr3shShr3k/WiFi-Sniper---How-To-Guide/blob/e1d926227065981ccc4211b678de5f6d185f1799/assets/images/finishedprod.jpg)

## Configuring Pi 5 
After you install any debian based distro onto the Pi 5, we need to make sure that we install the necessary driver for the Alfa card in order for it to function with linux. When I had set this up originally, Ubuntu did not detect the card as a USB device which pointed to me that I needed to install the right drivers. (You can find this out using lsusb). After git cloning the drivers for our model of Alfa card from https://github.com/aircrack-ng/rtl8812au/, cd into the rtl8812au directory and make the dkms_install file. Then restart the network manager and reboot the device. After this, check and see if the Alfa card is properly being detected now using modprobe or lsusb commands and you should see the device pop up. The last step in this is to disable the onboard Broadcom wireless card already on the Pi so that only the wireless interface for the Alfa card is used when we run Kismet. We can disable this by blacklisting the broadcom drivers in /etc/modprobe.d/blacklist.conf then rebooting 1 last time. 

![AlfaCardUSB](https://github.com/Fr3shShr3k/WiFi-Sniper---How-To-Guide/blob/6395bd523949ac6c75fc8dd7f47c69ed1959b08a/assets/images/Screenshot%20from%202025-04-14%2002-38-53.png)

![AlfaCardIfconfig]()

Note*** From research and testing I've done, the onboard Broadcom wireless chipset on Rasperry Pi's are not compatible to run with the Airmon suite of network recon tools however works with Kismet just fine. 
Installing Kismet is also straight forward, simply clone the repo off https://www.kismetwireless.net/git/kismet.git and compile it. I followed along with the installation instructions on Kismet's official documentation here: https://www.kismetwireless.net/docs/readme/installing/linux/

Congratulations! Your Pi should now be set up to start scanning! 
