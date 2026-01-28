# AWS Managed AD / AD-Trust
---
## 1.  Verzeichnis in AWS einrichten


<img width=50% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_28.01.26_20.25.png">

---
## 2. Aufsetzung AWS Managed

### 2.1 Schritt:

<img width=70% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_28.01.26_20.28.png">

-----
### 2.2 Schritt:

Hier habe ich die Domain "aws.lukavukadin.ch" verwendet, wie in der Planung definiert:

<img width=70% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_28.01.26_20.36.png">

---
### 2.3 Schritt:

Hier habe ich mein VPC ausgewählt und die beiden erstellten private Subnetze:

<img width=70% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_28.01.26_20.38.png">

### 2.4 Schritt:

Jetzt habe ich das Verzeichnis erstellt:

<img width=70% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_28.01.26_20.42.png">

Der AD ist jetzt "Aktiv":


<img width=100% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_28.01.26_21.36.png">

-----

## 3. Conditional Forwarder

Jetzt habe ich auf meinem Domain Controller einen Conditional Forwarder aufgesetzt:

<img width=100% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_28.01.26_21.40.png">