# MS Entra ID & MS Entra Connect
---
## 1. Vorbereitung der Azure-Umgebung

Ich habe mich in der Microsoft Azure Umgebung mit meiner privaten E-Mail eingeloggt und somit die $80 Guthaben bekommen:

<img width=95% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_27.01.26_11.42.png">

----
## 2. Einrichtung von Microsoft Entra Connect

### 1. Schritt - Microsoft Entra Connect Agent herunterladen

Dann habe ich mein Microsoft Entra ID Connect eingerichtet. Über dem Entra admin center habe ich Entra Connect für on-premise auf dem M159-DC Server installiert.

<img width=95% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_27.01.26_15.29.png">

----
### 2. Schritt - Custom-UPN Suffix hinzufügen (Lokal am DC1)

Hier habe ich einen alternativen UPN-Suffix hinzugefügt, denn ich dann bei der Synchronisation von Entra ID verwenden werde:

<img width=50% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_27.01.26_17.54.png">

----

### 3. Schritt - Installation von Entra Connect starten

Hier habe ich Customize gewählt, damit ich die sicherstellen kann das die geforderte Password Hash Synchronization exlpizit aktiviert ist:

<img width=70% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_27.01.26_18.01.png">


Hier bin ich dann auf Install gedrückt:

<img width=70% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_27.01.26_18.03.png">


In diesem Schritt habe ich überprüft ob die "Password Hash Synchronization" ausgewählt ist:

<img width=70% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_27.01.26_18.06.png">


Bei diesem Schritt sieht man das ich einen User brauche damit ich mich mit Entra ID connecten kann, das habe ich dann im nächsten Schritt gemacht:

<img width=70% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_27.01.26_18.26.png">


Deswegen habe ich einen User angelegt mit Global Administration Rechten.

<img width=50% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_27.01.26_18.20.png">


Hier sieht man den erfolgreich erstellen Admin:

<img width=100% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_27.01.26_18.28.png">


Dann konnte ich den User hier auswählen:

<img width=80% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_27.01.26_18.29.png">


Dann musste ich MFA einrichten für den User:

<img width=80% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_27.01.26_18.45.png">


Hier musste ich dann das Directory hinzufügen also mein Active Directory:

<img width=80% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_27.01.26_18.49.png">


Hier habe ich den AD Account erstellt:

<img width=60% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_27.01.26_18.51.png">
<img width=60% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_27.01.26_18.54.png">


Ich habe neben dem lokalen Suffix `lukavukadin.m159` zusätzlich `entra-vukadin.v6.rocks` als routingfähigen UPN-Suffix konfiguriert, um eine spätere Internet-Anbindung zu ermöglichen. Da diese Suffixe im Tenant noch nicht verifiziert sind, habe ich die Bestätigung **Continue without matching** gewählt, um mit der Synchronisation fortzufahren:

<img width=80% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_27.01.26_18.57.png">


Hier habe ich alle Domains and OUs ausgewählt, da es für dieses Projekt am sichersten ist, damit nichts vergessen geht:

<img width=80% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_27.01.26_19.02.png">


Hier noch mal überprüfen ob "Password hash synchronization" ausgewählt ist:

<img width=80% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_27.01.26_19.06.png">


Entra wurde erfolgreich konfiguriert:

<img width=80% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_27.01.26_19.13.png">


Jetzt habe ich auf dem DC1 überprüft ob die Synchronisation funktioniert hat:

<img width=80% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_27.01.26_19.16.png">

----
## Konfiguration des Hybrid Microsoft Entra ID Join

<img width=80% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_27.01.26_19.24.png">


Ich habe den **Service Connection Point (SCP)** für den Forest `lukavukadin.m159` konfiguriert, damit meine lokalen Geräte den Microsoft Entra Tenant automatisch finden können. Hierzu wurden die **Enterprise Admin Credentials** hinterlegt, um die notwendigen Registrierungsinformationen direkt im Active Directory zu speichern:

<img width=100% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_27.01.26_19.28.png">


Die Konfiguration war erfolgreich:

<img width=90% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_27.01.26_19.42.png">


Dann habe ich eine Gruppenrichtlinie erstellt und auf **Enabled** gesetzt, um die automatische Geräteregistrierung für alle domänengebundenen Computer zu aktivieren.

<img width=90% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_27.01.26_19.48.png">

----
### Custom-UPN (Domain) zu Entra-ID hinzufügen

Ich habe die öffentliche Domäne `entra-vukadin.v6.rocks` im Entra-Portal hinzugefügt, um den Prozess der Identitätsverifizierung für professionelle UPN-Suffixe vorzubereiten.

<img width=100% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_27.01.26_20.11.png">


Hier habe ich dann den TXT Record Adresse kopiert und sie unter meine Zone eingetragen:

<img width=50% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_27.01.26_20.08.png">
<img width=100% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_27.01.26_21.07.png">


Hier sieht man das ich erfolgreich meine Domain Verfied habe:

<img width=90% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_27.01.26_20.58.png">

<br>

Nach der Konfiguration des SCP, der Gruppenrichtlinie und der Domain-Verifizierung zeigt der Befehl `dsregcmd /status` nun erfolgreich **`AzureAdJoined : YES`** an. Damit ist der **Hybrid Microsoft Entra ID Join** für den Domain Controller vollständig abgeschlossen und das Gerät ist sowohl lokal als auch in der Cloud registriert.

<img width=90% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_27.01.26_21.06.png">