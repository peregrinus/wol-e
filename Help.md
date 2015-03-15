#WOL-E commands
# WOL-E Syntax #

## Waking up single computers ##
To wake up a single computer use the following command:
  * ./wol-e.py -m 00:12:34:56:78:90 -b 192.168.1.255 -p 9

If you do not specify a broadcast address or port wol-e will set the following as defaults for you:

  * Port: 9
  * Broadcast: 255.255.255.255

If a password is required use the -k 00:12:34:56:78:90 at the end of the above command.

## Sniffing the network for WOL requests and passwords ##
To sniff the network for WOL traffic use the following command:

  * ./wol-e.py -s -i eth0

All captured WOL requests will be displayed on screen and written to  WOLClients.txt in the scripts current working directory, this includes passwords if the SecureOn feature is in use.

## Bruteforce powering on WOL clients ##
To bruteforce the network use the following command:

  * ./wol-e.py -a

Place the address ranges into the bfmac.lst that you wish to bruteforce. They should be in the following format:
  * 00:12:34:56

If you do not specify a broadcast address or port wol-e will set the following as defaults for you:

  * Port: 9

If you wish to bruteforce a different port use the -p PORT at the end of the above command. The script will then send the requests for the 65,025 MAC addresses in that range to be enabled.

## Detecting Apple devices on the network for WOL enabling ##
If you want to scan the network for Apple devices on your subnet use the following command:

  * ./wol-e.py -f

This will output to the screen and write to AppleTargets`.`txt any Apple MAC address that are detected, this includes non laptop and workstation devices so not all of the detected addresses are suitable for WOL.


## Attempt to wake all detected Apple targets in `AppleTargets.txt` ##
If you want to attempt to wake all targets found from using -f use the following command:
  * wol-e.py -fa

This will send a single WOL packet to each client in the list and tell you how many clients were attempted.