# Projekt-Setup-Sheet

## 1. Übersicht Umgebung

Diese Umgebung umfasst:

- **1x Windows Server (DC)** auf AWS EC2
    
- **1x Windows Server (Client)** auf AWS EC2
    
- **1x Windows Server (Admin Center)** auf AWS EC2 zur Verwaltung der AWS Managed AD
    
- **AWS Managed AD** mit Trust zur On-Premises(EC2) AD
    
- **Entra Connect** zur Synchronisation mit Entra ID
    
- **Lokale AD-Domain**, später öffentliche Domain als UPN
    

---

## 2. Allgemeine Angaben

|**Feld**|**Wert**|
|---|---|
|Vorname|Luka|
|Nachname|Vukadin|
|Klasse|PE23c|
|Dokumentation (GIT-Repository-Link)|[github.com/lukavukadin/m159](https://www.google.com/search?q=https://github.com/lukavukadin/m159&authuser=1)|

---

## 3. Ressourcen

| **Feld**                             | **Wert**                |
| ------------------------------------ | ----------------------- |
| Active Directory Second-Level-Domäne | lukavukadin.m159        |
| Geplante öffentliche Domain (UPN)    | entra-vukadin.v6.rocks  |
| Azure Education Account              | luka.vukadin7@gmail.com |
| Azure Education Account Passwort     |                         |

---

## 4. AWS VPC Setup

|**Komponente**|**VPC-ID**|**CIDR**|**Name**|
|---|---|---|---|
|**VPC**|vpc-0470f613e45697700|10.0.0.0/16|M159-VPC|
|**Subnet Private 1**|-|10.0.128.0/20|M159-subnet-private1-us-east-1a|
|**Subnet Private 2**|-|10.0.144.0/20|M159-subnet-private2-us-east-1b|
|**Subnet Public 1**|-|10.0.0.0/20|M159-subnet-public1-us-east-1a|
|**Subnet Public 2**|-|10.0.16.0/20|M159-subnet-public2-us-east-1b|

---

## 5. AWS Sicherheitsgruppen

### Sicherheitsgruppe für Domain Controller

|**Regeltyp**|**Port(e)**|**Quelle**|
|---|---|---|
|RDP|3389 (TCP)|0.0.0.0/0|
|LDAP|389 (TCP/UDP)|10.0.0.0/16|
|LDAPS|636 (TCP)|10.0.0.0/16|
|Kerberos|88 (TCP/UDP)|10.0.0.0/16|
|SMB|445 (TCP)|10.0.0.0/16|
|DNS|53 (TCP/UDP)|10.0.0.0/16|
|RPC|135, 49152-65535 (TCP)|10.0.0.0/16|
|ICMP|Alle|10.0.0.0/16|
|Global Catalog|3268 (TCP)|10.0.0.0/16|
|Global Catalog SSL|3269 (TCP)|10.0.0.0/16|
|Kerberos Password|464 (TCP/UDP)|10.0.0.0/16|

### Sicherheitsgruppe für Clients

|**Regeltyp**|**Port(e)**|**Beschreibung**|**Quelle**|
|---|---|---|---|
|RDP|3389|Remote Desktop|0.0.0.0/0|
|TCP|88|Kerberos Auth|10.0.0.0/16|
|TCP|135|RPC Mapper|10.0.0.0/16|
|TCP|139|NetBIOS Session|10.0.0.0/16|
|TCP|389|LDAP|10.0.0.0/16|
|UDP|53|DNS|10.0.0.0/16|
|TCP|445|SMB/CIFS|10.0.0.0/16|
|TCP|49152-65535|RPC Ephemeral|10.0.0.0/16|
|ICMP|Alle|Ping etc.|10.0.0.0/16|

---

## 6. Active Directory Umgebung

### On-Premises Active Directory (AWS EC2)

| **Feld**                | **Wert**             |
| ----------------------- | -------------------- |
| AD Third-Level-Domäne-1 | ec2.lukavukadin.m159 |
| Öffentlicher UPN-Suffix | lukavukadin.ch       |
| Domänenadministrator    | Administrator        |
| Kennwort                | Schule2026!          |

### Azure AD (Entra ID)

| **Feld**                  | **Wert**                        |
| ------------------------- | ------------------------------- |
| Entra AD Tenant Name      | [Wird nach Azure Setup ergänzt] |
| Azure Administrator (UPN) | luka.vukadin@edu.tbz.ch         |
| Entra Connect Server      | dc1.ec2.lukavukadin.m159        |

### AWS Managed AD

| **Feld**                | **Wert**                        |
| ----------------------- | ------------------------------- |
| AD Third-Level-Domäne-2 | aws.lukavukadin.ch              |
| Trust-Typ               | Tree-Root Trust                 |
| AWS Managed Admin User  | admin                           |
| Trust Passwort          | Trust2026!M159                  |
| Subnetz 1               | M159-subnet-private1-us-east-1a |
| Subnetz 2               | M159-subnet-private2-us-east-1b |

---

## 7. EC2-Instanzen

| **Komponente**     | **FQDN**                    | **Private IP** | **Subnetz** | **Lokaler Admin** |
| ------------------ | --------------------------- | -------------- | ----------- | ----------------- |
| **IaaS/OnPrem DC** | dc1.ec2.lukavukadin.m159    | 10.0.128.10    | Private 1   | Administrator     |
| **Windows Client** | client.ec2.lukavukadin.m159 | 10.0.0.50      | Private 1   | Administrator     |
| **Admin Center**   | admin.aws.lukavukadin.ch    | 10.0.0.60      | Public 1    | Administrator     |

---

## 8. Abteilungen & Benutzer

|**Abt.**|**Name**|**Benutzername**|**Vorname**|**Nachname**|**Kennwort**|**Bereich**|
|---|---|---|---|---|---|---|
|1|Sekretariat|s.vukadin|Sandra|Vukadin|Start2026!|intern|
|2|Buchhaltung|b.meier|Beat|Meier|Start2026!|intern|
|3|GL|l.vukadin|Luka|Vukadin|Start2026!|intern|
|4|Promoter|p.tester|Peter|Tester|Start2026!|extern|

---
## 09. Python-App-Registration (Entra-ID)

| **Name**                | **Wert**              |
| ----------------------- | --------------------- |
| Directory (tenant) ID   | <AZURE_CLIENT_SECRET> |
| Application (client) ID | <AZURE_CLIENT_SECRET> |
| Client Secret ID        | <AZURE_CLIENT_SECRET> |
