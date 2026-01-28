# SSO Python App
---
### 1. Python installieren und App herunterladen

Zuerst habe ich mit diesen Befehlen auf dem CLIENT Python heruntergeladen und gestartet:

<img width=95% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_28.01.26_10.46.png">
<img width=95% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_28.01.26_10.52.png">


Mit "python --version" nachgeschaut ob Python auch wirklich installiert wurde:

<img width=95% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_28.01.26_10.51.png">

----
### 2. App lokal einrichten

Zuerst habe ich das Repository von Aeschlimann "m159" auf meinen lokalen Rechner geklont:

<img width=95% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_28.01.26_11.02.png">


Dann habe ich es unter documents auf de CLIENT rüberkopiert:

<img width=95% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_28.01.26_11.04.png">

----
### 3. Python-Umgebung (venv) einrichten

Als erstes habe ich die virtuelle Umgebung im Ordner der Applikation erstellt und sie aktiviert:

<img width=95% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_28.01.26_11.08.png">

Dann habe ich die Paktete mit dem Befehl `pip install flask authlib python-dotenv` installiert:

<img width=100% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_28.01.26_11.19.png">
<img width=100% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_28.01.26_11.43.png">

---
### 4. Registrierung der App in Microsoft Entra ID

Als erstes habe ich die App auf Entra registriert:

<img width=100% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_28.01.26_11.26.png">


Dannach habe ich ein Secret für den CLIENT erstellt:

<img width=100% height=100% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_28.01.26_11.30.png">

-----
### 5. Konfiguration der .env Datei

Jetzt habe ich in der .env Datei der App die CLIENT_ID, CLIENT_SECRET und TENANT ID hinzugefügt:

<img width=60% height=100% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_28.01.26_11.40.png">