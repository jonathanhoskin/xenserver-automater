## Create a new VM with custom xenstore data:
	UUID=`xe vm-install template=mytemplate  new-name-label=newvm`
	xe vm-param-set uuid=$UUID xenstore-data:vm-data/ip=192.168.1.20
	xe vm-param-set uuid=$UUID xenstore-data:vm-data/gw=192.168.1.254
	xe vm-param-set uuid=$UUID xenstore-data:vm-data/nm=255.255.255.0


## Install files on guest VM:

Copy xe-set-* into /usr/sbin/ and chmod +x


## Modify networking script
Edit /etc/init.d/networking:

* BEFORE:
			start)
        		/lib/init/upstart-job networking start
        		;;
* AFTER:
				start)
        		/usr/sbin/xe-set-network
        		/usr/sbin/xe-set-hostname
        		/lib/init/upstart-job networking start
        		;;
