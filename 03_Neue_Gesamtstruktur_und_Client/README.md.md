### 1. Schritt: AD DS-Rolle auf `dc1` installieren

**Unter Server Roles - "Active Directory Domain Services ausgewählt"**

<img width=80% height=80% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_11.37.png">

----
### 2. Schritt: `dc1` promoten

##### Deployment Configuration:

<img width=60% height=60% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_11.49.png">


##### Domain Controller Options:

<img width=60% height=60% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_11.51.png">
Passwort: Tbz12345


##### DNS Options (einfach überspringen, meldung kommt da ich die Root-Instanz gerade erst erstellte):

<img width=60% height=60% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_11.55.png">

##### Additional Options (NetBIOS):

<img width=60% height=60% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_11.58.png">

##### Paths & Review (lassen wie es ist):

<img width=60% height=60% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_12.00.png">

##### Installation:

<img width=60% height=60% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_12.01.png">

##### Server wurde Automatisch Neugestartet

<img width=60% height=60% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_12.08.png">

##### DNS und AD DS wurde erfolgreich erstellt

<img width=60% height=60% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_12.19.png">

-----

### 3. Schritt: DNS-Konfiguration

#### 3.1 DNS-Forwarder (Weiterleitung):

##### Unter Tools gegangen und DNS ausgewählt:

<img width=60% height=60% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_12.21.png">

##### Dann auf meinem DNS rechtsklick gedrückt und auf properties gegangen:

<img width=60% height=60% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_12.22.png">


##### Dannach auf Frowarders und dort auf Edit:

<img width=60% height=60% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_12.23.png">


##### Hier habe ich die IP 9.9.9.9 hinzugefügt:

<img width=60% height=60% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_12.28.png">

**Begründung:** Quad9 (9.9.9.9) legt einen höheren Fokus auf Datenschutz (keine Speicherung der IP) und blockiert automatisch den Zugriff auf bekannte bösartige Webseiten (Phishing/Malware), was die Sicherheit eines Servers erhöht.


#### 3.2 Reverse-Lookup-Zone einrichten:

##### Jetzt musste ich eine neue Zone erstellen:

<img width=60% height=60% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_12.34.png">

##### Primary zone ausgewählt - und nachschauen ob store the zon ein active Directory gesetzt war:

<img width=60% height=60% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_12.37.png">


##### Replikations-Bereich ist gut wie es schon angekreuzt ist:

<img width=60% height=60% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_12.39.png">

<br>
##### Bei der IP-Version festlegen habe ich die IPv4 Reverse Lookup Zone ausgewählt

<br>
##### Unter **Network ID** die drei Segemente meiner internet IP-Adresse eingegeben:

<img width=60% height=60% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_12.41.png">

##### Dynamische Updates habe ich das Kreuzchen gelassen wie es ist und erledigt:

<img width=60% height=60% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_12.43.png">

<img width=60% height=60% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_12.45.png">

-----
#### 3.3 PTR-Record aktualisieren:


















----
### 4. Schritt: AD-Papierkorb aktivieren




----
### 5. Schritt: Client in die Domäne einbinden (Domain Join)