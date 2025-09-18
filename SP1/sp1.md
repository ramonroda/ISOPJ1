---
layout: defaut
title: "Sprint 1: Instal.lacio i Configuracio Inicial"
---

## Virtualitzacio i Instal.lacio del SO Ubuntu

#### Pas 1
- Primerament obrirem Virtualbox i polsarem a "nova", seguidament ens obrira una pagina on aurem de posar-li un nom a la 
maquina virtual, amb el meu cas "Ubuntu 22.04" tal com es veu a la imatge i polsarem "Endavant":

<img width="858" height="469" alt="image" src="https://github.com/user-attachments/assets/34006d87-4824-4670-8bee-d6d257101e67" />

- Escollim la RAM i nuclis de CPU que volem per la maquina:

<img width="861" height="467" alt="image" src="https://github.com/user-attachments/assets/27d3addf-aa48-43fd-b1f6-b2658fb9f5f6" />

- Escollim l'espai que volem assignar al disc dur de la maquina, polsarem "Endavan" i "Finish":

<img width="726" height="443" alt="image" src="https://github.com/user-attachments/assets/fc3b42c9-8e00-4f87-9073-057c0d043a6c" />

#### Pas 2 
- Abans d'iniciar la maquina, hem de posar la iso amb el sistema operatiu, anem a parametres de la maquina i a "Emmagatzematge", premem on es veu a la image i la afegim:
<img width="875" height="541" alt="image" src="https://github.com/user-attachments/assets/d8268c87-6607-46b1-95b8-32c8d55c7246" />

- I a xarxa, posem xarxa nat, ja que Les màquines virtuals dins de la mateixa xarxa NAT poden connectar-se entre elles i igual que amb nat, te sortida a internet
<img width="872" height="546" alt="image" src="https://github.com/user-attachments/assets/973b28f5-66c3-4437-ac35-c54d8b429beb" />


- Iniciem la maquina:
<img width="383" height="89" alt="image" src="https://github.com/user-attachments/assets/bc058112-80d2-422d-8f53-64a937cf4bea" />

---

### Particions
- Per a l'apartat de particions, he creat les particions normals (/home, /boot, /) i /swap, perque com tenim 4gb de RAM, si es plena, el sistema pot utilitzar la partició
swap com a memòria extra, quedaria aixi (he posat un terminal per que veigues que la captura es feta per mi):
<img width="821" height="639" alt="image" src="https://github.com/user-attachments/assets/06594374-441c-4c0a-a89a-60bccf05ba70" />



## Llicenciament
- Ubuntu com a tal utilitza la "GNU GPLv2" per al seu nucli i a la majoria de les seues aplicacions, pero Ubuntu es una distribució de GNU/Linux, i no té una sola
  llicència, sinó una combinació de llicències de programari lliure i codi obert com ara GPL, LGPL, MIT... Aquesta llicència asegura que el codi sigui lliure i que qualsevol
  modificació també te de ser lliure.
  <img width="357" height="200" alt="image" src="https://github.com/user-attachments/assets/1170e64e-5fe9-4ded-b0e5-fd0c5cfd46c1" /> <img width="200" height="200" alt="image" src="https://github.com/user-attachments/assets/0e431ffd-b61c-4b5b-8823-c3c653192151" /> <img width="357" height="200" alt="image" src="https://github.com/user-attachments/assets/b4edc107-2e67-4478-a2b0-2c7d1f198da8" />




## Gestors d'arrencada per a instal.lacions DUALS
## Punts de restauracio
## Configuracio de la xarxa
## Comandes generals i instal.lacions
