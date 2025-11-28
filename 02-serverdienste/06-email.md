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

## Aufgabe 2

Unterscheiden Sie die Protokolle SMTP, IMAP und POP3.

## Aufgabe 3

Beschreiben Sie den Aufbau einer E-Mail.

## Aufgabe 4

Beschreiben Sie die drei gängigen Authentifizierungsverfahren im
E-Mail-System.

## Aufgabe 5

a)  Zum Abrufen von E-Mails werden u. a. die Protokolle IMAP und POP3
    eingesetzt Beschreiben Sie die Unterschiede der beiden Protokolle.

<!-- -->

b)  Als E-Mail-Client lässt sich eine Vielzahl von Produkten einsetzen.
    Recherchieren Sie drei Produkte, die einen Mail User Agent (MUA)
    anbieten.

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

    - Auflösen des Domain-Anteils einer E-Mail-Adresse in eine
      IP-Adresse

    - Protokoll zum Abrufen von E-Mails

    - Protokoll zum Senden von E-Mails

    - Software, die E-Mails auf Postfächer verteilt

    - leitet E-Mails in die Richtung des Ziels weiter

<!-- -->

d)  Die Stadt Marburg verwendet E-Mail-Adressen nach dem Muster
    `Vorname.Nachname@Amt.stadt-marburg.de`. Gegeben ist die
    E-Mail-Adresse `monika.musterfrau@buergerbuero.stadt-marburg.de`.
    Zerlegen Sie die Adresse in die einzelnen Bestandteile (FQDN) und
    benennen Sie diese.

<!-- -->

e)  Sie sollen einem neuen Auszubildenden die Wichtigkeit des
    DNS-Systems erklären. In einem ersten Beispiel haben Sie über die
    Namensauflösung beim Surfen im Internet gesprochen. Der
    Auszubildende möchte aber noch einen weiteren Anwendungszweck
    kennenlernen. Beschreiben Sie die Rolle des DNS beim Versenden einer
    E-Mail an eine externe E-Mail-Adresse.

<!-- -->

f)  Ein Mitarbeiter berichtet, dass der E-Mail-Server des Katasteramts
    einmal auf einer „Blocklist" eines bekannten
    Internet-Service-Providers stand. Zwei Tage lang wurden viele
    E-Mails des Katasteramts als Spam-E-Mails von diesem Provider
    abgelehnt. Der Mitarbeiter fragt Sie nach einem möglichen Grund.
    Diskutieren Sie in Partnerarbeit die Gefahren eines „offenen
    SMTP-Relays". Beschreiben Sie einen allgemeinen Lösungsansatz.

<!-- -->

g)  Der Mitarbeiter erklärt Ihnen, dass er bei E-Mails, die ihm seltsam
    vorkommen, den E-Mail-Header untersucht. Oftmals würde sich der
    Absender im E-Mail-Header vom dargestellten Absender unterscheiden.
    Erklären Sie am folgenden Beispiel, warum es sich hierbei
    wahrscheinlich um eine Spam-E-Mail handelt.

    ::: {text="xs"}
        Return-Path: <>
        Authentication-Results: gmx.net; dkim=none
        Received: from atlportal.ssdis.com ([146.0.40.20]) by mx.katasteramt.stadt-wolkenlos.
        (mxx014 [212.227.15.9]) with ESMTP (Nemesis) id 1MmjfY-1os0pU0OKko-00js6i for
        <peter.peterson@katasteramt.stadt-wolkenlos.de>; Mon, 23 Jan 2023 10:37:50 +0100
        From: Post-Tracking <0eevcu7t4wb2ml2@kiseet.fluctima.us.com.de>
        To: peter.peterson@katasteramt.stadt-wolkenlos.de
        Subject: Paketverfolgung online
        MIME-Version: 1.0
        Content-Type: text/html; charset="UTF-8"
        Content-Transfer-Encoding: 7bit
        List-Unsubscribe: <mailto:leave-ig@atlportal.ssdis.com>
        Message-Id: <LYRIS-a.b-__Date@atlportal.ssdis.com>
        Envelope-To: <peter.peterson@katasteramt.stadt-wolkenlos.de>
    :::
