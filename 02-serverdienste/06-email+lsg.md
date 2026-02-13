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

::: {.solution}
MUA steht für Mail User Agent, mit diesem werden E-Mails gelesen,
verfasst und abgesendet. Dazu sendet der MUA die E-Mail an den eigenen
E-Mail-Server.

Der E-Mail-Server wird Mail Transfer Agent (MTA) genannt. Dieser sendet
die E-Mail an den MTA der Empfänger-Domain. Zum senden kommen das Simple
Mail Transfer Protocol (SMTP) oder Simple Mail Transfer Protocol Secure
(SMTPS) zu Einsatz.

Vgl. Buch S. 26--27
:::

## Aufgabe 2

Unterscheiden Sie die Protokolle SMTP, IMAP und POP3.

::: {.solution}
Simple Mail Transfer Protocol (SMTP) dient zum Senden von E-Mail
zwischen MUA und MTA sowie ziwschen den MTAs zum Einsatz.

IMAP und POP3 kommen zum Empfangen von E-Mails zwischen MUA und MTA zum
Einsatz. IMAP hat gegenüber POP3 einen wesentlich größeren
Funktionsumfang, d. h. es können z. B. Ordnerstrukturen verwaltet werden
und der gemeinsame Zugriff mehrerer Benutzer mit Rechtevergabe ist
möglich.

Vgl. Buch S. 26--27. Anders als im Buch dargestellt, werden bei POP3 die
E-Mail *nicht* zwingend gelöscht, sondern können auch auf dem Server
verbleiben.
:::

## Aufgabe 3

Beschreiben Sie den Aufbau einer E-Mail.

::: {.solution}
Eine E-Mail besteht aus dem E-Mail-Header, der aus mehreren Feldern
besteht, d. h. ein Schlüssel-Wert-Paar pro Zeile, und dem E-Mail-Body.
Der E-Mail-Body besteht aus einem oder mehreren Teilen, wie z. B.
einfachem Text, HTML oder Anhängen, die meist in Base64 codiert sind.

Vgl. Buch S. 29-30
:::

## Aufgabe 4

Beschreiben Sie die drei gängigen Authentifizierungsverfahren im
E-Mail-System.

::: {.solution}
#### »DKIM

Beim Verfahren DomainKeys Identified Mail soll sichergestellt werden,
dass der Inhalt einer E-Mail auf dem Weg zwischen Sender und Empfänger
nicht verändert wurde. DKIM verwendet dazu das Verfahren der digitalen
Signatur. Über die komplette E-Mail (Header und Body) wird ein Hash-Wert
H gebildet und anschließend mit dem privaten Schlüssel des Absenders
verschlüsselt. E-Mail und verschlüsselter Hash-Wert werden an den
Empfänger gesendet. Dieser entschlüsselt den empfangenen Hash-Wert mit
dem zum Absender passenden öffentlichen Schlüssel. Er bildet einen
eigenen Hash-Wert H' über die komplette E-Mail. Abschließend vergleicht
er die beiden Hash-Werte H und H'. Wenn diese identisch sind, ist die
Integrität gewährleistet.

#### SPF

Beim Sender Policy Framework wird der Domain-Teil der
Absender-E-Mail-Adresse einer empfangenen E-Mail geprüft (z. B. lautet
bei der E-Mail-Adresse „test...com" der Domain-Teil „example. com"). Der
empfangende E-Mail-Server befragt das DNS-System, ob es einen
SPF-Eintrag zu der Domain gibt. In diesem SPF-Eintrag ist eine
IP-Adresse hinterlegt, von der E-Mails mit entsprechendem Domain-Teil
kommen dürfen. Diese IP-Adresse wird mit der Absender-IP-Adresse
verglichen. Nur wenn die beiden IP-Adressen übereinstimmen, gilt der
Absender als verifiziert.

#### DMARC

Die Spezifikation Domain-based Message Authentication, Reporting and
Conformance kann zusätzlich zu DKIM und SPF festlegen, was mit E-Mails
passiert, bei denen SPF und oder DKIM fehlschlägt. Dazu muss es im
DNS-System eine DMARC-Richtlinie geben, die anzeigt, wie mit der E-Mail
zu verfahren ist.«

Buch S. 28
:::

## Aufgabe 5

a)  Zum Abrufen von E-Mails werden u. a. die Protokolle IMAP und POP3
    eingesetzt Beschreiben Sie die Unterschiede der beiden Protokolle.

    ::: {.solution}
    IMAP und POP3 kommen zum Empfangen von E-Mails zwischen MUA und MTA
    zum Einsatz. IMAP hat gegenüber POP3 einen wesentlich größeren
    Funktionsumfang, d. h. es können z. B. Ordnerstrukturen verwaltet
    werden und der gemeinsame Zugriff mehrerer Benutzer mit
    Rechtevergabe ist möglich.

    Vgl. Buch S. 26--27. Anders als im Buch dargestellt, werden bei POP3
    die E-Mail *nicht* zwingend gelöscht, sondern können auch auf dem
    Server verbleiben.
    :::

<!-- -->

b)  Als E-Mail-Client lässt sich eine Vielzahl von Produkten einsetzen.
    Recherchieren Sie drei Produkte, die einen Mail User Agent (MUA)
    anbieten.

    ::: {.solution}
    - Apple Mail
    - Evolution
    - MicroSoft Outlook
    - RoundCube
    - Thnderbird
    :::

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

    ::: {.solution}
    1.  Mail Transfer Agent: leitet E-Mails in die Richtung des Ziels
        weiter
    2.  SMTP: Protokoll zum Senden von E-Mails
    3.  Domain Name Service: Auflösen des Domain-Anteils einer
        E-Mail-Adresse in eine IP-Adresse
    4.  IMAP: Protokoll zum Abrufen von E-Mails
    5.  Mail Delivery Agent: Software, die E-Mails auf Postfächer
        verteilt
    6.  Mail User Agent: Programm zum Versenden und Empfangen von
        E-Mails
    :::

<!-- -->

d)  Die Stadt Marburg verwendet E-Mail-Adressen nach dem Muster
    `Vorname.Nachname@Amt.stadt-marburg.de`. Gegeben ist die
    E-Mail-Adresse `monika.musterfrau@buergerbuero.stadt-marburg.de`.
    Zerlegen Sie die Adresse in die einzelnen Bestandteile (FQDN) und
    benennen Sie diese.

    ::: {.solution}
    - Local Part: monika.musterfrau

    - @

    - Domain: buergerbuero. stadt-marburg. de

      - Subdomain: buergerbuero
      - Domain: stadt-marburg
      - TLD: de
    :::

<!-- -->

e)  Sie sollen einem neuen Auszubildenden die Wichtigkeit des
    DNS-Systems erklären. In einem ersten Beispiel haben Sie über die
    Namensauflösung beim Surfen im Internet gesprochen. Der
    Auszubildende möchte aber noch einen weiteren Anwendungszweck
    kennenlernen. Beschreiben Sie die Rolle des DNS beim Versenden einer
    E-Mail an eine externe E-Mail-Adresse.

    ::: {.solution}
    MX-Record: Domain-Name der E-Mail-Adresse → Domain-Name des
    E-Mail-Servers

    A-Record: Domain-Name des E-Mail-Servers → IP-Adresse
    :::

<!-- -->

f)  Ein Mitarbeiter berichtet, dass der E-Mail-Server des Katasteramts
    einmal auf einer „Blocklist" eines bekannten
    Internet-Service-Providers stand. Zwei Tage lang wurden viele
    E-Mails des Katasteramts als Spam-E-Mails von diesem Provider
    abgelehnt. Der Mitarbeiter fragt Sie nach einem möglichen Grund.
    Diskutieren Sie in Partnerarbeit die Gefahren eines „offenen
    SMTP-Relays". Beschreiben Sie einen allgemeinen Lösungsansatz.

    ::: {.solution}
    Offene SMTP-Relays leiten E-Mails ohne Authentifizierung weiter und
    werden oft für Spam verwendet.

    Blocklisten werden zur Vermeiden bzw. Verminderung von Spam
    eingesetzt.

    Falls man vermutet, dass der eigene Server betroffen ist, kann man
    dann einen Blacklist-Check durchführen.

    Meist sind IP-Adressbereiche betroffen und der Server-Provider muss
    aktiv werden, d. h. den Spam-Versender stoppen und eine Löschung der
    IP-Adressbereiche von der Black-List beantragen.
    :::

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

    ::: {.solution}
    - Die Domains unter `Received` und `From` stimmen nicht überein.
    - Die Mail-Domain des Absenders ist auffällig, das sie aus sehr
      verschachtelt Subdomains besteht
    - Der Name des Absenders passt nicht zur E-Mail-Adresse
    - Der Local-Part des Absenders ist krpytisch und vermutlich eine
      zufällige Zeichen- und Zahlenkombination
    - Der Betreff ist sehr generisch und soll zum öffnen der E-Mail
      anregen, da er auf viele Alltagssituationen passt
    :::
