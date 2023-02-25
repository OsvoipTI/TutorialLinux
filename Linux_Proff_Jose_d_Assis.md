Linux - Professor de Assis


Reset senha root - Debian

ro quiet alterar para rw init=/bin/bash 

passwd


-h = halt

shutdown -h 2  ( desligar em 2 minutos)

Crtl + C = cancela shit

Mkdir -p 
 
SYSTEM D

systemd-analyze - tempo carregamento do sistema
systend-analyze blame - lista carragamento de todos os serviços do sistema

hostnamectl

systemctl - status de todos os serviços ativos no sistema

systemctl status ssh.service = verifica o status do serviço
systemctl start ssh.service = verifica o status do serviço
systemctl stop ssh.service = verifica o status do serviço
systemctl restart ssh.service = verifica o status do serviço

systemctl is-enable ssh.service = ativa service na inicialização do sistema 

systemctl disable ssh.service = desativa service na inicialização do sistema


NETWORK

Nomeclatura do rede Debian

enp1s0


lspci
01:00.0 Ethernet controller: Red Hat, Inc. Virtio network device (rev 01) ==  enp1s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP 
07:00.0 Ethernet controller: Red Hat, Inc. Virtio network device (rev 01) ==  enp7s0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN



ifdown - derruba interface
ifup - sob interface e carrega ip 


Moutar unidade remota (PenDrive)

fdisk 
vFat - nao precisa de parametro , monta direto  = mount /dev/sdx /media
NTFS - precisa de parametro para montar == apt install ntfs-3g == mount ntfs-3g /dev/sdx /media



LVM









