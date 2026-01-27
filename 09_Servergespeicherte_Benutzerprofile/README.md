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

Deshalb habe ich die Datei "fslogix.admx" in dem Verzeichnis: C:\Windows\PolicyDefinitions\en-US kopiert:

<img width=70% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_27.01.26_23.57.png">