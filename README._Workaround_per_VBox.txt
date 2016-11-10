====================================================================================
step 1 VIRTUALBOX
====================================================================================

wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- |  apt-key add -

wget -q https://www.virtualbox.org/download/oracle_vbox.asc -O- | apt-key add -


deb http://download.virtualbox.org/virtualbox/debian jessie contrib

apt-get update

apt-get install virtualbox-5.1

apt-get install dkms

=================================================================================
step 2  

creo un servizio per "aggirare" drblsrv ...
riferimenti :
https://sourceforge.net/p/drbl/mailman/message/23305607/
https://sourceforge.net/p/drbl/mailman/message/23182310/
https://sourceforge.net/p/drbl/mailman/message/23182310/

per i servizi:
http://guide.debianizzati.org/index.php/Gestione_e_creazione_di_servizi_in_Debian
=================================================================================


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

=====================================================================================
step 3 
disinstalla drbl ...
=====================================================================================

drblsrv -u

=====================================================================================
step 4 
cambia password di root per "aggirare" il mancato funzionamento di drbl-client-root-passwd
=====================================================================================

passwd rootc

=====================================================================================
step 5 
aggiornare il s/o
=====================================================================================
controlla ..
nano /etc/apt/sources.list 

apt-get update
apt-get upgrade


=====================================================================================
step 6
DRBLSRV  insttlalazione drbl
=====================================================================================

wget -q http://drbl.org/GPG-KEY-DRBL -O- |  apt-key add -

deb http://free.nchc.org.tw/drbl-core drbl stable

apt-get update ; 


apt-get install drbl 

verifica ....
ls /usr/share/drbl/setup/files/DBN/

drblsrv -i



























