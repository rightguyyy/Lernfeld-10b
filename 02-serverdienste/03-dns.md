---
css: ../css/style.css
date: Schuljahr 2025/2026
lang: de-DE
subtitle: Lernfeld 10b -- Serverdienste bereitstellen und
  Administrationsaufgaben automatisieren
title: Serverdienste -- DNS
---
 
## Aufgabe 1
 
Erläutern Sie am Beispiel von `h394.dc23.eu.mycloud.eu` die Begriffe
FQDN, Subdomain und TLD.
 
Geben Sie dazu auch die Bedeutung der Akronyme an.
 
A:
 
FQDN (Fully Qualified Domain Name): Vollständiger, eindeutiger Domainname eines Hosts im DNS – hier h394.dc23.eu.mycloud.eu.
Subdomain: Teil einer größeren Domain, z. B. dc23.eu.mycloud.eu ist eine Subdomain von mycloud.eu.
TLD (Top-Level-Domain): Oberste Ebene in der DNS-Hierarchie – hier .eu.
 
Akronyme:
 
FQDN = Fully Qualified Domain Name
DNS = Domain Name System
TLD = Top-Level Domain
 
## Aufgabe 2
 
Erklären, sie was ein DNS-Root-Server und dessen Aufgabe ist.
 
A:
 
DNS-Root-Server:
Das sind die obersten Server in der DNS-Hierarchie.
Sie beantworten keine Namen direkt, sondern verweisen Resolver auf die zuständigen TLD-Server (z. B. .com, .de, .eu).
Es gibt 13 Root-Server-Instanzen (A–M), die weltweit redundant verteilt sind.
 
 
## Aufgabe 3
 
Unterscheiden Sie die Begriffe Forward- und Reverse-Lookup.
 
A.
 
Forward-Lookup: Name → IP-Adresse (z. B. server01.example.com → 192.168.1.10)
 
Reverse-Lookup: IP-Adresse → Name (z. B. 192.168.1.10 → server01.example.com)
 
 
## Aufgabe 4
 
Erläutern Sie, inwiefern eine Fritzbox als DNS-Forwarder arbeitet und
inwiefern Sie als authoritativer Server arbeitet.
 
A:
 
Fritzbox als DNS-Forwarder:
Leitet DNS-Anfragen der Clients an den vom Provider vorgegebenen DNS-Server weiter.
→ Arbeitet hier nicht autoritativ, sondern als Zwischenstation.
 
Fritzbox als autoritativer Server:
Nur für lokale Namen (z. B. pc.fritz.box).
→ Verwaltet eigene Zone und beantwortet diese direkt.
 
 
## Aufgabe 5
 
Beschreiben Sie, was Cache-Poisoning ist und wie es mit DNSSEC
verhindert werden kann.
 
A:
 
Cache-Poisoning:
Manipulation des DNS-Caches durch gefälschte Antworten, sodass eine Domain auf eine falsche IP zeigt.
Beispiel: Angreifer schleust falschen Eintrag für bank.de ein → Nutzer landet auf Fake-Seite.
 
Schutz durch DNSSEC:
Antworten werden kryptografisch signiert.
Der Client kann die Signatur prüfen und erkennt manipulierte Daten.
 
 
## Aufgabe 6
 
Erklären Sie, wozu »DNS over TLS« eingeführt wurde und wie es
funktioniert.
 
A:
 
Verschlüsselt DNS-Anfragen zwischen Client und Resolver über TLS (Port 853).
→ Schützt vor Mitlesen und Manipulation der DNS-Kommunikation.
→ Ziel: Vertraulichkeit und Integrität der Namensauflösung.
 
 
## Aufgabe 7
 
Sie sollen die Funktionsweise des DNS-Protokolls genauer betrachten.
Ohne eine funktionierende Namensauflösung sind viele Anwendungen nicht
nutzbar.
 
a)  Beschreiben Sie, was mit einem DNS-Forward-Lookup erreicht wird und
    geben Sie den Ablauf an.
 
A:
 
Forward-Lookup:
Auflösung eines Hostnamens in eine IP-Adresse.
 
Ablauf:
 
Client fragt lokalen Resolver (z. B. Fritzbox).
Falls nicht im Cache → Anfrage an Root-Server.
Root-Server verweist auf TLD-Server.
TLD-Server verweist auf autoritativen Nameserver der Domain.
Dieser liefert die IP-Adresse zurück.
Resolver speichert Ergebnis im Cache.
 
<!-- -->
 
b)  Entscheiden Sie, ob die folgenden Aussagen zum DNS richtig oder
    falsch sind.
 
    a)  Die Datei „hosts" wurde historisch für die Namensauflösung
        verwendet und kommt heute nicht mehr zum Einsatz.
 
    <!--Falsch – wird noch für lokale Auflösungen genutzt. -->
 
    b)  Eine Zone legt fest, für welchen Bereich in der DNS-Hierarchie
        ein Server autoritativ ist.
 
    <!-- Richtig-->
 
    c)  Die DNS-Root-Server sind in der Hierarchie die obersten Server
        und werden von Resolvern als erstes angefragt. Sie kennen jedoch
        nur die IP-Adressen von DNS-Servern der Top-Level-Domänen.
 
    <!--Richtig -->
 
    d)  Aus Sicherheitsgründen gibt es die 13 DNS-Root-Server mehrfach.
        Über IP-Multicast wird der geografisch am nächsten gelegene
        Server ausgewählt.
 
    <!-- Falsch – über Anycast, nicht Multicast.-->
 
    e)  Root-Hint ist eine Textdatei, die von der IANA-Webseite
        heruntergeladen werden kann. Sie enthält die 13 IPv4- und
        IPv6-Adressen der DNS-Root-Server. Sofern kein Forwarder
        eingetragen ist, benötigt jeder Resolver diese Datei, um eine
        Abfrage in der DNS Hierarchie starten zu können.
 
    <!-- Richtig -->
 
    f)  DNS over TLS (DoT) und DNS over HTTPS (DoH) zielen darauf ab,
        die Verbindung vom DNS-Client zum DNS-Resolver abzusichern.
 
    <!-- Richtig-->
 
    g)  DNSSEC zielt darauf ab, die Abfrage eines DNS-Clients zum
        DNS-Resolver abzusichern.
 
<!-- Falsch – sichert Daten zwischen Resolver ↔ autoritativen Server. -->
 
c)  Erklären Sie den Unterschied zwischen einem Fully Qualified Domain.
    Name (FQDN) und einem Uniform Resource Locator (URL).
 
A:
 
FQDN: Vollständiger Domainname (z. B. server01.example.com).
URL: Enthält zusätzlich Protokoll und Pfad (z. B. https://server01.example.com/index.html).
 
→ FQDN = Teil der URL.
 
<!-- -->
 
d)  Eine Angriffsart auf das DNS-System ist ein sogenanntes
    „DNS-Cache-Poisoning". Beschreiben Sie den Ablauf dieses Angriffs
    und erläutern Sie eine Möglichkeit, sich davor zu schützen.
 
A:
 
DNS-Cache-Poisoning – Ablauf:
 
Angreifer sendet gefälschte Antwort an Resolver, bevor die echte Antwort kommt.
Falsche IP wird im Cache gespeichert.
Nutzer wird auf manipulierte Seite umgeleitet.
 
Schutz:
 
Einsatz von DNSSEC zur Signaturprüfung
Kurze TTL-Werte
Nur vertrauenswürdige Forwarder verwenden
 
 
 