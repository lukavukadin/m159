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

##### Bei der IP-Version festlegen habe ich die IPv4 Reverse Lookup Zone ausgewählt

##### Unter **Network ID** die drei Segemente meiner internet IP-Adresse eingegeben:

<img width=60% height=60% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_12.41.png">

##### Dynamische Updates habe ich das Kreuzchen gelassen wie es ist und erledigt:

<img width=60% height=60% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_12.43.png">

##### hier sieht man die erfolgreich erstellte Zone:

<img width=60% height=60% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_12.45.png">

-----
#### 3.3 PTR-Record aktualisieren:

##### Um sicherzustellen, dass die IP-Adresse des Domain Controllers korrekt aufgelöst werden kann, habe ich in den Eigenschaften des Host-Eintrags (**dc1**) innerhalb der Forward-Lookup-Zone `lukavukadin.m159` die Option **"Update associated pointer (PTR) record"** aktiviert.

<img width=80% height=80% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_13.38.png">



##### Durch diese Einstellung wurde in der zuvor erstellten **Reverse-Lookup-Zone** automatisch ein neuer Zeiger-Eintrag (**PTR**) mit der IP **`10.0.0.10`** generiert. Dieser verweist nun korrekt auf den vollqualifizierten Domänennamen (FQDN) `dc1.lukavukadin.m159`.

<img width=80% height=80% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_13.40.png">


##### Um die korrekte Funktion der **Reverse-Lookup-Zone** und des **PTR-Records** zu validieren, habe ich einen Test mittels `nslookup` im Terminal durchgeführt.

<img width=100% height=100% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_13.47.png">


##### Um sicherzustellen, dass der Client den Domain Controller im Netzwerk finden kann, habe ich ein `nslookup` auf die IP des DCs durchgeführt.

<img width=100% height=100% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_13.56.png">

**Ergebnis**: Die Namensauflösung funktioniert einwandfrei. Der Client erreicht den DNS-Dienst des DCs, was die Basis für die Aufnahme in die Domäne bildet.

----
### 4. Schritt: AD-Papierkorb aktivieren

##### Um eine zusätzliche Sicherheitsebene gegen versehentliches Löschen von Objekten (Benutzer, Gruppen) zu schaffen, habe ich das **Recycle Bin Feature** via PowerShell für die gesamte Gesamtstruktur aktiviert.

**Befehl (PowerShell auf dc1):**

`Enable-ADOptionalFeature -Identity 'Recycle Bin Feature' -Scope ForestOrConfigurationSet -Target 'lukavukadin.m159'

<img width=100% height=100% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_13.54.png">

----
### 5. Schritt: Client in die Domäne einbinden (Domain Join)

##### Der Domain Join schlug fehl, da Port 445 blockiert war. Der Test via PowerShell bestätigte dies: **TcpTestSucceeded : False**.

<img width=80% height=80% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_14.08.png">


##### Deswegen habe ich in der AWS Security Group  eine Regel für **Alle TCP**-Ports aus dem Subnetz **10.0.0.0/24** hinzugefügt. Ich habe **10.0.0.0/24** gewählt, da dies exakt mein Subnetz abdeckt und unnötige Zugriffe von ausserhalb (Best Practice) verhindert.

<img width=80% height=80% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_14.14.png">


##### Jetzt war der Port-Check erfolgreich:

<img width=80% height=80% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_14.18.png">


##### Ich habe nun nochmal versucht auf die Domain zu joinen:

<img width=40% height=40% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_14.02.png">


##### Ich habe es geschafft den Client auf meine Domain hinzuzufügen!:

<img width=40% height=40% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_14.24.png">


Der Erfolg des Domain Joins habe ich direkt auf dem Domain Controller (dc1) überprüft. Der Host **`CLIENT`** wurde automatisch im Container **Computers** angelegt.

<img width=50% height=50% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_14.45.png">


### 6. Schritt: Remote Desktop (RDP) für User erlauben


<img width=50% height=50% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_14.58.png">








### 7. Schritt: Manueller PTR-Eintrag für den Client (DNS Fix)



<img width=50% height=50% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_15.02.png">




<img width=50% height=50% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_21.01.26_15.03.png">
