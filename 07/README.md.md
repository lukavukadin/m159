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

Laut Aufgabe sollen wir **neue GPOs** erstellen und diese mit den **korrekten OUs verknüpfen**.



<img width=90% height=90% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_23.01.26_11.11.png">