## Create and start a new VM with custom xenstore data:
	UUID=`xe vm-install template=mytemplate  new-name-label=newvm`
	xe vm-param-set uuid=$UUID xenstore-data:vm-data/ip=192.168.1.20
	xe vm-param-set uuid=$UUID xenstore-data:vm-data/gw=192.168.1.254
	xe vm-param-set uuid=$UUID xenstore-data:vm-data/nm=255.255.255.0
	xe vm-start uuid=$UUID

## Install scripts on guest VM:

Copy usr/sbin/xe-set-* into /usr/sbin/ and chmod +x

## Install Upstart script on guest VM:

Copy etc/init/xe-automate.conf into /etc/init/

## Reboot