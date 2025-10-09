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
#### Pas 1
- A la maquina virtual, activem la seguent opcio:
<img width="877" height="579" alt="image" src="https://github.com/user-attachments/assets/3abcf2cd-9d14-4580-a41a-5f60ca00b557" />

- Posem la ISo de Windows i arranquem fins arribar aqui:
  <img width="595" height="254" alt="image" src="https://github.com/user-attachments/assets/103597d2-c02d-4225-9610-cb2b2cb441e4" />
  <img width="639" height="306" alt="image" src="https://github.com/user-attachments/assets/f6586b35-be7b-43e8-925d-b035614ba9b9" />

- Instalem Windows a la particio lliure:

  <img width="642" height="474" alt="image" src="https://github.com/user-attachments/assets/c1fac733-d1d9-4f22-bffd-19780207e716" />

- Creem cuenta domini:
  <img width="569" height="402" alt="image" src="https://github.com/user-attachments/assets/1f0fa471-d29d-48b6-8fde-e1d9fb847a3f" />

- I ja tenim windows instalat:
  <img width="608" height="768" alt="image" src="https://github.com/user-attachments/assets/0a1aeded-b73b-4804-b240-df4d49b47338" />

#### Pas 1
- Per recuperar el grub posem la iso de Super-Grub2:
  <img width="463" height="253" alt="image" src="https://github.com/user-attachments/assets/12e1d3ef-9b08-4e02-946f-efdcff2f0886" />
  
  - entrem al boot menu de vbox
    <img width="622" height="316" alt="image" src="https://github.com/user-attachments/assets/3630cc08-41c2-4057-a697-1665c3f871ea" />

  - Seleccionem "detect and show boot methods":
      <img width="475" height="232" alt="image" src="https://github.com/user-attachments/assets/0fc802dc-88d6-472a-acd5-6d6621441f27" />

  - i hem de buscar grub.cfg de ubuntu:
    <img width="593" height="305" alt="image" src="https://github.com/user-attachments/assets/254bad85-31c9-4c2e-9430-b800220b71c5" />

  - Un cop entrem a Ubuntu, executem les seguents comandes per arreglar el grup desde el terminal, per que finalment ens surtigue el que es veu a la imatge:
  <img width="516" height="116" alt="image" src="https://github.com/user-attachments/assets/c173a3f0-381c-4b02-acc8-963eca7527b4" />
  <img width="437" height="56" alt="image" src="https://github.com/user-attachments/assets/ad983333-33b0-4fce-ae51-2deab0c26e3b" />
  <img width="673" height="94" alt="image" src="https://github.com/user-attachments/assets/8d9dc0cc-9ecd-4832-8dab-f1858ed559d8" />
  
- Reiniciem i veurem que ja entrem al grub per poder seleccionar ubuntu o windows
   <img width="634" height="182" alt="image" src="https://github.com/user-attachments/assets/d9b6c5ed-2b03-4e73-ad19-decb42bae7d5" />




## Punts de restauracio
## Configuracio de la xarxa
## Comandes generals i instal.lacions
