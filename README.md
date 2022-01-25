Akshat0404/MAC_CHANGER


This tool has to be used on linux kernel.

Steps to use the tool:

  1.     git clone https://github.com/Akshat0404/MAC_CHANGER.git

  2. Now open the MAC_CHANGER file.

  3.     ./MAC_CHANGER

  4. Now look for a python file named mac_changer.py in MAC_CHANGER directory using ls command.

  5. Now run the mac_changer.py using the command;
 
          python3 mac_changer.py -h
          
          python3 mac_changer.py --help
          
  7. The -h or --help will list out the following arguments that can be used using this tool:
      
          Usage: mac_changer.py [options]

             Options:

             -h, --help            show this help message and exit

             -n NETWORK_INTERFACE, --network_interface=NETWORK_INTERFACE
                                    Name of the network interface of which the MAC address
                                    has to be changed

             -c NEW_MAC, --new_mac=NEW_MAC
                                   New MAC address
    
  7. Now in the next few commands, we will see how this tool works.

  8.   Here we use -n or --network_interface to specify the network interface to which we wanna change the MAC address.

       -c or --new_mac is used to specify the new mac address.
       
       Below is a demo command;
       
            python3 mac_changer.py -n eth0 -c 00:a4:45:56:f2:6b;
  
  9. By running this command the mac address of the network interface eth0 changes to the mac address we want i.e. 00:a4:45:56:f2:6b and the following message will appear after        the successful execution of the command;
       
          [+] MAC address of eth0 has been changed to 00:a4:45:56:f2:6b.
       
      The same implies for the network interface wlan0.
  10. Now if we run the ifconfig command, we can see that the MAC address has been changed to 00:a4:45:56:f2:6b;
      
         ifconfig

              eth0: flags=xxxx<UP,BROADCAST,RUNNING,MULTICAST>  mtu xxxx

                  inet xx.x.x.xx  netmask xxx.xxx.xxx.x  broadcast xx.x.x.xxx

                  ether 00:a4:45:56:f2:6b  txqueuelen xxxx  (Ethernet)

                  RX packets xx  bytes 46960 (45.8 KiB)

                  RX errors 0  dropped 0  overruns 0  frame 0

                  TX packets xx  bytes 10412 (10.1 KiB)

                  TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


              lo: flags=xx<UP,LOOPBACK,RUNNING>  mtu xxxxx

                  inet xxx.x.x.x  netmask xxx.x.x.x

                  inet6 ::x  prefixlen xxx  scopeid 0x10<host>

                  loop  txqueuelen xxxx  (Local Loopback)

                  RX packets x  bytes 400 (400.0 B)

                  RX errors 0  dropped 0  overruns 0  frame 0

                  TX packets 8  bytes 400 (400.0 B)

                  TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
          
  
      PS: I have denoted some sensitive information with x.
      
  11. We all know that lo network interface doesn't need a MAC address;
     
           python3 mac_changer.py -n lo -c 00:11:22:33:44:55
      
      So if we mention in the network interface argument, the following error appears
      
           Usage: mac_changer.py [options]

           mac_changer.py: error: [-] This network interface does not have MAC address
         
  12. We know that wlan0, lo and eth0 are the valid network interfaces among which only wlan0 and eth0 need a MAC address. So, if any other interface is mentioned other than           wlan0 and eth0, the following error message shows up;
     
           python3 mac_changer.py -n wlan -c 00:00:00:00:00:00
      
      In the above command I have specified wlan as network interface, which is not valid, lets see what the tool does after this command.
      
          Usage: mac_changer.py [options]

          mac_changer.py: error: [-] wlan is not a valid network interface. Please specify a valid network interface.
  
  13. We also know that MAC address is of the format xx:xx:xx:xx:xx:xx, where x is any number from 0-9, lower case alphabet from a-f or upper case alphabet from A-F.

          python3 mac_changer.py -n eth0 -c 00:29:4r:5h:Z2 
      
      As you can see the format of MAC address in the above command is wrong.
      
      So, if the incorrect format of MAC address is specified, an error message would show up;
      
          Usage: mac_changer.py [options]

          mac_changer.py: error: [-] You have specified an incorrect format for MAC address. Please Enter the MAC address in the format xx:xx:xx:xx:xx:xx, where x is lower case alphabets from a-f or upper case alphabets from A-F or numbers from 0-9.
          
          
I hope that this tool helps you.
Thanks😃
