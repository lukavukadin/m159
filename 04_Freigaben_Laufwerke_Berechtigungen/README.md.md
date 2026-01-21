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
### 2. Schritt: Benutzer anlegen

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
### 4. Schritt: Die Freigabe

#### Zuerst habe ich den Hauptordner **"Daten"** im Netzwerk freigegeben. In den erweiterten Freigabe-Einstellungen habe ich einen Haken bei **"Share this folder"** gesetzt. Die Freigabeberechtigungen für die Gruppe **"Jeder"** habe ich auf **"Change"** und **"Read"** konfiguriert, um den Zugriff über das Netzwerk grundsätzlich zu ermöglichen:

<img width=70% height=70% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_21.24.png">

----

### 5. Schritt: Vererbung deaktivieren

#### Um die volle Kontrolle über die Unterordner zu erhalten und Standard-Zugriffe zu unterbinden, habe ich die Vererbung auf dem Ordner **"Daten"** deaktiviert.

Über **Security -> Advanced -> Disable inheritance** habe ich die Option **"Convert inherited permissions into explicit permissions on this object"** gewählt. Dies erlaubt es, die übernommenen Rechte manuell anzupassen. Anschliessend habe ich alle Standard-Benutzergruppen (wie z. B. `Users`) entfernt, sodass nur noch Administratoren und das System Zugriff haben:

<img width=70% height=70% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_21.30.png">

#### Hier sieht man das nur noch System/Admins drin sind:

<img width=70% height=70% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_21.42.png">