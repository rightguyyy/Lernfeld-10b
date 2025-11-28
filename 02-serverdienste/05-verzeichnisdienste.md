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

## Aufgabe 2

Beschreiben Sie die Aufgabe von Gruppenrichtlininen im AD.

## Aufgabe 3

a)  In einem Verzeichnisdienst sind die Daten in einer hierarchischen
    Struktur angeordnet und nicht in Tabellen, wie es von relationalen
    Datenbanken bekannt ist.

    Beschreiben Sie den Vorteil einer hierarchischen Anordnung von
    Daten. Geben Sie die Grundvoraussetzung an, die für einen sinnvollen
    Einsatz in dieser Form gegeben sein muss.

<!-- -->

b)  Die Daten eines Verzeichnisdienstes werden als Directory Information
    Base bezeichnet. Die Knoten in dem Verzeichnisbaum sind sogenannte
    Object Entries, die Attribute enthalten. Nennen Sie drei typische
    Attributtypen, die in einem Verzeichnisdienst verwendet werden.

<!-- -->

c)  Das Active Directory ist die Umsetzung eines Verzeichnisdienstes von
    Microsoft, der mit dem Windows-Server-Betriebssystem zur Verfugung
    gestellt wird. Über den Verzeichnisdienst können Gruppennchtlinien
    verteilt werden.

    Beschreiben Sie Aspekte, die mit Gruppenrichtlinien umsetzbar sind.
    Geben Sie Einsatzgebiete für Gruppenrichtlinien und die Art der
    Verknüpfung mit Gruppenrichtlinienobjekten (GPO) an.

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

<!-- -->

e)  Im Active Directory wurde eine GPO erstellt und eine
    Gruppenrichtlinie konfiguriert. Die GPO wurde einer OU zugeordnet
    und darin ist ein Computer enthalten. Wenn Sie den Computer starten,
    sehen Sie aber nicht die Einstellung der Gruppenrichtlinie im
    Computer.

    Beschreiben Sie eine Vorgehensweise, um den Fehler zu finden.
