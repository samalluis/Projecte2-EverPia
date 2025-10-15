# Seguretat Lògica: recuperant accés a sistemes
---

## Pas 1: Creació de la maquina virtual 

Per a aquesta maquina haurem de ficar una memoria base de **8 GB i 2 processadors**, i no ficar cap disc ja que utilitzarem un disc amb una iso ja creada. Ara anirem a la opció de **"Hard disk"**
habilitat la opció de **"Use an existing virtual hard disk file"** i seleccionarem el disc amb la iso, i ja ho tindriem llest per arrancar la maquina.

---

## Pas 2: Canvi de contrasenya amb GRUB

Al entrar a la maquina trobarem que no sabem la contrasenya a si que tindrem que canviar-la, per poder fer aixo necesitarem entrar al grub, i per entrar al grub el primer que farem sera reiniciar la maquina mentres prement la tecla escape d'aquesta manera entrarem al grub i un cop a dins del grub utilitzarem les seguents comandes per poder entrar en modo root:

**1 - linux /boot/vmlinuz-6.8.0-52-generic root=/dev/sda3 rw init=/bin/bash**

**2 - initrd /boot/initrd.img-6.8.0-52-generic**

**3 - boot**

despres de fer servir aquestas comendes ja estarem en mode root, un cop a dins nomes tindrem que fer un "passwd miquel" i ja podrem canviar la contraseña.

Quant ja tinguem la contrasenya canviada reiniciarem la maquina i introduirem la contrasenya nova per poder entrar al usuari, i un cop a dins començem amb la protecció del GRUB.

---

## Pas 3: Proteccio del GRUB basica

Ara començem amb la proteccio basica del GRUB, primer crearem una contrasenya per el GRUB, pero visualment estara encripatada, pero poder fer aixo utilitzarem la comanda **"grub-mkpasswd-pbkdf2"** un cop utilitzada ens demanara una contrasenya i que la repitem, i ens donara la contrasenya encriptada en hash.

Aquest hash el copiarem, i seguidament entrarem al ficher **"sudo nano /etc/grub.d/40_custom"** un cop a dins baixarem al final i introduirem les seguents lineas de text:
set superusers="root"
password_pbkdf2 root (enganchar el hash anteriorment copiat)


Un cop fet tot aixo guardem els canvis amb **"control + o" "enter" "control + x"**, i un cop fora guardarem tots el canvis del que hem fet al GRUB amb la comanda **"sudo update-grub"**.

I amb aixo ja tindriam la proteccio basica del GRUB, fent que quant reinicias la maquina, sempre et demani el root + contrasenya, tan com per poder entrar al GRUB, com per una arrencada de sistema normal, aquest ultim pot arribar ser un inconvenient ja que aixo pot ser que no l'hi agradi al client.

---

## Pas 4: Proteccio avançada del GRUB 

Un cop tenim la protecció bàsica del GRUB configurada, el següent pas és fer que el sistema pugui arrencar normalment sense demanar contrasenya, però que només es necessiti usuari i contrasenya per editar o accedir a opcions avançades del GRUB.

Primer, obrirem el fitxer /etc/grub.d/10_linux, que és el responsable de generar les entrades del menú del GRUB.

Ens desplacem pel fitxer (és llarg, té més de 400 línies) fins trobar les següents línies:

Aquestas lineas les podem trobar facilment fent un **control + w**, aquesta combinació et obrira un cercador de paraules, i nomes introduint la paraula **menuentry** ens portara directament on volem arribar.

A cada una de les dues línies anteriors, ens situem després del paràmetre ${CLASS} i afegim la comanda **"--unrestricted"**:

D’aquesta manera indiquem que aquestes entrades es poden executar sense contrasenya, però que la resta d’opcions del GRUB (com editar, accedir a la línia de comandes o veure altres kernels) continuaran protegides.
Després de fer els canvis, guardem el fitxer amb **control + o, enter, control + x**
I regenerem la configuració del GRUB amb un **sudo update-grub**:

Finalment, reiniciem la màquina perquè s’apliquin els canvis.

### Resultat final
El sistema arrenca automàticament sense demanar contrasenya.
Si intentes editar les opcions del GRUB, accedir a la consola o veure els modes avançats, et demanarà usuari i contrasenya.
Això ofereix una protecció equilibrada, ja que evita modificacions no autoritzades al GRUB però no incomoda l’usuari en l’arrencada normal.


## Explicacio de les comandes

---

### 1. linux /boot/vmlinuz-6.8.0-52-generic root=/dev/sda3 rw init=/bin/bash

Aquesta línia carrega el nucli (kernel) de Linux i li passa paràmetres d’arrencada.

**Desglossant-la:**
- linux → indica al GRUB que carregui un nucli Linux.
- /boot/vmlinuz-6.8.0-52-generic → és el fitxer del nucli (kernel) que vols arrencar.
- root=/dev/sda3 → especifica quin dispositiu serà la partició arrel (/) del sistema.
- rw → munta el sistema de fitxers arrel en mode lectura-escriptura (read-write).

init=/bin/bash → substitueix el procés d’inici normal (/sbin/init o systemd) per una shell Bash.
Això és útil per entrar al sistema manualment, per exemple per canviar contrasenyes o reparar fitxers.

**En resum:**
Carrega el nucli i li diu que la partició arrel és /dev/sda3, que s’ha de muntar en mode lectura-escriptura i que s’ha d’iniciar amb una shell Bash en lloc del procés d’inici normal.

### 2. initrd /boot/initrd.img-6.8.0-52-generic

Aquesta comanda carrega la imatge de disc RAM inicial (initrd = initial RAM disk).

**Funció:**
Conté mòduls del nucli i scripts d’inici necessaris per muntar el sistema arrel (per exemple, controladors de disc, sistemes de fitxers, etc.).
És essencial perquè el sistema pugui accedir al disc i carregar completament Linux.

**En resum:**
Carrega al GRUB la imatge initrd, que és un petit sistema de fitxers temporal que ajuda el nucli a arrencar.

### 3. boot

Aquesta és la comanda que inicia efectivament l’arrencada després d’haver carregat el nucli i l’initrd.

Funció:
Diu al GRUB que transfereixi el control al nucli que acabes de carregar amb les comandes anteriors.
Fins que no executes boot, el sistema no comença realment a arrencar.

En resum:
Inicia el procés d’arrencada amb el nucli i paràmetres que s’han carregat.






