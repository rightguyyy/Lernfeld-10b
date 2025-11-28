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

::: {.solution}
- Die vollständige Domain wird FQDN (Fully Qualifired Domain Name)
  genannt, dies ist hier `h394.dc23.eu.mycloud.eu`.

- Die TLD (Top-Level-Domain) ist das letzte Label, d. h. hier `eu`.

- Als Subdomain werden sind meist Label ab der 3. Ebene oder darunter
  bezeichnet. Hier ist `eu.mycloud.eu` eine Subdomain von `mycloud.eu`,
  `dc23.eu.mycloud.eu` ist eine Subdomain von `eu.mycloud.eu` und
  `h394.dc23.eu.mycloud.eu` ist eine Subdomain von `dc23.eu.mycloud.eu`.

Vgl. Buch S. 15.
:::

## Aufgabe 2

Erklären, sie was ein DNS-Root-Server und dessen Aufgabe ist.

::: {.solution}
Die 13 Root-Server kennen ausschließlich die Namen und die IP-Adressen
der DNS-Server der TLDs und verwalten auch ausschließlich diese
Informationen. Hat zur Auflösung einer Domain ein DNS-Server diese
Information nicht zur Verfügung, dann ist der erste Schritt, diese
Information bei einen Root-Server abzufragen.

Vgl. Buch S. 16.
:::

## Aufgabe 3

Unterscheiden Sie die Begriffe Forward- und Reverse-Lookup.

::: {.solution}
Forward-Lookup: Zu einem Domänennamen wird die IP-Adresse abgefragt.

Reverse-Lookup: Zu einer IP-Adresse wird der Domänenname abgefragt.

Siehe Buch Seite 17.
:::

## Aufgabe 4

Erläutern Sie, inwiefern eine Fritzbox als DNS-Forwarder arbeitet und
inwiefern Sie als authoritativer Server arbeitet.

::: {.solution}
Eine Fritzbox arbeitet im Heimnetzwerk hauptsächlich als DNS-Forwarder.
Das bedeutet, dass sie DNS-Anfragen von Geräten im Netzwerk
entgegennimmt und an einen externen DNS-Server weiterleitet, den sie vom
Internetprovider zugewiesen bekommt oder den der Nutzer manuell
konfiguriert hat. Der DNS-Forwarder speichert die Ergebnisse temporär
(Caching), um bei wiederholten Anfragen schneller zu antworten.

Als authoritativer DNS-Server hingegen arbeitet die Fritzbox in einem
Heimnetzwerk nur begrenzt. Sie kann DNS-Namen für lokale Geräte im
Heimnetz auflösen, die entweder manuell in der Benutzeroberfläche
eingetragen wurden oder über DHCP automatisch vergeben werden. Für das
Internet spielt sie jedoch keine Rolle als autoritativer Server, da sie
keine DNS-Zonen für externe Domains verwaltet und keine offiziellen
DNS-Dienste anbietet.
:::

## Aufgabe 5

Beschreiben Sie, was Cache-Poisoning ist und wie es mit DNSSEC
verhindert werden kann.

::: {.solution}
Wenn eine Resolver einen autoritativen DNS-Server nach einer Information
fragt (z. B. ein A-Record), geschieht dies i. d. R. per UDP. Ein
Angreifer kann daher dem Resolver eine gefälschte Antwort mit der
IP-Adresse des autoritativen DNS-Servers zu senden. Der Resolver
speichert dann diese falsche Information in seinen Cache. Bis zum Ablauf
der TTL werden alle Anfragen durch Clients, die diese gefälschte
Information des Resolvers verwenden, für diese Domäne an eine gefälschte
IP-Adresse gerichtet, z. B. an einen für diesen Angriff vorbereiteten
Dienst des Angreifers.

Vgl. Buch S. 18--19.
:::

## Aufgabe 6

Erklären Sie, wozu »DNS over TLS« eingeführt wurde und wie es
funktioniert.

::: {.solution}
Die Verbindung vom Client zum Recursive Resolver erfolgt per TLS, um
Vertraulichkeit und Integrität sicherzustellen. Dazu wird das
Verschlüsselungsprotokoll Transport Layer Security (TLS) eingesetzt.

Vgl. Buch S. 19--20.
:::

## Aufgabe 7

Sie sollen die Funktionsweise des DNS-Protokolls genauer betrachten.
Ohne eine funktionierende Namensauflösung sind viele Anwendungen nicht
nutzbar.

a)  Beschreiben Sie, was mit einem DNS-Forward-Lookup erreicht wird und
    geben Sie den Ablauf an.

    ::: {.solution}
    Ein DNS-Forward-Lookup dient dazu, einen Domainnamen (z. B.
    "example.com") in eine IP-Adresse (z. B. "93.184.216.34")
    aufzulösen, damit Computer die Adresse verstehen und eine Verbindung
    herstellen können.

    Ablauf eines DNS-Forward-Lookups:

    1.  Anfrage vom Client: Ein Gerät (Client) fragt einen DNS-Resolver
        nach der IP-Adresse für eine bestimmte Domain.

    2.  Überprüfung des Cache: Der DNS-Resolver (z. B. die Fritzbox oder
        ein DNS-Server) prüft, ob die gesuchte Information im Cache
        vorhanden ist. Falls ja, wird die Antwort direkt zurückgegeben.

    3.  Weiterleitung der Anfrage: Ist die IP-Adresse nicht im Cache,
        leitet der Resolver die Anfrage an den nächsten zuständigen
        DNS-Server weiter, in der Regel den des Internetanbieters.

    4.  Iterative Auflösung: Der DNS-Server kontaktiert gegebenenfalls
        andere DNS-Server, beginnend bei den Root-Servern, über die
        Top-Level-Domain (TLD)-Server, bis der autoritative Server der
        Domain erreicht wird, der die korrekte IP-Adresse zurückliefert.

    5.  Antwort an den Client: Die gefundene IP-Adresse wird zum
        Resolver zurückgesendet, der sie an den anfragenden Client
        weitergibt.

    6.  Caching der Antwort: Der Resolver speichert die Antwort im
        Cache, um bei zukünftigen Anfragen schneller reagieren zu
        können.
    :::

<!-- -->

b)  Entscheiden Sie, ob die folgenden Aussagen zum DNS richtig oder
    falsch sind.

    a)  Die Datei „hosts" wurde historisch für die Namensauflösung
        verwendet und kommt heute nicht mehr zum Einsatz.

        ::: {.solution}
        Falsch. Die „hosts"-Datei wird nach wie vor verwendet, obwohl
        sie heute in modernen Netzwerken seltener zum Einsatz kommt. Sie
        kann aber weiterhin für die manuelle Namensauflösung genutzt
        werden, bevor DNS-Abfragen gemacht werden.
        :::

    <!-- -->

    b)  Eine Zone legt fest, für welchen Bereich in der DNS-Hierarchie
        ein Server autoritativ ist.

        ::: {.solution}
        Richtig. Eine DNS-Zone definiert den Verantwortungsbereich eines
        autoritativen DNS-Servers innerhalb der DNS-Hierarchie, z. B.
        für eine bestimmte Domain oder Subdomain.
        :::

    <!-- -->

    c)  Die DNS-Root-Server sind in der Hierarchie die obersten Server
        und werden von Resolvern als erstes angefragt. Sie kennen jedoch
        nur die IP-Adressen von DNS-Servern der Top-Level-Domänen.

        ::: {.solution}
        Teilweise richtig. Die DNS-Root-Server sind die höchsten in der
        DNS-Hierarchie. Sie verweisen jedoch nur auf die zuständigen
        DNS-Server der Top-Level-Domains (z. B. .com, org). Zu kennen
        dazu aber nicht nur die IP-Adressen sondern auch die Namen der
        DNS-Server der Top-Level-Domänen.
        :::

    <!-- -->

    d)  Aus Sicherheitsgründen gibt es die 13 DNS-Root-Server mehrfach.
        Über IP-Multicast wird der geografisch am nächsten gelegene
        Server ausgewählt.

        ::: {.solution}
        Falsch. Es gibt tatsächlich 13 Root-Server-Namen, aber jede
        dieser Instanzen verwendet Anycast-Technologie, nicht
        IP-Multicast, um weltweit verteilt auf viele physische Server
        zuzugreifen, sodass Anfragen an den nächstgelegenen Server
        geroutet werden.
        :::

    <!-- -->

    e)  Root-Hint ist eine Textdatei, die von der IANA-Webseite
        heruntergeladen werden kann. Sie enthält die 13 IPv4- und
        IPv6-Adressen der DNS-Root-Server. Sofern kein Forwarder
        eingetragen ist, benötigt jeder Resolver diese Datei, um eine
        Abfrage in der DNS Hierarchie starten zu können.

        ::: {.solution}
        Richtig. Die Root-Hint-Datei enthält die IP-Adressen der
        Root-Server und wird benötigt, wenn kein DNS-Forwarder
        konfiguriert ist, damit der Resolver die DNS-Hierarchie
        durchlaufen kann.
        :::

    <!-- -->

    f)  DNS over TLS (DoT) und DNS over HTTPS (DoH) zielen darauf ab,
        die Verbindung vom DNS-Client zum DNS-Resolver abzusichern.

        ::: {.solution}
        Richtig. Beide Technologien verschlüsseln die Kommunikation
        zwischen DNS-Client und DNS-Resolver, um Abfragen vor Abhören
        oder Manipulation zu schützen.
        :::

    <!-- -->

    g)  DNSSEC zielt darauf ab, die Abfrage eines DNS-Clients zum
        DNS-Resolver abzusichern.

        ::: {.solution}
        Falsch. DNSSEC (DNS Security Extensions) sichert die
        Authentizität der Daten, die ein Resolver von einem
        autoritativen Server erhält, ab und schützt vor Manipulationen
        durch DNS-Spoofing. Es verschlüsselt jedoch nicht die Verbindung
        selbst.
        :::

<!-- -->

c)  Erklären Sie den Unterschied zwischen einem Fully Qualified Domain.
    Name (FQDN) und einem Uniform Resource Locator (URL).

    ::: {.solution}
    Ein Fully Qualified Domain Name (FQDN) ist ein Bestandteil einer URL
    (Uniform Resource Locators):

    - FQDN:
      - Ein FQDN ist ein vollständiger Domainname.
      - Er besteht meist aus mehrern Labels: einer oder mehrere
        Subdomain(s), dem Domainnamen und der Top-Level-Domain (z. B.
        `www.example.com`).
      - Der FQDN beschreibt nur den Domainnamen und keine weiteren
        Details wie Pfade oder Protokolle.
    - URL:
      - Eine URL ist eine vollständige Webadresse, die den Zugriff auf
        eine Ressource beschreibt.
      - Sie enthält das Protokoll (z. B. `https://`), den FQDN, einen
        Pfad zur Ressource und eventuell zusätzliche Parameter (z. B.
        `https://www.example.com/index.html?query=test`).
    :::

<!-- -->

d)  Eine Angriffsart auf das DNS-System ist ein sogenanntes
    „DNS-Cache-Poisoning". Beschreiben Sie den Ablauf dieses Angriffs
    und erläutern Sie eine Möglichkeit, sich davor zu schützen.

    ::: {.solution}
    DNS-Cache-Poisoning (oder DNS-Spoofing) ist ein Angriff, bei dem
    manipulierte DNS-Einträge in den Cache eines DNS-Resolvers
    eingeschleust werden, sodass Benutzer auf falsche, oft bösartige
    Webseiten umgeleitet werden. Der Angreifer verändert die Zuordnung
    von Domainnamen zu IP-Adressen, ohne dass der Benutzer dies merkt.

    - Ablauf des DNS-Cache-Poisoning:

      1.  Anfrage an den DNS-Resolver: Ein Benutzer fragt einen Resolver
          nach der IP-Adresse einer Domain, die dieser nicht in seinem
          Cache gespeichert hat.
      2.  Manipulation der DNS-Antwort: Der Angreifer sendet eine
          gefälschte DNS-Antwort an den Resolver, bevor die echte
          Antwort eintrifft. Diese gefälschte Antwort enthält falsche
          IP-Adressen.
      3.  Speicherung der falschen Einträge im Cache: Der DNS-Resolver
          speichert die falschen Informationen im Cache und verwendet
          sie, bis sie ablaufen (TTL), wodurch alle zukünftigen Anfragen
          zu dieser Domain an die manipulierte IP-Adresse weitergeleitet
          werden.

    - Schutzmaßnahme:

      Eine gängige Schutzmaßnahme ist die Implementierung von DNSSEC
      (Domain Name System Security Extensions). DNSSEC stellt sicher,
      dass die vom DNS-Resolver erhaltenen DNS-Antworten kryptografisch
      signiert sind. Dadurch kann der Resolver die Authentizität der
      DNS-Antwort überprüfen und verhindern, dass gefälschte Einträge
      akzeptiert werden.
    :::
