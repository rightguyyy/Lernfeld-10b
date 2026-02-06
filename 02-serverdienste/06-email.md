---
css: ../css/style.css
date: Schuljahr 2025/2026
lang: de-DE
subtitle: Lernfeld 10b -- Serverdienste bereitstellen und
  Administrationsaufgaben automatisieren
title: Serverdienste -- E-Mail
---

## Aufgabe 1

Unterscheiden Sie MUA und MTA.

Ein Mail User Agent (MUA) ist das Programm des Benutzers zum Lesen, Schreiben und Verwalten von E-Mails (z. B. Mailclient).  
Ein Mail Transfer Agent (MTA) ist die Serversoftware, die E-Mails zwischen Mailservern annimmt, weiterleitet und zustellt.

## Aufgabe 2

Unterscheiden Sie die Protokolle SMTP, IMAP und POP3.

SMTP wird zum Versenden und Weiterleiten von E-Mails zwischen Clients und Mailservern bzw. zwischen Mailservern genutzt.  
IMAP dient zum Abrufen und Verwalten von E-Mails direkt auf dem Server, Ordner und Status bleiben serverseitig gespeichert.  
POP3 dient ebenfalls zum Abrufen von E-Mails, lädt diese jedoch meist lokal herunter und löscht sie anschließend vom Server.

## Aufgabe 3

Beschreiben Sie den Aufbau einer E-Mail.

Eine E-Mail besteht aus zwei Hauptteilen:

Header: Enthält Metadaten wie Absender (From), Empfänger (To), Betreff (Subject), Datum, Mailserver-Informationen (Received) und weitere technische Angaben.  
Body: Enthält den eigentlichen Inhalt der Nachricht. Dieser kann Text, HTML oder Anhänge enthalten. Anhänge werden über MIME kodiert übertragen.

## Aufgabe 4

Beschreiben Sie die drei gängigen Authentifizierungsverfahren im
E-Mail-System.

SMTP-Auth: Benutzername und Passwort zur Anmeldung am Mailserver vor dem Versand.  
POP3/IMAP-Login: Benutzer authentifiziert sich mit Zugangsdaten zum Abrufen von Mails.  
Zertifikats- oder TLS-basierte Authentifizierung: Verschlüsselte Verbindung mit Zertifikaten, um Identität und Vertraulichkeit sicherzustellen.

## Aufgabe 5

a)  Zum Abrufen von E-Mails werden u. a. die Protokolle IMAP und POP3
    eingesetzt Beschreiben Sie die Unterschiede der beiden Protokolle.

IMAP speichert E-Mails zentral auf dem Server und synchronisiert mehrere Geräte. Ordner, Status und Mails bleiben online erhalten.  
POP3 lädt E-Mails lokal herunter und löscht sie oft vom Server. Synchronisation mehrerer Geräte ist nur eingeschränkt möglich.

<!-- -->

b)  Als E-Mail-Client lässt sich eine Vielzahl von Produkten einsetzen.
    Recherchieren Sie drei Produkte, die einen Mail User Agent (MUA)
    anbieten.

Mozilla Thunderbird  
Microsoft Outlook  
Apple Mail

<!-- -->

c)  Ordnen Sie einzelne Geräte und Protokolle ihren Aufgaben beim
    E-Mail-Versand und -Empfang zu.

    1.  Mail Transfer Agent
    2.  SMTP
    3.  Domain Name Service
    4.  IMAP
    5.  Mail Delivery Agent
    6.  Mail User Agent

    - Programm zum Versenden und Empfangen von E-Mails
      6

    - Auflösen des Domain-Anteils einer E-Mail-Adresse in eine
      IP-Adresse
      3

    - Protokoll zum Abrufen von E-Mails
      4

    - Protokoll zum Senden von E-Mails
      2

    - Software, die E-Mails auf Postfächer verteilt
      5

    - leitet E-Mails in die Richtung des Ziels weiter
      1

<!-- -->

d)  Die Stadt Marburg verwendet E-Mail-Adressen nach dem Muster
    `Vorname.Nachname@Amt.stadt-marburg.de`. Gegeben ist die
    E-Mail-Adresse `monika.musterfrau@buergerbuero.stadt-marburg.de`.
    Zerlegen Sie die Adresse in die einzelnen Bestandteile (FQDN) und
    benennen Sie diese.

monika.musterfrau = lokaler Benutzername (Local-Part)  
buergerbuero = Subdomain/Amt  
stadt-marburg = Domain  
de = Top-Level-Domain (TLD)

FQDN: buergerbuero.stadt-marburg.de

<!-- -->

e)  Sie sollen einem neuen Auszubildenden die Wichtigkeit des
    DNS-Systems erklären. Beschreiben Sie die Rolle des DNS beim Versenden einer
    E-Mail an eine externe E-Mail-Adresse.

Der sendende Mailserver fragt im DNS nach dem MX-Record der Empfänger-Domain. Dieser liefert den zuständigen Mailserver. Anschließend wird die E-Mail per SMTP an diesen Server zugestellt.

<!-- -->

f)  Ein Mitarbeiter berichtet, dass der E-Mail-Server des Katasteramts
    einmal auf einer „Blocklist" eines bekannten
    Internet-Service-Providers stand. Diskutieren Sie die Gefahren eines „offenen
    SMTP-Relays". Beschreiben Sie einen allgemeinen Lösungsansatz.

Ein offenes SMTP-Relay erlaubt jedem das Weiterleiten von E-Mails ohne Authentifizierung. Spammer nutzen dies zum Massenversand. Dadurch landet die Server-IP auf Blocklisten und legitime Mails werden abgelehnt.  
Lösung: Relay nur für authentifizierte Benutzer erlauben, SMTP-Auth aktivieren, Firewall-Regeln setzen, Spam-Filter und Rate-Limits verwenden.

<!-- -->

g)  Der Mitarbeiter erklärt Ihnen, dass er bei E-Mails, die ihm seltsam
    vorkommen, den E-Mail-Header untersucht. Erklären Sie am folgenden Beispiel, warum es sich hierbei
    wahrscheinlich um eine Spam-E-Mail handelt.

Return-Path ist leer.  
DKIM fehlt (dkim=none), keine Authentifizierung.  
Absenderadresse wirkt zufällig und passt nicht zum angeblichen Zweck.  
Mail stammt von einem fremden Server mit unbekannter Domain.  
Diese Merkmale sprechen für gefälschte Absenderdaten (Spoofing) und damit wahrscheinlich Spam oder Phishing.