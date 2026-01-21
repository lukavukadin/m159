## 1. Schritt: Struktur im Active Directory (OUs & Gruppen)

### 1.1 OUs für Abteilungen erstellen (auf dc1)

#### Für eine saubere Verwaltung habe ich die Haupt-OU **`M159_Unternehmen`** erstellt. Diese unterteilt  in:

- **`Abteilungen`**: Enthält OUs für die Benutzer (Sekretariat, GL, Buchhaltung, Promoter).
    
- **`Gruppen`**: Zentraler Ort für alle Sicherheitsgruppen (ehemals "Group" habe ich verschoben).

<img width=80% height=80% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_16.56.png">

### 1.2 Gruppen & Nesting (auf dc1)

#### Hier habe ich alle Gruppen im OU Gruppen erstellt:

<img width=80% height=80% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_17.03.png">

#### Unter GRP_Inter die Abteilungen Buchaltung, GL und Sekretariat hinzugefügt:

<img width=80% height=80% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_17.07.png">

