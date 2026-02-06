---
css: ../css/style.css
date: Schuljahr 2025/2026
lang: de-DE
subtitle: Lernfeld 10b -- Serverdienste bereitstellen und
  Administrationsaufgaben automatisieren
title: Serverdienste -- Webserver
---

## Aufgabe 1

Erläutern Sie die Aufgabe eines Websersers.

Ein Webserver stellt Webseiten und andere Ressourcen über HTTP bzw. HTTPS bereit. Er nimmt Anfragen von Clients (Browsern) entgegen, verarbeitet diese und liefert die angeforderten Inhalte wie HTML, Bilder oder Skripte zurück.

## Aufgabe 2

Nennen Sie vier bekannte Webserver.

Apache HTTP Server  
Nginx  
Microsoft IIS  
Lighttpd

## Aufgabe 3

Vervollständigen Sie die Tabelle zu HTTP-Status-Codes

| Nummer | Status | Bedeutung |
|----|----|----|
| 200 | OK | Die Anfrage war erfolgreich und das Ergebnis wird übermittelt |
| 301 | Moved Permanently | Ressource wurde dauerhaft auf eine neue URL verschoben |
| 403 | Forbidden | Zugriff auf die Ressource ist nicht erlaubt |
| 404 | Not Found | Angeforderte Ressource wurde nicht gefunden |

## Aufgabe 4

Erklären Sie, wozu im Zusammenhang mit HTTPS eine PKI mit Zertifikaten
benötigt wird und wie eine PKI funktioniert.

Eine PKI (Public Key Infrastructure) stellt digitale Zertifikate bereit, mit denen sich Server eindeutig identifizieren können. Der Client prüft das Zertifikat, um sicherzustellen, dass er mit dem echten Server kommuniziert. Zertifizierungsstellen (CA) signieren Zertifikate. Der Browser vertraut diesen CAs und überprüft die Signatur. So werden Authentizität, Integrität und Verschlüsselung ermöglicht.

## Aufgabe 5

a)  Nach der Entscheidung für einen Webserver soll überlegt werden, ob
    der Einsatz von HTTPS sinnvoll ist. Beurteilen Sie, ob bei einem nur
    intern verwendeten Webserver der Einsatz des HTTPS-Protolkolls
    sinnvoll ist.

Ja, auch intern ist HTTPS sinnvoll. Daten können im internen Netz mitgelesen oder manipuliert werden. HTTPS schützt durch Verschlüsselung und stellt zusätzlich die Identität des Servers sicher.

<!-- -->

b)  Vergleichen Sie die beiden Protokolle HTTP und HTTPS, indem Sie die
    Aussagen den Protokollen zuordnen.

    | Aussage                                             | HTTP | HTTPS |
    |-----------------------------------------------------|------|-------|
    | transportiert die Daten einer Webseite              |  X   |   X   |
    | kann die Authentizität einer Webseite sicherstellen |      |   X   |
    | verbraucht weniger Ressourcen                       |  X   |       |
    | kann Datenverkehr verschlüsseln                     |      |   X   |
    | verwendet Zertifikate                               |      |   X   |

<!-- -->

c)  Sie sollen die HTTPS-Technik in Verbindung mit TLS bei einem Meeting
    erläutern.

Client baut TCP-Verbindung zum Server auf.  
Client sendet ClientHello mit unterstützten Verfahren.  
Server antwortet mit ServerHello und sendet Zertifikat.  
Client prüft Zertifikat und Serveridentität.  
Schlüsselaustausch zur Erzeugung eines gemeinsamen Sitzungsschlüssels.  
Danach erfolgt die verschlüsselte Datenübertragung über HTTPS.

<!-- -->

d)  Der interne Webserver soll Zertifikate verwenden. Entscheiden Sie,
    welche Einsatzszenarien durch die Verwendung eines Zertifikats
    umgesetzt werden können.

1. Ja  
2. Nein  
3. Ja  
4. Nein  

<!-- -->

e)  Ein Mitarbeiter möchte wissen, wie ein Zertifikat funktioniert.

Der öffentliche Schlüssel dient dazu, Daten zu verschlüsseln oder digitale Signaturen zu prüfen. Nur der Server mit dem passenden privaten Schlüssel kann die Daten entschlüsseln.  
Der Fingerabdruck (Hashwert des Zertifikats) dient zur eindeutigen Identifikation des Zertifikats. Damit kann überprüft werden, ob das Zertifikat unverändert und echt ist.

<!-- -->

f)  Bei der Kommunikation zwischen Server und Client werden sowohl die
    symmetrische als auch die asymmetrische Verschlüsselung eingesetzt.

    | Verschlüsselungsart | Funktionsweise | Vorteile | Nachteﬂe |
    |----|----|----|----|
    | symmetrische Verschlüsselung | ein Schlüssel zur Ver- und Entschlüsselung | schnell, geringe Rechenlast | aufwendiger Schlüsselaustausch |
    | asymmetrische Verschlüsselung | Schlüsselpaar aus öffentlichem und privatem Schlüssel | einfacher Schlüsselaustausch, Identitätsprüfung möglich | langsamer, höhere Rechenlast |

<!-- -->

g)  Ein wichtiger Ablauf bei der Arbeit mit Zertifikaten ist die
    digitale Signatur. Beschreiben Sie den Ablauf der digitalen
    Signatur, indem Sie die Abschnitte in der Grafik erläutern.

Vom Dokument wird ein Hashwert gebildet.  
Der Hash wird mit dem privaten Schlüssel des Absenders verschlüsselt (Signatur).  
Empfänger entschlüsselt die Signatur mit dem öffentlichen Schlüssel.  
Er bildet selbst einen Hash des Dokuments und vergleicht beide Werte.  
Stimmen sie überein, ist das Dokument unverändert und der Absender authentisch.

## Aufgabe 6: Zusatzaufgabe {#aufgabe-6}

Eine Seite des internen Webservers soll den Essensplan einer Kantine
abbilden. Sie sollen je ein kurzes Konzept für die Umsetzung als
statische Internetseite sowie als dynamische Internetseite erstellen.

Statisch: HTML-Seite mit festem Speiseplan, manuelle Aktualisierung jede Woche per Dateiänderung auf dem Server. Einfach, keine Serverlogik notwendig.  

Dynamisch: Datenbank mit Gerichten, Pflege über Webformular. Serverseitiges Skript (z. B. PHP) erzeugt die Seite automatisch. Inhalte können schnell geändert und zeitgesteuert angezeigt werden.
