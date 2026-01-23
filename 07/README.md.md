## Aufgabe 7: Directory Information Tree (DIT) & Gruppenrichtlinien (GPO)

### 1. Schritt: DIT (Directory Information Tree) erstellen

Zuerst habe ich eine Skizze erstellt, wie mein DIT aussehen soll:

<img width=100% height=100% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/dit.excalidraw.png">

----
### 2. Schritt: Struktur im Active Directory anlegen

Dies habe ich dann auf dem DC aufgesetzt:

<img width=35% height=20% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_23.01.26_10.45.png">

----
### 3. Schritt: Benutzer & Computer verschieben

Nun habe ich alle Benutzer und Computer in die jeweiligen OU's verschoben!

---
### 4. Schritt: Passwortrichtlinien anpassen

Jetzt habe ich die Default Domain Policy geändert in folgende Passworteinstellungen:

- Passwortänderung auf 0 gesetzt, das bedeutet das Passwort läuft nie ab!
- Passwortkomplexität

<img width=90% height=90% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_23.01.26_10.56.png">

----

### 5. Schritt: Netzlaufwerke per GPO verteilen

Ich habe die Netzlaufwerke so konfiguriert, dass sie automatisch beim Login verbunden werden. Dabei nutzte ich separate GPOs für jede Ebene (Firma, Bereich, Abteilung), um die Zuweisung über die OUs zu steuern.

**Mein Vorgehen:**

- **GPOs erstellt:** Eigene Objekte für Pool, Intern, Extern und alle Abteilungen angelegt.
    
- **Einstellungen:** Unter `Drive Maps` die UNC-Pfade (z.B. `\\dc1\Pool`) mit der Aktion **Update** und festen Laufwerksbuchstaben hinterlegt.
    
- **Verknüpfung:** Die GPOs mit den jeweiligen OUs verknüpft (z.B. Pool auf Domänenebene, Abteilungslaufwerke auf Abteilungs-OUs).

<img width=30% height=40% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_23.01.26_13.53.png">


Hier ein Beispiel von der Gruppe Pool, wie ich sie erstellt habe. Zuerst habe ich sie unter dem Ordner "Group Policy Object erstellt, dann unter Properties das demensprechende Laufwerk hinzugefügt:


<img width=40% height=40% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_23.01.26_14.01.png">

<img width=40% height=40% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_23.01.26_11.16.png">


In diesem Bild sieht man alle erstellten GPO's:

<img width=80% height=40% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_23.01.26_13.59.png">

#### Erfolgskontrolle

Als Test habe ich mich mit dem s.vukadin User eingeloggt, um zu schauen, ob ich es richtig gemacht habe. 

Ich habe es Erfolgreich erstellt, Sandra auf der Abteilung Sekretariat, sieht die Laufwerke Pool, Intern und Sekreteriat

<img width=80% height=40% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_23.01.26_14.08.png">

----
### 5. Schritt: Desktop-Verknüpfung mit positiver Sicherheitsfilterung

Zuerst habe ich eine neue GPO erstellt:

<img width=60% height=40% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_23.01.26_14.35.png">


Dann habe ich die GPO konfiguriert und sie mit meiner obersten OU verknüpft:

<img width=35% height=40% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_23.01.26_14.34.png">
<img width=40% height=40% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_23.01.26_14.37.png">


Jetzt wollen wir einstellen das Promoter "Peter Tester" keinen Zugriff darauf hat, deswegen müssen wir unter Securty Filtering Authenticated User löschen und GRP_Intern hinzufügen:

<img width=60% height=40% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_23.01.26_14.47.png">


Anscheinden Seit einem Windows-Update vor ein paar Jahren reicht die Sicherheitsfilterung alleine oft nicht aus, weil der Computer selbst die GPO auch "lesen" können muss.

Deswegen habe ich das gemacht:

<img width=80% height=40% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_23.01.26_14.48.png">

#### Erfolgskontrolle

Zuerst habe ich die Policy getestet, indem ich mich mit einem Benutzer aus der Gruppe "Intern" und einem Benutzer aus der Gruppe "Extern" eingeloggt habe.

Mit dem User Sandra Vukadin (Sekreteriat) hat die Anbindung funktioniert und mit dem Benutzer Peter Tester (Promoter) nicht, was bestätigt, dass die Sicherheitsfiltrierung korrekt funktioniert hat:

<img width=60% height=40% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_23.01.26_14.57.png">

<img width=60% height=40% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_23.01.26_15.03.png">


----
### 6. Schritt: GPO mit WMI-Filter

Als erstes habe ich unter dem Ordner "WMI Filters" ein neuen Filter erstellt, der Eine Datei 
(`WMI-Filter.txt`)  nur dann auf einen Computer kopieren soll, wenn darauf **Windows 10** läuft:

<img width=50% height=40% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_23.01.26_15.06.png">


Als nächstes ging ich unter den Ordner Pool und erstellte die Txt-Datei "WMI-Filter.txt":

<img width=70% height=40% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_23.01.26_15.14.png">


Jetzt erstellte ich ein GPO und konfigurierte es folgendermassen:

<img width=40% height=40% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_23.01.26_15.17.png">
<img width=40% height=40% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_23.01.26_15.18.png">


Dann musste ich unter WMI Filtering im Dropdown den neunen Windows 10 Filter auswählen:

<img width=40% height=40% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_23.01.26_15.20.png">


Zum Schluss habe ich das GPO zur OU Promoter verknüpft:

<img width=40% height=40% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_23.01.26_15.22.png">

#### Erfolgskontrolle

