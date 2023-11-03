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
9. Baixar o kernel e o firmware base do Arch Linux. pacstrap -K /mnt base linux linux-firmware vim dhcpcd
10. Gerar o fstab. genfstab -U /mnt >> /mnt/etc/fstab
11. Fazer o chroot para o diretório /mnt. arch-chroot /mnt
12. Alterar o fuso horário do Arch Linux. ln -sf /usr/share/zoneinfo/America/Sao_Paulo /etc/localtime hwclock --systohc
13. Alterar a localização do Arch Linux. vim /etc/locale.gen (descomentar linha PTBR-UTF8) e dps export LANG=pt_BR.UTF-
14. locale-gen
15. echo KEYMAP=br-abnt2 >> /etc/vconsole.conf
16. Fixar o layout do Arch Linux. KEYMAP=br-abnt2

## Pós-instalação
15. Configurar o hostname da rede.
16. Configurar o IP local no arquivo /etc/hosts.
17. Criar senha para o usuário root ou criar outros usuários.
18. pacman -S grub efibootmgr
19. grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=arch_grub --recheck
20. grub-mkconfig -o /boot/grub/grub.cfg
21. systemctl enable dhcpcd
22. pacman -S  os-prober mtools network-manager network-manager-applet networkmanager wpa_supplicant wireless_tools dialog
23. useradd -m -g users -G wheel,storage,power -s /bin/bash nomedousuario
24. sudo usermod -aG sudo SEU_USUÁRIO ou  SEU_USUÁRIO ALL=(ALL:ALL) ALL no /etc/sudoers
25. COISAS IMPORTANTES A CONSIDERAR:
26. NO LINUX TUDO É UM ARQUIVO, INCLUSIVE UMA CONFIGURAÇÃO, ESSE ARQUIVO PODE SER ALTERADO DE MANEIRA AUTOMATIZADA ATRAVÉS DE UM COMANDO SEJA UM ECHO (QUE ACABA SENDO UAM EDIÇÃO MANUAL) OU UM COMANDO PROPRIO DO UTILITARIO/FERRAMENTA (QUE FAZ ESSA EDIÇÃO MANUAL PRA
27. VOCÊ) OU ATRAVÉS DA EDIÇÃO MANUAL DO ARQUIVO. EXEMPLO: sudo usermod -aG sudo SEU_USUÁRIO OU COM UM VIM /ETC/SUDOERS
28. hostnamectl set-hostname nomedoseuhost OU VIM /ETC/HOSTNAME
29. ln -sf /usr/share/zoneinfo/America/Sao_Paulo /etc/localtime OU timedatectl set-timezone America/Sao_Paulo



Links úteis:
- [Fórum do Arch Linux - Configuração do Layout ABNT2](https://bbs.archlinux.org/viewtopic.php?id=225407)
- [Vídeo Tutorial no YouTube - Instalação do Arch Linux](https://youtu.be/4orYC5ARfn8?si=InYiFS8E6tPLKyfn)
- [Guia de Instalação do Arch Linux (em Português)](https://wiki.archlinux.org/title/Installation_guide_(Portugu%C3%AAs)#Chroot)

Links úteis:
- [Fórum do Arch Linux - Configuração do Layout ABNT2](https://bbs.archlinux.org/viewtopic.php?id=225407)
- [Vídeo Tutorial no YouTube - Instalação do Arch Linux](https://youtu.be/4orYC5ARfn8?si=InYiFS8E6tPLKyfn)
- [Guia de Instalação do Arch Linux (em Português)](https://wiki.archlinux.org/title/Installation_guide_(Portugu%C3%AAs)#Chroot)
