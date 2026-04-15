# Instal·lació del sistema operatiu

## – Crear la màquina virtual amb VirtualBox

* El primer pas serà crear una màquina virtual nova.

<img width="64" height="79" alt="image" src="https://github.com/user-attachments/assets/089160e8-5503-4738-848f-eb3928d6274f" />

## Assignar recursos (RAM mínima 4 GB, disc mínim 40 GB)

* En aquest apartat configure els recursos de maquinari que tindrà la màquina virtual:

    1. **Memòria base: 6144 MB (6 GB)** – una quantitat adequada per a Windows 10.
    2. **Processadors: 2 CPUs** – per assegurar un funcionament fluid.
  
  <img width="395" height="97" alt="image" src="https://github.com/user-attachments/assets/cac6384f-88ec-43fd-8ce8-e16fd1fb6a30" />

<img width="355" height="174" alt="image" src="https://github.com/user-attachments/assets/344909d5-6807-4ae8-a3fa-7d7ebb5b04e4" />

## – Carregar la ISO de Windows 10.

* En aquest punt seleccione, en el meu cas, la imatge ISO de Windows 10.

<img width="269" height="137" alt="image" src="https://github.com/user-attachments/assets/f306b8fd-ad83-4ce0-8fee-cb4ec4890955" />

* Aquest seria el resum final de la màquina virtual creada.

<img width="607" height="661" alt="image" src="https://github.com/user-attachments/assets/f66f11b1-f198-4fd5-8728-966a6fe46b98" />

## – Instal·lar el sistema (idioma, usuari, contrasenya)

* A continuació comença la instal·lació del sistema. Primer escollim l’idioma i, després de completar la configuració inicial, indiquem el nom d’usuari i la contrasenya que tindrà l’equip.

<img width="621" height="453" alt="image" src="https://github.com/user-attachments/assets/5946321a-0147-4dbc-98e0-3d06a51c2875" />

<img width="551" height="486" alt="image" src="https://github.com/user-attachments/assets/6fbdea22-acf6-4df1-aba2-5bbf42380b8d" />


## Pas 5 – Comprovar que arrenca correctament

* Una vegada finalitzada tota la configuració, comprovarem que el sistema s’inicia sense problemes.

<img width="722" height="264" alt="8" src="https://github.com/user-attachments/assets/75152ae0-8270-45d2-9799-fa92cac40405" />


# Fase 2 – Punts de restauració

## Pas 6 – Cercar "Crear un punt de restauració"

* Des del cercador de Windows escrivim **"Crear un punt de restauració"** i obrim aquesta eina.

<img width="325" height="91" alt="9" src="https://github.com/user-attachments/assets/71ecec13-54a0-46a1-81c5-18a2a3a78c76" />

## Pas 7 – Activar la protecció del sistema al disc C:

* Dins d’aquesta finestra cal activar la protecció del disc **C:**, que inicialment apareix desactivada.

<img width="408" height="461" alt="10" src="https://github.com/user-attachments/assets/14e42337-f5c5-4769-87a7-f9f0141897e1" />

## Pas 8 – Crear un punt de restauració manual

* Polse **Crear...** per generar manualment un nou punt de restauració.

<img width="379" height="209" alt="11" src="https://github.com/user-attachments/assets/b7162ce7-3eef-4d83-998e-6fc0da3c24af" />

* Com a nom del punt de restauració, podem posar aquest mateix com a exemple i crear-lo.

<img width="337" height="113" alt="14" src="https://github.com/user-attachments/assets/c58ce58f-003e-48e4-9877-e330d4c3d8bd" />

## Pas 9 – Fer un canvi (programa)

* Com a modificació del sistema, he descarregat un arxiu corresponent a **LibreOffice**. Com que la protecció del disc C: està activada, Windows podria desfer aquest canvi mitjançant una restauració.

<img width="321" height="175" alt="15" src="https://github.com/user-attachments/assets/7efec49c-6bea-4d1c-af5c-c4b04e7e7c64" />

## Pas 10 – Restaurar i comprovar

* Polse **Restaurar sistema...** per començar el procés de restauració cap al punt creat anteriorment.

<img width="402" height="218" alt="16" src="https://github.com/user-attachments/assets/f25ae7c3-5f47-49f2-bad3-6c4c519a7a86" />

* Seleccionarem el punt de restauració que havíem creat, que en aquest cas és l’únic disponible. I confirmarem que tot siga correcte abans de continuar. Després deixarem que el sistema carregue i complete la restauració.

<img width="495" height="204" alt="19" src="https://github.com/user-attachments/assets/f5a1ece6-6db0-49e8-b199-014f5b896f18" />

* Quan acabe el procés, si tornem a buscar el programa que havíem descarregat, veurem que ja no apareix.

<img width="399" height="151" alt="20" src="https://github.com/user-attachments/assets/7119be1d-e076-4537-b0a5-42a041e1503b" />

<img width="334" height="157" alt="21" src="https://github.com/user-attachments/assets/1af29be1-12d6-4eb3-bd97-f10c989ee62f" />

# Fase 3 – Llicències de Windows

## Pas 12 – Veure si Windows està activat

Com es pot observar a la captura anterior, el sistema **no està activat**.

<img width="444" height="224" alt="22" src="https://github.com/user-attachments/assets/c32283b1-b711-43ea-94cc-4fab57e7131d" />

## Pas 13 – Executar al CMD: `slmgr /xpr`

* Obric el símbol del sistema i execute la comanda `slmgr /xpr`. S’obri una finestra de **Windows Script Host** que indica: *"Windows(R), Professional edition: Windows está en modo de notificación"*. Això confirma que el sistema funciona, però no disposa d’una llicència activa.

<img width="615" height="317" alt="24" src="https://github.com/user-attachments/assets/a20519ba-dbb9-494b-8f78-6e897e1ba0f8" />

## Pas 14 – Tipus de llicenciament de Windows

> **Tipus de llicències de Windows més habituals:**
>
> | Tipus | Descripció |
> |---|---|
> | **OEM** | Ve preinstal·lada pel fabricant (Dell, HP...). Està vinculada al maquinari i no es pot transferir. |
> | **Retail** | És adquirida directament per l’usuari i es pot traslladar d’un equip a un altre. |
> | **Volume (MAK/KMS)** | Pensada per a empreses amb molts ordinadors. L’activació es fa amb un servidor intern o una clau mestra. |
> | **Digital License** | Queda associada al compte de Microsoft i s’activa automàticament en iniciar sessió. |
>
> En aquest cas, el sistema es troba en **mode notificació** (sense una llicència vàlida), una situació freqüent en entorns de pràctiques o proves.

## Pas 15 – Preu aproximat d'una llicència Windows

> **Preus oficials de Microsoft (abril 2026):**
>
> | Edició | Preu aprox. (web oficial) |
> |---|---|
> | Windows 11 Home | ~115 - 145 € |
> | Windows 11 Pro | ~199 - 259 € |
> | Llicencie OEM (claus digitals) | ~15 - 45 € |
>
> Tot i que Microsoft centra actualment la venda en Windows 11, encara es poden localitzar llicències de Windows 10 en plataformes com Amazon o en altres botigues de programari. Les llicències OEM solen tindre un preu molt més baix perquè queden associades de manera permanent a la placa base del primer ordinador on s’activen.

# Fase 4 – Gestor d'arrencada

## Pas 16 – Obrir Command Prompt com a administrador

* Al cercador de Windows escric **"cmd"** (Símbol del sistema) i seleccione **"Ejecutar como administrador"** per disposar dels permisos necessaris per executar `bcdedit`.

<img width="351" height="202" alt="image" src="https://github.com/user-attachments/assets/a515bf08-4063-464a-b274-16caff5aaa9d" />

## Pas 17 – Executar bcdedit

* Execute la comanda `bcdedit`, que mostra tota la configuració del gestor d’arrencada de Windows (**BCD – Boot Configuration Data**).

<img width="507" height="516" alt="26" src="https://github.com/user-attachments/assets/f94c5439-b147-4efe-acdc-a5714d235703" />

## Pas 19 – Interpretar dades concretes

> **Del bloc Boot Manager:**
>
> | Camp | Valor | Significat |
> |---|---|---|
> | `default` | `{current}` | El sistema que s’inicia per defecte és el Windows actual |
> | `timeout` | `30` | El menú d’arrencada espera 30 segons abans d’iniciar automàticament |
>
> **Del bloc Boot Loader:**
>
> | Camp | Valor | Significat |
> |---|---|---|
> | `device` | `partition=C:` | Windows està instal·lat a la partició C: |
> | `path` | `\WINDOWS\system32\winload.exe` | És el fitxer encarregat de carregar el sistema operatiu |
> | `description` | `Windows 11` | És el nom que identifica el sistema operatiu |

---

## Pas 20 – Respostes a les preguntes curtes

> **Quin sistema s'està arrencant?**
> → **Windows 10** (identificador `{current}`).
>
> **A quin disc o partició està instal·lat?**
> → A la partició **C:** del primer disc dur.
>
> **Quant temps espera abans d'arrencar?**
> → **30 segons** (`timeout 30`).
>
> **Quin fitxer inicia Windows?**
> → `\WINDOWS\system32\winload.exe`

---

## Pas 21 – Interpretació final

> **Qui decideix l’arrencada (Boot Manager):**
> El **Windows Boot Manager** (`bootmgr`) és qui s’encarrega de mostrar el menú d’arrencada i de determinar quin sistema operatiu es posarà en marxa, d’acord amb la configuració guardada al BCD.
>
> **Qui carrega el sistema (Boot Loader):**
> El **Windows Boot Loader** (`winload.exe`) és el component que carrega el nucli de Windows a la memòria i posa en funcionament el sistema una vegada el Boot Manager ja ha pres la decisió.

---

# Fase 5 – Xarxa bàsica

## Pas 22 – Obrir la configuració de xarxa

* Obric **Configuració > Red e Internet** ① i accedisc a **Ethernet** ② per consultar i modificar els paràmetres de la connexió de xarxa.

<img width="695" height="386" alt="27" src="https://github.com/user-attachments/assets/9cc709f4-b501-4151-a3eb-f3629e926ea3" />

## Pas 23 – Consultar la IP amb `ipconfig`

* Obric el CMD i execute `ipconfig`. Allí es mostren les dades de la interfície Ethernet:
    - **Adreça IPv4:** `10.0.2.15`
    - **Màscara de subxarxa:** `255.255.255.0`
    - **Porta d’enllaç (gateway):** `10.0.2.2`

<img width="543" height="203" alt="28" src="https://github.com/user-attachments/assets/04700c53-8cdd-4389-a95d-c8df3a8b90f4" />

## Pas 24 – Configurar IP dinàmica (DHCP automàtic)

* A la configuració d’Ethernet, comprove que l’assignació de l’adreça IP està en mode **Automático (DHCP)**. Amb aquest sistema, el router reparteix automàticament una IP al dispositiu cada vegada que es connecta, sense necessitat d’introduir-la manualment.

<img width="364" height="152" alt="29" src="https://github.com/user-attachments/assets/c20f044c-16f8-4c1b-a132-65c1e1b0632a" />

## Pas 25 – Configurar IP fixa (manual)

* A la pantalla d’informació de l’adaptador Ethernet es veu la configuració actual, obtinguda per DHCP, que després es podria establir manualment:
    - **IP:** `10.0.2.16`
    - **Màscara:** `255.255.255.0` (prefix /24)
    - **Gateway:** `10.0.2.2`
    - **DNS:** `8.8.8.8`

  Per definir una IP fixa, des d’aquest mateix panell es pot prémer **Editar** en l’apartat "Asignación de IP", canviar-lo a **Manual** i introduir aquests mateixos valors de manera estàtica.

<img width="330" height="224" alt="30" src="https://github.com/user-attachments/assets/f7a297fe-7609-4e34-97b2-83c1e066658f" />

## Pas 26 – Comprovar la connexió amb `ping google.com`

* Execute `ping google.com` al CMD. El resultat mostra que s’han rebut correctament els 4 paquets enviats, amb 0 pèrdues i un temps de resposta aproximat de **12 ms**, cosa que confirma que la connexió a Internet funciona bé.

<img width="530" height="212" alt="31" src="https://github.com/user-attachments/assets/319c6046-d9ff-4ae3-b41c-cbc0d65fd582" />

# Fase 6 – Comandes generals

## Pas 27 – Obrir PowerShell

* Busque **"Windows PowerShell"** al cercador i l’obric.

<img width="309" height="146" alt="32" src="https://github.com/user-attachments/assets/7785df58-af7a-4bce-835d-ac8fe5f5cd1a" />

## Pas 28 – Diferenciar CMD i PowerShell

> | Característica | CMD (Símbol del Sistema) | PowerShell |
> |---|---|---|
> | **Propòsit** | Executar comandes bàsiques i tradicionals de Windows | Automatitzar tasques avançades i scripting |
> | **Objectes** | Funciona amb text pla | Funciona amb **objectes** .NET |
> | **Potència** | Més limitada, heretada de MS-DOS | Molt més potent, amb canonades d’objectes |
> | **Scripts** | Fitxers `.bat` | Fitxers `.ps1` |
> | **Exemple** | `dir`, `copy`, `del` | `Get-ChildItem`, `Copy-Item`, `Remove-Item` |
>
> **Quan convé usar cadascun:**
> - **CMD** → Per a operacions ràpides, scripts senzills o compatibilitat amb programes antics.
> - **PowerShell** → Per automatitzar processos, administrar el sistema i treballar amb serveis, registres o objectes més complexos.

## Pas 29 – Comandes bàsiques (provades)

* Execute `dir` per veure els fitxers i carpetes del directori `C:\Users\RamonRoda\Documents`. En el llistat apareix el fitxer **ramon.txt**, que havia creat prèviament.

<img width="460" height="203" alt="image" src="https://github.com/user-attachments/assets/39b75ab4-9197-4362-9298-dc4e60c5468c" />


* Després execute `cd C:\Users\RamonRoda\Documents` per situar-me en la carpeta de documents, `mkdir ramon` per crear una carpeta nova i `echo hola > fitxer.txt` per generar un fitxer de text.

<img width="397" height="198" alt="image" src="https://github.com/user-attachments/assets/e63b004a-9783-447d-bba5-b56ad7f59802" />


* Torne a executar `dir` per comprovar que tant la carpeta **prova** com el fitxer **fitxer.txt** (14 bytes) s’han creat correctament.

<img width="456" height="218" alt="image" src="https://github.com/user-attachments/assets/a56f7a93-f165-40a3-9997-cc44cb19f497" />


* Finalment, execute `del fitxer.txt` per esborrar el fitxer i torne a llançar `dir` per verificar que ja no figura en el llistat.

<img width="386" height="192" alt="image" src="https://github.com/user-attachments/assets/66d6e7d7-6e16-48f6-8d1f-90c2ff6ccaa6" />


## Pas 30 – Comandes útils del sistema

* `tasklist` → Mostra tots els **processos que estan actius** al sistema, amb el seu PID, la sessió i el consum de memòria. S’hi poden veure processos com `System`, `svchost.exe`, `wininit.exe`, etc.

<img width="571" height="306" alt="image" src="https://github.com/user-attachments/assets/edb795c7-32bc-4662-805b-73d13b167ccc" />


* `taskkill /IM notepad.exe /F` → Tanca forçadament el procés **Notepad**. El sistema indica: *"se terminó el proceso Notepad.exe con PID 7540"*.

<img width="443" height="107" alt="image" src="https://github.com/user-attachments/assets/cdcb2eeb-55e1-4d99-bec4-91f0bf4fe4b6" />

* `systeminfo` → Ofereix informació detallada del sistema, com ara el nom de l’equip (**DESKTOP-EQI60GD**), el sistema operatiu (**Windows 10 Pro**), el fabricant (**VirtualBox**), la memòria, el processador, la data d’instal·lació, etc.

<img width="780" height="285" alt="image" src="https://github.com/user-attachments/assets/f3529cbc-5274-441c-a530-299621ceb698" />


* `hostname` i `whoami` → `hostname` mostra el nom de l’ordinador (**DESKTOP-EQI6OGD**) i `whoami` indica l’usuari actual (**DESKTOP-EQI6OGD\nicksist**).

<img width="298" height="35" alt="image" src="https://github.com/user-attachments/assets/51f5f026-5310-419d-bfa8-94346dc11a66" />

<img width="284" height="47" alt="image" src="https://github.com/user-attachments/assets/10991041-f8a4-479e-a552-27544c77ea3a" />


## Pas 31 – Comandes de xarxa

* `ipconfig` mostra la configuració IP de l’adaptador Ethernet: **IP 10.0.2.16**, màscara **255.255.255.0** i gateway **10.0.2.2**.

  `ping google.com` envia paquets a Google i el resultat verifica la connexió a Internet amb **0% de pèrdua** i un temps de resposta aproximat de 12 ms.

<img width="553" height="233" alt="image" src="https://github.com/user-attachments/assets/f856db7a-c594-44b9-a6a4-bcd9aaf04714" />

<img width="478" height="185" alt="image" src="https://github.com/user-attachments/assets/9d7ec058-8b9f-45c3-8c67-abd86bdb0320" />


* `netstat -an` ensenya totes les **connexions de xarxa obertes** del sistema, tant les que estan en estat **LISTENING** com les que apareixen com a **ESTABLISHED**. És una eina útil per detectar ports oberts o connexions actives.

<img width="480" height="282" alt="image" src="https://github.com/user-attachments/assets/c568df49-95ff-4d09-b17e-40b1c30fe1dc" />


## Pas 32 – Comandes interessants (avançades)

* `tree` → Representa l’estructura de carpetes en forma d’arbre a partir del directori actual. En aquest cas es poden veure subcarpetes de l’usuari RamonRoda, com ara `Desktop`, `Documents`, `Downloads`, `prova`, etc.

<img width="323" height="320" alt="image" src="https://github.com/user-attachments/assets/4f7dee9d-8460-425d-9816-ae14636e1546" />


* `cls` → Esborra completament el contingut visible de la terminal i deixa el cursor a l’inici.

<img width="237" height="68" alt="image" src="https://github.com/user-attachments/assets/ce362620-f858-440b-93e3-568b24df9df6" />


* `help` → Mostra l’ajuda de PowerShell amb informació sobre cmdlets, funcions i conceptes disponibles.

<img width="640" height="259" alt="image" src="https://github.com/user-attachments/assets/68149843-2c11-4a10-9c73-84658edcc369" />


> **Nota sobre `shutdown /s /t 0`:** Aquesta comanda apaga l’equip de manera immediata (temps = 0 segons). No he fet captura perquè això hauria apagat la màquina virtual durant la sessió.

## Pas 33 – Mini interpretació

> **Què mostra `tasklist`?**
> → Mostra tots els **processos actius** en el moment d’executar la comanda, incloent el nom del procés, el seu **PID** (identificador de procés), la sessió corresponent i el consum de memòria. Serveix per veure quins programes estan oberts i utilitzant recursos.
>
> **Què mostra `ipconfig`?**
> → Mostra la **configuració de xarxa** de les interfícies del sistema: adreça IP, màscara de subxarxa, porta d’enllaç predeterminada i adreces IPv6. És molt útil per detectar problemes de connexió.
>
> **Què mostra `systeminfo`?**
> → Ofereix un **resum complet del sistema**: nom de l’equip, versió del sistema operatiu, fabricant del maquinari, quantitat de RAM, processador instal·lat, data d’instal·lació de Windows i molta més informació. És semblant a l’apartat "Sobre aquest equip", però molt més detallat.

# Fase 7 – Instal·lació d'aplicacions

## Pas 34 – Descarregar un programa des del navegador (VS Code)

* A la pàgina oficial `code.visualstudio.com/Download` trie la versió per a **Windows (Windows 10, 11)** i comence la descàrrega de l’instal·lador.

<img width="879" height="377" alt="50" src="https://github.com/user-attachments/assets/7c24bf27-8564-4548-ac65-b1f0592c0984" />

## Pas 35 – Instal·lar seguint l'assistent

* Continue l’assistent d’instal·lació. Primer accepte l’**acord de llicència** de Microsoft per a VS Code i polse **Següent**.

<img width="589" height="459" alt="51" src="https://github.com/user-attachments/assets/d6596886-2277-43e2-b9f0-526790578ae7" />

* Després confirme la **carpeta de destinació** on s’instal·larà VS Code: `C:\Users\Eros\AppData\Local\Programs\Microsoft VS Code` (amb un mínim requerit de 576,5 MB).

<img width="587" height="208" alt="52" src="https://github.com/user-attachments/assets/2269871a-4e1d-4f3b-b9c2-412f64091f50" />

En aquest punt ja quedaria tot preparat per a la instal·lació i només caldria clicar a **"Instalar"**.

<img width="591" height="464" alt="53" src="https://github.com/user-attachments/assets/c590c040-11fe-4ec6-a454-833a4407b549" />

## Pas 36 – Obrir i comprovar que funciona

* **Visual Studio Code** s’obri correctament i mostra la pantalla de benvinguda amb les opcions de **Walkthrough: Setup VS Code**. Això confirma que el programa funciona correctament a Windows 11.

<img width="1018" height="239" alt="54" src="https://github.com/user-attachments/assets/02a280a4-ddd8-4297-a7de-c08b0a6ec2de" />

## Pas 37 – Instal·lar una aplicació des de Microsoft Store

* Obric la **Microsoft Store** i instal·le **Spotify**. Per fer-ho, clique **Obtener**.

<img width="569" height="342" alt="55" src="https://github.com/user-attachments/assets/6f7f5729-3f8a-47ff-81e0-417c0c42dcca" />

## Pas 38 – Obrir i comprovar el funcionament

* Una vegada instal·lat, obrim l’aplicació **Spotify** per verificar que s’executa correctament.

<img width="1014" height="606" alt="56png" src="https://github.com/user-attachments/assets/55182e26-5778-484a-b2c3-5b6b35b5456a" />

## Pas 39 – Desinstal·lar una aplicació

* Obric **Configuració > Aplicaciones** ① i entre a **Aplicaciones instaladas** ② per veure el llistat de programes instal·lats.

* Des del menú desplegable, seleccione **Desinstalar** per començar l’eliminació de VS Code.

<img width="456" height="474" alt="57" src="https://github.com/user-attachments/assets/92cfaeb7-19c2-4aee-a222-8924adc23292" />


## Pas 40 – Verificació: comprovar que ja no apareix al sistema

* Faig una cerca de **"Spotify"** al cercador de Windows. Abans apareixia com a millor coincidència; ara ja **no es mostra cap aplicació instal·lada**, només suggeriments de cerca web. Això confirma que Spotify s’ha desinstal·lat correctament.

<img width="515" height="487" alt="58" src="https://github.com/user-attachments/assets/0fcdfc70-b9bd-4217-aafa-4e09c06b8de1" />
