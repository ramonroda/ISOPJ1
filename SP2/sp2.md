### Sprint 2: Instal·lació, Configuració de Programari de Base i Gestió de Fitxers
## Sistemes de fitxers i particions
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
Canvi temporal (en sessió Shell)
Es pot modificar la umask directament amb la comanda umask + mascara.
Aquest canvi només és vàlid mentre dura la sessió actual.
En l’exemple, s’ha provat amb l’usuari root, aplicant 001, cosa que permet lectura i escriptura al grup i a altres usuaris. No és recomanable, ja que pot exposar fitxers i permetre execució o modificacions no desitjades.
Per fer que la configuració sigui permanent per a futurs usuaris, s’ha editat el fitxer /etc/login.defs, establint una umask fixa. S’ha configurat 077, de manera que només l’usuari propietari té permisos complets sobre els fitxers i directoris que crea.

<img width="736" height="466" alt="image" src="https://github.com/user-attachments/assets/77bc6b15-0ab5-4c32-8ec6-65bf35c070a2" />



















