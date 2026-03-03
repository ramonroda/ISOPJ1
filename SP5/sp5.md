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

Ara enviem  un log notice a prova mireia 2  
<img width="653" height="23" alt="image" src="https://github.com/user-attachments/assets/587810e2-8527-4ee0-b6b8-0e139bcbdfec" />

comprobem que arriba al tail 



