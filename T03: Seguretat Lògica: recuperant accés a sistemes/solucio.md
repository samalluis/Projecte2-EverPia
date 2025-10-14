# Seguretat Lògica: recuperant accés a sistemes
---

## Pas 1: Creació de la maquina virtual 

Per a aquesta maquina haurem de ficar una memoria base de **8 GB i 2 processadors**, i no ficar cap disc ja que utilitzarem un disc amb una iso ja creada. Ara anirem a la opció de **"Hard disk"**
habilitat la opció de **"Use an existing virtual hard disk file"** i seleccionarem el disc amb la iso, i ja ho tindriem llest per arrancar la maquina.

---

## Pas 2: Canvi de contrasenya amb GRUB

Al entrar a la maquina trobarem que no sabem la contrasenya a si que tindrem que canviar-la, per poder fer aixo necesitarem entrar al grub, i per entrar al grub el primer que farem sera reiniciar la maquina mentres prement la tecla escape d'aquesta manera entrarem al grub i un cop a dins del grub utilitzarem les seguents comandes per poder entrar en modo root:

1 - set root=(hd0,gpt3)
2 - linux /boot/vmlinuz-6.8.0-52-generic root=/dev/sda3 rw init=/bin/bash
3 - initrd /boot/initrd.img-6.8.0-52-generic
4 - boot

despres de fer servir aquestas comendes ja estarem en mode root, un cop a dins nomes tindrem que fer un "passwd miquel" i ja podrem canviar la contraseña.

Quant ja tinguem la contrasenya canviada reiniciarem la maquina i introduirem la contrasenya nova per poder entrar al usuari, i un cop a dins començem amb la protecció del GRUB.

---

## Pas 3: Proteccio del GRUB basica

Ara començem amb la proteccio basica del GRUB, primer crearem una contrasenya per el GRUB, pero visualment estara encripatada, pero poder fer aixo utilitzarem la comanda **"grub-mkpasswd-pbkdf2"** un cop utilitzada ens demanara una contrasenya i que la repitem, i ens donara la contrasenya encriptada en hash, aquest hash el copiarem, i seguidament entrarem al ficher **"sudo nano /etc/grub.d/40_custom"** un cop a dins baixarem al final i introduirem les seguents lineas de text:

set superusers="root"
password_pbkdf2 root (enganchar el hash anteriorment copiat)

Un cop fet tot aixo guardem els canvis amb **"control + o" "enter" "control + x"**
i un cop fora guardarem tots el canvis del que hem fet al GRUB amb la comanda **"sudo update-grub"**, i amb aixo ja tindriam la proteccio basica del GRUB, fent que quant reinicias la maquina, sempre et demani el root + contrasenya, tan com per poder entrar al GRUB, com per una arrencada de sistema normal, aquest ultim pot arribar ser un inconvenient ja que aixo pot ser que no l'hi agradi al client.

---

## Pas 4: Proteccio avançada del GRUB (password nomes si no es la arrancada normal)






