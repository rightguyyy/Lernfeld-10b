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

::: {.solution}
DHCP umfasst mehrere Schritte, die oft als DORA-Prozess bezeichnet
werden: Discover, Offer, Request, und Acknowledge.

1.  »Wenn ein Client erstmals eine IP-Adresse benötigt, schickt er eine
    DHCPDISCOVER-Nachricht (mit seiner MAC-Adresse) als
    Netzwerk-Broadcast an die verfügbaren DHCP-Server (es kann mehrere
    im selben Subnetz geben). Dieser Broadcast hat als
    Absender-IP-Adresse 0.0.0.0 und als Zieladresse 255.255.255.255, da
    der Absender noch keine IP-Adresse besitzt und seine Anfrage „an
    alle" richtet. Dabei ist der UDP-Quellport 68 und der UDP-Zielport
    67.

2.  Die DHCP-Server antworten mit DHCPOFFER und machen Vorschläge für
    eine IP-Adresse. Das geschieht entweder mit einem Broadcast an die
    Adresse 255.255.255.255 mit UDP-Quellport 67 und UDP-Zielport 68
    oder mit einem Unicast an die vorgeschlagene IP-Adresse und die
    MAC-Adresse des Clients, je nachdem ob der Client in der
    DHCPDISCOVER-Nachricht das Broadcast-Bit gesetzt hat.

3.  Der Client darf nun unter den eingetroffenen Angeboten (DHCPOFFER)
    wählen. Wenn er sich für eines entschieden hat (z. B. wegen längster
    Lease-Zeit oder wegen Ablehnung eines speziellen, evtl. falsch
    konfigurierten DHCP-Servers, oder einfach für die erste Antwort),
    kontaktiert er per Broadcast und einem im Paket enthaltenen
    Serveridentifier den entsprechenden Server mit der Nachricht
    DHCPREQUEST. Alle eventuellen weiteren DHCP-Server werten das als
    Absage für ihre Angebote.

4.  Der vom Client ausgewählte Server bestätigt in einer
    DHCPACK-Nachricht (DHCP-Acknowledged) die IP-Adresse mit den
    weiteren relevanten Daten, oder er zieht sein Angebot zurück
    (DHCPNAK, siehe auch Sonstiges).« (Vgl.
    <https://de.wikipedia.org/wiki/Dynamic_Host_Configuration_Protocol#Initiale_Adresszuweisung_(Lease/Vergabe)>)

5.  Bevor der Client sein Netzwerkinterface mit der zugewiesenen Adresse
    konfiguriert, sollte er noch prüfen, ob nicht versehentlich noch ein
    anderer Rechner die Adresse verwendet. Das geschieht üblicherweise
    durch einen ARP-Request mit der soeben zugeteilten IP-Adresse.
    Antwortet ein anderer Host im Netz auf diesen Request, so wird der
    Client die vorgeschlagene Adresse mit einer DHCPDECLINE-Nachricht
    zurückweisen.

### Zusätzliche Nachrichten:

- DHCPNAK: Wenn der Server feststellt, dass eine Anfrage ungültig oder
  die angebotene IP-Adresse bereits anderweitig vergeben ist, kann er
  eine DHCPNAK-Nachricht (Negative Acknowledge) senden. Dies
  signalisiert dem Client, den Prozess erneut zu starten.
- DHCPRELEASE: Der Client kann die zugewiesene IP-Adresse freigeben,
  wenn er sie nicht mehr benötigt, indem er eine DHCPRELEASE-Nachricht
  an den Server sendet.

Vgl. <https://www.rfc-editor.org/rfc/rfc2131>
:::

## Aufgabe 2

Geben Sie drei Informationen an, welche bei einer DHCP-Offer-Nachricht
vom DHCP-Server an den Client gesendet werden.

::: {.solution}
- IP address lease time
- server identifier
- Maximum message size
- client identifier

Bei einer DHCP-Offer-Nachricht sendet der DHCP-Server dem Client mehrere
wichtige Informationen, die für die Netzwerkkonfiguration des Clients
notwendig sind. Drei zentrale Informationen, die typischerweise in einer
DHCPOFFER-Nachricht enthalten sind, sind:

1.  IP-Adresse: Der Server schlägt dem Client eine IP-Adresse vor, die
    dieser für die Kommunikation im Netzwerk verwenden kann.

2.  Subnetzmaske: Diese Angabe definiert, welcher Teil der IP-Adresse
    den Netzwerkanteil und welcher Teil den Hostanteil darstellt, und
    hilft dem Client dabei, zu verstehen, welche anderen IP-Adressen
    sich im gleichen Subnetz befinden.

3.  Gateway-Adresse (Standard-Gateway): Dies ist die IP-Adresse des
    Standard-Gateways, über das der Client Anfragen an andere Netzwerke,
    wie das Internet, weiterleiten kann.

Zusätzlich können auch Informationen wie die DNS-Server-Adressen und die
Lease-Dauer enthalten sein, aber die oben genannten drei sind die
wesentlichen Bestandteile einer DHCP-Offer-Nachricht.
:::

## Aufgabe 3

Die DHCP- Request Nachricht wird als Broadcast-Nachricht an alle
Teilnehmer im Netzwerk gesendet. Begründen Sie dieses Vorgehen.

::: {.solution}
Die DHCP-Request-Nachricht wird als Broadcast-Nachricht an alle
Teilnehmer im Netzwerk gesendet, um sicherzustellen, dass sowohl der
ausgewählte DHCP-Server als auch alle anderen DHCP-Server im Netzwerk
über die Wahl des Clients informiert werden. Die wichtigsten Gründe für
dieses Vorgehen sind:

1.  Benachrichtigung aller DHCP-Server: Wenn mehrere DHCP-Server auf die
    ursprüngliche DHCP-Discover-Nachricht mit einem DHCPOFFER
    geantwortet haben, informiert der Client mit der
    DHCP-Request-Nachricht alle DHCP-Server, dass er die IP-Adresse
    eines bestimmten Servers akzeptiert hat. Dies stellt sicher, dass
    die anderen Server ihre angebotenen IP-Adressen wieder freigeben
    können und sie nicht länger für den Client reservieren.

2.  Fehlende IP-Adresse des Clients: Zu diesem Zeitpunkt hat der Client
    noch keine endgültig zugewiesene IP-Adresse, die er für
    unicast-basierte Kommunikation verwenden könnte. Da der Client noch
    keine eigene IP-Adresse besitzt oder verwendet, muss die
    Kommunikation in Form eines Broadcasts geschehen, damit die
    Nachricht alle Teilnehmer erreichen kann.

3.  Netzwerkkonformität und Konfliktvermeidung: Durch das Senden als
    Broadcast kann sichergestellt werden, dass keine IP-Adresskonflikte
    im Netzwerk entstehen. Alle Geräte und Server im Netzwerk werden
    über die Entscheidung des Clients informiert, sodass keine zwei
    Geräte versehentlich dieselbe IP-Adresse erhalten.
:::

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

::: {.solution}
Ziel-MAC-Adresse (6 Byte): ff ff ff ff ff ff

Dies ist eine Broadcast-MAC-Adresse, was bedeutet, dass diese Nachricht
an alle Geräte im Netzwerk gesendet wird.

Quell-MAC-Adresse (6 Byte): 08 00 27 e2 ed 6e

Dies ist die MAC-Adresse des DHCP-Clients, der die
DHCP-Request-Nachricht gesendet hat.
:::

## Aufgabe 5

Diskutieren Sie in Partnerarbeit die Aufgabe eines DHCP-Relays bei DHCP.

::: {.solution}
Ein DHCP-Relay dient der Kommunikation zwischen DHCP-Clients und
DHCP-Servern über verschiedene Netzwerke hinweg.

### Aufgaben und Funktion eines DHCP-Relays

1.  Weiterleiten von DHCP-Nachrichten zwischen verschiedenen Subnetzen:

    - DHCP-Clients verwenden Broadcast-Nachrichten, um mit DHCP-Servern
      zu kommunizieren (z. B. DHCPDISCOVER). Broadcasts erreichen jedoch
      nur Geräte im gleichen Subnetz. Wenn sich der DHCP-Server in einem
      anderen Subnetz befindet, würde der Client ihn nicht direkt
      erreichen.
    - Der DHCP-Relay empfängt die Broadcast-Nachricht eines DHCP-Clients
      und leitet sie über Unicast an den DHCP-Server weiter, der sich in
      einem anderen Subnetz befinden. Auf diese Weise wird das Problem
      der beschränkten Reichweite von Broadcast-Nachrichten überwunden.

2.  Rückleitung der Antworten an den Client:

    Der DHCP-Server antwortet dem DHCP-Relay auf dessen Anfrage. Der
    DHCP-Relay empfängt die Antwort (z. B. DHCPOFFER oder DHCPACK) und
    sendet sie per Broadcast oder Unicast an den entsprechenden Client
    zurück.

3.  Reduzierung der Notwendigkeit mehrerer DHCP-Server:

    Ein DHCP-Relay ermöglicht es, dass ein zentraler DHCP-Server mehrere
    Subnetze und Netzwerke bedienen kann. Ohne DHCP-Relay müsste in
    jedem Subnetz ein eigener DHCP-Server eingerichtet werden, was die
    Netzwerkverwaltung komplizierter und teurer machen würde.

4.  Integration in Router oder Layer-3-Geräte:

    Oft sind DHCP-Relays in Routern oder anderen Layer-3-Geräten
    implementiert, da diese ohnehin an der Grenze zwischen verschiedenen
    Subnetzen arbeiten und den Verkehr zwischen diesen Netzwerken
    routen.
:::

## Aufgabe 6

Welche der Informationen können mittels DHCP verteilt werden?

- IPv4-Adresse

- Subnetzmaske

- Systemzeit

- DNS-Server

- Lease-Zeit

- ARP-Tabelle des Systems

::: {.solution}
Von den aufgeführten Informationen können nicht alle mittels DHCP
verteilt werden. DHCP dient hauptsächlich der automatischen Zuweisung
von IP- und Netzwerkkonfigurationsdaten an Clients. Folgende
Informationen können mittels DHCP verteilt werden:

### Informationen, die mittels DHCP verteilt werden können

1.  IPv4-Adresse:

    Die Hauptaufgabe von DHCP ist die Zuweisung einer dynamischen
    IP-Adresse an den Client.

2.  Subnetzmaske:

    DHCP kann die Subnetzmaske an den Client verteilen, damit dieser
    weiß, welches Netzwerksegment er verwendet.

3.  DNS-Server:

    DHCP kann die IP-Adresse(n) der DNS-Server bereitstellen, damit der
    Client DNS-Abfragen (z. B. zur Namensauflösung) durchführen kann.

4.  Lease-Zeit:

    Die Lease-Zeit gibt an, wie lange der Client die zugewiesene
    IP-Adresse verwenden darf, bevor er sie entweder verlängern oder
    freigeben muss.

### Informationen, die *nicht* durch DHCP verteilt werden können

1.  Systemzeit:

    DHCP verteilt keine Informationen zur Systemzeit. Dies erfolgt in
    der Regel über Protokolle wie NTP (Network Time Protocol).

2.  ARP-Tabelle des Systems:

    Die ARP-Tabelle (Address Resolution Protocol) wird durch den Client
    selbst aufgebaut, indem er über das Netzwerk MAC-Adressen erlernt.
    DHCP hat keinen Einfluss auf die Verteilung von ARP-Tabellen.
:::

## Aufgabe 7

Ein Client hat die nachfolgend dargestellte IP-Adressenkonfiguration.

![](images/ip-konfiguration.png){width="85%"}

Beschreiben Sie, aus welchem IP-Adressbereich die abgebildete Adresse
stammt und in welcher Situation ein Client diese Adresse bekommt.

::: {.solution}
Der Adressbereich 169.254.0.0/16 gehört zu den APIPA-Adressen (Automatic
Private IP Addressing), auch bekannt als Link-Local Adressen.

### Eigenschaften des Bereichs

- Adressbereich: 169.254.0.0 bis 169.254.255.255
- Subnetzmaske: 255.255.0.0 (entspricht einem /16-Präfix)

### Verwendung

- Diese Adressen werden von einem Gerät automatisch verwendet, wenn es
  keine IP-Adresse von einem DHCP-Server erhalten kann.
- APIPA ist eine Funktion in Betriebssystemen wie Windows, die es einem
  Gerät erlaubt, sich selbst eine IP-Adresse zuzuweisen, um in lokalen
  Netzwerken (ohne Router oder DHCP) mit anderen Geräten zu
  kommunizieren.
- Diese Adressen sind nicht routbar und werden nur für die lokale
  Kommunikation innerhalb eines Netzwerks verwendet.

### Anwendungsfall

Wenn ein Computer keine DHCP-Adresse erhält, wird eine
169. 254. x. x-Adresse automatisch vergeben, damit der Computer dennoch
in einem lokalen Netzwerk (z. B. für Dateifreigaben oder Druckdienste)
kommunizieren kann.
:::

## Aufgabe 8

Grenzen Sie die Begriffe „Lease-Time", „Renewal-Time" und „Rebind-Time"
voneinander ab.

::: {.solution}
#### Lease-Time

- Die Lease-Time gibt die Gesamtdauer an, für die einem Client eine
  IP-Adresse vom DHCP-Server zugewiesen wird.

- Während dieser Zeit darf der Client die IP-Adresse verwenden.

- Nach Ablauf dieser Zeit muss der Client die Adresse entweder freigeben
  oder eine Verlängerung beantragen.

#### Renewal-Time

- Die Renewal-Time ist der Zeitpunkt, an dem der Client beginnen soll,
  beim ursprünglichen DHCP-Server eine Verlängerung seiner IP-Adresse zu
  beantragen. Dies geschieht normalerweise nach 50 % der Lease-Zeit. Der
  Client sendet eine DHCPREQUEST-Nachricht direkt an den DHCP-Server, um
  die IP-Adresse zu verlängern. Wenn der Server antwortet, wird die
  Lease-Zeit zurückgesetzt.

#### Rebind-Time

- Die Rebind-Time ist der Zeitpunkt, an dem der Client, falls keine
  Antwort vom ursprünglichen DHCP-Server kommt, versucht, die Lease von
  jedem verfügbaren DHCP-Server zu erneuern.

  Dies geschieht in der Regel nach 87,5 % der Lease-Zeit. Wenn der
  ursprüngliche DHCP-Server nicht antwortet, sendet der Client eine
  Broadcast-Anfrage, um von einem beliebigen DHCP-Server eine
  Verlängerung zu erhalten.
:::

## Aufgabe 9

Beschreiben Sie ein Anwendungsbeispiel für die automatische Zuordnung
bei DHCP.

::: {.solution}
Ein typisches Anwendungsbeispiel für die automatische Zuordnung von
IP-Adressen mittels DHCP (Dynamic Host Configuration Protocol) ist die
Zuweisung von IP-Adressen in einem Unternehmensnetzwerk:

In einem großen Unternehmen gibt es viele Mitarbeiter, die regelmäßig an
verschiedenen Arbeitsplätzen im Büro arbeiten. Die Arbeitsplätze sind
mit Laptops ausgestattet, und die Mitarbeiter bewegen sich häufig
zwischen verschiedenen Büros oder Besprechungsräumen. Das Unternehmen
hat ein Netzwerk mit einem DHCP-Server eingerichtet, um die IP-Adressen
für alle Geräte automatisch zu verwalten.
:::

## Aufgabe 10

Geben Sie mindestens fünf (typische) Parameter an, die mit DHCP
konfiguriert werden können.

::: {.solution}
- IPv4-Adresse des Clients
- Subnetzmaske
- Gateway-Adresse
- DNS-Servers-Adresse
- NTP-Server-Adresse
- SMTP-Server
- POP3-Server

(Siehe Seite 12 unten)
:::

## Aufgabe 11

Erläutern Sie die DHCP-Adressvergabeverfahren manuelle, automatische und
dynamische Zuordnung.

::: {.solution}
Siehe S. 12

Die DHCP-Adressvergabe kann auf verschiedene Weisen erfolgen, je nach
den Anforderungen des Netzwerks und der zugewiesenen IP-Adressen. Die
drei Hauptverfahren sind manuelle, automatische und dynamische
Zuordnung. Hier sind die Unterschiede und Erläuterungen zu jedem
Verfahren:

#### Manuelle Zuordnung (statische Zuordnung)

- Bei der manuellen Zuordnung wird einer bestimmten MAC-Adresse eine
  feste IP-Adresse zugewiesen, die immer für diesen speziellen Client
  reserviert ist.

- Dies wird häufig für Server, Drucker oder Netzwerkgeräte verwendet,
  die eine konstante IP-Adresse benötigen, um ordnungsgemäß zu
  funktionieren. Administratoren konfigurieren den DHCP-Server so, dass
  er für bestimmte Geräte feste IP-Adressen vergibt, basierend auf deren
  MAC-Adressen.

- Vorteile:

  - Einfachheit und Vorhersehbarkeit, da die IP-Adresse nicht ändert.
  - Nützlich für Geräte, die immer erreichbar sein müssen.

- Nachteile:

  - Erhöhter Verwaltungsaufwand, da jede IP-Adresse manuell konfiguriert
    werden muss.
  - Mangelnde Flexibilität, wenn sich die Netzwerkinfrastruktur ändert
    oder Geräte hinzugefügt oder entfernt werden.

#### Automatische Zuordnung

- Bei der automatischen Zuordnung wird eine IP-Adresse dauerhaft einem
  Gerät zugewiesen, jedoch ohne dass der Administrator jede Zuordnung
  manuell einrichten muss. Der DHCP-Server merkt sich, welche IP-Adresse
  dem Client zugewiesen wurde, und vergibt sie jedes Mal, wenn dieser
  sich anmeldet.

- Ideal für Geräte, die immer die gleiche IP-Adresse benötigen, aber
  nicht ständig manuell konfiguriert werden sollen, wie z. B. Laptops
  oder mobile Geräte.

- Vorteile:

  - Reduziert den Verwaltungsaufwand im Vergleich zur manuellen
    Zuordnung.
  - Bietet eine gewisse Flexibilität, da der DHCP-Server die Zuweisungen
    verwaltet.

- Nachteile:

  - Wenn ein Gerät dauerhaft nicht mehr im Netzwerk ist, bleibt die
    IP-Adresse reserviert, was möglicherweise zu einem Mangel an
    verfügbaren IP-Adressen führen kann.

#### Dynamische Zuordnung

- Die dynamische Zuordnung ist der gebräuchlichste Ansatz bei DHCP.
  Hierbei vergibt der DHCP-Server IP-Adressen aus einem Adresspool für
  eine bestimmte Lease-Zeit. Nach Ablauf dieser Zeit kann die IP-Adresse
  entweder verlängert oder an einen anderen Client vergeben werden.

- Verwendung:

  - Dies wird in Umgebungen verwendet, in denen Clients häufig wechseln
    oder sich verbinden und trennen, wie z. B. in Büros oder
    öffentlichen WLANs.

- Vorteile:

  - Effiziente Nutzung der IP-Adressressourcen, da Adressen nach
    Gebrauch wieder freigegeben werden.
  - Erfordert keine manuelle Konfiguration, was die Verwaltung
    vereinfacht.

- Nachteile:

  - Clients können eine andere IP-Adresse erhalten, wenn sie sich erneut
    verbinden, was bei bestimmten Anwendungen (z. B. Fernzugriff oder
    Serverdienste) problematisch sein kann.
:::

## Aufgabe 12

Beschreiben Sie Maßnahmen, um die Ausfallsicherheit von DHCP zu erhöhen.

::: {.solution}
#### DHCP-Redundanz

- DHCP-Server-Redundanz:

  - mehrere DHCP-Server in einem Netzwerk:

  Diese Server können entweder als Master-Slave-Konfiguration oder in
  einem Load-Balancing-Modell arbeiten, um sicherzustellen, dass ein
  Server die Aufgaben eines anderen übernehmen kann, falls einer
  ausfällt.

- Failover-Konfiguration:

  Wenn einer der Server ausfällt, übernimmt der andere die Aufgabe und
  stellt sicher, dass die IP-Zuweisung weiterhin funktioniert.

#### Regelmäßige Sicherung und Wiederherstellung

- Backups des DHCP-Datenbank:

  im Falle eines Serverausfalls können die Konfiguration und die
  zugewiesenen IP-Adressen schnell wiederhergestellt werden können.

- Dokumentation:

  eine Dokumentation der DHCP-Konfiguration, IP-Adresspools und
  Zuweisungen erleichtern die Wiederherstellung im Notfall.

#### Monitoring und Alarmierung

- Überwachung der DHCP-Server:

  Monitoring-Tools überwachen den Status und die Leistung der
  DHCP-Server in Echtzeit. Dies ermöglicht es, Probleme frühzeitig zu
  erkennen und zu beheben, bevor sie zu Ausfällen führen.

- Alarmierungssysteme:

  die werden Administratoren benachrichtigen, wenn ein DHCP-Server nicht
  mehr verfügbar ist oder ungewöhnliche Aktivitäten festgestellt werden.

#### Sicherheitsmaßnahmen

- DHCP-Snooping:

  DHCP-Snooping auf Switches aktivieren, um sicherzustellen, dass nur
  autorisierte DHCP-Server im Netzwerk Anfragen beantworten können. Dies
  schützt vor möglichen Angriffen, die die DHCP-Dienste stören könnten.

#### Optimierung der Lease-Zeit

- Angemessene Lease-Zeiten:

  Zu kurze Lease-Zeiten können zu unnötigem Datenverkehr führen, während
  zu lange Lease-Zeiten die IP-Adressnutzung ineffizient machen können.

#### Lastverteilung

- Lastenausgleich:

  Lastverteilungstechniken stellen sicher, dass die Last zwischen
  mehreren DHCP-Servern gleichmäßig verteilt wird. Dies kann die
  Leistung verbessern und das Risiko eines Serverausfalls verringern.

Siehe auch Buch S. 13--14
:::

## Aufgabe 13

Geben Sie an, was SLAAC bedeutet und erklären Sie, wie es funktioniert.

::: {.solution}
Stateless Address Auto Configuration (SLAAC) ist ein Mechanismus, mit
dessen Hilfe sich ein Netzwerkknoten eine eigene IPv6-Adresse selbst
zuweist.

Im ersten Schritt weist der Netzwerkknoten sich eine Link-Local-Adresse
zu, mit der er nur im lokalen Netzwerk kommunizieren kann. Dadurch kann
er aber andere Knoten erreichen und sendet ein Router-Solicitation (RS),
um von einem Router ein Router-Advertisement (RA) zu empfangen. Mit dem
Router-Advertisement erhält er das Präfix für eine globale
Unicast-Adresse, mit dessen Hilfe sich eine eindeutige globale Adresse
bildet. Die Nachricht Router-Advertisement beinhaltet auch die
Gateway-Adresse.

(Vgl. grünes Buch S. 14)
:::
