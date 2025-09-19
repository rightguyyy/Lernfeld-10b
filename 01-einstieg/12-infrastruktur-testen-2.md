---
date: Schuljahr 2025/2026
lang: de-DE
subtitle: Lernfeld 10b -- Serverdienste bereitstellen und
  Administrationsaufgaben automatisieren
title: Infrastruktur testen
---

## Aufgabe 1

a)  Kreuzen Sie an, welche Informationen aus Ihrer Sicht eine
    Testspezifikation allgemein enthalten sollte.

    - [ ] Speicherort Testspezifikation

    - [X] Erwartetes Testergebnis

    - [ ] Namen der Unternehmensleitung

    - [X] Zielsetzung des Tests

    - [ ] Gründungsjahr der Firma

    - [X] Durchzuführende Testschritte

    - [ ] Anschrift der Vertriebsfiliale

<!-- -->

b)  Erstellen Sie ein Vorlagendokument für Testspezifikationen und
    Testprotokolle für die Infrastruktur, in denen die folgenden
    Informationen enthalten sind:

    - verfügbare Datenraten
    - Funktionsprüfungen
    - Normalfälle
    - Fehler und Ausnahmen
    - Testszenario
    - beteiligte Personen
    - Testdauer
    - Versionshinweis

    Ergänzen Sie die Vorlage um weitere Informationen, die aus Ihrer
    Sicht sinnvoll sind.

    Testspezifikation
Zielsetzung des Tests

.....................................................................

Testszenario

.....................................................................

Rahmenbedingungen

Testumgebung (Hardware, Netzwerk, Software):

Voraussetzungen / Abhängigkeiten:

Testfälle

Normalfälle

Beschreibung: ................................................

Erwartetes Ergebnis: .........................................

Fehler und Ausnahmen

Beschreibung: ................................................

Erwartetes Ergebnis / Fehlermeldung: .........................

Funktionsprüfungen

Beschreibung: ................................................

Erwartetes Ergebnis: .........................................

Messungen

Verfügbare Datenraten: .......................................

Latenzzeiten (falls relevant): ................................

Testdauer

Geplante Dauer: ..................................................

Zeitfenster / Durchführungstermine: ..............................

Testprotokoll
Durchführung

Datum / Uhrzeit: .............................................

Tester: ......................................................

Tatsächliche Dauer: ..........................................

Ergebnisse

Normalfälle: Bestanden / Nicht bestanden

Fehler und Ausnahmen: Bestanden / Nicht bestanden

Funktionsprüfungen: Bestanden / Nicht bestanden

Gemessene Datenraten: ........................................

Abweichungen: ................................................

Beobachtungen

.....................................................................

Bewertung

Testergebnis gesamt: Erfolgreich / Nicht erfolgreich

Offene Punkte / Nachtests erforderlich: ......................

Freigabe

Prüfer / Verantwortlicher: ...................................

Datum: .......................................................

## Aufgabe 2

Erstellen Sie eine neue Testspezifikation für den beschriebenen Test und
das entsprechende Testprotokoll zur anschließenden Durchführung des
Tests.

Im Folgenden werden die Anforderungen an den Test beschrieben.

#### Test der Übertragungsrate zwischen einem Client und einem Server in einem bestehenden Netz

| iperf3-Software | bmon-Software |
|:---|:---|
| iperf3_3. 9-1_amd64. deb | bmon_4. 0-4build1_amd64. deb |
| libiperf0_3. 9-1_amd64. deb | libconfuse2_3. 2. 1+dfsg-4_amd64. deb |
| libsctp1_1. 0. 1 8+dfsg-1_amd64.deb | libconfuse-common_3. 2. 1+dfsg 4_all.deb |
| libssl1. 1_1. 1. 0g-2ubuntu4_amd64. deb | libnl-route-3-200_3. 2. 29-0ubuntu3_amd64. deb |
|  | libnl-3-200_3. 2. 29-0ubuntu3_amd64. deb |
|  |  |

Die Monitor-Software „bmon" ist in einem terminal-Fenster gestartet und
auf die Schnittstelle eingestellt, die geprüft werden soll (z. B. eth0).
Das Speedtest-Tool „iperf3" wird für die Messung der Übertragungsrate
verwendet.

| System | Parameter      | Bemerkung                             |
|:-------|:---------------|:--------------------------------------|
| Server | `iperf —s -fK` | zeige Übertragungsrate in KByte/s     |
| Client | `iperf -c`     | starte Test zur angegebenen Server-IP |

Die Übertragungsraten werden von „iperf" in Textform angezeigt und von
„bmon" grafisch dargestellt. Die folgenden Abbildungen zeigen dies
Ausgabe.

![](images/bmon.png) bmon-Monitor-Tool

![](images/iperf-client.png) iperf-Client

![](images/iperf-server.png) iperf-Server

Der Server muss vor dem Client gestartet werden, ansonsten wird
„connection refused" gemeldet. Mit „bmon" wird die Grundlast auf dem
Netzabschnitt festgelegt. Die von „iperf" angezeigte Übertragungsrate
„Bitrate" soll mindestens 0,2 Gbit/sec betragen und mindestens 10% der
Grundlast ausmachen. Die Testdauer beträgt ca. 1 Minute.

Testspezifikation
Allgemeine Angaben

Projekt / System: Netzwerkinfrastruktur Test

Test-ID: NET-TR-001

Version / Änderungsstand: 1.0

Datum: ....................

Beteiligte Personen / Rollen: Testleiter, Tester, Administrator

Zielsetzung

Überprüfung der Übertragungsrate zwischen einem Client und einem Server in einem bestehenden Netz.

Testszenario

Ein Server wird mit iperf3 als Serverprozess gestartet.

Ein Client führt die Messung der Übertragungsrate mit iperf3 durch.

Parallel wird die Netzwerklast mit bmon auf der geprüften Schnittstelle (z. B. eth0) überwacht.

Rahmenbedingungen

Server Software: iperf3_3.9-1_amd64.deb, erforderliche Bibliotheken installiert

Client Software: iperf3_3.9-1_amd64.deb

Monitoring Software: bmon_4.0-4build1_amd64.deb

Netzwerk: bestehendes LAN, mind. 1 Gbit/s Anbindung

Testfälle
1. Normalfall

Beschreibung: Start iperf3-Server (iperf3 -s -f K) → Start Client (iperf3 -c <Server-IP>).

Erwartetes Ergebnis: Übertragungsrate ≥ 0,2 Gbit/s und ≥ 10 % der gemessenen Grundlast laut bmon.

2. Fehler / Ausnahme

Beschreibung: Client wird vor Server gestartet.

Erwartetes Ergebnis: Fehlermeldung „connection refused“.

3. Funktionsprüfung Monitoring

Beschreibung: Start von bmon auf Schnittstelle eth0.

Erwartetes Ergebnis: Grundlast wird grafisch dargestellt, Traffic-Anstieg während Test sichtbar.

Messungen

Übertragungsrate (iperf3): in KByte/s

Grundlast (bmon): in Bit/s

Testdauer: ca. 60 Sekunden

Abnahmekriterien

Bitrate ≥ 0,2 Gbit/s

Bitrate ≥ 10 % der Grundlast

Testprotokoll
Durchführung

Datum / Uhrzeit: ....................

Tester: ....................

Server-IP: ....................

Tatsächliche Dauer: ....................

Ergebnisse

Normalfall: Bestanden / Nicht bestanden

iperf3 Bitrate: ....................

bmon Grundlast: ....................

Bedingung ≥ 0,2 Gbit/s erfüllt? Ja/Nein

Bedingung ≥ 10 % Grundlast erfüllt? Ja/Nein

Fehler / Ausnahme: Bestanden / Nicht bestanden

Ausgabe: „connection refused“? Ja/Nein

Monitoring: Bestanden / Nicht bestanden

bmon zeigt Lastverlauf an? Ja/Nein

Beobachtungen

........................................................................

Bewertung

Testergebnis gesamt: Erfolgreich / Nicht erfolgreich

Abweichungen: ...................................................

Offene Punkte / Nachtests erforderlich: .........................

Freigabe

Prüfer / Verantwortlicher: .................................

Datum: .................................