# DRBL nel Laboratorio sistemi



todo:

come root
 addgroup nis-users
 
 aggiungi tutti gli utenti nel gruppo
 
 visudo 
 
 aggiungi la riga:
 
 %nis-users ALL=NOPASSWD: /usr/lib/yp/ypinit -m
 
 
 nano /etc/bash.bashrc
 
 aggiungi in fondo:
 
 PATH=$PATH:/opt/tool-lab
 export PATH
  
