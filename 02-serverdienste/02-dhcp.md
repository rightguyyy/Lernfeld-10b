---
css: ../css/style.css
date: Schuljahr 2025/2026
lang: de-DE
subtitle: Lernfeld 10b -- Serverdienste bereitstellen und
  Administrationsaufgaben automatisieren
title: Serverdienste -- DHCP
---

## Aufgabe 1

Beschreiben Sie den Nachrichtenverlauf bei DHCP.

DORA-Prinzip:

Discover – Client sendet Broadcast, sucht DHCP-Server.

Offer – DHCP-Server bietet Konfiguration an.

Request – Client fordert angebotene Konfiguration an.

Acknowledge – Server bestätigt und vergibt die Parameter.

## Aufgabe 2

Geben Sie drei Informationen an, welche bei einer DHCP-Offer-Nachricht
vom DHCP-Server an den Client gesendet werden.

IPv4-Adresse

Subnetzmaske

Lease-Zeit
(weitere möglich: Standard-Gateway, DNS-Server)

## Aufgabe 3

Die DHCP- Request Nachricht wird als Broadcast-Nachricht an alle
Teilnehmer im Netzwerk gesendet. Begründen Sie dieses Vorgehen.

Der Client kennt den endgültigen DHCP-Server noch nicht eindeutig, daher wird die Nachricht als Broadcast gesendet. Alle Server sehen, ob sie gewählt wurden, und der gewählte Server bestätigt.

## Aufgabe 4

Eine DHCP-Request-Nachricht ist in einen Ethernet-Rahmen geschachtelt.
Es folgt der Mitschnitt eines Ethernet-Rahmens. Benennen Sie die Ziel-
und die Quell-MAC-Adresse.

- Ziel-Mac-Adresse (6 Byte)
- Quell-Mac-Adresse (6 Byte)
- Type (2 Byte)
- Daten (46--1500 Byte)
- Frage Check Sequence (4 Byte)

<!-- -->

    ff ff ff ff ff ff 08 00 27 e2 ed 6e 08 00 45 00
    01 67 00 01 00 00 80 11 39 86 00 00 00 00 0O ff

Ziel-MAC-Adresse: ff:ff:ff:ff:ff:ff (Broadcast)

Quell-MAC-Adresse: 08:00:27:e2:ed:6e

## Aufgabe 5

Diskutieren Sie in Partnerarbeit die Aufgabe eines DHCP-Relays bei DHCP.

Weiterleitung von DHCP-Anfragen über Subnetzgrenzen hinweg. Ermöglicht DHCP auch in Netzen ohne lokalen DHCP-Server.

## Aufgabe 6

Welche der Informationen können mittels DHCP verteilt werden?

- IPv4-Adresse

- Subnetzmaske

- Systemzeit

- DNS-Server

- Lease-Zeit

- ARP-Tabelle des Systems

IPv4-Adresse ✅

Subnetzmaske ✅

DNS-Server ✅

Lease-Zeit ✅
(Systemzeit ❌, ARP-Tabelle ❌)

## Aufgabe 7

Ein Client hat die nachfolgend dargestellte IP-Adressenkonfiguration.

![](images/ip-konfiguration.png){width="85%"}

Beschreiben Sie, aus welchem IP-Adressbereich die abgebildete Adresse
stammt und in welcher Situation ein Client diese Adresse bekommt.

Adresse aus 169.254.0.0/16 (APIPA-Bereich). Client erhält sie, wenn kein DHCP-Server erreichbar ist und keine manuelle Konfiguration existiert.

## Aufgabe 8

Grenzen Sie die Begriffe „Lease-Time", „Renewal-Time" und „Rebind-Time"
voneinander ab.

Lease-Time: Gesamtdauer, wie lange IP gültig ist.

Renewal-Time (T1): Zeitpunkt (i. d. R. 50 % der Lease-Time), an dem Client beim ursprünglichen Server Verlängerung anfragt.

Rebind-Time (T2): Zeitpunkt (i. d. R. 87,5 % der Lease-Time), an dem Client bei allen Servern Verlängerung anfragt.

## Aufgabe 9

Beschreiben Sie ein Anwendungsbeispiel für die automatische Zuordnung
bei DHCP.

Automatische IP-Vergabe in einem Unternehmensnetz: Clients erhalten beim Hochfahren automatisch Adresse, Gateway, DNS usw., ohne manuelle Konfiguration.

## Aufgabe 10

Geben Sie mindestens fünf (typische) Parameter an, die mit DHCP
konfiguriert werden können.

IPv4-Adresse

Subnetzmaske

Gateway-Adresse

DNS-Server

Lease-Zeit
(Weitere: WINS-Server, NTP-Server, Boot-Server)

## Aufgabe 11

Erläutern Sie die DHCP-Adressvergabeverfahren manuelle, automatische und
dynamische Zuordnung.

Manuell: Administrator bindet IP fest an MAC-Adresse.

Automatisch: Client erhält dauerhafte IP aus Pool, immer gleich.

Dynamisch: Client erhält IP nur zeitlich begrenzt (Lease-Time). Nach Ablauf kann Adresse neu vergeben werden.

## Aufgabe 12

Beschreiben Sie Maßnahmen, um die Ausfallsicherheit von DHCP zu erhöhen.

Redundante DHCP-Server (Failover, Load Balancing)

DHCP-Cluster oder Replikation

Mehrere Server in unterschiedlichen Netzen

## Aufgabe 13

Geben Sie an, was SLAAC bedeutet und erklären Sie, wie es funktioniert.

Verfahren in IPv6. Clients generieren ihre IPv6-Adresse selbständig mithilfe von Router Advertisements (RA). Router teilt Netzpräfix mit, Client hängt Interface-Identifier an. Kein DHCP-Server nötig.