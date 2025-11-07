---
date: Schuljahr 2025/2026
lang: de-DE
subtitle: Lernfeld 10b -- Serverdienste bereitstellen und
  Administrationsaufgaben automatisieren
title: Infrastruktur testen
---

Grundlage: Abschnitt 4.7, S. 415--419

## Aufgabe 1

Beschreiben Sie, wie Sie Netzwerkkabel auf Ihre Funktion prüfen können.

::: {.solution}
Zunächst führt, falls möglich, man eine visuelle Inspektion auf
Beschädigungen durch. Um Netzwerkkabel auf Funktion zu prüfen, kann man
ein Netzwerkkabeltester-Gerät verwenden, um die Verbindung und
Signalintegrität zu testen.
:::

## Aufgabe 2

Recherchieren Sie den Einsatzzweck von Crosskabeln.

::: {.solution}
Crosskabel werden verwendet, um gleichartige Geräte direkt miteinander
zu verbinden, z. B. Computer mit Computer oder Switch mit Switch, ohne
dazwischen einen Router oder Switch zu benötigen. Bei moderne
Netzwerk-Hardware wird ein Crosskabel allerdings nicht mehr benötigt, da
die Hardware diese Funktion ggf. übernimmt.
:::

## Aufgabe 3

Beschreiben Sie eine Möglichkeit, wie Sie die NetzwerkKonfiguration
eines Server überprüfen.

::: {.solution}
Die Netzwerkkonfiguration eines Servers kann mit dem Befehl `ifconfig`
oder `ip addr` (Linux) oder \`ipconfig /all (Windows) in der
Befehlszeile überprüft werden, um Informationen über die
Netzwerkschnittstellen anzuzeigen.
:::

## Aufgabe 4

Nennen Sie ein Shell-Kommando inklusive Beispiel, mit dem Sie die
Funktion des DHCP-Servers überprüfen.

::: {.solution}
### Windows

    ipconfig /release → aktuelle IP-Adresse
    ipconfig /renew → Fehlermeldung, wenn es nicht geht

### Shell-Kommandos zur Überprüfung des DHCP-Servers:

``` shell
sudo dhclient -v
```

``` shell
dhcping -s [IP-Adresse des DHCP-Servers]
```

#### Beispiel

``` shell
sudo dhcping -s 10.3.19.254
```

### Eingehendere Tests

``` shell
sudo nmap --script broadcast-dhcp-discover -e enp0s31f6
```

``` shell
sudo nmap -sU -p 67 --script dhcp-discover 192.168.1.1
```

``` shell
sudo dhcpcd -T enp0s31f6
```

``` shell
sudo nmap -6 --script broadcast-dhcp6-discover -e enp0s31f6
```
:::

## Aufgabe 5

Nennen Sie ein Shell-Kommando inklusive Beispiel, mit dem Sie die
Funktion des DNS-Servers überprüfen.

::: {.solution}
Shell-Kommandos zur Überprüfung des DNS-Servers:

    nslookup [Domainname] [DNS-Server-IP]

oder

``` shell
dig [RR] [Name] [@Server]
```
:::

## Aufgabe 6

Nennen Sie ein Shell-Kommando, mit dem Sie die Netzwerkkomponenten
innerhalb des Subnetzes auflisten können.

::: {.solution}
Shell-Kommando zum Auflisten der Netzwerkkomponenten im Subnetz:

    nmap -sn [Subnetz-IP]
:::
