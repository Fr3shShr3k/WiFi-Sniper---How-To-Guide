# WiFi Sniper User Manual

## 📡Operating Kismet
Simply run 'kismet' in the terminal, and it will open a web service running on localhost:2501 (Default Port) which you will connect to over your internet browser. 

![Kismetbooting](https://github.com/Fr3shShr3k/WiFi-Sniper---How-To-Guide/blob/a48cf164314de786ce7eba169534978943e02264/assets/images/Screenshot%20from%202025-04-14%2003-25-03.png)

We should now start seeing Wifi networks start coming in and being scanned on Kismet. 

![Kismet](https://github.com/Fr3shShr3k/WiFi-Sniper---How-To-Guide/blob/067698dfd94a6468a4c0c868cc97c4650e7266da/assets/images/Screenshot%20from%202025-04-14%2003-26-41.png)

If you exit kismet, all networks found are saved to a csv in the users home directory under example file names: Kismet-2025-04-13-13-42-05/
Kismet has other abilities such as the ability to sniff packets and act as an IDS which can detect whether there are other active network sniffing programs on the same connected network, which it can
save the packet data into a .pcap. 
