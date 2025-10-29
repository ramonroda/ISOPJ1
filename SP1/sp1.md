---
layout: defaut
title: "Sprint 1: Instal.lacio i Configuracio Inicial"
---

## Virtualitzacio i Instal.lacio del SO Ubuntu

#### Pas 1
- Primerament obrirem Virtualbox i polsarem a "nova", seguidament ens obrira una pagina on aurem de posar-li un nom a la 
maquina virtual, amb el meu cas "Ubuntu 22.04" tal com es veu a la imatge i polsarem "Endavant":
-
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
  
- Entrem al boot menu de vbox
<img width="622" height="316" alt="image" src="https://github.com/user-attachments/assets/3630cc08-41c2-4057-a697-1665c3f871ea" />

- Seleccionem "detect and show boot methods":
<img width="475" height="232" alt="image" src="https://github.com/user-attachments/assets/0fc802dc-88d6-472a-acd5-6d6621441f27" />

- I hem de buscar grub.cfg de ubuntu:
<img width="593" height="305" alt="image" src="https://github.com/user-attachments/assets/254bad85-31c9-4c2e-9430-b800220b71c5" />

- Un cop entrem a Ubuntu, executem les seguents comandes per arreglar el grup desde el terminal, per que finalment ens surtigue el que es veu a la imatge:
<img width="516" height="116" alt="image" src="https://github.com/user-attachments/assets/c173a3f0-381c-4b02-acc8-963eca7527b4" />
<img width="437" height="56" alt="image" src="https://github.com/user-attachments/assets/ad983333-33b0-4fce-ae51-2deab0c26e3b" />
<img width="673" height="94" alt="image" src="https://github.com/user-attachments/assets/8d9dc0cc-9ecd-4832-8dab-f1858ed559d8" />
  
- Reiniciem i veurem que ja entrem al grub per poder seleccionar ubuntu o windows
<img width="634" height="182" alt="image" src="https://github.com/user-attachments/assets/d9b6c5ed-2b03-4e73-ad19-decb42bae7d5" />

## Punts de restauracio
- Instal.lem timeshift amb la comanda "sudo apt install timeshift":
<img width="518" height="21" alt="image" src="https://github.com/user-attachments/assets/2afa5d7b-5afc-4310-98e1-662502752998" />

- creem la particio amb: fdisk /dev/sdb i seguim amb els seguents pasos:
<img width="873" height="348" alt="image" src="https://github.com/user-attachments/assets/9e31b5c7-93e7-4541-9687-2d8180ca9fea" />

- Amb "sudo fdisk -l" veurem que ja tenim sdb1 en 15gb:
<img width="615" height="193" alt="3" src="https://github.com/user-attachments/assets/1885b373-6d64-430c-994b-ff6a912e9138" />

- Formatem:
<img width="782" height="238" alt="image" src="https://github.com/user-attachments/assets/e2d2b9fc-8c78-4bb9-a77a-4a9c34ef19e4" />

- Per a comprovar si al fer la instantanea es guarda tot, creem archiu:
<img width="920" height="146" alt="5" src="https://github.com/user-attachments/assets/f87e72d3-4ba8-4f09-9f00-13bc178b7e24" />

- Obrim timeshift i seleccionem el disc formatat:
<img width="599" height="233" alt="7" src="https://github.com/user-attachments/assets/06663d9c-46b1-40f8-9805-fe1414b8530a" />

- Seleccionem cuan es que volem que es faiguin les instantanies:
<img width="519" height="351" alt="8" src="https://github.com/user-attachments/assets/f9b8db10-9a45-4874-9e7c-2995f4efcb9d" />

- Seleccionem del que volem fer la instantanea:
<img width="719" height="252" alt="9" src="https://github.com/user-attachments/assets/a2b7603f-d1bd-4a99-93b6-db2d676e1253" />

-Borrem els archius que haviem creat avans i recuperem la instantanea:
<img width="509" height="220" alt="12" src="https://github.com/user-attachments/assets/d754a7a2-e624-412a-a8db-ae8f5d218930" />
<img width="511" height="187" alt="11" src="https://github.com/user-attachments/assets/53dbda31-c76e-4417-b0fd-6baed2ab94cb" />
<img width="826" height="623" alt="13" src="https://github.com/user-attachments/assets/5b4acff9-6209-455b-b525-bec580556710" />
<img width="507" height="150" alt="14" src="https://github.com/user-attachments/assets/02628d38-84ad-4658-9533-0f6ae3d332ad" />

- i si tot a hanat be, ens aurien de sortir els archius creats que haviem borrat:
<img width="536" height="74" alt="16" src="https://github.com/user-attachments/assets/8c613f4b-f346-4866-906e-8c8250bc953b" />

## Configuracio de la xarxa
- fem ip a per veure la nostra ip:
<img width="936" height="230" alt="image" src="https://github.com/user-attachments/assets/95b4ed06-e3d9-4fcd-a82a-e4fb02c2dc73" />

- Assignem IP, mascara, gateway i dns manualment per interficie grafica, i comprovarem que funciona fen un ping a google:
<img width="590" height="480" alt="image" src="https://github.com/user-attachments/assets/1187e31f-7950-47a1-a07a-5899e9c0096a" />
<img width="723" height="257" alt="image" src="https://github.com/user-attachments/assets/80088f52-44ed-4298-8136-5840deaf3769" />

- Ara farem el mateix per terminal amb netplan, editem el fitcher "etc/ntplan/tabulem" i posem el seguent:
<img width="393" height="304" alt="18" src="https://github.com/user-attachments/assets/2a709fa0-d76e-4224-848b-d6828ab9bec2" />

- Apliquem i comprovem:
<img width="808" height="328" alt="image" src="https://github.com/user-attachments/assets/c30c2bae-6831-42e8-86ae-97ddef0535db" />

## Comandes generals i instal.lacions
<img width="434" height="34" alt="image" src="https://github.com/user-attachments/assets/01eaa5a3-41a1-49a2-89eb-679c0295563d" />

- Amb la comanda "apt-cache policy htop", veem quin es el candidat:
<img width="687" height="163" alt="image" src="https://github.com/user-attachments/assets/8751a62e-60ed-420b-8a91-bfc9462d118f" />

- Per a canviar el candidat preferit, crearem amb nano "/etc/apt/preferences.d/htop.pref" i afegirem el seguent:
<img width="563" height="168" alt="image" src="https://github.com/user-attachments/assets/e76dc5ee-3691-4f4b-9316-9439a7f92a7f" />

- Actualitzem i comprovem:

<img width="455" height="109" alt="image" src="https://github.com/user-attachments/assets/fa4d57e3-c0ec-4f7c-a8aa-5ce5c1a0b87e" />
