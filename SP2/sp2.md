### Sprint 2: Instal·lació, Configuració de Programari de Base i Gestió de Fitxers
## Sistemes de fitxers i particions
## Mida sector

El sector és la unitat mínima física del disc on es guarden les dades i per defecte són **512 bytes**. No es pot cambiar la mida.

## Mida block

És la unitat mínima lògica on es guarden les dades al SO, per defecte són 4096 bytes. I es pot canviar la mida quan es formata el disc.

La mida del block o cluster i el sistema de fitxers pot ser diferent a cada partició del mateix disc.

- **Fragmentació interna:** Es produeix quan un fitxer s’emmagatzema dins d’un bloc però no l’arriba a omplir completament, deixant part de l’espai sense utilitzar. En el cas del nostre exemple, només s’estan utilitzant 8 bytes dels 4096 que permet el bloc, de manera que la resta queda desaprofitada i això genera fragmentació.
<img width="336" height="113" alt="image" src="https://github.com/user-attachments/assets/35650f8a-d166-4165-9053-927b217c0a99" />

- **Fragmentació externa:** Succeeix quan les parts d’un mateix fitxer queden distribuïdes en diversos blocs físics del disc, fet que provoca que la lectura sigui més lenta, ja que el sistema ha de buscar totes les parts per accedir al contingut complet.
- Tipus de formateig:
Formatatge de baix nivell: Elimina completament el sistema de fitxers i el contingut del disc, a més de reparar o reassignar sectors defectuosos.

Formatatge de mig nivell: Neteja el sistema de fitxers i elimina sectors malmesos, deixant el disc preparat per a un ús posterior.

Formatatge d’alt nivell: Només esborra l’estructura del sistema de fitxers, però manté les dades encara accessibles fins que siguin sobreescrites.

- Gestio de particions
- Comandes
<img width="548" height="105" alt="image" src="https://github.com/user-attachments/assets/f52435cf-a47f-4b09-bec4-613804d5b781" />

Per verificar si una partició presenta fragmentació, es pot fer ús de l'eina **e4defrag**, que analitza el sistema de fitxers i mostra el nivell de fragmentació detectat.
<img width="688" height="328" alt="image" src="https://github.com/user-attachments/assets/0e08ddc9-0a9f-47ac-a874-d3c2599fcb90" />

Desfragmentació de la partició

<img width="437" height="148" alt="image" src="https://github.com/user-attachments/assets/8c903980-3807-4c3b-a950-5718367a77cc" />

Els volums permeten afegir una **capa d’abstracció** sobre les particions físiques, facilitant la gestió i flexibilitat del disc sense dependre directament de la configuració original. Amb **GParted** podem realitzar pràcticament les mateixes operacions que amb les eines en línia d'ordres.  L’única limitació és que **no és possible modificar la mida del bloc**, que per defecte és de **4096 bytes**.
<img width="780" height="247" alt="6" src="https://github.com/user-attachments/assets/57aa6495-39ed-44f1-a191-d885c004f0a2" />

Crear partició, i formatejar-la, i altres proves per a demostrar que podem fer de tot excepete modificar la mida del bloc
<img width="905" height="432" alt="7" src="https://github.com/user-attachments/assets/924d75bb-5a34-466b-b838-29619108b6dc" />
<img width="573" height="222" alt="8" src="https://github.com/user-attachments/assets/660d5b5c-66f5-43d1-b654-732ad72b2b43" />

Crear un sistema de fitxers en format ext4 a la partició generada, indicant manualment la mida del bloc a 2048 bytes mitjançant l’opció -b

<img width="839" height="250" alt="9" src="https://github.com/user-attachments/assets/08b371df-e36b-49dc-9b08-5c3d4108dcbb" />

Creem un sistema de fitxers NTFS sobre la partició /dev/sdb2.
<img width="507" height="138" alt="10" src="https://github.com/user-attachments/assets/ed2d6824-a194-42f5-bd69-72e7c3a5639e" />

I verifiquem que les particions es mostren correctament dins de GParted.
<img width="789" height="264" alt="11" src="https://github.com/user-attachments/assets/11bc714f-229c-4d2c-8f43-e25b2657f52d" />
<img width="364" height="108" alt="12" src="https://github.com/user-attachments/assets/175a7ec3-286d-4b51-aef1-56e6e79e816c" />
<img width="611" height="183" alt="13" src="https://github.com/user-attachments/assets/298acc85-19d9-4894-bcb3-3675ef2c3e25" />
<img width="430" height="183" alt="14" src="https://github.com/user-attachments/assets/7c479702-997d-4fe4-bf04-3a11fe58aac9" />

Si tornem a muntar, veiem que tornen a apareixer els fitxers.

<img width="623" height="234" alt="15" src="https://github.com/user-attachments/assets/8921babe-7671-4bfe-a941-d3273d8e147b" />

Per fer que el muntatge sigui permanent, modifiquem el fitxer /etc/fstab, afegint la mateixa informació que utilitzàvem en el muntatge manual. Un cop guardats els canvis, reiniciem el sistema perquè s’apliquin.

<img width="738" height="284" alt="16" src="https://github.com/user-attachments/assets/bcf0df87-91ab-4765-beb4-b862f738ed3c" />


### Gestio d'usuaris, grups i permisos
- Usuaris
passwd. Aquest arxiu emmagatzema les dades de tots els usuaris del sistema, tant dels que poden iniciar sessió de manera gràfica com dels comptes interns utilitzats pel propi sistema. Des d’aquí es pot comprovar si un usuari té o no contrasenya (encara que no es desi en aquest fitxer), així com consultar el seu grup per defecte i el directori personal assignat.

<img width="1015" height="636" alt="1" src="https://github.com/user-attachments/assets/4d89de5e-31bf-43f3-bfa4-c5ac36105414" />

shadow. En aquest arxiu s’hi llisten tots els comptes d’usuari del sistema juntament amb la seva contrasenya xifrada, en cas que en disposin. A més, els diferents camps permeten conèixer aspectes relacionats amb la vigència de la contrasenya, com la seva caducitat o la data de l’últim canvi. En resum, es pot considerar el fitxer que centralitza tota la informació vinculada a les contrasenyes dels usuaris.

<img width="612" height="345" alt="image" src="https://github.com/user-attachments/assets/68e6c0d4-950c-4586-809b-8bbab8e1dc54" />

Aquest fitxer recopila la llista completa dels grups existents al sistema i permet identificar quins usuaris estan associats a cadascun d’ells.

<img width="693" height="495" alt="2" src="https://github.com/user-attachments/assets/1af86dd2-1231-4e69-9e63-23ff85e36f52" />

Aquest arxiu inclou informació similar a la del fitxer /etc/group, però amb un detall addicional: aquí es pot consultar quin usuari exerceix com a administrador o responsable de cada grup.

<img width="596" height="358" alt="image" src="https://github.com/user-attachments/assets/6187e004-0495-4b9e-93e0-93902158dbf9" />

Ara procedirem a crear un nou compte d’usuari al sistema utilitzant l’assistent que ofereix la comanda adduser

<img width="589" height="432" alt="5" src="https://github.com/user-attachments/assets/2e842d09-2824-4779-b434-3397a7f84c6b" />

Un cop creat l’usuari, comprovem que als fitxers mencionats anteriorment s’han generat les entrades corresponents a aquest nou compte.

<img width="1012" height="582" alt="6" src="https://github.com/user-attachments/assets/2338c9a6-af32-421a-a058-f38090df8baa" />

Si eliminem l’usuari amb userdel -r alumnat, comprovarem que s’han suprimit tant les entrades associades com el seu directori personal.

<img width="575" height="70" alt="image" src="https://github.com/user-attachments/assets/3389956e-8c50-4d10-96da-009e68d10a98" />
<img width="505" height="100" alt="image" src="https://github.com/user-attachments/assets/ed6629ab-cbc0-40fb-a755-eb3f6e2390d0" />

A continuació creem un altre usuari, aquesta vegada utilitzant la comanda useradd. Un cop creat, consultem el fitxer /etc/passwd i podem observar que se li han assignat diferents paràmetres per defecte, com l’intèrpret de comandes i la ruta del seu directori personal. Tot i així, encara que s’indiqui un home directory, aquest no es genera automàticament.

<img width="526" height="110" alt="image" src="https://github.com/user-attachments/assets/3baca9e8-8bb0-4e2e-a1ad-2958970eca20" />

- Grups
Podem generar un nou grup amb la comanda addgroup asix, i posteriorment ajustar-ne la configuració o característiques utilitzant groupmod.

<img width="478" height="44" alt="image" src="https://github.com/user-attachments/assets/cae0f1ab-8d05-446d-b665-ffd96c1e9718" />
<img width="487" height="83" alt="image" src="https://github.com/user-attachments/assets/1ebb740e-7de6-4bd5-acf7-f889c2154058" />

Per afegir usuaris ho podem fer de diverses maneres, com per exemple:

<img width="487" height="83" alt="image" src="https://github.com/user-attachments/assets/3453b0c5-1e31-4f60-ab80-73d0dbaecae6" />
<img width="462" height="62" alt="image" src="https://github.com/user-attachments/assets/b992af27-6992-4076-b0ab-dafb47c6fcd8" />
<img width="500" height="45" alt="image" src="https://github.com/user-attachments/assets/3906fa86-cd6c-45b0-a528-a9a360e5e94b" />

Per retirar un usuari d’un grup, podem utilitzar la comanda deluser alumnat2 asixA, la qual elimina la seva associació amb aquest grup.

<img width="509" height="99" alt="image" src="https://github.com/user-attachments/assets/642e262e-394e-4d6b-8ba9-2e199b79f6a3" />

- ICACLS
Per visualitzar els permisos ACL configurats en un fitxer o directori, podem utilitzar l’ordre getfacl. Per exemple, podem consultar-los en la carpeta ramon

<img width="510" height="279" alt="image" src="https://github.com/user-attachments/assets/ed06d990-8894-4e41-ad25-dd3238442b11" />

Si, per exemple, no volem que un segon usuari tingui accés a la carpeta, podem aplicar una regla restrictiva mitjançant setfacl per denegar-li els permisos.

<img width="537" height="230" alt="image" src="https://github.com/user-attachments/assets/86d59015-e58c-478e-975c-fd97f7c9148d" />

I posteriorment verifiquem que el segon ja no té permís per accedir-hi.

<img width="645" height="101" alt="image" src="https://github.com/user-attachments/assets/5fc6e558-61c9-4c11-ac99-1f851142857c" />

Amb setfacl -b ramon, restablim els permisos eliminant totes les ACL aplicades prèviament.

<img width="456" height="383" alt="image" src="https://github.com/user-attachments/assets/daf65c9b-9a1e-495d-852f-8b5a748f31f5" />

### Exercisi
He generat el grup palomes i hi he afegit els usuaris persona1 i persona2. A més, també he creat els comptes d’usuari persona3 i persona4.

<img width="385" height="26" alt="image" src="https://github.com/user-attachments/assets/31e2d522-cf32-4529-8589-016d3a9902db" />
<img width="827" height="393" alt="image" src="https://github.com/user-attachments/assets/e7aee194-d36a-4206-a989-3cf2e052c9d1" />

He creat una carpeta i un fitxer a l’interior que seran compartits entre els quatre usuaris.

<img width="570" height="215" alt="image" src="https://github.com/user-attachments/assets/2f04fc24-b229-48d6-986e-224c263fd806" />
<img width="445" height="108" alt="image" src="https://github.com/user-attachments/assets/d95f8c33-656f-4436-9ebf-d64cd62c399b" />

- UMASK
Es pot modificar la umask directament amb la comanda umask + mascara. Aquest canvi només és vàlid mentre dura la sessió actual.
En l’exemple, s’ha provat amb l’usuari root, aplicant 001, cosa que permet lectura i escriptura al grup i a altres usuaris. No és recomanable, ja que pot exposar fitxers i permetre execució o modificacions no desitjades. Per fer que la configuració sigui permanent per a futurs usuaris, s’ha editat el fitxer /etc/login.defs, establint una umask fixa. S’ha configurat 077, de manera que només l’usuari propietari té permisos complets sobre els fitxers i directoris que crea.

<img width="736" height="466" alt="image" src="https://github.com/user-attachments/assets/77bc6b15-0ab5-4c32-8ec6-65bf35c070a2" />

# Gestió de processos (Linux)

Un **procés** és un programa en execució. Quan s’inicia, el sistema li assigna un **PID** (Process ID) i queda associat a un usuari i a uns recursos (CPU, memòria, E/S).  
El sistema operatiu reparteix el temps de CPU entre processos amb el **planificador**, i cada procés pot passar per diversos **estats** (executant-se, preparat, adormit/esperant, aturat o zombi).

## Conceptes clau

- **PID**: identificador únic del procés.
- **PPID**: PID del procés pare.
- **Usuari**: qui l’ha iniciat (o el servei que l’executa).
- **Prioritat**: influència sobre quan s’executa (nice/renice).
- **Senyal**: “missatge” per controlar un procés (SIGTERM, SIGKILL, etc.).

- **ps** → fotografia puntual del sistema
- **top** → vista dinàmica en temps real
- **htop** → versió millorada i més visual (si està instal·lat)

Exemples:

```bash
ps aux
ps -ef
ps -u $USER
```
Per filtrar un procés, podem utilitzar grep en combinació amb altres eines.

Podem filtrar per els processos del usuari alumne

<img width="589" height="435" alt="h1" src="https://github.com/user-attachments/assets/8ac36569-9852-4e5d-9355-df4eb00ada66" />

## Fitxers importants

* En Linux, la informació d'usuaris i grups es gestiona de manera centralitzada mitjançant fitxers de configuració de text ubicats dins del directori /etc.

Explicació **/etc/passwd**:
<img width="776" height="525" alt="image" src="https://github.com/user-attachments/assets/27e3f2cf-1738-4bf6-bed6-2131dc9d086b" />

Cada línia representa un usuari i conté 7 camps separats per dos punts:

**nom_usuari:x:UID:GID:GECOS:directori_home:shell**

Descripció detallada de cada camp

1. **nom_usuari**

    Exemple: root, anna, mysql

    Descripció:

        Nom únic que identifica l'usuari al sistema

        És el que s'utilitza per iniciar sessió

        Normalment té un màxim de 32 caràcters

2. **x (camp de contrasenya)**

    Exemple: x, *, !

    Descripció:

        x indica que la contrasenya està emmagatzemada a /etc/shadow

        * o ! vol dir que el compte està blocat

        Si està buit, l'usuari no té contrasenya (insicur)

3. **UID (User ID)**

    Exemple: 0, 1000, 33

    Descripció:

        Número d'identificació únic de l'usuari

        0 = usuari root (superusuari)

        1-999 = usuaris del sistema (serveis)

        1000+ = usuaris normals

4. **GID (Group ID)**

    Exemple: 0, 1000, 33

    Descripció:

        Número del grup principal de l'usuari

        Defineix els permisos per defecte per a nous arxius

5. **GECOS (Informació addicional)**

    Exemple: Anna Garcia,,,, Pere Lopez,Vendes,555-1234

    Descripció:

        Informació opcional sobre l'usuari

        Normalment només s'inclou el nom complet

        Format: Nom complet,Despatx,Telefon,Altres

6. **directori_home**

    Exemple: /home/anna, /root, /var/www

    Descripció:

        Directori personal de l'usuari

        On s'emmagatzemen els seus arxius personals

        Directori per defecte en iniciar sessió

7. **shell**

    Exemple: /bin/bash, /bin/sh, /usr/sbin/nologin

    Descripció:

        Intèrpret d'ordres que s'executa en iniciar sessió

        /bin/bash = shell Bash normal

        /usr/sbin/nologin o /bin/false = no permet inici de sessió (comptes de servei)

Explicació **/etc/shadow**:

<img width="582" height="487" alt="image" src="https://github.com/user-attachments/assets/9d9b8ba9-316e-4850-a2d1-e4d86760d877" />

L'arxiu /etc/shadow conté la informació de les contrasenyes dels usuaris i les polítiques d'expiració. És un arxiu segur que només pot llegir l'usuari root.

Cada línia representa un usuari i conté 9 camps separats per dos punts:

**nom_usuari:contrasenya_encryptada:darrers_canvis:minims:maxims:avis:inactiu:caducitat:camp_reserva**

Descripció detallada de cada camp

1. **nom_usuari**

    Exemple: root, anna, mysql

    Descripció:

        Nom de l'usuari (ha de coincidir amb /etc/passwd)

        Serveix com a clau d'enllaç entre els dos arxius

2. **contrasenya_encryptada**

    Exemple: $6$rounds=5000$t..., *, !!

    Descripció:

        Contrasenya encryptada amb hash

        * o !! = compte blocat o sense contrasenya

        Format: $algoritme$salt$hash

        Algoritmes comuns: $1$ (MD5), $5$ (SHA-256), $6$ (SHA-512)

3. **darrers_canvis (last change)**

    Exemple: 19157, 0

    Descripció:

        Data de l'últim canvi de contrasenya en dies des de l'1/1/1970

        0 = ha de canviar-la en el proper login

        19157 = 19,157 dies des de l'1/1/1970

4. **minims (minimum days)**

    Exemple: 0, 7

    Descripció:

        Dies mínims que han de passar abans de poder canviar la contrasenya

        0 = es pot canviar en qualsevol moment

5. **maxims (maximum days)**

    Exemple: 99999, 90

    Descripció:

        Dies màxims que la contrasenya és vàlida

        99999 = quasi etern (273 anys)

        90 = ha de canviar-la cada 90 dies

6. **avis (warning days)**

    Exemple: 7, 0

    Descripció:

        Quants dies abans de la caducitat s'envia un avís

        7 = avisa 7 dies abans que caduqui

7. **inactiu (inactive days)**

    Exemple: -1, 30

    Descripció:

        Dies de gràcia després de caducar abans que el compte es desactivi

        -1 = sense període d'inactivitat

8. **caducitat (expiration date)**

    Exemple: ``, 20000

    Descripció:

        Data absoluta de caducitat del compte en dies des de l'1/1/1970

        Buit = el compte no caduca mai

9. **camp_reserva (reserved field)**

    Exemple: (buit)

    Descripció:

        Camp reservat per a ús futur

        Normalment està buit

Explicació **/etc/group**:

<img width="632" height="449" alt="image" src="https://github.com/user-attachments/assets/8028595d-5b21-4d19-a651-adb8bacd4545" />

L'arxiu /etc/group conté la informació dels grups del sistema i els seus membres. Defineix els grups d'usuaris i les seves relacions.

Estructura de cada línia

Cada línia representa un grup i conté 4 camps separats per dos punts:

**nom_grup:contrasenya_grup:GID:llista_membres**

Descripció detallada de cada camp

1. **nom_grup**

    Exemple: root, users, sudo, www-data

    Descripció:

        Nom del grup

        Ha de ser únic al sistema

        Normalment en minúscules

2. **contrasenya_grup**

    Exemple: x, *

    Descripció:

        x indica que la contrasenya del grup està a /etc/gshadow

        * o buit = no hi ha contrasenya de grup

        Rarament s'utilitza en sistemes moderns

3. **GID (Group ID)**

    Exemple: 0, 100, 1000, 33

    Descripció:

        Número d'identificació únic del grup

        0 = grup root

        1-999 = grups del sistema

        1000+ = grups d'usuaris normals

4. **llista_membres**

    Exemple: anna,pere,marta, root, (buit)

    Descripció:

        Llista d'usuaris que són membres del grup, separats per comes

        No inclou l'usuari que té aquest grup com a grup primari

        Buit = cap usuari addicional al grup

Explicació **/etc/gshadow**:

<img width="585" height="467" alt="image" src="https://github.com/user-attachments/assets/a0ae2deb-1d6b-417b-98f0-4ca6a5ea08e4" />

L'arxiu **/etc/gshadow** conté la informació segura dels grups, incloent contrasenyes de grup i administradors. És la contrapart segura de **/etc/group**.

Estructura de cada línia

Cada línia representa un grup i conté 4 camps separats per dos punts:

**nom_grup:contrasenya_encryptada:administradors:membres**

Descripció detallada de cada camp

1. **nom_grup**

    Exemple: root, sudo, developers

    Descripció:

        Nom del grup (ha de coincidir amb /etc/group)

        Serveix com a clau d'enllaç entre els dos arxius

2. **contrasenya_encryptada**

    Exemple: !, $6$rounds=5000$..., *

    Descripció:

        Contrasenya encryptada per canviar al grup amb newgrp

        ! o * = no hi ha contrasenya de grup

        Contrasenya vàlida = hash encryptat

        Rarament s'utilitza en sistemes moderns

3. **administradors**

    Exemple: anna,root, pere, (buit)

    Descripció:

        Llista d'usuaris que poden gestionar el grup

        Poden afegir/eliminar membres i canviar la contrasenya del grup

        Separats per comes

4. **membres**

    Exemple: marta,jordi, user1,user2, (buit)

    Descripció:

        Llista d'usuaris que són membres del grup

        Ha de coincidir amb el camp de membres de /etc/group

        Separats per comes

## ACL

### Importància de les ACL a Ubuntu

Raons principals per utilitzar ACL

1. Flexibilitat en gestió de permisos

    Superen les limitacions del model usuari/grup/altres

    Permeten assignar múltiples usuaris i grups al mateix recurs

    Ofereixen control granular d'accés

2. Escalabilitat en entorns complexos

    Necessàries en sistemes amb múltiples usuaris i grups

    Essencials en servidors compartits

    Importants en entorns corporatius

3. Seguretat més precisa

    Permeten implementar polítiques d'accés detallades

    Milloren el principi de mínim privilegi

    Faciliten l'auditoria d'accés

<img width="482" height="303" alt="image" src="https://github.com/user-attachments/assets/64efa175-9d8e-4c04-96d1-c4b5ae7b83eb" />

<img width="467" height="306" alt="image" src="https://github.com/user-attachments/assets/fbfe01a7-ccfb-4175-b50e-f548b7de06f2" />

<img width="458" height="308" alt="image" src="https://github.com/user-attachments/assets/e06293ef-3e0d-4821-ac72-c9e64b99cdad" />

## Umask

Què és la umask?

Màscara que determina els permisos per defecte per a nous arxius i directoris.

On es configura a Ubuntu?

Arxius principals:

    Sistema: /etc/profile i /etc/bash.bashrc

    Usuari: ~/.bashrc

Comprovar umask actual:

**umask**

<img width="164" height="72" alt="image" src="https://github.com/user-attachments/assets/d1512d74-029a-4650-8ce8-f75a29fb9098" />

Valors per defecte a Ubuntu

**Usuaris normals:**
    umask: 0002

    Arxius: 664 (rw-rw-r--)

    Directoris: 775 (rwxrwxr-x)

**Usuari root:**

    umask: 0022

    Arxius: 644 (rw-r--r--)

    Directoris: 755 (rwxr-xr-x)

<img width="239" height="98" alt="image" src="https://github.com/user-attachments/assets/aa3b2165-614f-4792-9605-412a09e662bd" />

**Com funciona el càlcul?**

Permisos base:

    Arxius: 666 (rw-rw-rw-)

    Directoris: 777 (rwxrwxrwx)

Exemple umask 002:

Arxiu:   666 - 002 = 664 (rw-rw-r--)
Directori: 777 - 002 = 775 (rwxrwxr-x)

* Aqui he canviat temporalment el umask i he fet una provat creant una carpeta i un arxiu.

<img width="807" height="550" alt="image" src="https://github.com/user-attachments/assets/7e0fc2cd-d7f1-4981-b5c2-9e37ff32855c" />

* Per a fer-ho permanenment podem fer-ho modificant l'arxiu **login.defs**

<img width="832" height="542" alt="image" src="https://github.com/user-attachments/assets/a55151b4-d9f5-4ebf-8d22-be420f8e5208" />


## Gestió de processos

Els processos són programes en execució dins del sistema. Cada procés té un PID (Identificador de Procés), un usuari propietari i pot trobar-se en diferents estats (actiu, en espera, aturat…). El sistema operatiu planifica i reparteix el temps de CPU entre ells.
Eines bàsiques per gestionar-los

    ps, top, htop: veure processos actius.

    kill, pkill: finalitzar un procés per PID o nom.

    nice, renice: ajustar la prioritat d'execució.

    systemctl, service: controlar serveis (daemons). No l'abordarem aquí específicament.

A nivell pràctic, cada procés hereta permisos de l'usuari que l'ha iniciat i pot estar vinculat a un servei o a una sessió d'usuari.

A continuació, veurem com utilitzar-les de manera bàsica.

**Ús de pstree**

```
Paràmetre	Funció
-p	Mostra el PID de cada procés.
-u	Mostra l'usuari propietari de cada procés.
-h	Ressalta el procés actual (útil quan es filtra).
-n	Ordena processos per PID dins de cada arbre.
-a	Mostra els arguments complets del procés (línia de comandes).
```

Per filtrar un procés, podem utilitzar grep en combinació amb altres eines.

Aquí he filtrat per els processos del usuari alumnat.

<img width="688" height="683" alt="image" src="https://github.com/user-attachments/assets/28d88fb8-12bd-4b5b-bef2-6ce486ce1092" />

I aquí ho he fet com a root.

<img width="852" height="404" alt="image" src="https://github.com/user-attachments/assets/c2d91135-a9de-4974-b985-33f95379d963" />

**ps** Aquesta comanda, mostra informació sobre una selecció dels processos actius. Si volem una actualització repetitiva de la selecció i la informació mostrada, hauriem de usar top en comptes d’això.

Alguns dels parametres mes comuns són:
```
a: mostra processos de tots els usuaris, no només del terminal actual.
u: mostra informació en format d’usuari, amb columnes com %CPU, %MEM, USER.
x: inclou processos sense terminal associat (daemons i serveis).
-e: Mostra tots els processos del sistema, equivalent a -A.
-o: Permet personalitzar exactament quines columnes vols que surti.
i molts més
```
<img width="814" height="405" alt="image" src="https://github.com/user-attachments/assets/306bf402-896b-4682-93f1-c008e976fd39" />

Podem filtrar per obtenir les terminals que l’usuari fa servir amb ps aux | grep usuari | grep tty

Aixó, mostra els processos d’un usuari concret que s’estan executant en terminals.

```
ps aux: mostra tots els processos amb informació detallada.
grep usuario: filtra només els processos propietat de l’usuari “usuario”.
grep tty: filtra només els processos que tenen un terminal associat (tty).
```

<img width="909" height="258" alt="image" src="https://github.com/user-attachments/assets/9369664e-7092-4a98-ac24-488652887839" />

Si volem matar un proces, podem fer servir kill, te diversos modes de terminar:

```
Tipus de Kill 	Senyal 	Descripció 	Comanda

Kill suau 	SIGTERM 	Demana al procés finalitzar netament 	kill PID
Kill forçat 	SIGKILL 	Mata immediatament, sense netejar recursos 	kill -9 PID
Recarregar config 	SIGHUP 	Demana al procés que recarregui la configuració 	kill -1 PID
Pausa 	SIGSTOP 	Pausa l’execució del procés 	kill -STOP PID
Continuar 	SIGCONT 	Continua un procés pausat 	kill -CONT PID
Interrupció Ctrl-C 	SIGINT 	Senyal d’interrupció (Ctrl+C) 	kill -2 PID
Abortar 	SIGABRT 	Senyal d’error abortat, sovint genera core dump 	kill -6 PID
```

Aqui tenim un exemple obrint xclock al fons amb el “&” i matant-lo suau, mentres comprovem amb ps aux que s’ha mort.

<img width="778" height="198" alt="image" src="https://github.com/user-attachments/assets/6e99650d-2bca-4675-8983-561b49e2f9c8" />

També tenim la comanda **top**

**top** és una comanda que mostra informació en temps real sobre processos i l'ús del sistema.

<img width="800" height="478" alt="image" src="https://github.com/user-attachments/assets/0f505c5f-6b43-4243-9130-4f0ec89411d1" />

```
Part superior (resum del sistema):

    Temps: Temps d'execució del sistema

    Usuaris: Nombre d'usuaris connectats

    Load average: Càrrega mitjana (1, 5, 15 minuts)

    Tasques: Total, en execució, dormint, aturades, zombie

    %CPU: Ús del processador (us, sy, ni, id, wa, hi, si, st)

    Memòria: Total, lliure, usada, memòria buffer/cache

    Swap: Memòria d'intercanvi (swap) total i usada

Part inferior (llista de processos):

    PID: Identificador del procés

    USUARI: Propietari del procés

    PR: Prioritat

    NI: Valor "nice" (prioritat ajustable)

    VIRT: Memòria virtual utilitzada

    RES: Memòria resident (física)

    SHR: Memòria compartida

    %CPU: Percentatge d'ús de CPU

    %MEM: Percentatge d'ús de memòria

    TEMPS+: Temps total d'execució

    COMANDAMENT: Nom de la comanda
```

També tenim htop que es el mateix pero de manera interactiva.


<img width="800" height="528" alt="image" src="https://github.com/user-attachments/assets/84f2efcd-8892-42f4-b921-57d80b949945" />

Estats principals

Codi	Estat (Català)	Descripció
R	En execució (Running)	El procés està actiu o llest per ser assignat a la CPU
W	En espera (Waiting)	El procés espera un recurs o un esdeveniment
S	Aturat (Stopped)	El procés ha estat detingut, normalment per un senyal, sovint durant depuració
Z	Zombi (Zombie)	El procés ha finalitzat però encara conserva una entrada a la taula de processos
T	Trencat	Procés aturat per depuració o per senyal de trencament
D	Dormint	Procés inactiu, esperant I/O, no pot ser interromput
I	Inactiu (Idle)	El procés està completament inactiu, sense consumir CPU; molt habitual en fils del kernel

Ara amb la comanda renice podem modificar la prioritat de un procés


<img width="598" height="240" alt="image" src="https://github.com/user-attachments/assets/a62442bb-87ea-4b7d-a17e-4df77da88eee" />


Mostra la llista de feines (processos) que tens en execució o aturades dins de la sessió actual del terminal.

Exemple de sortida:

[1]+  Aturat     nano fitxer.txt
[2]-  Executant  sleep 100 &


Això vol dir:

[1] i [2] són els números de feina

Aturat → el procés està pausat

Executant → el procés està funcionant en segon pla

🔹 fg %1

Serveix per portar una feina del segon pla o pausada al primer pla (foreground).

fg = foreground

%1 indica la feina número 1 (segons el que mostra jobs)

En aquest cas:

fg %1

Recupera la feina número 1 i la torna a executar ocupant el terminal.

Llencar processos amb &

# Còpies de seguretat i automatització de tasques

## Teoria copies de seguretat

Còpies de seguretat

Una còpia de seguretat és una duplicació de les dades que permet recuperar informació en cas de pèrdua, dany, error humà, virus o qualsevol altre desastre. Aquestes còpies s’emmagatzemen de manera independent de les dades originals, preferiblement en un altre dispositiu, servidor o servei al núvol.

Normalment segueixen polítiques definides, com ara el temps de retenció, el nombre de versions guardades i la realització de proves de restauració per assegurar que les dades es poden recuperar correctament.

Tipus principals de còpia de seguretat
Còpia completa

Desa totes les dades cada vegada que es fa la còpia.

És la més lenta i la que ocupa més espai, però també la més segura i la més fàcil de restaurar, ja que només cal una única còpia per recuperar tota la informació.

Còpia incremental

Només guarda els canvis realitzats des de l’última còpia, sigui completa o incremental.

És molt ràpida i ocupa poc espai. L’inconvenient principal és que, per restaurar les dades, cal disposar de la còpia completa inicial i de totes les còpies incrementals posteriors.

Còpia diferencial

Guarda tots els canvis fets des de l’última còpia completa.

És més ràpida que la còpia completa i ocupa un espai intermig. La restauració és més senzilla que amb les incrementals, però cada nova còpia diferencial ocupa més espai fins que es fa una nova còpia completa.

Exemples de funcionament
Còpia completa

Dilluns: còpia completa
Dimarts: còpia completa
Dimecres: còpia completa

Si es perd un fitxer dijous, només cal restaurar la còpia completa de dimecres.

Còpia incremental

Dilluns: còpia completa
Dimarts: còpia incremental
Dimecres: còpia incremental

Per recuperar un fitxer perdut dijous, cal la còpia completa de dilluns i totes les còpies incrementals fins dimecres.

Còpia diferencial

Dilluns: còpia completa
Dimarts: còpia diferencial
Dimecres: còpia diferencial

Si es perd un fitxer dijous, cal la còpia completa de dilluns i l’última còpia diferencial, la de dimecres.

RAID i emmagatzematge

Els sistemes RAID combinen diversos discs perquè funcionin conjuntament, millorant el rendiment i/o la seguretat segons el tipus de RAID utilitzat.

RAID 0 uneix la capacitat i la velocitat de diversos discs, però no ofereix cap protecció: si un disc falla, es perden totes les dades.
RAID 1 crea una còpia mirall: les dades es dupliquen i, si un disc falla, l’altre continua funcionant.
RAID 5 i RAID 6 reparteixen les dades i la informació de paritat entre diversos discs, oferint un bon equilibri entre velocitat i seguretat.
RAID 10 combina la velocitat del RAID 0 amb la seguretat del RAID 1.

És important recordar que RAID no és una còpia de seguretat. Si s’esborren fitxers o un virus afecta les dades, l’error es replica a tots els discs.

Imatge de disc

Una imatge de disc és una còpia exacta de tot un disc o partició, incloent el sistema operatiu, els programes, la configuració i les dades. S’utilitza per clonar equips o restaurar un sistema complet tal com estava en un moment concret.

És molt completa, però requereix molt espai i temps per crear-se. A canvi, permet restaurar un ordinador sencer en molt poc temps.

Snapshot

Un snapshot és una captura instantània de l’estat d’un sistema de fitxers o d’un dispositiu d’emmagatzematge. Normalment depèn de la tecnologia utilitzada (LVM, ZFS, Btrfs, màquines virtuals, etc.) i és molt ràpid de crear, ja que només guarda els canvis fets a partir del moment en què es crea.

Els snapshots són útils per tornar enrere ràpidament o fer proves, però no són una còpia de seguretat segura si es guarden al mateix disc. Si el disc falla, el snapshot també es perd.

Resum final

La còpia de seguretat serveix per protegir les dades guardant-les en un lloc segur.
La imatge de disc copia tot el sistema exactament com és en un moment concret.
El snapshot permet tornar enrere ràpidament, però no protegeix contra fallades del mateix disc.

No s’ha de confiar només en snapshots locals com a única protecció. La millor estratègia combina snapshots per recuperacions ràpides i còpies de seguretat externes per protegir-se davant desastres.

1. cp -> Es una copia simple no inteligent nomes transfereix fitxers localment es molt simple de utilitzar pero no optimitzar
2. rsync -> Es una eina inteligent que nomes copia els fitxers modificats i la sincronitzacio pot ser local o en remot via ssh
3. dd -> Es una eina per a clonar discs o particions i no es inteligent copia tots els sectors

### Comanda cp

Comanda cp (teoria)

La comanda cp s’utilitza en sistemes operatius Linux i Unix per copiar fitxers i directoris d’una ubicació a una altra. Permet duplicar informació mantenint, si es vol, atributs com permisos, dates i propietari.

Funcionament general

cp copia un o més fitxers cap a un fitxer o directori de destí. Quan el destí ja existeix, el fitxer pot ser sobreescrit segons les opcions utilitzades. Per defecte, cp només copia fitxers; per copiar directoris cal indicar-ho explícitament.

Opcions i paràmetres principals
Còpia recursiva

Permet copiar directoris sencers amb tots els seus subdirectoris i fitxers. Sense aquesta opció, els directoris no es copien.

Mode interactiu

Fa que el sistema demani confirmació abans de sobreescriure un fitxer existent, evitant pèrdues accidentals d’informació.

Mode forçat

Sobreescriu els fitxers de destí sense demanar confirmació, fins i tot si estan protegits contra escriptura.

Mode detallat

Mostra informació del procés de còpia, indicant quins fitxers s’estan copiant.

Actualització

Només copia els fitxers que són més nous que els del destí o que encara no existeixen, estalviant temps i espai.

Conservació d’atributs

Manté els permisos, el propietari, el grup i les dates originals dels fitxers copiats.

Mode arxiu

Realitza una còpia completa conservant l’estructura, els atributs i els enllaços, i és l’opció més utilitzada per fer còpies de seguretat de directoris.

Gestió d’enllaços

La comanda pot tractar els enllaços simbòlics de diverses maneres:

Copiar l’enllaç com a enllaç

Seguir l’enllaç i copiar el fitxer real

No seguir l’enllaç i conservar-lo tal com és

També permet crear enllaços simbòlics o enllaços durs en lloc de fer una còpia real del fitxer.

Altres funcionalitats

cp pot copiar múltiples fitxers alhora cap a un mateix directori.
Permet mantenir l’estructura de directoris original quan es copien fitxers individuals.
Pot limitar la còpia perquè no travessi diferents sistemes de fitxers.
Es pot utilitzar com a eina bàsica dins d’estratègies de còpies de seguretat simples.

<img width="814" height="502" alt="image" src="https://github.com/user-attachments/assets/3a0f03a7-290c-4bdf-b715-d17e6ff61284" />

### Comanda rsync

La comanda rsync és una eina de Linux/Unix utilitzada per sincronitzar fitxers i directoris entre dues ubicacions, ja sigui dins del mateix sistema, entre diferents discs o entre equips a través de la xarxa. És especialment eficient per a còpies de seguretat i transferències de dades grans.

Funcionament general

rsync compara els fitxers d’origen i destí i només transfereix les diferències, fent que sigui molt més ràpid i eficient que copiar tot el contingut de nou. Pot treballar amb fitxers locals o remots i permet mantenir atributs i permisos dels fitxers originals.

Opcions i paràmetres principals
Mode recursiu

Permet copiar directoris sencers, incloent subdirectoris i fitxers. Sense aquesta opció, només es copien fitxers individuals.

Conservació d’atributs

Manté propietari, grup, permisos, dates i atributs especials dels fitxers copiats. Això assegura que la còpia sigui exacta a l’original.

Compressió

Redueix la quantitat de dades transferides quan s’utilitza en xarxa, comprimint els fitxers durant la transmissió.

Modes detallats

Permet mostrar informació del procés de sincronització, indicant quins fitxers es transfereixen i quins ja estan actualitzats.

Actualització i sincronització

Només copia fitxers que han canviat o que no existeixen al destí, evitant duplicacions innecessàries i estalviant temps i espai.

Eliminació de fitxers obsolets

Permet eliminar del destí els fitxers que ja no existeixen a l’origen, mantenint les dues ubicacions sincronitzades exactament.

Modes segurs

Pot funcionar a través de connexions segures (per exemple SSH) quan es sincronitzen fitxers entre diferents equips, protegint la informació durant la transferència.

Enllaços i enllaços simbòlics

Rsync pot copiar enllaços simbòlics com a enllaços o bé seguir-los i copiar el contingut real, segons es configuri.

Altres funcionalitats

Permet filtrar fitxers per extensió, nom o directoris específics.

Admet transferències parcials per reprendre còpies interrompudes.

Pot funcionar de manera programada per automatitzar còpies de seguretat regulars.

És molt eficaç per sincronitzar grans quantitats de dades entre servidors, discs locals o sistemes de backup.


<img width="831" height="553" alt="image" src="https://github.com/user-attachments/assets/9943cfe0-4f51-4ea0-aef1-a78b1a21185a" />


### Comanda dd

La comanda dd és una eina de Linux/Unix utilitzada per copiar i transformar dades a baix nivell, normalment fitxers, discs o dispositius de blocs. És molt potent i flexible, ja que treballa amb dades binàries directament i permet fer còpies exactes sector per sector.

Funcionament general

dd llegeix dades des d’una font i les escriu en un destí especificat, amb la possibilitat de transformar-les durant el procés. Es pot utilitzar per crear imatges de discs, copiar particions, fer còpies de seguretat de dispositius complets o fins i tot escriure fitxers d’arrencada.

Opcions i paràmetres principals
Input (if)

Defineix el fitxer o dispositiu d’origen d’on s’han de llegir les dades.

Output (of)

Especifica el fitxer o dispositiu de destí on s’escriuran les dades.

Block size (bs)

Permet establir la mida dels blocs de dades llegits i escrits. Ajustar aquesta mida pot millorar el rendiment de la còpia.

Count

Indica quants blocs s’han de copiar des de l’origen. Permet limitar la quantitat de dades copiades.

Skip

Permet saltar un nombre determinat de blocs al començar a llegir de l’origen, útil per treballar amb fragments de discs o fitxers grans.

Seek

Permet saltar blocs al destí abans de començar a escriure, facilitant la còpia parcial dins d’un dispositiu o fitxer.

conv

Permet aplicar transformacions a les dades durant la còpia, com per exemple canviar majúscules/minúscules, convertir entre formats o truncar dades.

Status

Mostra informació del progrés de la còpia, útil en operacions amb grans quantitats de dades.


<img width="838" height="402" alt="image" src="https://github.com/user-attachments/assets/4d50189f-63f2-45aa-bcdd-2388e9661969" />


## Automatizació de tasques

cron i anacron son 2 eines de automatitzacio que permeten executar tasques periodiques

cron executa tasques programades en una data i hora especifiques si el sistema esta apagat la tasca es perd es ideal per a tasques en dates i hores concretes i per accions especifiques d'un usuari.

anacron es ideal per executar tasques periodiques on no cal una hora i data especific normalment se utilitza per a tasques de manteniment del sistema i no requereix que el sistema estigui obert perque quan se obri ja l'executara

### Cron i Anacron

El cron es guarda a la ruta /etc/crontab i aixi es com es veu:

<img width="840" height="499" alt="image" src="https://github.com/user-attachments/assets/58a9e222-7c9e-4374-b4d8-f117c07f0028" />

Amb aquesta comanda podem especificar desde quin usuari volem entrar i el primer cop que entrem ens dirá en quin editor volem fer-ho.

<img width="570" height="249" alt="image" src="https://github.com/user-attachments/assets/cca679f2-48c8-4ef4-a2bb-5871b48e834d" />

Amb aquesta ruta podem veure tots els binaris del cron.

<img width="452" height="221" alt="image" src="https://github.com/user-attachments/assets/fa38ebd5-4062-4a01-b029-a349e83eb3a6" />

I aquest es el anacron que esta guardat amb aquesta ruta:

<img width="779" height="309" alt="image" src="https://github.com/user-attachments/assets/14754dd3-3d60-4773-9541-e1c5c360df76" />

Ara he programat un script que conté el següent codi:

<img width="804" height="155" alt="image" src="https://github.com/user-attachments/assets/e9615aee-f127-479b-93df-a709b3ace087" />

Li dono permisos de execució


<img width="565" height="243" alt="image" src="https://github.com/user-attachments/assets/e69df30a-2dfb-4210-b4c3-1afa00092a24" />

Vaig a Documentos i creo 2 imatges que seran les que es copiaran.

<img width="561" height="157" alt="image" src="https://github.com/user-attachments/assets/76327edb-949e-4eda-b21e-a957350bc5f9" />

Copio el script i el poso al cron.daily

<img width="695" height="122" alt="image" src="https://github.com/user-attachments/assets/c9d60722-7dd5-4792-9d85-efaf871edbc2" />

Finalment comprovo que esta alli

<img width="834" height="302" alt="image" src="https://github.com/user-attachments/assets/3fb8e7b7-73ba-4eb3-ac74-ddabc0fbe133" />

I reemplaçem aquest valor per 1.

<img width="774" height="300" alt="image" src="https://github.com/user-attachments/assets/93cc8bf8-3ade-41a6-95de-a5ae7a255eff" />

## Quotes d'usuari

Que es una quota?

En Linux, una quota és un mecanisme de control d’ús d’espai i fitxers dins d’un sistema de fitxers. Serveix per limitar la quantitat de disc o nombre d’inodes (fitxers) que un usuari o grup pot utilitzar, evitant que una sola persona ocupi tot l’espai i afecti la resta de l’equip.

```
edquota -u usuari -> veure quotes un usuari

setquota -u usuari -> establir quotes 1 usuari

repquota /dev/sdc1 -> informe quotes de tots els usuaris el que ocupen

quotaon /mnt/dades -> activar

quotaoff /mnt/dades -> desactivar

quotacheck -cug /mnt/dades -> crear arxius per a quotes usuari i grup si no estan per defecte
```

Per dur a terme aquesta part necesitem instalar el paquet **quota**.

<img width="801" height="534" alt="image" src="https://github.com/user-attachments/assets/14866908-0812-44eb-a86f-ad64ac1cdd42" />

I farem el muntatge de aquesta carpeta permanentment, ademes aquí afegirem usrquota i grpquota per a que puguesim configurar les quotes aqui.

<img width="397" height="123" alt="image" src="https://github.com/user-attachments/assets/a224df27-6d27-4dc3-8aaa-776ac52c2917" />

Fem un reboot i amb aquesta comanda podem comprovar que esta muntat correctament.


<img width="837" height="446" alt="image" src="https://github.com/user-attachments/assets/ff25a286-aa6e-40d9-aa32-9eeabef97492" />

Amb aquesta comanda podem generar els 2 arxius per a les quotes.

<img width="612" height="86" alt="image" src="https://github.com/user-attachments/assets/219e9a5a-f28c-47b9-9026-0a3896d57a76" />

I amb aquesta comanda activem les quotes.

<img width="543" height="99" alt="image" src="https://github.com/user-attachments/assets/e6bbfba1-d5fd-4aa2-9f68-f47641d1a4d5" />

Ara farem la quota per al usuari gina.

<img width="523" height="71" alt="image" src="https://github.com/user-attachments/assets/6e52e0c3-f248-4853-9d46-f2ea1f3c1345" />

I li direm el maxim que pot arribar a gastar en espai amb aquella carpeta.

<img width="809" height="113" alt="image" src="https://github.com/user-attachments/assets/16a970ec-450a-4fcb-973f-1ed45008fa2e" />

Amb aquesta comanda podem veure els dies de gracia.

<img width="714" height="286" alt="image" src="https://github.com/user-attachments/assets/6dec0f6d-5b6f-49e7-8f44-616939219c0c" />

Ara entrem desde el usuari gina i anem a la carpeta aquesta.

<img width="554" height="225" alt="image" src="https://github.com/user-attachments/assets/fa49a9ac-7615-41b3-8adb-5c4c08a286a1" />

Podem veure que per al usuari gina ara ens apareix.

<img width="724" height="181" alt="image" src="https://github.com/user-attachments/assets/2e2a8df5-fd57-4539-aab1-b3235fdae6b0" />

Amb aquesta comanda crearem un arxiu.

<img width="730" height="92" alt="image" src="https://github.com/user-attachments/assets/7b93d97d-894a-458b-b38a-e420f35da5f0" />

I tornem a crear un altre arxiu per a ocupar espai amb aquesta carpeta.


<img width="755" height="102" alt="image" src="https://github.com/user-attachments/assets/a849984a-d0b9-45f9-9c52-cbcc889b2f21" />

Si observem estem apunt de excedirnos del limit.

<img width="727" height="174" alt="image" src="https://github.com/user-attachments/assets/72db7ce4-aa2b-4d58-a78e-d833ac4da60a" />

Finalment crearem un altre arxiu

<img width="755" height="170" alt="image" src="https://github.com/user-attachments/assets/12bde2a5-f469-4b3a-999d-bfdf715827eb" />

I aquest no se ha afegit ja que ens hem excedit.


<img width="576" height="271" alt="image" src="https://github.com/user-attachments/assets/0bfb4120-948d-4b66-9b3c-3df60b33bfa4" />


I si creo un altre arxiu ja no hem deixará.

<img width="755" height="174" alt="image" src="https://github.com/user-attachments/assets/5fc4fba2-33b4-40b7-b7a7-95bc1069d72f" />

Amb aquesta comanda podem modificar els dies de gracia.

<img width="807" height="247" alt="image" src="https://github.com/user-attachments/assets/d3aa6cf9-5d9b-41c1-921e-fa792c834845" />


