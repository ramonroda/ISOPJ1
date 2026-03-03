## Configuracio previa
Hem de posar tant el server com el client amb la mateixa xarxa, amb el meu cas amb el nom "NatNetwork"
<img width="696" height="366" alt="image" src="https://github.com/user-attachments/assets/0c0dd486-7ecc-4f5a-b084-6fb591aa3920" />

<img width="496" height="316" alt="image" src="https://github.com/user-attachments/assets/6e7cb857-b455-4b5d-b8d5-abd7bc9e5f0f" />


## Configuracio del server

En primer lloc, accedim a un terminal dins de la màquina servidor i executem l’ordre ip a per consultar quina adreça IP li ha estat assignada mitjançant DHCP. Un cop identificada aquesta adreça, procedim a configurar-la manualment com a IP estàtica utilitzant la interfície gràfica. És imprescindible que un servidor disposi d’una adreça IP fixa, ja que si fos dinàmica podria variar amb el temps i dificultar l’accés als serveis que ofereix. Disposar d’una IP estàtica garanteix estabilitat, accessibilitat constant i una correcta comunicació amb els clients de la xarxa.

<img width="586" height="478" alt="1" src="https://github.com/user-attachments/assets/5cf91aff-5bfc-4800-95af-b8de0313f9c4" />

Posteriorment, accedim al fitxer /etc/hosts, on associarem el nou hostname a l’adreça de loopback del sistema. A més, afegirem el domini que es crearà més endavant, vinculant-lo a l’adreça IP estàtica que hem configurat prèviament. Aquest pas és fonamental per garantir una correcta resolució de noms dins del sistema

<img width="577" height="258" alt="3" src="https://github.com/user-attachments/assets/a1a0cd17-53d8-4989-9806-4b3130cbd908" />

Tot seguit, procedim a instal·lar els serveis necessaris per poder desplegar i administrar el servei LDAP dins del sistema.

<img width="512" height="117" alt="4" src="https://github.com/user-attachments/assets/bb440af8-13a3-4bba-96f8-445d5a143576" />

Al llarg del procés d’instal·lació, el sistema sol·licitarà l’establiment d’una contrasenya per a l’usuari administrador del servei LDAP. És important conservar-la, ja que serà necessària per a futures tasques d’administració i configuració.

<img width="816" height="313" alt="5" src="https://github.com/user-attachments/assets/6460f6d7-411e-4bb5-b7a4-d2e1e49ee1e6" />

Per comprovar el contingut del domini, podem utilitzar l’ordre slapcat, la qual permet visualitzar tots els elements i entrades que formen part del directori LDAP.

<img width="586" height="274" alt="6" src="https://github.com/user-attachments/assets/79c3a1ba-03fe-4060-a8f3-6cf172b57377" />

Ara, anem a baixades, i descomprimim el fitxer arxius.zip.

<img width="468" height="200" alt="7" src="https://github.com/user-attachments/assets/0ef38d27-6da0-43aa-9742-66603f9a58ef" />

Mitjançant l’ordre dpkg-reconfigure slapd és possible tornar a configurar el servei LDAP i afegir nous elements al domini d’una manera més senzilla i guiada. Com a alternativa, també es poden utilitzar els fitxers de configuració .ldif que hem descomprimit prèviament, tot i que aquest mètode resulta menys còmode i més complex de gestionar.

<img width="459" height="138" alt="8" src="https://github.com/user-attachments/assets/05650d77-625c-4aea-8df1-eb85282b0353" />

A continuació, afegim al fitxer /etc/hosts el domini que havíem definit anteriorment, de manera que quedi correctament associat i reconegut pel sistema.

<img width="731" height="301" alt="9" src="https://github.com/user-attachments/assets/2f177331-76c7-4cf9-9dda-dee0147edf9b" />

Nom de l'organització.

<img width="723" height="301" alt="10" src="https://github.com/user-attachments/assets/25eccc4c-a3fb-446c-9fe0-be64edf1e433" />

Eliminem la base de dades en purgar.

<img width="728" height="302" alt="11" src="https://github.com/user-attachments/assets/245663a1-01ed-4beb-81d4-76880a9f9f16" />

Finalment, desplacem la base de dades anterior i executem l’ordre slapcat per verificar que tots els canvis configurats s’han aplicat correctament i que el directori LDAP funciona tal com s’esperava.

<img width="761" height="323" alt="12" src="https://github.com/user-attachments/assets/3b8cffbf-696d-462d-b4c2-0227f2c17870" />

En aquest punt, encara no s’han creat elements com usuaris, grups o unitats organitzatives; tot i això, el domini ja es troba correctament configurat i operatiu.

<img width="617" height="575" alt="13" src="https://github.com/user-attachments/assets/7185ef65-30f2-46c6-9878-b4f83a1f0126" />

### Creacio de elements a ldap

A continuació, procedirem a crear una unitat organitzativa. Per fer-ho, utilitzarem el fitxer uo.ldif, un dels arxius que hem descomprimit prèviament, el qual ens servirà com a plantilla per definir aquesta nova estructura dins del domini.

<img width="332" height="248" alt="14" src="https://github.com/user-attachments/assets/e29e967f-7ef1-49e6-b6c0-e3a161d57884" />

Per importar el contingut del fitxer al directori LDAP, executem l’ordre:

<img width="835" height="213" alt="15" src="https://github.com/user-attachments/assets/20a720c4-f1ea-49f2-9aed-6c9e50c6c844" />

Ara, afegirem un usuari amb usu.ldif

<img width="552" height="440" alt="16" src="https://github.com/user-attachments/assets/d9f95166-5d16-4298-b2cf-40ec43d00f6e" />

I executarem la comanda:

<img width="847" height="145" alt="17" src="https://github.com/user-attachments/assets/2f8a0174-0c68-4d1b-96aa-c68ca72db4df" />

El mateix per crear un grup

<img width="501" height="215" alt="18" src="https://github.com/user-attachments/assets/4c24052d-e37a-4a3f-b66d-7c2b68d099ff" />

Ja fet tot al server pasem al client

### Configuració del client

Provem de intentar fer un ping al servidor.

<img width="650" height="249" alt="20" src="https://github.com/user-attachments/assets/1ba83b2f-f28b-480b-803b-ded5e5c33058" />

Ens hem de descarregar els següents paquets:

<img width="807" height="145" alt="19" src="https://github.com/user-attachments/assets/ee546bf3-5346-49fa-b0aa-7c90c84746b5" />

Durant el procés d’instal·lació, es mostrarà un assistent de configuració que sol·licitarà la introducció de l’adreça IP corresponent al domini.

<img width="713" height="429" alt="21" src="https://github.com/user-attachments/assets/758a0126-76ba-433a-9e04-811f8ba1fc71" />

El nom

<img width="636" height="324" alt="22" src="https://github.com/user-attachments/assets/e777d245-ceb2-4a5f-8744-42181bf55f6a" />

Versio (3)

<img width="483" height="315" alt="23" src="https://github.com/user-attachments/assets/238feaa0-d7a2-436f-8541-8df551a23512" />

Deixem per defecte i premem "si"

<img width="639" height="384" alt="24" src="https://github.com/user-attachments/assets/63520d7c-bd8a-460b-8d33-8fcd7fcc6e0e" />

<img width="702" height="354" alt="25" src="https://github.com/user-attachments/assets/65bbaf5d-f8b7-477f-8a54-3e5921999fe2" />

Administrador

<img width="448" height="288" alt="26" src="https://github.com/user-attachments/assets/a754377b-c3c6-4251-b553-5528ddb01097" />

MD5

<img width="532" height="353" alt="27" src="https://github.com/user-attachments/assets/573616a1-3c03-45aa-98fe-85f3837b7b92" />

Modifiquem /etc/pam.d/common-session

<img width="789" height="463" alt="29" src="https://github.com/user-attachments/assets/79b3bfe6-cde6-4890-9399-ee8ffcf773ce" />

Modifiquem /etc/pam.d/common-password

<img width="1213" height="712" alt="28" src="https://github.com/user-attachments/assets/7ce59ee1-d843-4e53-8c0b-c9d880bcc539" />

Ara, modificarem /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf.

<img width="938" height="186" alt="30" src="https://github.com/user-attachments/assets/f1e7dea2-143f-42a2-8929-e0952fcca98b" />

<img width="833" height="73" alt="31" src="https://github.com/user-attachments/assets/71aa57f5-7cee-448a-a734-70d87e81a56b" />

Al reiniciar auriem de poder iniciar com a a alu1 (o el nostre nou usuari ldap)

<img width="477" height="383" alt="image" src="https://github.com/user-attachments/assets/97026251-08d0-48de-92e4-a8113d541abe" />

## SAMBA 
Samba fa que un servidor Linux “parli el mateix idioma” que Windows

## Configuracio Server SMB
Instal.lem el paquet samba

<img width="415" height="112" alt="1" src="https://github.com/user-attachments/assets/fb8833d1-071c-42cc-90e0-e79d21ccd1c0" />

Despres creem la carpeta que es vol compartir, assignant-li permisos totals per a tots els usuaris, sense establir cap usuari ni grup com a propietaris.

<img width="601" height="170" alt="2" src="https://github.com/user-attachments/assets/8fb07ab1-1b78-4d41-9cd9-6498b99a6bd3" />

Ara he creat els usuaris edgar, naim i eros sense accés interactiu al sistema, així com la creació del grup madrid i l’assignació dels usuaris edgar i eros a aquest grup. Finalment, es verifica la creació dels usuaris mitjançant el fitxer /etc/passwd.ç

Assignem contrasenyes

<img width="304" height="242" alt="12(passwd)" src="https://github.com/user-attachments/assets/f31fa558-92c7-4ef7-8e7c-b05752f85ca6" />


<img width="455" height="358" alt="3" src="https://github.com/user-attachments/assets/4631c741-2456-4ffd-a862-a67c7613e85b" />

Per configurar el recurs compartit cal editar el fitxer /etc/samba/smb.conf. S’hi defineix la ruta de la carpeta mitjançant l’opció path.
Es permet l’accés a usuaris anònims o convidats amb guest ok. Els directoris creats tindran una màscara de permisos 0755 (directory mask).
Es permet navegar pel recurs (browseable), no és només de lectura (read only = no) i permet l’escriptura (writable = yes). Els permisos de lectura es concedeixen al grup @madrid, a l’usuari naim i al convidat. Només l’usuari naim i el convidat poden escriure al recurs. Finalment, es bloqueja explícitament l’accés a l’usuari edgar.

<img width="461" height="434" alt="4" src="https://github.com/user-attachments/assets/15f5f3f7-01f6-4c5c-92b8-3ef5ba6dfc67" />

Reiniciem els serveis i comprovem que estiguen actius

<img width="499" height="540" alt="5" src="https://github.com/user-attachments/assets/5694f9c5-d773-4ac4-9d15-2de14aa0df6f" />

## Configuracio client smb

Comprovem ping amb el servidor

<img width="613" height="121" alt="6" src="https://github.com/user-attachments/assets/ae9ffb9b-9df0-455b-a27a-8e4608e151fc" />

Instalem el paquet smbclient

<img width="461" height="33" alt="7" src="https://github.com/user-attachments/assets/a26a8f54-df01-494b-9118-2be47488fe79" />

I ja pdem connectar-nos mitjançant el navegador de fitxers

<img width="441" height="43" alt="8" src="https://github.com/user-attachments/assets/dfd91cdc-2311-4a8c-9cb0-f85abe95f618" />

### Prova amb usuari anonim

He provat amb l'anonim i he pogut conectarme, crear carpeta i esborar-la

<img width="442" height="203" alt="9" src="https://github.com/user-attachments/assets/36d1f7c3-0b7e-44be-afcd-0d37dd008c8e" />

<img width="231" height="131" alt="10" src="https://github.com/user-attachments/assets/066eeb22-ec65-43e8-b382-3685905227c1" />

Per desconectarmos hem de clicar on surt a la imatge

<img width="304" height="332" alt="11" src="https://github.com/user-attachments/assets/1608f633-0a1d-4b9b-8acb-e88906e6031d" />

### Prova amb usuari naim

Te permis per tot

<img width="571" height="436" alt="13" src="https://github.com/user-attachments/assets/7c4cbc15-fe9c-45f4-b206-5a431d2b3bb1" />

<img width="465" height="186" alt="14" src="https://github.com/user-attachments/assets/14791559-6c0a-402d-a31f-06073d3a57a5" />

<img width="421" height="148" alt="15" src="https://github.com/user-attachments/assets/08645e20-1bf2-4387-9807-17bdcada6287" />

### Prova amb usuari eros

Pot accedir pero no crear ni eliminar directoris o fitxers.

<img width="574" height="431" alt="16" src="https://github.com/user-attachments/assets/6bdcec73-8173-424d-ace7-ec163bd850b3" />

<img width="445" height="239" alt="17" src="https://github.com/user-attachments/assets/de8f7866-fb78-478c-b59b-ebec2bcfb8f5" />

<img width="634" height="220" alt="18" src="https://github.com/user-attachments/assets/b905c610-0bcb-49bd-befa-bee0b2bb0ddd" />


## NFS

### Configuracio server

Es un protocol que permet compartir carpetes i archius (no impresores), a traves de una xarxa local la autenitcacio se fa atraves de host, no de usuari, a diferencia de samba, i poden accedir tant clients windows com linux.

Primer exercisi nfs sense ldap. Primer instalem el paquet de nfs

<img width="594" height="112" alt="1" src="https://github.com/user-attachments/assets/c6af8938-7998-478f-9085-492316b17acf" />

Creem la carpeta compartida per fer les proves i li donem els permisos

<img width="640" height="246" alt="1" src="https://github.com/user-attachments/assets/f8f646d6-8e53-422d-8d91-38998a2f532c" />

Ara la compartim via nfs, primer editem l'archiu etc/exports, i hem de posar la carpeta i el filtre

<img width="500" height="338" alt="1" src="https://github.com/user-attachments/assets/bd5565d8-b55f-4292-b9b6-a3dc917cf6ef" />

Ara hem de reiniciar el servei i comprovar que esta actiu

<img width="730" height="240" alt="1" src="https://github.com/user-attachments/assets/83412ea6-df9b-43e4-97ab-cfd69b809d19" />

Creem una carpeta per veure si al client tambe la veurem

<img width="328" height="76" alt="1" src="https://github.com/user-attachments/assets/f6eb2403-1c08-4f7e-b201-1bed6981f594" />

### Configuracio client

Primer instalem el paquet nfs-common i rpcbind

<img width="635" height="271" alt="1" src="https://github.com/user-attachments/assets/ad2aaba6-d7a3-446e-ae65-a8870b345cd5" />

El ateix que el server, creem carpeta i donem permisos

<img width="629" height="342" alt="1" src="https://github.com/user-attachments/assets/2245b245-1a8b-4610-ba3f-f02cdc8cdd34" />

Editem el archiu fstab i posem la ip del server l'archiu, l'archiu...

<img width="832" height="362" alt="1" src="https://github.com/user-attachments/assets/d1534df7-49a3-40f9-ae5c-deb84f7177b3" />


Ara per comprovar que tot ha anat be, anem a l'archiu prova i amb un ls auriem de veure "hola"

<img width="614" height="152" alt="1" src="https://github.com/user-attachments/assets/be7b40c5-37ce-4de0-b6da-4d594cf3b190" />

Amb ldap

<img width="387" height="210" alt="1" src="https://github.com/user-attachments/assets/da7afedc-5a37-488a-8ecf-406c203769ab" />

I editem el exports

<img width="642" height="342" alt="1" src="https://github.com/user-attachments/assets/fd8ee28a-fcf3-43db-bdee-929015bee3cd" />

Al client hem de crear homes

<img width="403" height="90" alt="1" src="https://github.com/user-attachments/assets/1af6efad-0f97-42de-b81b-8f83270176db" />

I editem el fstab

<img width="835" height="367" alt="1" src="https://github.com/user-attachments/assets/c9b40828-01bb-4341-9a9d-2f300efa5050" />

ara afegirem a marcel

<img width="649" height="444" alt="1" src="https://github.com/user-attachments/assets/c106ef42-a93d-4a4e-a8cb-81f99675db6a" />

<img width="726" height="105" alt="1" src="https://github.com/user-attachments/assets/fe275478-2a98-4772-9abf-3abb45801650" />

<img width="494" height="168" alt="1" src="https://github.com/user-attachments/assets/b4ecff5a-c5be-42fa-bc6f-f865c26ff7f0" />


