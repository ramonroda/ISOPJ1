## LOGS (Ramon i Ofkir)

### directoris i fixer importans
La carpeta principal on es guarden els logs es la carpeta /var/log

<img width="780" height="826" alt="image" src="https://github.com/user-attachments/assets/b5ab52ce-3937-4b40-95c3-fa101f0102ad" />

El fixer syslog guarda tots els logs generals del sistema

<img width="971" height="909" alt="unnamed" src="https://github.com/user-attachments/assets/1c4363ef-002e-437d-acd6-69c9a87b5ff7" />

La carpeta log rotate serveix per indicar cada cuant guarda un log com .zip i cada cuan el elemina
<img width="933" height="128" alt="image" src="https://github.com/user-attachments/assets/733c1415-70a4-4419-96fd-aecb5ccca322" />

Aqui indiqum que els logs messages nomes 4 .zip

<img width="968" height="521" alt="unnamed" src="https://github.com/user-attachments/assets/d1750ef9-5ada-4375-bb7d-6f291174c1c6" />

El fixer 50-default.conf sirve para configurar en quin fixxer es guaren el logs.

<img width="999" height="904" alt="unnamed" src="https://github.com/user-attachments/assets/c9a23c8f-7127-4347-8417-c7cdff32c849" />

### proves

per fer les proves hem fet un tail -f a syslog

<img width="932" height="425" alt="unnamed" src="https://github.com/user-attachments/assets/5e1a2dc1-0fef-4cb0-ab3b-19ae643d65c6" />

Ahora generem un log de mail

<img width="639" height="22" alt="image" src="https://github.com/user-attachments/assets/1881874d-1eb8-401f-954e-47815dfc77f4" />

Comprobem que se ha generat al tail

<img width="948" height="436" alt="unnamed" src="https://github.com/user-attachments/assets/162a8df9-ebe9-4e8b-aa19-0d6293066274" />

ara al fixer 50-default.conf editem la configuracio de mail per a que cuan surti un log de err(error) el envie mail.log.

<img width="948" height="436" alt="unnamed" src="https://github.com/user-attachments/assets/162a8df9-ebe9-4e8b-aa19-0d6293066274" />
 al modifica el fixer 50-default.conf hem de renciar el servei rsyslog
 
 <img width="569" height="24" alt="image" src="https://github.com/user-attachments/assets/abf42701-4264-4f0f-b77e-01f0b9e4f384" />

Ara enviem  un log notice a prova mireia 2  
<img width="653" height="23" alt="image" src="https://github.com/user-attachments/assets/587810e2-8527-4ee0-b6b8-0e139bcbdfec" />

comprobem que arriba al tail 

<img width="524" height="134" alt="Captura de pantalla de 2026-03-02 12-21-07" src="https://github.com/user-attachments/assets/5d13f1b1-83cd-42dd-af02-3ef3ac7c96ab" />

Ara si fem un cat /var/log/mail.log | grep prova, podem comprobar que surt prova mireia pro no prova mireia 2 ja que hem configurat que nomes guarde logs de error 

<img width="672" height="86" alt="Captura de pantalla de 2026-03-02 12-21-16" src="https://github.com/user-attachments/assets/2ddfa018-6d8f-4f68-8941-8b4376c9e42f" />

Ara fiquem mail.err la diferencia en tre fer mail.=err es que ara guardara tant els logs de error com el logs que tingen un problema mes greu.

<img width="699" height="93" alt="Captura de pantalla de 2026-03-02 12-25-28" src="https://github.com/user-attachments/assets/6de13fc1-9a22-4a45-9abd-abcd666b4ce3" />

Ara enviem un log de err com a mireia prova 3

<img width="569" height="24" alt="image" src="https://github.com/user-attachments/assets/9328f7e6-2f0a-4191-acc1-f2c67050d291" />

comprovem que el log surt al tail

<img width="478" height="87" alt="Captura de pantalla de 2026-03-02 12-24-17" src="https://github.com/user-attachments/assets/4a70bdaa-86e3-4e66-9e5d-cbccd0b92ef6" />

ara comprobem que al fixer mail .log se agi creat

<img width="705" height="109" alt="Captura de pantalla de 2026-03-02 12-24-23" src="https://github.com/user-attachments/assets/59063717-03e2-4a2d-a54d-0383ea9c6537" />

Ara enviem com a prova mireeia 5 un log crit 

<img width="648" height="23" alt="image" src="https://github.com/user-attachments/assets/1ddf6db2-3cbd-48dc-b264-6cf86b24da15" />


ara comprobem que al fixer mail.log surte ja que crit es mes greu que err

<img width="596" height="96" alt="image" src="https://github.com/user-attachments/assets/61550a00-7914-4c9d-910b-96a20fe45e15" />

Ara podem fer que tots els logs critics ariben al fixe mireia.log

<img width="556" height="34" alt="image" src="https://github.com/user-attachments/assets/abd0d8d2-4e7b-4719-9b72-5e0af00b56e4" />

Enviem com cron un error critic 

<img width="648" height="126" alt="Captura de pantalla de 2026-03-02 12-28-46" src="https://github.com/user-attachments/assets/fc133a56-cf7c-42ba-a8d2-b7c3e3736192" />

fem un cat a mireia.log

<img width="652" height="86" alt="Captura de pantalla de 2026-03-02 12-29-00" src="https://github.com/user-attachments/assets/4b08a317-b4f8-448e-b6c4-787f0ff2bb36" />

i comprobem que a arribat el log

### journalctl
Amb la opcio -p podem filtra per el tipus de log 

<img width="921" height="324" alt="Captura de pantalla de 2026-03-02 12-30-48" src="https://github.com/user-attachments/assets/fa59fb05-740e-4fea-9298-60c35e85a3e5" />

amb la opcio --facility podem filtra per servei

<img width="705" height="198" alt="Captura de pantalla de 2026-03-02 12-33-20" src="https://github.com/user-attachments/assets/f37bed72-8488-4c38-b2f4-dc31bef4b67a" />

### Part 2
#### Servidor (reb els logs)

<img width="745" height="419" alt="image" src="https://github.com/user-attachments/assets/4be29713-8da3-4a7f-a78a-c2db8d6a884d" />

<img width="745" height="419" alt="Captura de pantalla de 2026-03-03 13-55-03" src="https://github.com/user-attachments/assets/4c2b80e6-a331-44f5-8995-9202134e99a1" />



<img width="726" height="258" alt="Captura de pantalla de 2026-03-03 13-55-58" src="https://github.com/user-attachments/assets/66d24f86-6fa1-4aed-bbf5-cbc59fb05321" />

<img width="556" height="106" alt="Captura de pantalla de 2026-03-03 13-56-13" src="https://github.com/user-attachments/assets/103e3c94-1209-40ff-807c-59b360c9580d" />

<img width="877" height="164" alt="image" src="https://github.com/user-attachments/assets/f2e33e07-a6b0-47d7-8793-5915213da61c" />


