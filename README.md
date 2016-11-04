# DRBL nel Laboratorio sistemi



todo:

come root
 addgroup nis-users
 
 aggiungi tutti gli utenti nel gruppo
 
 visudo 
 
 aggiungi la riga:
 
 %nis-users ALL=NOPASSWD: /usr/lib/yp/ypinit -m
 
 
 edit /etc/profile
 
 aggiungi:
 
 PATH=$PATH:/opt/tool-lab
 
 export PATH
  
