---
css: ../css/style.css
date: Schuljahr 2025/2026
lang: de-DE
subtitle: Lernfeld 10b -- Serverdienste bereitstellen und
  Administrationsaufgaben automatisieren
title: Serverdienste -- Verzeichnisdienste
---

## Aufgabe 1

Benennen Sie die Attributstypen in Verzeichnisdiensten.

::: {.solution}
- cn -- common name
- sn -- surname
- ou -- organizational unit
- st -- state
- c -- country
- mail -- E-Mail-Adresse
:::

## Aufgabe 2

Beschreiben Sie die Aufgabe von Gruppenrichtlininen im AD.

::: {.solution}
»Gruppenrichtlinien sind Sammlungen von Benutzer- und
Computerkonfigurationseinstellungen, die mit Computern, Standorten,
Domänen oder Organisationseinheiten verknüpft werden, um das Verhalten
des Benutzerdesktops zu steuern. Darüber hinaus werden in ihnen Aspekte
wie Sicherheitseinstellungen, An- und Abmeldeskripte, Skripte für den
Start und das Herunterfahren eines Computers definiert oder
beispielsweise Ordnerumleitungen festgelegt. Mit Gruppenrichtlinien kann
das Verhalten des Betriebssystems bestimmt und dessen Optionen
eingeschränkt werden. Es gibt aber auch Gruppenrichtlinien, mit denen
das Verhalten und die Optionen von Anwendungen, z. B. Microsoft Office
oder dem Webbrowser, von zentraler Stelle aus gesteuert werden können.«

Vgl. Buch S. 24
:::

## Aufgabe 3

a)  In einem Verzeichnisdienst sind die Daten in einer hierarchischen
    Struktur angeordnet und nicht in Tabellen, wie es von relationalen
    Datenbanken bekannt ist.

    Beschreiben Sie den Vorteil einer hierarchischen Anordnung von
    Daten. Geben Sie die Grundvoraussetzung an, die für einen sinnvollen
    Einsatz in dieser Form gegeben sein muss.

    ::: {.solution}
    Dadurch kann die Unternehmensstruktur im Verzeichnisdienst
    abgebildet im werden. Das setzt voraus, dass auch im Unternehmen
    eine solche Struktur vorliegt und sich nur relativ selten verändert.

    »Wenn mehrere OUs ineinander verschachtelt sind, so wirkt die
    Gruppenrichtlinie einer OU nicht nur auf dessen Computer- oder
    Benutzerobjekte, sondern über die Vererbung auch auf Objekte, die in
    untergeordneten OUs liegen. Gibt es beispielsweise eine OU „Standort
    frankfurt" mit den Sub-OU „Vertrieb frankfurt", „Produktion
    frankfurt" und „einkauf frankfurt" und sind für die OU „Standort
    frankfurt" Gruppenrichtlinien definiert, so wirken diese auf alle
    Objekte in tiefer gelegenen OUs.«

    geographische Struktur und Aufteilung des Unternehmens kann
    abgebildet werden.
    :::

<!-- -->

b)  Die Daten eines Verzeichnisdienstes werden als Directory Information
    Base bezeichnet. Die Knoten in dem Verzeichnisbaum sind sogenannte
    Object Entries, die Attribute enthalten. Nennen Sie drei typische
    Attributtypen, die in einem Verzeichnisdienst verwendet werden.

    ::: {.solution}
    - cn -- common name
    - sn -- surname
    - ou -- organizational unit
    - st -- state
    - c -- country
    - mail -- E-Mail-Adresse
    :::

<!-- -->

c)  Das Active Directory ist die Umsetzung eines Verzeichnisdienstes von
    Microsoft, der mit dem Windows-Server-Betriebssystem zur Verfugung
    gestellt wird. Über den Verzeichnisdienst können Gruppennchtlinien
    verteilt werden.

    Beschreiben Sie Aspekte, die mit Gruppenrichtlinien umsetzbar sind.
    Geben Sie Einsatzgebiete für Gruppenrichtlinien und die Art der
    Verknüpfung mit Gruppenrichtlinienobjekten (GPO) an.

    ::: {.solution}
    Gruppenrichtlinien sind Sammlungen von Benutzer- und
    Computerkonfigurationsein­ stellungen \[...\], um das Verhalten des
    Benutzerdesktops zu steuern. Darüber hinaus werden in ihnen Aspekte
    wie Sicherheitseinstellungen, An- und Abmeldeskripte, Skripte für
    den Start und das Herunterfahren eines Computers definiert oder
    beispielsweise Ordnerumleitungen festgelegt. Mit Gruppenrichtlinien
    kann das Verhalten des Betriebssystems bestimmt und dessen Optionen
    eingeschränkt werden. Es gibt aber auch Gruppenrichtlinien, mit
    denen das Verhalten und die Optionen von Anwendungen, z. B.
    Microsoft Office oder dem Webbrowser, von zentraler Stelle aus
    gesteuert werden können.

    - Passwortvorgaben
    - Netzwerkzugriffe, Zugriff auf Dateien und Server, Ordnerfreigaben
    - Benutzeroberflächen, Hintergründe, Apps
    - Softwareverwaltung, Installation, Updates
    :::

<!-- -->

d)  Eine Gruppenrichtlinie hat als Funktion: Letzten Benutzernamen nicht
    anzeigen. Durch diese Funktion wird nach dem Start des Computers
    kein Benutzername angezeigt, der sich zuvor angemeldet hatte.
    Dadurch müssen die Benutzer ihren Benutzernamen für die Anmeldung
    selber eingeben. Folgende OU-Struktur besteht:

        + OU-Standaort-Wolkenlos
              |
              + OU-Clients
                    |
                    + OU-Notebooks

    - Dem OU-Standort-Wolkenlos ist ein GPO zugeordnet, in der die
      Gruppenrichtlinie *deaktiviert* ist.

    - Den OU-Clients ist eine GPO zugeordnet, in der die
      Gruppenrichtlinie *nicht konfiguriert* ist.

    - Den OU-Notebooks ist ein GPO zugeordnet, in der die
      Gruppenrichtlinie *aktiviert* ist.

    Beschreiben Sie, ob bei Computern, die der OU „Clients" bzw. der OU
    „Notebooks" zugeordnet sind, bei der Anmeldung der Benutzername
    selbst eingegeben werden muss oder per Mausklick ausgewählt werden
    kann.

    ::: {.solution}
    Die OU-Clients erben die Einstellung von OU-Standort-Wolkenlos, wo
    die Richtlinie deaktiviert ist, daher wird dort der Benutzername
    angezeigt und kann mit der Maus ausgewählt werden.

    Da bei den Notebooks die Gruppenrichtlinie aktiviert ist, wird die
    Einstellung von OU-Standort-Wolkenlos überschrieben. Damit muss dort
    der Benutzername eingegeben werden.
    :::

<!-- -->

e)  Im Active Directory wurde eine GPO erstellt und eine
    Gruppenrichtlinie konfiguriert. Die GPO wurde einer OU zugeordnet
    und darin ist ein Computer enthalten. Wenn Sie den Computer starten,
    sehen Sie aber nicht die Einstellung der Gruppenrichtlinie im
    Computer.

    Beschreiben Sie eine Vorgehensweise, um den Fehler zu finden.

    ::: {.solution}
    »Folgende Ansatzpunkte können bei der Fehlersuche helfen:

    - Verbindung von Client-Server überprüfen: Bei einem Ping-Test ist
      eine aktive Firewall zu beachten, die den Ping unterbinden kann.
    - Funktionierende Namensauflösung vom Client mithilfe von „nslookup"
      überprüfen.
    - Im Active Directory überprüfen, ob das Computer- oder
      Benutzerobjekt in der richtigen OU mit der angehefteten
      Gruppenrichtlinie liegt.
    - In der Ereignisanzeige des Clients nach entsprechenden
      Fehlermeldungen suchen.
    - In der Ereignisanzeige des Servers nach entsprechende
      Fehlermeldungen suchen.
    - Mithilfe des Kommandozeilentools „gpresult" überprüfen, welche
      Gruppenrichtlinien wirken.« (Vgl. Buch S. 25)
    :::
