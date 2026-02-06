---
css: ../css/style.css
date: Schuljahr 2025/2026
lang: de-DE
subtitle: Lernfeld 10b -- Serverdienste bereitstellen und
  Administrationsaufgaben automatisieren
title: Übungsaufgaben Serverdienste
---

## Aufgabe 1

Beschreiben Sie eine Möglichkeit, wie Sie die NetzwerkKonfiguration
eines Server überprüfen.

Mit dem Befehl ip addr oder ifconfig lassen sich IP-Adressen, Netzmasken und Schnittstellen anzeigen. Zusätzlich kann ip route zur Prüfung der Routing-Tabelle verwendet werden.

## Aufgabe 2

Nennen Sie ein Shell-Kommando inklusive Beispiel, mit dem Sie die
Funktion eines DNS-Servers mit der IP-Adresse `5.6.7.8` überprüfen.

nslookup example.com 5.6.7.8

oder

dig @5.6.7.8 example.com

## Aufgabe 3

Für spätere Aufgaben, z. B. die Konfiguration der Firewall, müssen für
bestimmte Dienste die entsprechenden OSI-Schicht-4-Ports gesammelt
werden. Ordnen Sie Dienste bestimmten Well-Known-Ports zu. Füllen Sie
dazu die Tabelle aus.

| Dienst | Port |
|--------|-----:|
| HTTP   |   80 |
| HTTPS  |  443 |
| SMTP   |   25 |
| DNS    |   53 |
| IMAP   |  993 |
| FTP    |   21 |
| NTP    |  123 |
| SSH    |   22 |
| SNMP   |  161 |
| POP3S  |  995 |

## Aufgabe 4

Bei der Kommunikation zwischen Client und Server werden IP-Adressen und
Ports verwendet. Die Kombination wird „Socket" genannt. PC1 mit der
IP-Adresse 10.20.30.57 baut eine HTTPS-Verbindung mit dem Server S
10.0.0.20 aufbaut. Ergänzen Sie die Tabelle um die fehlenden Angaben.

| Verbindung | Quell-IP-Adresse | Quell-Port | Ziel-IP-Adresse | Ziel-Port |
|------------|------------------|------------|-----------------|-----------|
| Anfrage    | 10.20.30.57      | 32462      | 10.0.0.20       | 443       |
| Antwort    | 10.0.0.20        | 443        | 10.20.30.57     | 32462     |

## Aufgabe 5

Beschreiben Sie den Nachrichtenverlauf bei DHCP (»DORA-Prozess«).

Discover: Client sucht einen DHCP-Server.  
Offer: Server bietet eine IP-Adresse an.  
Request: Client fordert das Angebot an.  
Acknowledge: Server bestätigt die Zuweisung.

## Aufgabe 6

Geben Sie mindestens fünf (typische) Parameter an, die mit DHCP
konfiguriert werden können.

IP-Adresse  
Subnetzmaske  
Standard-Gateway  
DNS-Server  
Lease-Time  
NTP-Server

## Aufgabe 7

Erläutern Sie die DHCP-Adressvergabeverfahren manuelle, automatische und
dynamische Zuordnung.

Manuell: Feste Zuordnung einer bestimmten IP zu einer MAC-Adresse.  
Automatisch: Server weist einmalig eine feste IP aus einem Pool zu.  
Dynamisch: IP wird zeitlich begrenzt (Lease) vergeben und später neu verteilt.

## Aufgabe 8

Grenzen Sie die Begriffe „Lease-Time", „Renewal-Time" und „Rebind-Time"
voneinander ab.

Lease-Time: Gesamtdauer der IP-Zuweisung.  
Renewal-Time (T1): Zeitpunkt zur Verlängerung beim ursprünglichen Server.  
Rebind-Time (T2): Zeitpunkt zur Verlängerung bei beliebigem Server, falls T1 fehlschlägt.

## Aufgabe 9

Geben Sie an, was SLAAC bedeutet und erklären Sie, wie es funktioniert.

SLAAC (Stateless Address Autoconfiguration) ermöglicht Clients im IPv6-Netz selbstständig eine Adresse zu bilden. Der Router sendet Router Advertisements, aus Präfix und Interface-ID wird automatisch die IPv6-Adresse gebildet.

## Aufgabe 10

Erläutern Sie am Beispiel von `ah9IeB.east.us.your-server.com` die
Begriffe FQDN, Subdomain und TLD.

FQDN (Fully Qualified Domain Name): vollständiger Domainname inkl. aller Ebenen → ah9IeB.east.us.your-server.com  
Subdomain: east.us.your-server  
TLD (Top Level Domain): com

## Aufgabe 11

Erklären, sie was ein DNS-Root-Server und dessen Aufgabe ist.

Ein DNS-Root-Server ist die oberste Instanz im DNS-System. Er kennt die zuständigen Nameserver der Top-Level-Domains und verweist Anfragen an diese weiter.

## Aufgabe 12

Unterscheiden Sie die Begriffe Forward- und Reverse-Lookup.

Forward-Lookup: Domainname wird in eine IP-Adresse aufgelöst.  
Reverse-Lookup: IP-Adresse wird in einen Domainnamen aufgelöst.

## Aufgabe 13

Beschreiben Sie, was Cache-Poisoning ist und wie es mit DNSSEC
verhindert werden kann.

Cache-Poisoning ist das Einschleusen falscher DNS-Einträge in den Cache eines Servers, um Nutzer auf falsche Ziele umzuleiten. DNSSEC schützt durch kryptografische Signaturen, mit denen die Echtheit der Antworten überprüft wird.

## Aufgabe 14

Erklären Sie, wozu »DNS over TLS« eingeführt wurde und wie es
funktioniert.

DNS over TLS verschlüsselt DNS-Anfragen, damit sie nicht mitgelesen oder manipuliert werden können. Die Kommunikation zwischen Client und DNS-Server erfolgt über eine TLS-geschützte Verbindung.

## Aufgabe 15

Beschreiben Sie die drei Systeme zur Zeitmessung

Linux-Zeitmessung mit timestamp: Sekunden seit 01.01.1970 (Unix-Epoche).  
NTP-Zeitmessung im Timestamp-Format: Sekunden seit 01.01.1900 mit Bruchteilen.  
NTP-Zeitmessung im Datestamp-Format: Datum und Uhrzeit als lesbarer Zeitstempel.

## Aufgabe 16

Erklären Sie, was Stratum-0 ist.

Stratum-0 sind hochpräzise Zeitquellen wie Atomuhren oder GPS-Empfänger. Sie liefern die Referenzzeit und sind direkt nicht im Netzwerk erreichbar.

## Aufgabe 17

Benennen Sie die Attributstypen in Verzeichnisdiensten.

String-Attribute  
numerische Attribute  
Boolesche Attribute  
Zeit-/Datum-Attribute  
Binärdaten-Attribute

## Aufgabe 18

Beschreiben Sie die Aufgabe von Gruppenrichtlininen im AD.

Gruppenrichtlinien (GPO) dienen zur zentralen Verwaltung und Konfiguration von Benutzern und Computern im Active Directory. Damit können Sicherheitsrichtlinien, Softwareeinstellungen und Systemkonfigurationen automatisch verteilt und erzwungen werden.
