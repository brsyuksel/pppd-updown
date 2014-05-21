# updown

manage routines of pptp connections.

## usage

**all operations requires root privileges**

first, you must set unique ipparam for each peer files in `/etc/ppp/peers`
peer files must be look like: ( eg, `/etc/ppp/peers/myvpnprovider` )

	pty "pptp PROVIDER_ID_OR_DOMAIN --nolaunchpppd"
	[...]
	ipparam myfavprovider

download updown script in /etc/ppp directory

remove if there any ip-up or ip-down script, *don't forget get backups*

make ip-up and ip-down links via updown: `/etc/ppp/updown link`

create a configuration file for ipparam: `/etc/ppp/updown template myfavprovider`

updown create a file named updown.myfavprovider in /etc/ppp/ and it will open this file
in your editor. edit start and stop functions for connection's routines ( adding or deleting 
route entries, setting nameservers, logging etc. )

now, you can connect your provider via pppd: `pppd call myvpnprovider`