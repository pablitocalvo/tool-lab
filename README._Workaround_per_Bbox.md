VIRTUALBOX

wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- |  apt-key add -

wget -q https://www.virtualbox.org/download/oracle_vbox.asc -O- | apt-key add -


deb http://download.virtualbox.org/virtualbox/debian jessie contrib

apt-get update

apt-get install virtualbox-5.1

apt-get install dkms


nano /etc/init.d/drblVBox
-----------------------------------------------------
#!/bin/bash
### BEGIN INIT INFO
# Provides:          drblVBox
# Required-Start:    
# Required-Stop:     
# Should-Start:      
# Should-Stop:       
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6 
# Short-Description: Attiva il caricamento di Vboxdrv (workaround drblcli)
# Description:       Attiva il caricamento di Vboxdrv (workaround drblcli)
### END INIT INFO

/sbin/modprobe vboxdrv
#to do : aggiungere condizione uscita
exit 0


------------------------------------
chmod +x /etc/init.d/drblVBox

systemctl enable drblVBox
