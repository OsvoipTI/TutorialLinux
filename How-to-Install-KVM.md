Como instalar o hipervisor KVM no Debian 11|10

Neste guia, aprenderemos como instalar o servidor KVM Hypervisor Virtualization no Debian 11|10. KVM (Kernel-based Virtual Machine) é uma solução de virtualização completa de código aberto para sistemas Linux rodando em hardware x86 com extensões de virtualização (Intel VT ou AMD-V).

O KVM requer que você tenha a CPU em seu computador que tenha uma função Intel VT ou AMD-V. O KVM consiste em um módulo de kernel carregável, kvm.koque fornece a infraestrutura de virtualização principal e um módulo específico do processador, kvm-intel.ko ou kvm-amd.ko.

Instalar KVM/QEMU no Debian 11|10

Siga as etapas abaixo para instalar a virtualização KVM no sistema Debian 11|10 Linux. Todos os pacotes KVM para Debian estão disponíveis em repositórios upstream. O gerenciador de pacotes apt é usado para a instalação de todos os pacotes.


#sudo apt -y install qemu-kvm libvirt-daemon  bridge-utils virtinst libvirt-daemon-system

Carregue e habilite o módulo vhost_net .

#$ sudo modprobe vhost_net 
#$ lsmod | grep vhost
#vhost_net              24576  0
#tun                    49152  1 vhost_net
#vhost                  49152  1 vhost_net
#tap                    28672  1 vhost_net

#$ echo vhost_net | sudo tee -a /etc/modules 

Vamos também instalar ferramentas úteis de gerenciamento de máquinas virtuais.

#sudo apt -y install virt-top libguestfs-tools libosinfo-bin  qemu-system virt-manager

Isso fornecerá ferramentas semelhantes ao comando ls, cat, top do Linux para uso com máquinas virtuais.

Criar ponte KVM no Debian (opcional)

Para que suas máquinas virtuais se comuniquem com o mundo exterior, é necessária uma ponte Linux. A instalação do KVM no Debian 11|10 cria uma ponte Linux chamada virbr0 . Isso pode ser usado para todos os ambientes de teste.

Mas se você quiser que suas VMs sejam acessíveis pela rede, você precisará criar uma ponte na interface de rede física conectada à sua máquina.

Crie um em seu servidor/estação de trabalho Debian como abaixo.

sudo nano /etc/network/interfaces

Minha configuração de ponte usa uma interface de rede ( ens33 ) para criar uma ponte Linux chamada br1 . Substitua os valores fornecidos pelos seus.

# Primary network interface
auto ens33
iface ens3 inet manual

# Bridge definitions
auto br1
iface br1 inet static
bridge_ports ens33
bridge_stp off
address 172.16.54.149
network 172.16.54.0
netmask 255.255.255.0
broadcast 172.16.54.255
gateway 172.16.54.2
dns-nameservers 172.16.54.2
Reinicie sua máquina para que as alterações na configuração de rede entrem em vigor.

sudo reboot
Confirme os detalhes da rede IP.


$ ip addr
