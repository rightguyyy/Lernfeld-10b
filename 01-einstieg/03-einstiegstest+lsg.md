---
css: ../css/style.css
date: Schuljahr 2025/2026
lang: de-DE
subtitle: Lernfeld 10b -- Serverdienste bereitstellen und
  Administrationsaufgaben automatisieren
title: Einstiegstest LF10b
---

Überprüfen Sie Ihr Grundlagenwissen aus dem Lernfeld 9 »Netzwerke und
Dienste bereitstellen«.

Bearbeiten Sie die folgenden Teilaufgaben.

### Aufgabe 1

a)  Bringen Sie die folgenden Prozessschritte in eine sachlogische
    Reihenfolge.

    - Ziele, Migrationsstrategie

    - Konzeptionierung

    - Ist-Analyse

    - Betrieb

    - Umsetzung

    ::: {.solution}
    1.  Ist-Analyse

    2.  Ziele, Migrationsstrategie

    3.  Konzeptionierung

    4.  Umsetzung

    5.  Betrieb
    :::

<!-- -->

b)  Beschreiben Sie die folgenden Aspekte des Projektmanagements in
    eigenen Worten.

    - Aufwandsabschätzung

    - Abnahme

    - Projektstrukturplan

    - Stakeholder-Analyse

    ::: {.solution}
    - Aufwandsabschätzung: Alle zum Projekt gehörenden Aufgaben werden
      hinsichtlich ihres zeitlichen, finanziellen und personellen
      benötigten Umfangs eingeschätzt.

    - Abnahme: Überprüfung der erbrachten Leistung hinsichtlich der
      zuvor vereinbarten Anforderungen. Kann durch Abnahmetests oder
      Checklisten erfolgen.

    - Projektstrukturplan: Darstellung aller Teilaspekte eines Projektes
      (z. B. Arbeitspakete, Teilprojekte) in hierarchischer Form.
      Enthält meist auch die zuständigen Stakeholder.

    - Stakeholder-Analyse: Identifiziert alle für ein Projekt
      notwendigen Beteiligten bzw. Unternehmensbereiche. Berücksichtigt
      auch den möglichen Einfluss (positiv/negativ) auf den
      erfolgreichen Verlauf eines Projektes. Das Ergebnis kann in den
      Projektstrukturplan in Form von Teilprojektverantwortlichen
      einfließen.
    :::

<!-- -->

c)  Geben Sie je zwei Aspekte an, die in einem Lasten- bzw.
    Pflichtenheft enthalten sind.

    ::: {.solution}
    Lastenheft:

    - funktionale und nicht funktionale Anforderungen, die der Kunde an
      ein Projekt stellt.
    - Ist-Analyse bzw. Ausgangslage
    - kann aktuellen Netzplan enthalten
    - weitere Nennungen möglich

    Pflichtenheft:

    - Fachkonzept des Auftragsnehmers
    - Soll-Konzept inkl. Überlegungen zur technischen Umsetzung
    - Vertragsgrundlage
    - Abgrenzungen, die nicht innerhalb des Projektes erbracht werden
      weitere Nennungen möglich
    :::

### Aufgabe 2

Entscheiden Sie, ob die folgenden Aussagen richtig oder falsch sind.

a)  DevOps steht für Entwicklung und Betrieb eines Unternehmensbereichs.

    ::: {.solution}
    wahr
    :::

<!-- -->

b)  Unter CI versteht man kontinuierliche Identifikation von neuen
    Anforderungen an einen Unternehmensbereich.

    ::: {.solution}
    falsch, Integration statt Identifikation
    :::

<!-- -->

c)  Der Bereich DevOps kann als Schnittmenge der Bereiche Entwicklung,
    Betrieb und Buchhaltung betrachtet werden.

    ::: {.solution}
    falsch, Qualitätssicherung statt Buchhaltung
    :::

<!-- -->

d)  Der Bereich CD umfasst das Paketieren Freigeben, Konfigurieren und
    Überwachen einer Anwendungssoftware für die Kunden.

    ::: {.solution}
    wahr
    :::

### Aufgabe 3

a)  Ordnen Sie der Ethernet-Leitung die entsprechenden Bereiche 1-5 zu.
    Geben Sie weiterhin die Leitungsart (Kurzschreibweise) an.

    ![](images/lan-tp-kabel-querschnitt.png){width="50%"}

    | Nummer | Bereich        |
    |--------|----------------|
    |        | Folienschirm   |
    |        | Geflechtschirm |
    |        | Isolator       |
    |        | Ader           |
    |        |                |

    Leitungsart:

    ::: {.solution}
    1.  innere Folienabschirmung (leitend; Schutz gegen Störungen)

    2.  Ader (leitend; Signal)

    3.  innerer Isolator (nicht leitend)

    4.  äußere Geflechtabschirmung (leitend; Schutz gegen Störungen)

    5.  äußerer Isolator (nicht leitend)

    Leitungsart: S/FTP
    :::

<!-- -->

b)  Es sollen die unterschiedlichen Adressierungsarten in einem Netzwerk
    betrachtet werden. Ergänzen Sie die folgende Tabelle zu den
    häufigsten Adressarten.

    | OSI-Schicht | Adressenname | Länge in Bit | Aufgabe |
    |----|----|----|----|
    | 4 |  |  | Identifikation der Anwendung bzw. des Dienstes |
    |  | MAC |  |  |
    | 3 |  |  |  |
    |  |  | 32 Bit |  |

    ::: {.solution}
    | OSI-Schicht | Adressenname | Länge in Bit | Aufgabe |
    |----|----|----|----|
    | 4 | Port | 16 | Identifikation der Anwendung bzw. des Dienstes |
    | 2 | MAC | 48 | Identifikation der Hardwareschnittstelle (Netzwerkkarte) |
    | 3 | IPv6 | 128 | Identifikation eines Systems (PC) |
    | 3 | IPv4 | 32 Bit | Identifikation eines Systems (PC) |
    :::

<!-- -->

c)  Geben Sie für den folgenden Netzplan die statischen Routen für
    Router R1 an, sodass dieser alle Netze erreichen kann.

    ![](images/lan-netzwerkplan.png)

    | Ziel         | Next Hop | Schnittstelle |
    |--------------|----------|---------------|
    | 10.0.10.0/24 |          |               |
    | 10.0.20.0/24 |          |               |
    | 10.0.30.0/24 |          |               |
    | 10.0.40.0/24 |          |               |
    | 10.0.50.0/24 |          |               |

    ::: {.solution}
    | Ziel         | Next Hop           | Schnittstelle |
    |--------------|--------------------|---------------|
    | 10.0.10.0/24 | 10.0.10.1 (direkt) | eth0          |
    | 10.0.20.0/24 | 10.0.20.1 (direkt) | eth1          |
    | 10.0.30.0/24 | 10.0.20.2          | eth1          |
    | 10.0.40.0/24 | 10.0.40.1 (direkt) | eth2          |
    | 10.0.50.0/24 | 10.0.40.3          | eth2          |
    :::

<!-- -->

d)  Geben Sie für die folgenden Protokolle jeweils kurz deren Aufgaben
    innerhalb eines Netzes an.

    - DNS

    - DHCP

    - SSH

    - SMB

    - IMAP

    - SNMP

    ::: {.solution}
    - DNS: Auflösung von FQDN bzw. Name in IP-Adresse

    - DHCP: automatische IP-Adressvergabe sowie Konfigurationsparameter
      zu DNS, NTP, BOOTP

    - SSH: sicherer Remote-Zugang zu Kommandozeile

    - SMB: Drucker-/Dateifreigabe in Windows-Netzen

    - IMAP: E-Mail-Protokoll (nur Empfang)

    - SNMP: Monitoring-Protokoll zur Überwachung von Netzelementen
      (z. B. Netzdrucker, Switch, Router etc.)
    :::

### Aufgabe 4

a)  Geben Sie jeweils mindestens drei technische Anforderungen an eine
    Firewall, einen Server und ein NAS an.

    ::: {.solution}
    mögliche Antworten; andere Nennungen möglich; siehe Schülerbuch,
    Lernfeld 9, Kapitel 4.3.2

    Firewall:

    - URL-/Inhaltsfilter
    - Intrusion Detection
    - Intrusion Prevention
    - Datendurchsatz
    - Reporting

    Server:

    - Anzahl CPU Kerne
    - Größe des RAMs
    - Größe/Art des Datenspeichers (SSD/HDD)
    - Netzwerkanbindung
    - Betriebssystem

    Hier sind allgemeine Anforderungen aufgeführt. Für VMs und Dedicated
    Server sind andere Nennungen möglich.

    NAS:

    - Größe des Datenspeichers
    - Art des Datenspeichers (HDD, SSD)
    - RAID-System
    - Netzwerkanbindung
    - unterstützte Netzprotokolle
    :::

<!-- -->

b)  Entscheiden Sie, welche der folgenden Funktionen in einem
    SOHO-Router vorzufinden sind.

    1.  DSL-Modem
    2.  Analog-Modem
    3.  LWL-Modem
    4.  Webserver
    5.  Telefonanlage
    6.  TFTP-Server
    7.  WLAN-Accesspoint
    8.  Repeater
    9.  Firewall

    ::: {.solution}
    1.  DSL-Modem → ja
    2.  Analog-Modem → nein
    3.  LWL-Modem → ja
    4.  Webserver → ja
    5.  Telefonanlage → ja
    6.  TFTP-Server → nein
    7.  WLAN-Accesspoint → ja
    8.  Repeater → unter Umständen / nein
    9.  Firewall → ja
    :::

### Aufgabe 5

Berechnen Sie den Bezugspreis für einen Server mithilfe der gegebenen
Werte.

Listenbreis: 5000,00 €

Lieferrabatt: 3 %

Skonto: 2 %

Transportkosten: 5000,00 € pro 100 Stück

::: {.solution}
5 000,00 € (Listenpreis)  
− 150,00 € (= 5 000,00 € × 0,03) (Lieferrabatt)  
= 4 850,00 € (Zieleinkaufspreis)  
− 97,00 € (= 4 850,00 € × 0,02) (Skonto)  
= 4 753,00 € (Bareinkaufspreis)  
+ 50,00 € (= 5 000,00 €/100) (Bezugskosten)  
= 4 803,00 € (Bezugspreis)
:::

### Aufgabe 6

Geben Sie die Aufgabengebiete der folgenden Programme an.

Beispiel: ip (Linux): Konfiguration und Anzeige der IP-Adressen und
Routen

- bmon

- netstat

- ipconfg

- nslookup

- arp

- tracert/traceroute

::: {.solution}
- bmon: zeigt aktuellen Netzwerkverkehr grafisch an

- netstat: listet Informationen zu aktuellen Verbindungen auf; z. B.
  alle aktiven TCP-Ports

- ipconfig: ähnlich wie ip; nur unter Windows verfügbar; zeigt nur
  IP-Adressen (inkl. Gateway an)

- nslookup: DNS-Abfragen; inkl. Reverse-Lookup

- arp: zeigt MAC-Adressen und die dazugehörende IP-Adresse an, sofern
  diese vom System bereits gelernt wurden

- tracert/traceroute: zeigt die Hops (Router) bis zu einer IP-Adresse
  an, sofern diese eine entsprechende ICMP-Rückmeldung geben.
:::

### Aufgabe 7

Erklären Sie kurz die Unterschiede zwischen Docker, VirtualBox und
Proxmox.

::: {.solution}
- Docker: Container-System zum Aufbau von Anwendungen auf einem
  bestehenden System; Applikationsvirtualisierung

- VirtualBox: VirtualBox ist eine Virtualisierungssoftware, die eine
  isolierte Umgebung für virtuelle Maschinen auf einem
  Host-Betriebssystem bereitstellt. Es simuliert die Hardware, die ein
  Gastbetriebssystem benötigt, um ausgeführt werden zu können.

- Proxmox: Stellt eine eigenständige Virtualisierungsumgebung (ohne
  weiteres Betriebssystem) bereit. Bildet die Hardwareschnittstelle für
  die VM ab.
:::
