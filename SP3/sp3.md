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





































































