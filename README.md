# Configuração Básica do Ambiente Live para Instalação do Arch

## Pré-instalação
1. Alterar o layout para ABNT2: loadkeys br-abnt2 
2. Alterar a localização do ambiente live: vim /etc/locale.gen (descomentar linha PTBR-UTF8) e dps export LANG=pt_BR.UTF-8
3. Verificar a conexão com a internet. ping google.com
4. Atualizar o timezone/fuso-horário do ambiente live. timedatectl set-timezone America/Sao_Paulo

## Particionamento
5. Fazer o esquema de partições com FDISK. fdisk o
6. Formatar as partições. mkfs.ext4 /dev/sda
7. Montar as partições. mount /dev/sda /mnt
8. Alterar o mirror. vim /etc/pacman.d/mirrorlist 
## Instalação
9. Baixar o kernel e o firmware base do Arch Linux. pacstrap -K /mnt base linux linux-firmware
10. Gerar o fstab. genfstab -U /mnt >> /mnt/etc/fstab
11. Fazer o chroot para o diretório /mnt. arch-chroot /mnt
12. Alterar o fuso horário do Arch Linux. ln -sf /usr/share/zoneinfo/America/Sao_Paulo /etc/localtime hwclock --systohc
13. Alterar a localização do Arch Linux. vim /etc/locale.gen (descomentar linha PTBR-UTF8) e dps export LANG=pt_BR.UTF-
14. Fixar o layout do Arch Linux. KEYMAP=br-abnt2

## Pós-instalação
15. Configurar o hostname da rede.
16. Configurar o IP local no arquivo /etc/hosts.
17. Criar senha para o usuário root ou criar outros usuários.

Links úteis:
- [Fórum do Arch Linux - Configuração do Layout ABNT2](https://bbs.archlinux.org/viewtopic.php?id=225407)
- [Vídeo Tutorial no YouTube - Instalação do Arch Linux](https://youtu.be/4orYC5ARfn8?si=InYiFS8E6tPLKyfn)
- [Guia de Instalação do Arch Linux (em Português)](https://wiki.archlinux.org/title/Installation_guide_(Portugu%C3%AAs)#Chroot)
