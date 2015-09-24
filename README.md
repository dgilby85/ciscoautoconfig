# ciscoautoconfig

So it has been a few weeks since I started learning Python and wanted to share my first program. I am sure it is not 100% coded correctly or most efficiently, but it works and I use it everyday!!!

Let me explain the problem (which every network admin will relate to). We have a very large infrastructure, < 1500 routers and switches, and a lot of smaller 8 port switches and access points that move around. Not too many of the AP's move around, but our 8 porters, move all the time. And being the great Network Engineers that we are, we have configurations that have port security enabled, which doesn't make the switches very friendly to changes in port configurations based on type of device.

In my environment, we have Cisco devices of all ages and IOS versions, and writing EEM scripts only helps newer devices, so what about the older devices? The program I created was to help network administration in large scale networks. It makes searching through large sets of switches and applying changes a lot less tedious.

The program does a few things:

  Retrieves a list of IP addresses

  Prompts for SSH credentials

  Auto SSH's to devices in the list one at a time

  Downloads and parses 'sh cdp neighbor detail' and 'sh interface status' into dictionary's

  Then, in the menu, there are views for certain criteria:

1.     Show error disabled ports

2.     Show devices in CDP neighbor but not trunked or AP's not in AP vlan based on CDP model

3.     Show connected interfaces that are configured for trunk or AP's but have no CDP neighbor

  Then, a separate menu for changing interface configurations:

1.     Auto default and reconfigure port to either access, trunk, or AP depending on CDP model

2.     Auto default and reconfigure ports who are connected and configured for trunk or AP that have no CDP
     
3.     Auto default error disabled ports
    
4.     Manually configure port


The program is written in Python 2.7 and uses Paramiko to handle SSH connections. I use it on my Linux machine, but am working on porting it to windows.

Being that this is my first Python program, I'd really appreciate feedback on the code, thanks. 





	usage: autocisco.py [-h] -f HOSTS [-a ACCESS] [-w WIRELESS] [-v VOICE]

	An awesome Python Program to search through switches and auto configure ports
	based on CDP via SSH.

	optional arguments:

	  -h, --help            show this help message and exit
  
	  -f HOSTS, --hosts HOSTS Specify a hosts file
	
	  -a ACCESS, --access ACCESS  Enter Access Vlan Value -- (default = 1)
 
	  -w WIRELESS, --wireless WIRELESS  Enter Wireless Vlan Value -- (default = 1)
 
	  -v VOICE, --voice VOICE Enter Voice Vlan Value -- (default = 1)
