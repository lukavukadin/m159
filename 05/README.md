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

<img width=60% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_28.01.26_21.40.png">

<img width=80% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_28.01.26_21.42.png">

----
### 4. Domain Controller Trust

Jetzt bin ich auf "Active Directory Domains and Trusts" Tool gegangen und habe einen Trust erstellt:

<img width=80% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_28.01.26_22.42.png">


Hier habe ich meine Domain vom AWS Managed angegeben:

<img width=80% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_28.01.26_22.47.png">





<img width=80% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_29.01.26_01.37.png">

<img width=80% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_29.01.26_01.38.png">




<img width=80% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_29.01.26_01.39.png">


<img width=80% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_29.01.26_01.40.png">

<img width=80% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_29.01.26_01.41.png">



## Trust Relationship


<img width=80% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_29.01.26_01.49.png">

<img width=100% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_29.01.26_01.53.png">



### Trust validieren

<img width=80% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_29.01.26_02.01.png">



Somit habe ich die AWS Managed AD aufgesetzt und mit meinem bereits laufenden Domänenkontroller verbunden.

<img width=80% height=95% alt="Bildname" src="https://raw.githubusercontent.com/lukavukadin/m159/main/img/img_29.01.26_02.04.png">

