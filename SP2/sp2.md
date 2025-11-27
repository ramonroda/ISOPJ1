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


### Fitxers importants
### Comandes basiques
### Directoris i fitxers importants
### Gestio avançada
### PAM
