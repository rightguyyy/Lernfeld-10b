---
css: ../css/style.css
date: Schuljahr 2025/2026
lang: de-DE
subtitle: Lernfeld 10b -- Serverdienste bereitstellen und
  Administrationsaufgaben automatisieren
title: Serverdienste -- NTP
---
 
## Aufgabe 1
 
Beschreiben Sie die drei Systeme zur Zeitmessung
 
- Linux-Zeitmessung mit timestamp
A:
Misst Zeit seit dem 01.01.1970, 00:00 UTC (Unix-Epoch) in Sekunden.
Beispiel: 1730947200 = 07.11.2024, 00:00 UTC
 
- NTP-Zeitmessung im Timestamp-Format
A:
Misst Zeit seit dem 01.01.1900, 00:00 UTC, in 32 Bit für Sekunden und 32 Bit für Bruchteile einer Sekunde.
 
- NTP-Zeitmessung im Datestamp-Format
A:
Gibt Datum und Uhrzeit in lesbarem Format (z. B. 2025-11-07 12:30:15) aus, abgeleitet aus dem Timestamp.
 
 
## Aufgabe 2
 
Erklären Sie, was Stratum-0 ist.
 
A:
 
Physikalische Referenzzeitquelle (z. B. Atomuhren, GPS, Funkuhren).
Diese Geräte selbst sind nicht im Netzwerk erreichbar, sondern liefern Zeitsignale an Stratum-1-Server.
 
## Aufgabe 3
 
a)  Entscheiden Sie, ob die folgenden Aussagen zu Network Timing
    Protocol (NTP) richtig oder falsch sind.
 
    1.  Mit dem Begriff „Stratum" wird beim NTP die Ebene des Servers zu
        einer hochgenauen Hardwareuhr bezeichnet. Ein Stratum-1-Server
        ist mit einer Hardwareuhr verbunden. Stratum-2-Server erhalten
        ihre Uhrzeit von Stratum-1- oder anderen Stratum-2-Servern.
 
    <!-- Richtig-->
 
    2.  Mit dem NTP kann ein Client Zeitsignale von einem Server
        abfragen. Dazu wird die Netzwerklaufzeit zwischen Client und
        Server berechnet, um die Uhrzeit entsprechend anzupassen.
 
    <!--Richtig -->
 
    3.  Mit dem NTP wird ein Zeitüberlauf im Jahr 2038 stattfinden.
 
<!-- Falsch – betrifft 32-Bit-Unixzeit, nicht NTP. -->
 
b)  Ein Auszubildender bittet Sie, ihm zu erklären, was ein Überlauf bei
    einem Zeitzähler bedeutet. Sie entscheiden sich, dies anhand eines
    vereinfachten Datentyps zu erklären. Dazu wird ein vorzeichenloser
    Integer-Wert verwendet. Zur einfachen Veranschaulichung sollen nur 3
    Bit für die Darstellung von Zahlen verwenden werden. Mit den 3 Bit
    können Werte dargestellt werden. Als vorzeichenlose Zahl können die
    Werte 0, 1, 2, 3, 4, 5, 6 und 7 dargestellt werden.
 
    jede Sekunde soll der Zähler um eins erhöht werden.
 
    Erklären Sie anhand des Zählers den Überlauf, der nach der 7-ten
    Sekunde stattfindet.
 
A:
 
Überlauf mit 3-Bit-Zähler:
Wertebereich: 0–7.
Nach Erreichen von 7 → nächster Schritt = 0.
→ Zähler springt auf 0 zurück (Überlauf).
 
<!-- -->
 
c)  Der zuvor verwendete Zähler soll mit dem Wert 0 das Datum und die
    Uhrzeit 01.01.2025 0:00 und 0 Sekunden darstellen.
 
    Erklären Sie mit dem zuvor beschriebenen Überlauf d1e Darstellung
    der Uhrzeit, die in der 8. Sekunde erfolgt.
 
A:
 
Zähler springt auf 0 → System interpretiert das als erneuten Startzeitpunkt (01.01.2025 00:00:00).
→ Zeit wird falsch dargestellt, da alter Zustand wiederholt wird.
 
<!-- -->
 
d)  Erklären Sie die Anwendung des Epoch-Wertes, mit dem bei NTP der
    Überlauf verhindert wird.
 
A:
 
Definiert einen festen Startpunkt (z. B. 01.01.1900 für NTP).
Durch größere Datenfelder (z. B. 64 Bit) kann die Zeit fortlaufend gezählt werden, ohne dass sie in absehbarer Zeit überläuft.
 
<!-- -->
 
e)  Ein Kunde erinnert sich an ein Zeitproblem bei Computern, das beim
    Datumswechsel von 1999 auf 2000 auftrat. Ihn beunruhigt, ob so etwas
    zukünftig zu erwarten ist. Recherchieren Sie zu dem
    Jahr-2000-Datumsproblem, das auch als Millennium-Bug oder Y2K-Bug
    bezeichnet wurde.
 
    Erklären Sie das technische Problem das sich dahinter verbarg.
    Recherchieren Sie nach dem Aufwand, der betrieben wurde, um einen
    großflächigen Ausfall von Computersystemen zu vermeiden.
 
A:
 
Millennium-Bug (Y2K):
Viele Systeme speicherten das Jahr zweistellig (99 → 00).
Beim Jahreswechsel 1999/2000 interpretierten Programme 00 als 1900.
→ Gefahr falscher Datums- und Zeitberechnungen.
 
Aufwand:
Weltweit Milliardenkosten (geschätzt über 300 Mrd. USD) durch Code-Prüfungen, Tests und Updates.
 
<!-- -->
 
f)  Recherchieren Sie, welche zukünftigen Überlaufe von Zeitsystemen zu
    erwarten sind und notieren Sie wann sie stattfinden werden.
 
| System                        | Ursache                        | Zeitpunkt                          |
| ----------------------------- | ------------------------------ | ---------------------------------- |
| 32-Bit-Unixzeit               | Sekundenzähler läuft über      | 19. Januar 2038, 03:14:07 UTC      |
| NTP (32-Bit-Sekundenfeld)     | Überlauf seit 1900             | 7. Februar 2036, 06:28:16 UTC      |
| GPS-Zeit (1024-Wochen-Zyklus) | Wiederholung des Wochenzählers | Nächster Überlauf im Jahr 2039     |
 
