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