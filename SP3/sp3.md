### Configuracio del server

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




















