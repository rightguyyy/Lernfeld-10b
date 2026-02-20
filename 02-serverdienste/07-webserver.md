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

Ein Webserver stellt Webseiten und Webanwendungen über HTTP/HTTPS bereit.
Er verarbeitet Anfragen von Clients (Browsern), liefert Inhalte wie HTML,
CSS, Bilder oder APIs aus und kann auch dynamische Inhalte erzeugen.

## Aufgabe 2

Nennen Sie vier bekannte Webserver.

- Apache HTTP Server  
- Nginx  
- Microsoft IIS  
- LiteSpeed  

## Aufgabe 3

Vervollständigen Sie die Tabelle zu HTTP-Status-Codes

| Nummer | Status | Bedeutung |
|----|----|----|
| 200 | OK | Die Anfrage war erfolgreich und das Ergebnis wird übermittelt |
| 301 | Moved Permanently | Ressource wurde dauerhaft verschoben (Weiterleitung) |
| 403 | Forbidden | Zugriff verboten, Client hat keine Berechtigung |
| 404 | Not Found | Angeforderte Ressource wurde nicht gefunden |

## Aufgabe 4

Erklären Sie, wozu im Zusammenhang mit HTTPS eine PKI mit Zertifikaten
benötigt wird und wie eine PKI funktioniert.

Eine PKI (Public Key Infrastructure) stellt digitale Zertifikate aus und
verwaltet diese. Zertifikate enthalten den öffentlichen Schlüssel eines
Servers sowie Identitätsinformationen. Eine Zertifizierungsstelle (CA)
signiert das Zertifikat. Der Client prüft die Signatur anhand vertrauens-
würdiger Root-CAs. So werden Authentizität und sichere Schlüsselverteilung
für verschlüsselte HTTPS-Verbindungen gewährleistet.

## Aufgabe 5

a)  Nach der Entscheidung für einen Webserver soll überlegt werden, ob
    der Einsatz von HTTPS sinnvoll ist. Beurteilen Sie, ob bei einem nur
    intern verwendeten Webserver der Einsatz des HTTPS-Protolkolls
    sinnvoll ist.

Ja, auch intern sinnvoll. HTTPS schützt vor Mitschneiden im internen Netz,
verhindert Manipulationen (MITM) und ermöglicht Authentizität des Servers.
Gerade bei sensiblen Daten oder BYOD sollte HTTPS verwendet werden.

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
    erläutern. Mit einem Programmablaufplan (PAP) lassen sich Abläufe
    grafisch darstellen. Durch die grafische Darstellung wird der Ablauf
    einfacher nachvollziehbar.

    Erstellen Sie aus den gegebenen Ablaufschritten einen
    Programmablaufplan, z. B. mit
    [PlantUML](https://plantuml.com/de/activity-diagram-beta). Dazu
    können sie den
    [PlantUML-Online-Editor](https://www.plantuml.com/plantuml/uml/)
    verwenden.

    ![](images/pap-https-tls-elemente.png)

Beispiel-PAP in PlantUML:

```
@startuml
start
:Client sendet HTTPS-Anfrage;
:Server sendet Zertifikat;
:Client prüft Zertifikat (CA, Ablauf, Hostname);
:Client erzeugt Sitzungsschlüssel;
:Schlüssel mit öffentlichem Schlüssel verschlüsseln;
:Server entschlüsselt Sitzungsschlüssel;
:Symmetrisch verschlüsselte Kommunikation startet;
stop
@enduml
```

<!-- -->

d)  Der interne Webserver soll Zertifikate verwenden. Entscheiden Sie,
    welche Einsatzszenarien durch die Verwendung eines Zertifikats
    umgesetzt werden können.

1.  Eine Verbindung kann durch Verschlüsselung abgesichert werden. → Ja  
2.  Ein Load Balancing zwischen Servern kann einfach ausgefuhrt werden. → Nein  
3.  Ein Server kann seine Identität nachweisen → Ja  
4.  Webseiten, die ein Zertifikat anbieten, werden besser von Suchmaschinen bewertet. → Ja  

<!-- -->

e)  Ein Mitarbeiter möchte wissen, wie ein Zertifikat funktioniert. Er
    zeigt Ihnen ein Zertifikat einer besuchten Webseite.

    ![](images/zertifikat.png)

    Erläutern Sie dem Mitarbeiter die Aufgabe des öffentlichen
    Schlüssels und des „Fingerabdrucks".

Öffentlicher Schlüssel:  
Wird vom Client genutzt, um Daten (z. B. Sitzungsschlüssel) sicher an
den Server zu verschlüsseln. Nur der Server kann sie mit seinem privaten
Schlüssel entschlüsseln.

Fingerabdruck (Fingerprint):  
Hashwert des Zertifikats. Dient zur eindeutigen Identifikation und zum
Vergleich, ob ein Zertifikat manipuliert oder ausgetauscht wurde.

<!-- -->

f)  Bei der Kommunikation zwischen Server und Client werden sowohl die
    symmetrische als auch die asymmetrische Verschlüsselung eingesetzt.
    Geben Sie die grundlegenden Funktionsweisen an und nennen Sie Vor-
    und Nachteile der beiden Verschlüsselungsarten.

| Verschlüsselungsart | Funktionsweise | Vorteile | Nachteﬂe |
|----|----|----|----|
| symmetrische Verschlüsselung | ein Schlüssel zur Ver- und Entschlüsselung | sehr schnell, effizient | aufwendiger Schlüsselaustausch |
| asymmetrische Verschlüsselung | Schlüsselpaar aus öffentlichem und privatem Schlüssel | sicherer Schlüsselaustausch, Authentifizierung möglich | langsamer, mehr Rechenaufwand |

<!-- -->

g)  Ein wichtiger Ablauf bei der Arbeit mit Zertifikaten ist die
    digitale Signatur. Beschreiben Sie den Ablauf der digitalen
    Signatur, indem Sie die Abschnitte in der Grafik erläutern.

1. Aus den Daten wird ein Hashwert gebildet.  
2. Dieser Hash wird mit dem privaten Schlüssel des Absenders verschlüsselt (Signatur).  
3. Empfänger berechnet selbst den Hash der Daten.  
4. Empfänger entschlüsselt die Signatur mit dem öffentlichen Schlüssel.  
5. Stimmen beide Hashwerte überein, sind Integrität und Authentizität bestätigt.

## Aufgabe 6: Zusatzaufgabe {#aufgabe-6}

Eine Seite des internen Webservers soll den Essensplan einer Kantine
abbilden. Sie sollen je ein kurzes Konzept für die Umsetzung als
statische Internetseite sowie als dynamische Internetseite erstellen.

Statische Webseite:  
HTML-Seite mit fest eingetragenem Speiseplan, Pflege per manuellem
Bearbeiten und Upload (z. B. wöchentlich durch Verwaltung). Einfach,
geringer Aufwand, keine Serverlogik nötig.

Dynamische Webseite:  
Backend (z. B. PHP, Node.js oder Python) mit Datenbank für Menüs.
Pflege über Admin-Oberfläche, automatische Anzeige nach Datum.
Optional Filter (vegetarisch, Allergene), API-Anbindung möglich.
Mehr Aufwand, aber flexibel und automatisierbar.