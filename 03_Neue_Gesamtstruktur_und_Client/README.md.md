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



<img width=60% height=60% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_12.21.png">


<img width=60% height=60% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_12.22.png">













----
### 4. Schritt: AD-Papierkorb aktivieren




----
### 5. Schritt: Client in die Domäne einbinden (Domain Join)