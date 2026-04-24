---
layout: custom
title: "SPRINT 2 WINDOWS: DISCS, QUOTES, SCRIPTS, PROCESSOS I ACLs"
---

# 🚀 Sprint 2 – Windows: Discs, Quotes, Scripts, Processos i ACLs

---

## 🔹 Fase 1 – Preparació del sistema

### 👉 Pas 1 – Afegir un nou disc virtual a la màquina virtual

Per augmentar l'espai d'emmagatzematge de la màquina virtual és necessari afegir un nou disc des de la configuració de VirtualBox. Entrem a **Configuració → Emmagatzematge** de la màquina virtual "Windows 11 Pro". Premem a la icona per afegir un nou disc dur virtual i seleccionem **Crea un nou disc**.

En aquesta imatge es pot observar que s'ha creat el fitxer `Windows 11 Pro_1.vdi` (el segon disc), amb una mida virtual de **5,00 GB** i format **VDI (Normal)**. Apareix connectat al controlador SATA al port SATA 2, just a sota del disc principal del sistema.

>  Un disc VDI d'ubicació dinàmica ocupa molt poc espai real al host fins que s'hi escriu informació.

<img width="1452" height="692" alt="image" src="https://github.com/user-attachments/assets/20b17d50-09eb-42af-9258-5b8b4f1a2b45" />


---

### 👉 Pas 2 – Iniciar Windows i obrir Gestió de discs

Després de afegit el disc a VirtualBox, iniciem la màquina virtual amb Windows 11. Per gestionar els discs des de Windows, executem `diskmgmt.msc` (o clic dret al menú d'inici → **Gestió de discs**).

En la captura es veu que el sistema reconeix el nou **Disc 1** (4,98 GB) amb tot l'espai **No asignat**. Això demostra que Windows l'ha detectat sense problemes, però encara no s'ha inicialitzat ni creat cap partició.

>  Quan un disc és nou, Windows el detecta però és necessari inicialitzar-lo (triar GPT o MBR) abans de poder-hi crear particions.

<img width="270" height="91" alt="image" src="https://github.com/user-attachments/assets/0599ebb4-b833-4251-afde-70cfdbeeafa4" />


---

### 👉 Pas 3 – Inicialitzar el disc i crear dues particions: Dades (NTFS) i Portable (FAT32)

####  Crear la partició Dades (NTFS)

Premem dret sobre l'espai no asignat del Disc 1 i seleccionem **Nou volum simple…**

<img width="1056" height="497" alt="image" src="https://github.com/user-attachments/assets/a2f190f9-a70e-4b13-84d6-19ec7d7d65c6" />


S'inicia l'assistent per crear el volum. Indiquem **3000 MB** (3 GB) com a mida per a la primera partició, deixant la resta per a la segona.

<img width="349" height="236" alt="image" src="https://github.com/user-attachments/assets/881386f6-1141-49d8-9ac4-5a6952d67155" />


Configurem la lletra d'unitat **E:** a aquesta partició perquè sigui accessible des de l'Explorador de Windows.

<img width="415" height="135" alt="image" src="https://github.com/user-attachments/assets/57bcea36-26ce-4ddb-a3ad-b38009f934d1" />


Donem format a la partició amb el sistema de fitxers **NTFS**, que és el format natiu de Windows i l'únic que suporta quotes de disc i permisos ACL avançats. L'etiqueta del volum serà **Dades**.

<img width="454" height="355" alt="image" src="https://github.com/user-attachments/assets/482e7421-f985-4a3f-8cab-c161a09696d1" />


La pantalla final de l'assistent mostra tota la configuració seleccionada: 3000 MB, unitat E:, NTFS, etiqueta "Dades". Premem a **Finalizar** per crear la partició.

####  Crear la partició Portable (FAT32)

Amb l'espai restant del Disc 1 (2,05 GB aproximadament), creem una segona partició. Clic dret → **Nou volum simple…**

<img width="1262" height="501" alt="image" src="https://github.com/user-attachments/assets/b33b1f0a-6ddb-47a9-8b7a-e078bc8725c8" />

Usem tot l'espai disponible (2102 MB) per a aquesta partició, que simularà un dispositiu portàtil.

<img width="351" height="207" alt="image" src="https://github.com/user-attachments/assets/d0292bf1-88c0-4759-9849-dc6925c0d948" />

Configurem la lletra **F:** per a la partició Portable.

<img width="429" height="134" alt="image" src="https://github.com/user-attachments/assets/3a77d3d6-062f-4985-97b3-079b55b18d9e" />

Donem format a aquesta partició com a **FAT32** amb l'etiqueta **Portable**. FAT32 és compatible amb la majoria de dispositius (càmeres, consoles, etc.) però té la limitació de no poder emmagatzemar fitxers de més de 4 GB.

| Característica      | NTFS          | FAT32                  |
|---------------------|---------------|------------------------|
| Mida màx. fitxer    | Il·limitada   | 4 GB                   |
| Permisos ACL        | ✅ Sí         | ❌ No                  |
| Quotes de disc      | ✅ Sí         | ❌ No                  |
| Compatibilitat      | Windows/Linux | Universal              |
| Journaling          | ✅ Sí         | ❌ No                  |

<img width="433" height="306" alt="image" src="https://github.com/user-attachments/assets/1d71c6de-fc1f-4c08-b58f-72ed143fc3e5" />

La pantalla final confirma la creació de la partició Portable: 2102 MB, unitat F:, FAT32. Premem a **Finalizar**.

<img width="666" height="691" alt="image" src="https://github.com/user-attachments/assets/0d001d85-7547-4ad4-a2a1-9958b7d11efe" />

---

### 👉 Pas 4 – Assignar lletres i comprovar amb diskpart la configuració

Per comprovar la configuració de manera exacta, iniciem una consola CMD amb permisos d'administrador i executem `diskpart` seguit de les comandes de llistat:

```
DISKPART> list disk
DISKPART> sel disk 1
DISKPART> list part
DISKPART> list vol
```

La imatge mostra el resultat complet. Es pot confirmar:

- **Disc 0 (40 GB)**: disc principal del sistema amb la partició C: (NTFS, 39 GB).
- **Disc 1 (5 GB)**: el nou disc amb dues particions:
  - **Partició 2** → Volum 4 · Lletra **E:** · Etiqueta **Dades** · NTFS · 3000 MB ✅
  - **Partició 3** → Volum 5 · Lletra **F:** · Etiqueta **PORTABLE** · FAT32 · 2102 MB ✅

<img width="637" height="469" alt="image" src="https://github.com/user-attachments/assets/918b8509-eaaa-4031-9288-461ea6910aef" />

---

## 🔹 Fase 2 – Quotes i usuaris

### 👉 Pas 5 – Activar quotes de disc a la partició Dades (NTFS)

Les **quotes de disc** a Windows permeten limitar l'espai que cada usuari pot usar dins d'una partició NTFS. Per activar-les, obrim l'Explorador de Windows, clic dret sobre la unitat **Dades (E:)** i seleccionem **Propietats**.

<img width="532" height="673" alt="image" src="https://github.com/user-attachments/assets/313879e0-56f0-41dc-b3d2-a674b0d1141e" />

A la finestra de propietats ens dirigim a la pestanya **Cuota** i fem clic a **Mostrar configuració de cuota**.

<img width="643" height="493" alt="image" src="https://github.com/user-attachments/assets/6b48c836-ac46-4f5f-af69-26d58922d34e" />

---

### 👉 Pas 6 – Establir límit de 300 MB per usuari, amb notificació d'advertència

Dins del panell de configuració de quotes, activem les opcions:

-  **Habilita la administración de cuota**: activa el sistema de quotes.
-  **Denegar espacio en disco a usuarios que superen el límite**: bloqueja l'escriptura quan se supera el límit.
-  **Limitar espacio en disco a**: **300 MB**
-  **Establecer el nivel de advertencia en**: **150 KB** (l'usuari rebrà un avís quan quasi ompli el límit)
-  **Registrar un evento cuando algún usuario supere su límite de cuota**
-  **Registrar un evento cuando algún usuario supere su nivel de advertencia**

>  Amb el limit establert a 300 MB, cap usuari podrà escriure més dades un cop superi aquesta mida. L'advertència a 150 KB és inusualment baixa (seria recomanable posar-la a uns 250 MB), però serveix per il·lustrar el funcionament.

![Uploading image.png…]()

---

### 👉 Pas 7 – Crear dos usuaris loés necessaris: alumne1 i alumne2

Per crear usuaris loés necessaris a Windows, executem `lusrmgr.msc` (Gestió d'usuaris i grups loés necessaris) des de la finestra **Executar** (Win + R).

![Uploading image.png…]()

Dins de la consola, fem clic dret sobre **Usuaris → Usuari nou…**

![Uploading image.png…]()

Creem l'usuari **alumne1** amb la contrasenya corresponent. Activem l'opció **La contrasenya mai expira** per evitar problemes en les proves.

![19](imatges-windows/19.png)

De forma similar, creem l'usuari **alumne2** amb la mateixa configuració.

![20](imatges-windows/20.png)

---

### 👉 Pas 8 – Afegir-los a un grup nou anomenat Limitats

Dins de `lusrmgr.msc`, fem clic sobre la carpeta **Grupos** per veure tots els grups existents. Clic dret en un espai buit de la llista → **Grupo nuevo…**

![21](imatges-windows/21.png)

Indiquem el nom del grup **Limitats** i afegim els dos usuaris creats (`alumne1` i `alumne2`) com a membres. Premem a **Crear** per finalitzar.

![22](imatges-windows/22.png)

---

### 👉 Pas 9 – Provar la còpia de fitxers a Dades per veure com actuen les quotes

Per validar que les quotes funcionen sense problemes, obrim sessió com a **alumne1** i intentem crear fitxers de diverses mides a la partició `E:\` amb la comanda `fsutil file createnew`:

```
fsutil file createnew E:\prova.dat 350000000   → Error 112: Espai insuficient (supera els 300 MB)
fsutil file createnew E:\prova.dat 150000000   → Fitxer creat (150 MB)
fsutil file createnew E:\prova.dat 150000000   → Fitxer creat (re-escriu el mateix)
fsutil file createnew E:\prova2.dat 50000000   → Fitxer creat (50 MB)
fsutil file createnew E:\prova3.dat 50000000   → Fitxer creat (50 MB)
fsutil file createnew E:\prova4.dat 50000000   → Fitxer creat (50 MB)
fsutil file createnew E:\prova5.dat 50000000   → Error 112: Espai insuficient (ja s'han superat els 300 MB)
```

La imatge mostra clarament com el sistema **nega l'accés** quan l'usuari intenta superar els 300 MB assignats per la quota. L'error **112** és el codi de Windows per "espai en disc insuficient", que en aquest context és provocat artificialment per la quota, no per la mida real del disc.

![24](imatges-windows/24.png)

---

## 🔹 Fase 3 – Script de còpia i automatització

### 👉 Pas 10 – Afegir tercer disc virtual, formatar-lo en NTFS com a Backups

Des de la configuració de VirtualBox, afegim un **tercer disc** (`Windows 11 Pro_2.vdi`) de 5 GB connectat al port SATA 3. Servirà com a unitat de còpies de seguretat.

![25](imatges-windows/25.png)

Després de dins de Windows, obrim la **Gestió de discs** i loés necessariitzem el nou **Disc 2** (4,98 GB, no asignat). Clic dret → **Nou volum simple…**

![26](imatges-windows/26.png)

Donem format a tot el disc com a **NTFS** i li posem l'etiqueta **Backups**. Configurem la lletra **B:**.

![27](imatges-windows/27.png)

---

### 👉 Pas 11 – Crear carpeta CòpiesUsuaris dins Backups

Després de creat i muntat el disc Backups (B:), creem manualment la carpeta `CòpiesUsuaris` dins de la unitat B:. Aquesta carpeta actuarà com a contenidor principal on l'script crearà una subcarpeta per cada usuari.

La captura confirma que la carpeta `CòpiesUsuaris` ha estat creada sense problemes a `B:\`.

![28](imatges-windows/28.png)

---

### 👉 Pas 12 – Crear un script .bat que copiï C:\Users\%USERNAME% a B:\CòpiesUsuaris\%USERNAME%

Creem un fitxer `script.bat` (per exemple a `C:\Users\Ramon\Documents\script.bat`) amb el contingut següent:

```bat
@echo off
xcopy C:\Users\%USERNAME% B:\CòpiesUsuaris\%USERNAME% /E /I /Y
```

**Explicació de la comanda:**

| Paràmetre | Significat |
|-----------|------------|
| `@echo off` | Silencia la sortida de les comandes a la consola |
| `xcopy` | Copia fitxers i directoris (inclou subdirectoris) |
| `%USERNAME%` | Variable d'entorn que s'expandeix automàticament amb el nom de l'usuari actiu |
| `/E` | Copia tots els subdirectoris, fins i tot els buits |
| `/I` | Si la destinació no existeix, la crea com a directori |
| `/Y` | Sobreescriu fitxers existents sense demanar confirmació |

![29](imatges-windows/29.png)

---

### 👉 Pas 13 – Obrir gpedit.msc → Configuració d'usuari → Scripts → Inici de sessió

Per assignar l'script perquè s'executi automàticament en iniciar sessió, obrim l'**Editor de directrius de grup loés necessari** executant `gpedit.msc` des de la finestra **Executar** (Win + R).

![30](imatges-windows/30.png)

Dins de l'editor, naveguem per l'arbre de directives:

**Configuració d'usuari → Configuració de Windows → Scripts (inici de sessió o tancament de sessió)**

Fem doble clic sobre **Iniciar sessió** per obrir la finestra de propietats.

> ℹ️ La distinció entre **Configuració d'equip** i **Configuració d'usuari** és important: les directives d'equip s'apliquen al sistema sencer (independentment de qui hi ha iniciat sessió), mentre que les d'usuari s'apliquen per sessió d'usuari.

![31](imatges-windows/31.png)

---

### 👉 Pas 14 – Assignar l'script perquè s'executi automàticament en iniciar sessió

A la finestra de propietats d'**Iniciar sessió**, fem clic a **Agregar…** i introduïm la ruta completa al nostre script:

`C:\Users\Ramon\Documents\script.bat`

Premem a **Aceptar** per confirmar.

![32](imatges-windows/32.png)

> ⚠️ **Nota important sobre `gpedit.msc` i usuaris loés necessaris:** La directiva de grup loés necessari s'aplica a **tots** els usuaris del sistema (excepte administradors, en alguns casos). Per controlar l'script específicament per a `alumne1` i `alumne2`, una alternativa és copiar l'script a la carpeta de Documents de cada usuari i registrar-lo individualment. En aquest cas, l'script funciona de manera global per a qualsevol usuari que iniciï sessió.

---

## 🔹 Fase 4 – Verificació i documentació

### 👉 Pas 15 – Comprovació: l'script fa la còpia a Backups

Iniciem sessió amb l'usuari **alumne1**. L'script s'executa automàticament a l'inici de sessió i copia el contingut de `C:\Users\alumne1` a `B:\CòpiesUsuaris\alumne1`.

La captura del Explorador de Windows confirma que la còpia s'ha realitzat sense problemes: es veuen totes les carpetes del perfil d'alumne1 (`Contacts`, `Desktop`, `Documents`, `Downloads`, etc.) dins de `B:\CòpiesUsuaris\alumne1\`, amb data del 14/04/2026 a les 16:42.

![33](imatges-windows/33.png)

---

## 🔹 Fase 5 – Gestió de processos i serveis

### 👉 Pas 19 – Llistar processos actius

Iniciem sessió com a **alumne1**, obrim la consola (CMD) i executem `tasklist` per obtenir la llista de tots els processos actius, amb el seu PID, sessió i ús de memòria.

```
C:\Users\alumne1> tasklist
```

La imatge mostra processos típics del sistema: `System Idle Process`, `System`, `Registry`, `smss.exe`, `csrss.exe`, `wininit.exe`, `services.exe`, `lsass.exe`, `svchost.exe` (múltiples instàncies), etc.

![34](imatges-windows/34.png)

Redirigim la sortida a un fitxer de text per poder-la analitzar:

```
C:\Users\alumne1> tasklist > C:\Users\%USERNAME%\processos_inici.txt
```

La imatge mostra que la comanda s'ha executat sense problemes i que el fitxer `processos_inici.txt` (12.950 bytes) s'ha creat al directori de l'usuari `alumne1`. Fem `dir` per confirmar-ho.

![35](imatges-windows/35.png)

Comprovem alguns processos clau usant `findstr` per filtrar del fitxer guardat:

```
findstr explorer.exe C:\Users\%USERNAME%\processos_inici.txt
findstr SearchIndexer.exe C:\Users\%USERNAME%\processos_inici.txt
findstr OneDrive.exe C:\Users\%USERNAME%\processos_inici.txt
```

- **explorer.exe** (275 MB) → Gestor del sistema de fitxers i escriptori.
- **SearchIndexer.exe** (42 MB) → Servei d'indexació per a la cerca de Windows.
- **OneDrive.exe** (133–135 MB) → Sincronització al núvol de Microsoft; prescindible en entorns de laboratori.

![36](imatges-windows/36.png)

---

### 👉 Pas 20 – Identificar processos prescindibles

Filtrem el `tasklist` per trobar processos no essencials per a l'usuari en un entorn educatiu:

```
C:\Users\alumne1> tasklist | findstr "OneDrive.exe Teams.exe SkypeApp.exe"
```

La imatge mostra que **OneDrive.exe** s'executa en dues instàncies (PID 4272 i 1480), consumint uns 133-135 MB de RAM en total.

![37](imatges-windows/37.png)

**Taula de processos prescindibles identificats:**

| Nom del procés | Memòria aprox. | Justificació per eliminar |
|----------------|----------------|---------------------------|
| `OneDrive.exe` | ~135 MB | Sincronització al núvol innecessària en un entorn de VM sense connexió a internet real |
| `Teams.exe` | ~150-400 MB | Client de videoconferència no necessari per a tasques d'aula |
| `SkypeApp.exe` | ~80-150 MB | Aplicació de comunicació no requerida en l'entorn de laboratori |

> 💡 En màquines virtuals amb pocs recursos (4 GB de RAM), eliminar aquests processos pot alliberar entre 200-700 MB de memòria, millorant notablement el rendiment del sistema.

---

### 👉 Pas 21 – Eliminar processos manualment

Executem `taskkill` per finalitzar el procés d'OneDrive forçosament:

```
C:\Users\alumne1> taskkill /IM OneDrive.exe /F
```

La imatge mostra el resultat:
- El procés amb PID 4272 **no s'ha pogut terminar** (accés denegat, possiblement perquè és un procés del sistema o un usuari diferent).
- El procés amb PID 1480 **s'ha terminat sense problemes**.

Comprovem amb `tasklist | findstr OneDrive.exe` que ara només en queda una instància (PID 4272).

![38](imatges-windows/38.png)

> ⚠️ **Nota:** En alguns casos, un procés amb protecció de Windows (com alguns serveis de sistema o processos protegits) no pot ser terminat ni amb el flag `/F`. Això és un mecanisme de seguretat del sistema operatiu.

---

### 👉 Pas 22 – Automatitzar-ho a l'inici de sessió

Modifiquem l'script `script.bat` per incloure les comandes `taskkill` que eliminaran automàticament OneDrive i Teams cada vegada que un usuari iniciï sessió:

```bat
@echo off
xcopy C:\Users\%USERNAME% B:\CòpiesUsuaris\%USERNAME% /E /I /Y

taskkill /IM OneDrive.exe /F
taskkill /IM Teams.exe /F
```

![39](imatges-windows/39.png)

Per validar que funciona, obrim sessió com a **alumne2** i comprovem que OneDrive no s'executa:

```
C:\Users\alumne2> tasklist | findstr OneDrive.exe
(cap resultat)
```

La consola no retorna cap resultat, cosa que confirma que **OneDrive.exe no s'està executant** per a `alumne2` gràcies a l'script d'inici de sessió.

![40](imatges-windows/40.png)

---

### 👉 Pas 23 – Documentació: tasklist, anàlisi de processos crítics i rendiment

#### 📌 Fitxer de processos i anàlisi

El fitxer `processos_inici.txt` generat per `tasklist` conté la llista completa de processos en el moment d'inici de sessió. S'ha adjuntat a la documentació com a evidència.

#### 📌 Què passa si mates un procés crític com explorer.exe?

`explorer.exe` és el gestor de l'escriptori i de l'Explorador de fitxers de Windows. Si l'eliminem:

1. L'escriptori desapareix completament (barra de tasques, icones, fons).
2. No podem obrir cap finestra ni accedir a cap fitxer via GUI.
3. El sistema NO es penja: el kernel i els serveis segueixen funcionant.
4. Per recuperar-lo: `Ctrl + Alt + Supr → Administrador de tasques → Arxiu → Executar nova tasca → explorer.exe`

> ⚠️ **Prova controlada:** En un entorn de laboratori, eliminar `explorer.exe` és reversible. En un entorn de producció és necessaridria anar amb molta cura, ja que l'usuari quedaria sense interfície gràfica.

#### 📌 Com millora el rendiment en VMs?

| Acció | Recursos alliberats |
|-------|---------------------|
| Matar OneDrive.exe | ~135 MB RAM, CPU esporàdica |
| Matar Teams.exe | ~150-400 MB RAM, CPU i xarxa |
| Deshabilitar SearchIndexer | ~40 MB RAM, I/O disc reduït |
| Total estimat | +300-600 MB RAM disponible |

En màquines virtuals amb 4 GB de RAM, alliberar 300+ MB pot significar la diferència entre un sistema fluid i un de lent.

---

## 🔹 Fase 6 – Gestió de permisos (ACLs)

### 👉 Què són les ACLs i com funcionen a Windows

A Windows, cada fitxer i carpeta té una **llista de control d'accés (ACL, Access Control List)**. Aquesta llista defineix qui pot fer què amb aquell recurs.

Cada entrada d'una ACL es diu **ACE (Access Control Entry)** i indica:
- Quina **identitat** (usuari o grup) està afectada
- Quins **permisos** té (lectura, escriptura, execució, control total, etc.)
- Si el permís és **Permetre** o **Denegar**

**Permisos disponibles a Windows:**

| Permís | Descripció |
|--------|------------|
| Control total (F) | Accés complet: llegir, escriure, modificar, eliminar i canviar permisos |
| Modificar (M) | Llegir, escriure i eliminar fitxers, però no canviar permisos |
| Lectura i execució (RX) | Obrir fitxers i executar programes |
| Mostrar contingut | Llistar el contingut d'una carpeta |
| Lectura (R) | Obrir fitxers en mode només lectura |
| Escriptura (W) | Crear fitxers i subcarpetes |

**Herència:** Els permisos d'una carpeta pare es propaguen automàticament a les subcarpetes i fitxers. Quan es desactiva la herència, és necessari decidir si es conserven o descarten les entrades heretades.

---

### 👉 Pas 24 – Crear la carpeta Projectes

Iniciem sessió com a **administrador** i creem la carpeta `Projectes` dins de la partició Dades (E:). La carpeta s'ha creat sense problemes a `E:\Projectes`.

![41](imatges-windows/41.png)

---

### 👉 Pas 25 – Assignar permisos normals al grup Limitats

Premem dret sobre `E:\Projectes → Propietats → Seguretat`. Veiem els permisos actuals (heretats de `E:\`): Usuaris autenticats, SYSTEM, Administradors i Usuaris.

Premem a **Opciones avanzadas** per accedir a la configuració avançada de permisos.

![42](imatges-windows/42.png)

A la finestra d'opcions avançades veiem que els permisos estan **heretats** des de `E:\` (columna "Heredada de"). Premem a **Deshabilitar herencia** per trencar la herència i poder gestionar els permisos de forma independent.

![43](imatges-windows/43.png)

Eliminem l'entrada de **Usuarios (Astro\Usuarios)** per netejar els permisos per defecte que no necessitem. Seleccionem l'entrada i fem clic a **Quitar**.

![44](imatges-windows/44.png)

Ara afegim el grup **Limitats** amb **Control total**. Premem a **Agregar**, introduïm `Limitats`, i marquem tots els permisos bàsics (Control total, Modificar, Lectura i execució, Mostrar el contingut de la carpeta, Lectura, Escriptura).

El tipus és **Permitir** i s'aplica a **Esta carpeta, subcarpetes y archivos** per garantir herència cap avall.

![46](imatges-windows/46.png)

La captura de la configuració avançada final mostra el resultat: la columna **"Heredada de"** ara diu **"Ninguno"** per a totes les entrades, confirmant que la herència s'ha desactivat. El grup **Limitats (ASTRO\Limitats)** apareix amb **Control total**.

![47](imatges-windows/47.png)

---

### 👉 Pas 26 – Comprovar accés amb alumne1

Iniciem sessió com a **alumne1** (membre del grup Limitats). Creem un fitxer de text `hey.txt` a `E:\Projectes` amb el contingut "hola".

La captura confirma que alumne1 ha pogut crear i escriure el fitxer sense cap problema, tal com s'esperava (té **Control total** hereta del grup Limitats).

![48](imatges-windows/48.png)

El fitxer `hey.txt` s'ha creat sense problemes a `E:\Projectes` i conté el text "hola".

![49](imatges-windows/49.png)

---

### 👉 Pas 27 – Aplicar excepció per alumne2 (només lectura)

Tornem a iniciar sessió com a **administrador** i executem la comanda `icacls` per aplicar una excepció específica per a `alumne2`:

```
icacls "E:\Projectes" /grant:r alumne2:(R)
```

**Explicació:**
- `/grant:r` → Substitueix (reset) qualsevol permís existent per a aquell usuari.
- `alumne2:(R)` → Assigna **només lectura (R)** a l'usuari alumne2.

La sortida confirma: *"Se procesaron sense problemese 1 archivos"*. Ara `alumne2` té **només lectura**, tot i ser membre del grup Limitats que té Control total (la entrada explícita de l'usuari té **prioritat** sobre la del grup).

![51](imatges-windows/51.png)

---

### 👉 Pas 28 – Comprovar l'excepció amb alumne2

Iniciem sessió com a **alumne2** i accedim a `E:\Projectes`. La imatge mostra que la carpeta apareix **buida** per a alumne2 (no veu el fitxer creat per alumne1, o la carpeta s'ha estat modificada entre captures).

Quan alumne2 intenta crear un fitxer nou o modificar algun existent, rep un missatge de **denegació d'accés**.

![50](imatges-windows/50.png)

Tornem a iniciar sessió com a alumne1 i comprovem que pot llegir i veure el fitxer `hola.txt` creat a la sessió anterior.

![52](imatges-windows/52.png)

Quan alumne2 intenta crear una carpeta nova a `E:\Projectes`, el sistema nega l'operació (el menú contextual pot mostrar-se però la creació fallaria amb error d'accés).

![53](imatges-windows/53.png)

---

### 👉 Pas 29 – Consultar els permisos aplicats amb icacls

Executem la comanda des de la consola com a administrador per veure l'estat final de tots els permisos de `E:\Projectes`:

```
icacls "E:\Projectes"
```

La sortida és:

```
E:\Projectes NT AUTHORITY\SYSTEM:(OI)(CI)(F)
             Astro\Ramon:(OI)(CI)(F)
             Astro\alumne2:(R)
             BUILTIN\Administradores:(OI)(CI)(F)
             Astro\Limitats:(OI)(CI)(F)
```

**Interpretació dels codis ACL:**

| Codi | Significat |
|------|------------|
| `(OI)` | Object Inherit – els fitxers fills hereten aquest permís |
| `(CI)` | Container Inherit – les carpetes filles hereten aquest permís |
| `(F)`  | Full Control – control total |
| `(R)`  | Read – només lectura |

**Conclusions:**
- **SYSTEM i Administradors**: Control total `(OI)(CI)(F)` ✅
- **Astro\Ramon** (admin principal): Control total `(OI)(CI)(F)` ✅
- **Astro\Limitats** (grup): Control total `(OI)(CI)(F)` ✅ → alumne1 gaudeix d'aquest permís
- **Astro\alumne2**: Només lectura `(R)` ⚠️ → L'entrada explícita de l'usuari **té prioritat** sobre la del grup

> 📌 **Regla clau d'ACLs a Windows:** quan un usuari té dues entrades (una per usuari i una per grup) i entren en conflicte, la **entrada explícita de l'usuari** sempre té prioritat sobre la del grup, excepte si l'entrada de grup és "Deny" que sempre guanya.

![54](imatges-windows/54.png)
