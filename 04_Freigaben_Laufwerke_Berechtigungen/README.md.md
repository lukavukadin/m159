## 1. Schritt: Struktur im Active Directory (OUs & Gruppen)

### 1.1 OUs für Abteilungen erstellen (auf dc1)

#### Für eine saubere Verwaltung habe ich die Haupt-OU **`M159_Unternehmen`** erstellt. Diese unterteilt  in:

- **`Abteilungen`**: Enthält OUs für die Benutzer (Sekretariat, GL, Buchhaltung, Promoter).
    
- **`Gruppen`**: Zentraler Ort für alle Sicherheitsgruppen (ehemals "Group" habe ich verschoben).

<img width=80% height=80% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_16.56.png">

### 1.2 Gruppen & Nesting (auf dc1)

#### Hier habe ich alle Gruppen im OU Gruppen erstellt:

<img width=80% height=80% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_17.03.png">

#### Unter GRP_Intern habe ich die Abteilungen Buchhaltung, GL und Sekretariat hinzugefügt:

<img width=80% height=80% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_17.07.png">

#### Unter GRP_Extern habe ich die Abteilung Promoter hinzugefügt:

<img width=80% height=80% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_20.33.png">

----
## 2. Schritt: Benutzer anlegen

### Sekretariat

#### Der Benutzer für das Sekretariat wurde in der OU `Sekretariat` angelegt.

- **Name:** Sandra Vukadin
    
- **Logon-Name:** `s.vukadin`
    
- **Gruppe:** `GRP_Sekretariat` (Mitglied von `GRP_Intern`)

<img width=50% height=50% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_20.46.png">
<img width=50% height=40% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_20.53.png">


### Buchhaltung

Der Benutzer für die Buchhaltung wurde in der OU `Buchhaltung` angelegt.

- **Name:** Beat Meier
    
- **Logon-Name:** `b.meier`
    
- **Gruppe:** `GRP_Buchhaltung` (Mitglied von `GRP_Intern`)

<img width=50% height=50% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_20.48.png">
<img width=50% height=40% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_20.55.png">

### GL

Der Benutzer für die Geschäftsleitung wurde in der OU `GL` angelegt.

- **Name:** Luka Vukadin
    
- **Logon-Name:** `l.vukadin`
    
- **Gruppe:** `GRP_GL` (Mitglied von `GRP_Intern`)


<img width=50% height=50% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_20.50.png">
<img width=50% height=40% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_20.58.png">


### Promoter

Der Benutzer für die externen Promoter wurde in der OU `Promoter` angelegt.

- **Name:** Peter Tester
    
- **Logon-Name:** `p.tester`
    
- **Gruppe:** `GRP_Promoter` (Mitglied von `GRP_Extern`)


<img width=50% height=50% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_20.51.png">
<img width=50% height=40% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_20.59.png">

----

## 3. Schritt: Ordnerstruktur auf dem Laufwerk C: (dc1)

#### Ich habe jetzt Ordner aufgestellt wie es in der Berechtigungsmatrix steht:

<img width=100% height=100% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_21.04.png">

#### Als erstes habe ich den Ordner Daten im Laufwerk C: erstellt, dazu die erforderlichen Unterordner: 

- `C:\Daten\Pool`
- `C:\Daten\Intern`
- `C:\Daten\Extern`
- `C:\Daten\Abteilungen`

<img width=50% height=50% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_21.11.png">

#### Danach habe ich im Ordner Abteilungen Unterordner erstellt mit den vier Abteilungen:

- `C:\Daten\Abteilungen\Sekretariat`
- `C:\Daten\Abteilungen\Buchhaltung`
- `C:\Daten\Abteilungen\GL`
- `C:\Daten\Abteilungen\Promoter`

<img width=50% height=50% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_21.15.png">

----
## 4. Schritt: Die Freigabe

##### Zuerst habe ich den Hauptordner **"Daten"** im Netzwerk freigegeben. In den erweiterten Freigabe-Einstellungen habe ich einen Haken bei **"Share this folder"** gesetzt. Die Freigabeberechtigungen für die Gruppe **"Jeder"** habe ich auf **"Change"** und **"Read"** konfiguriert, um den Zugriff über das Netzwerk grundsätzlich zu ermöglichen, das selbe habe ich dann für die anderen Ordner gemacht:

<img width=70% height=70% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_21.24.png">


<img width=70% height=70% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_23.01.26_09.57.png">
----

## 5. Schritt: Vererbung deaktivieren

#### Um die volle Kontrolle über die Unterordner zu erhalten und Standard-Zugriffe zu unterbinden, habe ich die Vererbung auf dem Ordner **"Daten"** deaktiviert.

Über **Security -> Advanced -> Disable inheritance** habe ich die Option **"Convert inherited permissions into explicit permissions on this object"** gewählt. Dies erlaubt es, die übernommenen Rechte manuell anzupassen. Anschliessend habe ich alle Standard-Benutzergruppen (wie z. B. `Users`) entfernt, sodass nur noch Administratoren und das System Zugriff haben:

<img width=70% height=70% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_21.30.png">

##### Hier sieht man das nur noch System/Admins drin sind:

<img width=70% height=70% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_21.42.png">


----

## 6. Schritt: Umsetzung der Berechtigungs-Matrix

### 6.1 Ordner "Abteilungen"

#### Im Ordner Abteilungen: GRP_Intern hinzugefügt und berechtigung **Read & execute**  gegeben:


<img width=40% height=30% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_23.13.png">



### 6.2 Ordner "Intern" & "Extern"

#### Im Ordner Intern: GRP_Intern hinzugefügt und berechtigung **Modify** noch gegeben:

<img width=40% height=30% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_21.59.png">

#### Im Ordner Extern: GRP_Extern hinzugefügt und Berechtigung **Modify** noch gegeben:

<img width=40% height=30% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_22.02.png">

### 6.3 Ordner "Pool"

#### Im Ordner Pool: GRP_Extern und GRP_Intern hinzugefügt beide mit der Berechtigung **Modify**:

<img width=40% height=30% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_22.05.png">

### 6.4 Die "Abteilungsordner"

#### 1. Sekretariat:

Gruppen:

- GRP_Sekretariat hinzugefügt mit **Modify** Berechtigung (C)

<img width=40% height=20% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_22.20.png">


- GRP_GL  hinzugefügt mit **Read & execute** Berechtigung (R)

<img width=40% height=20% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_22.21.png">


#### 2. Buchhaltung:

Gruppen:

- GRP_Buchhaltung hinzugefügt mit **Modify** Berechtigung (C)

<img width=40% height=20% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_22.23.png">


- GRP_GL hinzugefügt mit Read & execute Berechtigung (R)

<img width=40% height=20% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_22.24.png">

#### 3. GL:

Gruppe:

- GRP_GL hinzugefügt mit **Modify** Berechtigung (C)

<img width=40% height=20% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_22.26.png">


#### 3. Promoter:

Gruppe: 

- GRP_Promoter hinzugefügt mit **Modify** Berechtigung (C)

<img width=40% height=20% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_22.28.png">


----

## 7. Schritt ABE aktivieren

#### Jetzt aktiviere ich ABE für alle Ordner damit: Ein User nur noch die Ordner sieht, für die er auch wirklich Rechte hat. Wer kein Recht auf die "GL" hat, sieht den Ordner nicht einmal.

##### Diese habe ich unter "File and Storage Services" -> "Shares" -> Freigabe "Daten" Rechtsklick drauf -> "Properties" -> "Settings" -> Haken bei "Enable access-based enumeration" 

<img width=70% height=50% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_22.36.png">


Bild von Jetzt


----

## 8. Schritt: Test

##### Bevor ich es testen konnte musste ich noch zuerst die Users die ich angelget habe in der Gruppe RDP hinzufügen:

<img width=40% height=40% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_22.50.png">

#### 1. Test: Sekretariat vs. Buchhaltung

Angemeldet als `s.vukadin`. Beim Versuch, den Pfad `\\dc1\Daten\Abteilungen\Buchhaltung` direkt aufzurufen, erscheint die Sicherheitsmeldung.

<img width=100% height=90% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_23.21.png">

#### 2. Test: GL Schreibrechte im Pool

Angemeldet als `l.vukadin`. Im Ordner `\\dc1\Daten\Pool` konnte erfolgreich ein neues Dokument "Test_GL.txt" erstellt werden.

<img width=100% height=90% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_23.25.png">

#### 3. Test: Promoter Zugriff auf Intern

Angemeldet als `p.tester`. Der Ordner `Intern` wird unter `\\dc1\Daten\` aufgrund von ABE gar nicht erst angezeigt. Ein direkter Zugriff wird verweigert.

<img width=100% height=90% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_23.29.png">

-----
## 9. Schritt: Group Nesting Konzept (AGDLP)

Um eine professionelle und skalierbare Berechtigungsstruktur zu gewährleisten, wurde das **AGDLP-Prinzip** implementiert. Dabei werden Benutzer nicht direkt berechtigt, sondern über eine Gruppenkaskade gesteuert.

- **A**ccount: Der einzelne Benutzer.
    
- **G**lobal Group: Repräsentiert die Abteilung (Rolle).
    
- **D**omain **L**ocal: Repräsentiert die Ressource und das Zugriffsrecht (z. B. "Sekretariat Ändern").
    
- **P**ermission: Die tatsächliche NTFS-Berechtigung am Ordner.

#### Visualisierung des Konzepts (Beispiel Sekretariat & GL)

<img width=60% height=60% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/Drawing 2026-01-22 08.37.11.excalidraw.png">


#### Domänenlokale Gruppen im AD erstellen

Jetzt habe ich DL_Sekretariat_C erstellt:

<img width=40% height=50% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_22.01.26_10.22.png">


Jetzt habe ich DL_GL_C erstellt:

<img width=40% height=50% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_22.01.26_10.21.png">


#### Globale Gruppen in Domänenlokale Gruppen schachteln (Nesting)

Hier habe ich GRP_Sekretariat zu DL_Sekreteriat_C hinzugefügt:

<img width=50% height=50% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_22.01.26_13.40.png">


Hier habe ich GRP_GL zu DL_GL_C  hinzugefügt:

<img width=50% height=50% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_22.01.26_11.08.png">


#### NTFS-Berechtigungen am Fileserver anpassen

Ich habe jetzt im Ordner Sekreteriat die Gruppe GRP_Sekreteriat gelöscht und habe die neu erstellte Gruppe DL_Sekreteriat_C hinzugefügt:

<img width=50% height=50% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_22.01.26_13.48.png">


Ich habe jetzt im Ordner GL die Gruppe GRP_Sekreteriat gelöscht und habe die neu erstellte Gruppe DL_Sekreteriat_C hinzugefügt:

<img width=50% height=50% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_22.01.26_13.57.png">