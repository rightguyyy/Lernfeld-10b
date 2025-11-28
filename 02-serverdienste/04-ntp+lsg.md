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
- NTP-Zeitmessung im Timestamp-Format
- NTP-Zeitmessung im Datestamp-Format

::: {.solution}
- Linux-Zeitmessung mit timestamp

  Der 1.1.1970 ist der Startzeitpunkt auf den sich der timestamp bezieht
  und wird als epoch bezeichnet. Die Zeit wird als
  32-bit-signed-integer-Wert relativ zu dem Startzeitpunkt in der
  koordinierten Weltzeit (Coordinated universal time -- UTC)
  gespeichert.

  In diesem Format kann die Zeit nur bis zum 19.1.2038 dargestellt
  werden. Das Problem wurde durch die Umstellung auf 64-Bit behoben,
  kann aber bei alten Systemen noch weiterhin bestehen.

- NTP-Zeitmessung im Timestamp-Format

  Deim Timestamp-Format werden 64 Bit verwendet. Die ersten 32 Bit sind
  die Sekunden seit Beginn des epoch, die aktuelle begann am 1.1.1900.
  Die Darstellung genügt 136 Jahre. Die zweiten 32 Bit dienen zur
  Darstellung des Bruchteils einer Sekunde, dabei ist eine Genauigkeit
  in Nanosekunden darstellbar.

- NTP-Zeitmessung im Datestamp-Format

  Das »NTP Date Format« besteht aus einer 32-Bit-signed-integer Era
  Number, einem 32-Bit-signed-integer Era Offset und einer 64-Bit
  Fraction, die eine Genauigkeit von 0,05 Attosekunden ermöglicht (Vgl.
  [RFC5905](https://www.rfc-editor.org/rfc/rfc5905#section-6)).
:::

## Aufgabe 2

Erklären Sie, was Stratum-0 ist.

::: {.solution}
NTP nutzt ein hierarchisches System verschiedener Strata. Als Stratum 0
bezeichnet man das Zeitnormal, eine hochgenaue Uhr, beispielsweise eine
Atomuhr oder eine Funkuhr.
:::

## Aufgabe 3

a)  Entscheiden Sie, ob die folgenden Aussagen zu Network Timing
    Protocol (NTP) richtig oder falsch sind.

    1.  Mit dem Begriff „Stratum" wird beim NTP die Ebene des Servers zu
        einer hochgenauen Hardwareuhr bezeichnet. Ein Stratum-1-Server
        ist mit einer Hardwareuhr verbunden. Stratum-2-Server erhalten
        ihre Uhrzeit von Stratum-1- oder anderen Stratum-2-Servern.

    ::: {.solution}
    richtig
    :::

    2.  Mit dem NTP kann ein Client Zeitsignale von einem Server
        abfragen. Dazu wird die Netzwerklaufzeit zwischen Client und
        Server berechnet, um die Uhrzeit entsprechend anzupassen.

    ::: {.solution}
    richtig
    :::

    3.  Mit dem NTP wird ein Zeitüberlauf im Jahr 2038 stattfinden.

    ::: {.solution}
    falsch, das betrifft die Linux-Zeitmessung mit
    32-Bit-signed-integer.
    :::

<!-- -->

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

    ::: {.solution}
    Mehr als die Zahl 7 ist nicht darstellbar. Danach beginnt der Zähler
    wieder von vorne, also bei 0, da dies üblicherweise bei der
    Integer-Arithmetik in der Hardware so implementiert ist.
    :::

<!-- -->

c)  Der zuvor verwendete Zähler soll mit dem Wert 0 das Datum und die
    Uhrzeit 01.01.2025 0:00 und 0 Sekunden darstellen.

    Erklären Sie mit dem zuvor beschriebenen Überlauf d1e Darstellung
    der Uhrzeit, die in der 8. Sekunde erfolgt.

    ::: {.solution}
    In der 8. Sekunde geht der Zähler wieder auf 0 zurück. Damit ist die
    Uhrzeit wieder bei 01.01.2025 0:00 und 0 Sekunden.
    :::

<!-- -->

d)  Erklären Sie die Anwendung des Epoch-Wertes, mit dem bei NTP der
    Überlauf verhindert wird.

    ::: {.solution}
    Durch die Era Number ist NTP gegenüber Überläufen der Zähler, bei
    denen der Zeitwert auf den Anfangswert zurückspringt gesichert.
    :::

<!-- -->

e)  Ein Kunde erinnert sich an ein Zeitproblem bei Computern, das beim
    Datumswechsel von 1999 auf 2000 auftrat. Ihn beunruhigt, ob so etwas
    zukünftig zu erwarten ist. Recherchieren Sie zu dem
    Jahr-2000-Datumsproblem, das auch als Millennium-Bug oder Y2K-Bug
    bezeichnet wurde.

    Erklären Sie das technische Problem das sich dahinter verbarg.
    Recherchieren Sie nach dem Aufwand, der betrieben wurde, um einen
    großflächigen Ausfall von Computersystemen zu vermeiden.

    ::: {.solution}
    Zur Speicherung und Verarbeitung von Jahreszahlen (in
    Dezimaldarstellung) wurden nur die letzten beiden Ziffern (Jahr und
    Jahrzehnt, etwa im Format „TTMMJJ" o. Ä.) benutzt. Viele (ältere)
    Programm konnten Jahreszahlen ab dem Jahr 2000 nicht korrekt
    verarbeiten.
    :::

<!-- -->

f)  Recherchieren Sie, welche zukünftigen Überlaufe von Zeitsystemen zu
    erwarten sind und notieren Sie wann sie stattfinden werden.

    ::: {.solution}

    Jahr-2027-Problem
    :   Am 1. Januar 2027 werden die Bits im Datenformat des Kalenders
        auf den Rechnern der 3000er-Serie von Hewlett-Packard
        aufgebraucht sein. Dabei handelt es sich um ein altes System der
        Mittleren Datentechnik, für das seit Dezember 2015 keine
        Unterstützung des Herstellers mehr besteht.

    Jahr-2038-Problem
    :   Zum 19. Januar 2038 könnten wiederum ähnliche Probleme auftreten
        und bei EDV-Systemen zu Softwareausfällen führen. Dieses Problem
        dürfte jedoch auf EDV-Systeme beschränkt sein, die die Unixzeit
        als Zeitstandard benutzen. Ursache dafür ist, dass im Jahr 2038
        die verwendete vorzeichenbehaftete 32-Bit-Ganzzahl nicht mehr
        zur Zeitdarstellung ausreicht und es somit zu einem
        arithmetischen Überlauf kommt.

    Jahr-2100-Problem
    :   Da in praktisch allen gängigen Echtzeituhren die Jahreszahl
        weiterhin nur durch die niederwertigen zwei Jahresziffern
        repräsentiert wird, kann es zum 1. Januar 2100 zu einer
        Wiederholung des Jahr-2000-Problems kommen, dann speziell für
        eingebettete Systeme, in denen diese Echtzeituhren verbaut
        wurden.

    GPS-Woche
    :   Die Wochenzählung des GPS-Zeitsignals begann 1980 bei Null und
        benutzt 10 Bit, was 1023 Wochen bzw. ca. 20 Jahren entspricht.
        Danach springt der Zähler wieder auf Null. Beim ersten Überlauf
        1999 bestanden ebenfalls Befürchtungen, dass dies nicht bei
        allen GPS-Empfängern problemlos verlaufen könnte. Der zweite
        Überlauf fand am 7. April 2019 um 01:59:42 MESZ statt.

    (Aus:
    <https://de.wikipedia.org/wiki/Jahr-2000-Problem#%C3%84hnliche_Probleme>)

    Eng verwandt zum Jahr-2038-Problem ist das Jahr **2036 (Numeronym:
    Y2K36)**. Am Donnerstag, 7. Februar 2036 um 06:28:16 Uhr UTC läuft
    der Zähler des ursprünglich für UNIX entwickelten
    Zeitsynchronisations-Protokolls NTP (Network Time Protocol) über. In
    modernen Implementierungen ist dieses Problem zwar behoben (siehe
    RFC 5905), doch sehr viele Geräte -- besonders eingebettete Systeme
    -- arbeiten noch nach dem alten Standard RFC 868.

    Auch hier ist der Hintergrund, dass die Zeitübermittlung als
    32-Bit-Zahl in Sekunden stattfindet, jedoch mit der Startzeit 1.
    Januar 1900, 00:00:00 Uhr UTC und nicht vorzeichenbehaftet. Bei sehr
    ordentlicher Implementierung der Systeme kommt es sogar hier zu
    keinem (größeren) Problem während der Berechnung, da die
    Zeitsynchronisation nach einer Differenz-Methode arbeiten sollte.

    (Aus:
    <https://de.wikipedia.org/wiki/Jahr-2038-Problem#Verwandtes_Jahr-2036-Problem>)

    Das **Jahr-2106-Problem** von EDV-Systemen könnte zu Ausfällen von
    Software im Jahr 2106 führen. Dieses Problem ist auf EDV-Systeme
    beschränkt, die die Unixzeit benutzen und diese als vorzeichenlose
    32-Bit-Integerzahl speichern. Es ist auch als Bitcoin-Killing-Bug
    medial bekannt.

    Beim Jahr-2106-Problem handelt es sich um ein ähnliches Problem wie
    das Jahr-2038-Problem. Allerdings mit dem Unterschied, dass statt
    einer vorzeichenbehafteten 32-Bit-Integer-Zahl eine vorzeichenlose
    32-Bit-Integer-Zahl verwendet wird. Dadurch tritt der Überlauf
    (wrap-around) erst im Jahr 2106 auf. Beispielsweise ist das embedded
    Unix Betriebssystem QNX ab Version 6.4.0 hiervon betroffen.

    (Aus: <https://de.wikipedia.org/wiki/Jahr-2106-Problem>)
    :::
