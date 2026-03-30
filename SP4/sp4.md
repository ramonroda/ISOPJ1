---
layout: custom
title: "Sprint 4: Configuració del Programari de Base i Sistemes d’Emmagatzematge en Ubuntu"
---

## Teoria RAID

### Què és un RAID?

El **RAID** (*Redundant Array of Independent Disks*) és una tecnologia que permet agrupar diversos discs físics en una única unitat lògica. L’objectiu principal és millorar el **rendiment**, garantir la **disponibilitat** del sistema i/o augmentar la **seguretat de les dades** mitjançant redundància. Des del punt de vista del sistema operatiu, tots els discs funcionen com si fossin un sol dispositiu.

### Avantatges principals del RAID

- **Tolerància a errors:** Alguns nivells permeten que un o més discs fallin sense perdre informació, gràcies a la redundància.
- **Alta disponibilitat:** El sistema pot continuar funcionant tot i la fallada d’un disc, reduint interrupcions.
- **Millor rendiment:** Certs tipus de RAID reparteixen les operacions entre diversos discs (*striping*), augmentant la velocitat.
- **Escalabilitat:** Es poden afegir discs per ampliar la capacitat o millorar la protecció.
- **Optimització de costos:** Permet aconseguir sistemes fiables utilitzant discs estàndard en lloc de solucions més cares.

### Tipus de RAID més habituals

| Nivell | Nom | Discos mínims | Descripció |
|--------|-----|---------------|------------|
| **RAID 0** | Striping | 2 | Divideix les dades entre diversos discs per augmentar el rendiment. No ofereix cap protecció: si falla un disc, es perden totes les dades. |
| **RAID 1** | Mirroring | 2 | Duplica la informació en tots els discs. Si un falla, es pot recuperar tot des de l’altre. La capacitat útil es redueix al 50%. |
| **RAID 5** | Striping amb paritat | 3 | Distribueix dades i paritat entre els discs. Permet recuperar la informació si falla un disc. Bona relació entre seguretat i rendiment. |
| **RAID 6** | Doble paritat | 4 | Similar al RAID 5, però pot suportar la fallada de dos discs simultanis. Major seguretat. |
| **RAID 10** | Mirroring + Striping | 4 | Combina RAID 1 i RAID 0. Ofereix alt rendiment i alta seguretat, però amb menor capacitat útil. |

### Configuracions combinades

- **RAID 0+1:** Primer es fa striping i després mirroring. Menys eficient davant fallades.
- **RAID 1+0 (RAID 10):** Primer mirroring i després striping. Més fiable i utilitzat.
- **RAID 50:** Combina diversos grups RAID 5 amb striping. Millora el rendiment.
- **RAID 60:** Combina RAID 6 amb striping. Ofereix gran seguretat i rendiment, però requereix molts discs.

### Volums lògics (LVM)

Els **volums lògics** (*Logical Volume Manager*) són un sistema que permet gestionar l’emmagatzematge de manera flexible, superant les limitacions de les particions tradicionals.

- **Volum físic (PV):** Disc o partició que forma part de LVM.
- **Grup de volums (VG):** Conjunt de volums físics que comparteixen espai.
- **Volum lògic (LV):** Espai assignat dins del grup, que es comporta com una partició.

Amb LVM es poden redimensionar volums, crear còpies instantànies (*snapshots*) i adaptar l’espai segons les necessitats. A més, es pot combinar amb RAID per obtenir alhora **flexibilitat i redundància**.

## Pràctica: RAID 1 amb mdadm a Ubuntu

En aquesta pràctica configurem un **RAID 1** (mirroring) entre dos discos virtuals de 2 GiB cadascun (`/dev/sdb` i `/dev/sdc`) fent servir l'eina `mdadm` a Ubuntu.

### Instal·lació de mdadm

`mdadm` és l'eina estàndard a Linux per gestionar arrays RAID per programari (*software RAID*). L'instal·lem amb `apt`:

<img width="827" height="518" alt="image" src="https://github.com/user-attachments/assets/6fa0414a-91c4-4744-8532-0362a14951af" />

El gestor de paquets descarrega i instal·la `mdadm` juntament amb la dependència `finalrd`. Confirma la instal·lació amb **S**.

---

### Explorar els discos disponibles

Comprovem amb `fdisk -l` que els dos discos virtuals (`/dev/sdb` i `/dev/sdc`) de 2 GiB estan disponibles i encara no estan particionats:

<img width="505" height="208" alt="image" src="https://github.com/user-attachments/assets/26d1ac07-cc33-42a5-b234-4314a1cc7d18" />

Els dos discos són idèntics: 2 GiB, model VBOX HARDDISK, sectors de 512 bytes. Cap dels dos té taula de particions.

---

### Crear la partició a /dev/sdb

Obrim `fdisk` per crear una partició primària que ocupi tot el disc `/dev/sdb`. Seleccionem **n** (nova partició), **p** (primària) i acceptem els valors per defecte per ocupar tot el disc. Finalment escrivim els canvis amb **w**:

<img width="829" height="541" alt="image" src="https://github.com/user-attachments/assets/5689efac-ab26-40bc-b755-37400adffd01" />


Es crea `/dev/sdb1` de tipus Linux que ocupa els 2 GiB del disc.

---

### Crear la partició a /dev/sdc

Repetim el mateix procés per al segon disc `/dev/sdc`. Creem una partició primària `/dev/sdc1` que ocupa tot el disc i escrivim els canvis:

<img width="810" height="539" alt="image" src="https://github.com/user-attachments/assets/a742b71a-bbf4-437e-bcee-dd63ad99f821" />


Ara els dos discos estan particionats i preparats per ser incorporats al RAID.

---

### Verificar les particions creades

Comprovem amb `fdisk -l` que les dues particions estan correctament creades:

<img width="548" height="398" alt="image" src="https://github.com/user-attachments/assets/e2e96917-6082-4970-8ab9-808090eeb13d" />

Tant `/dev/sdb1` com `/dev/sdc1` apareixen com a particions de tipus **Linux (83)** de 2 GiB cadascuna. El sistema està llest per crear l'array RAID.

---

### Crear el punt de muntatge

Creem el directori `/mnt/raid1` que servirà com a punt de muntatge del dispositiu RAID, i li assignem permisos oberts (777) perquè tots els usuaris hi puguin escriure:

<img width="767" height="247" alt="image" src="https://github.com/user-attachments/assets/b04fb5d8-a569-49d2-affe-9c17fcae2d77" />

El directori `raid1` queda creat a `/mnt/` i és accessible.

---

### Crear l'array RAID 1

Creem l'array RAID 1 amb `mdadm --create` indicant el dispositiu resultant (`/dev/md0`), el nivell (`--level=1`), el nombre de discos (`--raid-devices=2`) i els dos membres (`/dev/sdb1` i `/dev/sdc1`):

<img width="819" height="162" alt="image" src="https://github.com/user-attachments/assets/7d494c1c-3a1e-45b2-acf4-a01359a1038d" />

`mdadm` informa que l'array `/dev/md0` s'ha creat correctament i ha iniciat la sincronització entre els dos discos en segon pla.

---

### Formatar l'array com a ext4

Un cop creat l'array, el formatem amb el sistema de fitxers **ext4** perquè pugui ser muntat i utilitzat:

<img width="813" height="307" alt="image" src="https://github.com/user-attachments/assets/d8ccec39-01c8-41a0-a943-4d5342ec546f" />


`mkfs.ext4` crea el sistema de fitxers amb 523.520 blocs de 4k. L'array `/dev/md0` ja té un sistema de fitxers i un UUID únic assignat.

---

### Verificar l'estat del RAID

Consultem l'estat detallat de l'array amb `mdadm --detail /dev/md0` per confirmar que tot funciona correctament:

<img width="771" height="387" alt="image" src="https://github.com/user-attachments/assets/a195003c-a9a6-41eb-b544-7c1a5bf4d8d3" />

L'estat és **clean**, amb els dos dispositius **active sync** (`/dev/sdb1` i `/dev/sdc1`). La mida de l'array és de 2045 MiB (ja que amb RAID 1 la capacitat útil és la d'un sol disc).

---

### Desar la configuració de mdadm

Per fer que el RAID es reconstitueixi automàticament en reiniciar el sistema, exportem la configuració al fitxer `/etc/mdadm/mdadm.conf` amb dues comandes:

1. `mdadm --detail --scan` per llistar l'array en format de configuració.
2. `mdadm --detail --scan > /etc/mdadm/mdadm.conf` per desar-lo al fitxer.

<img width="822" height="118" alt="image" src="https://github.com/user-attachments/assets/cbdfebc7-822f-474d-a7e0-6e08cd51551a" />

L'array `/dev/md0` amb el seu UUID queda registrat.

---

### Contingut del fitxer mdadm.conf

Verifiquem el contingut del fitxer de configuració generat `/etc/mdadm/mdadm.conf` amb `nano`:

<img width="772" height="51" alt="image" src="https://github.com/user-attachments/assets/1235ee76-1156-4f7c-9d8e-1a3b9b832063" />

El fitxer conté la línia `ARRAY /dev/md0 metadata=1.2 name=eros-VirtualBox:0 UUID=...` i `DEVICE /dev/sdb1 /dev/sdc1`, que indica quins discos formen l'array.

---

### Configurar el muntatge automàtic amb /etc/fstab

Per muntar automàticament el RAID en cada arrencada, afegim una línia al fitxer `/etc/fstab`:

```
/dev/md0   /mnt/raid1   ext4   defaults   0   0
```

<img width="810" height="327" alt="image" src="https://github.com/user-attachments/assets/d15c50c0-21d0-4f03-9855-1c8e631ee826" />

La línia ressaltada en vermell és la nova entrada que hem afegit. Indica que `/dev/md0` s'ha de muntar a `/mnt/raid1` amb sistema de fitxers `ext4` i opcions per defecte en cada arrencada.

---

### Muntar tots els sistemes de fitxers i actualitzar initramfs

Executem `mount -a` per muntar tots els dispositius definits a `/etc/fstab` sense haver de reiniciar. A continuació actualitzem el **initramfs** perquè reconegui el RAID durant l'arrencada:

<img width="788" height="242" alt="image" src="https://github.com/user-attachments/assets/261f5a7a-1b0e-4aaf-9560-7a4a80c3669f" />

`update-initramfs` regenera les imatges d'arrencada per a tots els kernels instal·lats. Això garanteix que el RAID es carregui correctament en l'inici del sistema.

---

### Verificar el RAID després del reinici

Reiniciem la màquina i tornem a consultar `mdadm --detail /dev/md0` per comprovar que el RAID persisteix correctament:

<img width="649" height="544" alt="image" src="https://github.com/user-attachments/assets/ca99ea0d-082a-4d58-abdc-a21915e2605f" />

L'array continua en estat **clean**, amb els dos discos **active sync**. La configuració ha persistit correctament a través del reinici, confirmant que `fstab` i `mdadm.conf` funcionen bé.

---

### Crear fitxers de prova al RAID

Accedim a `/mnt/raid1/` i creem alguns fitxers i directoris de prova per verificar que el RAID és funcional:

<img width="713" height="314" alt="image" src="https://github.com/user-attachments/assets/8d131fa9-9a10-4bfe-b331-7784596fbaa6" />

Creem el fitxer `dijous` i el directori `divendres`. Amb `ls` confirmem que el sistema de fitxers del RAID funciona correctament i accepta escriptures.

---

### Simular la fallada d'un disc

Simulem la fallada del disc `/dev/sdb1` marcant-lo com a defectuós amb `mdadm /dev/md0 -f /dev/sdb1` i després traient-lo de l'array amb `-r`:

<img width="599" height="548" alt="image" src="https://github.com/user-attachments/assets/486a68c7-fc61-42f9-9d60-d726cb22cd3b" />

L'estat de l'array passa a **clean, degraded**: l'array continua funcionant però amb un sol disc actiu (`/dev/sdc1`). El disc `/dev/sdb1` apareix com a `faulty` i ha estat eliminat. Amb RAID 1, el sistema continua operatiu i les dades no es perden.

---

### Verificar accessibilitat de les dades durant la fallada

Mentre l'array és en estat degradat (un sol disc), comprovem que les dades que havíem creat (`dijous`, `divendres`) continuen accessibles. A més creem nous fitxers de prova:

<img width="579" height="220" alt="image" src="https://github.com/user-attachments/assets/f54942f3-9498-463c-ab08-9f37caf4b3f0" />

Els fitxers originals (`dijous`, `divendres`) i els nous (`dadadada`, `fbjqbfkq`) es llegeixen i escriuen sense cap problema, demostrant la tolerància a fallades del RAID 1.

---

### Recuperar el disc fallat i reconstituir el RAID

Aturem l'array, el tornem a muntar i reafegim el disc `/dev/sdb1` per reconstituir el RAID complet:

1. `mdadm --stop /dev/md0` per aturar l'array (cal primer desmontar-lo amb `umount -a`).
2. `mdadm --assemble /dev/md0` per torna a muntar-lo amb el disc disponible.
3. `mdadm /dev/md0 -a /dev/sdb1` per reafegir el disc recuperat.
4. `mount -a` per muntar-lo de nou.

<img width="798" height="495" alt="image" src="https://github.com/user-attachments/assets/acadc670-67d6-479f-8fa3-6ea6ae93bafa" />

El disc `/dev/sdb1` es reincorpora a l'array i `mdadm` comença la resincronització automàtica en segon pla. Les dades (`dadadada`, `dijous`, `divendres`, `fbjqbfkq`) segueixen íntegres al punt de muntatge, confirmant que el RAID 1 ha funcionat correctament davant la simulació de fallada.
