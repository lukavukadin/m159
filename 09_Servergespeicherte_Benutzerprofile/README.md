# Servergespeicherte Profile
---
## 1. Vorbereitung des Profil-Speichers (File Server)

Ich habe als erstes im Laufwerk C einen neuen Ordner namens: FSLogix_Profiles erstellt und diesen Freigegeben:

<img width=50% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_27.01.26_23.39.png">

----
## 2. Software & GPO-Vorlagen vorbereiten

### 2.1 Download von FSLogix

Hier habe ich die ZIP-Datei heruntergeladen:

<img width=70% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_27.01.26_23.53.png">

### 2.2 GPO-Templates (ADMX) installieren

Damit mein Server die FSLogix-Einstellungen im GPO-Editor überhaupt anzeigt, müssen wir ihm die "Vokabeln" geben:

Deshalb habe ich die Datei "fslogix.admx" in dem Verzeichnis: C:\Windows\PolicyDefinitions\ kopiert:

<img width=100% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_28.01.26_00.14.png">

Und die Datei "fslogix.adml" in dem Verzeichnis C:\Windows\PolicyDefinitions\en-US kopiert

<img width=100% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_28.01.26_00.17.png">

----
## 3. Konfiguration der Gruppenrichtlinie (GPO)

Jetzt, wo der Server die Einstellungen kennt, erstellen wir die Richtlinie.

### 3.1 GPO erstellen

Ich habe unter meiner Domain die GPO "GPO_FSLogix_Profiles" erstellt:

<img width=50% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_28.01.26_00.01.png">

### 3.2 Einstellungen setzen

Hier habe ich folgende Anpassungen im GPO gemacht:

- VHD Locations: `\\DC1\FSLogixProfiles`
- Delete Local Profile When VHD Should Apply: `Enabled`
- Enable: `Enabled`
- Size in MB: `5000`
  
<img width=80% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_28.01.26_00.26.png">

----

## 4. Installation des FSLogix Agents auf den Clients

Ich bin jetzt die .exe Datei gestartet und FSLogix heruntergeladen:

<img width=50% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_28.01.26_00.43.png">

### 4.1 Der erste Login-Test

Als erstes habe ich die den Client neugestartet und eine Datei unter Desktop erstellt:

<img width=50% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_28.01.26_01.08.png">


### 4.2 Kontrolle auf dem DC1 (Server)

