Como instalar o Terraform em sistemas Linux
PorJosphat Mutai-19 de janeiro de 2023228670
Este guia o guiará pelas etapas para instalar o Terraform no sistema Ubuntu / Debian / CentOS / Fedora / Arch Linux. O Terraform é uma ferramenta de automação de infraestrutura independente da nuvem usada para gerenciar recursos locais e na nuvem. Com ele, você pode criar, alterar e versão da infraestrutura implantada em provedores de serviços populares.

instalar terraform fedora 29 fedora 28
Antes de baixar o terraform, precisamos instalar as ferramentas wget e curl

- Debian / Ubuntu systems
#sudo apt update
#sudo apt install wget curl unzip

- RHEL based systems
#sudo yum install curl wget unzip

Como instalar o Terraform no Linux
O Terraform é distribuído como um tarball no Github. Verifique a versão mais recente na  página de versões do Terraform  antes de fazer o download abaixo.


# TER_VER=`curl -s https://api.github.com/repos/hashicorp/terraform/releases/latest | grep tag_name | cut -d: -f2 | tr -d \"\,\v | awk '{$1=$1};1'`
#wget https://releases.hashicorp.com/terraform/${TER_VER}/terraform_${TER_VER}_linux_amd64.zip

Após o download do arquivo, extraia e mova o arquivo binário terraform para o diretório /usr/local/bin .

$ unzip terraform_${TER_VER}_linux_amd64.zip
Archive:  terraform_xxx_linux_amd64.zip
 inflating: terraform

$ sudo mv terraform /usr/local/bin/
Isso tornará a ferramenta acessível a todas as contas de usuário.

$ which terraform
/usr/local/bin/terraform
Verifique a versão do Terraform instalada


$ terraform --version
Terraform v1.3.7
on linux_amd64
Para atualizar o Terraform no Linux, baixe a versão mais recente e use o mesmo processo para extrair e mover o arquivo binário para o local em seu PATH .


