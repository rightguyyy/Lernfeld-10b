---
css: ../css/style.css
date: Schuljahr 2025/2026
lang: de-DE
subtitle: Lernfeld 10b -- Serverdienste bereitstellen und
  Administrationsaufgaben automatisieren
title: Serverdienste -- Videokonferenz, WebRTC, VoIP
---

## Aufgabe 1

Recherchieren Sie in der Gruppe nach verfügbaren Videokonferenzsystemen.
Berücksichtigen Sie dabei folgende Aspekte:

- Anbieter/Dienstname

- Softwarevoraussetzung

- Hardwarevoraussetzung

- Serverstandort

- Datensicherung

- Weitere Features (außer Audio-/Videoübertragung)

Beispielsysteme:

Microsoft Teams  
Software: Browser oder Desktop-/Mobile-App  
Hardware: Webcam, Mikrofon, Lautsprecher/Headset  
Serverstandort: Azure-Rechenzentren (EU wählbar)  
Datensicherung: TLS-Verschlüsselung, optionale E2EE  
Features: Chat, Dateiablage, Bildschirmfreigabe, Integration in Microsoft 365  

Zoom  
Software: Browser oder Client  
Hardware: Webcam, Mikrofon  
Serverstandort: weltweit, Regionen auswählbar  
Datensicherung: TLS, optionale Ende-zu-Ende-Verschlüsselung  
Features: Breakout-Räume, Aufzeichnung, Whiteboard, Webinar-Modus  

Jitsi Meet  
Software: Browser oder App  
Hardware: Webcam, Mikrofon  
Serverstandort: abhängig vom Hoster (z. B. eigener Server möglich)  
Datensicherung: WebRTC-Verschlüsselung (DTLS-SRTP)  
Features: Open Source, Selbsthosting, Bildschirmfreigabe, Chat  

BigBlueButton  
Software: Browser  
Hardware: Webcam, Mikrofon  
Serverstandort: abhängig vom Betreiber (oft Uni/Schule oder eigener Server)  
Datensicherung: TLS, serverseitige Kontrolle bei Self-Hosting  
Features: Whiteboard, Breakout-Räume, Präsentationen, LMS-Integration  

## Aufgabe 2

a)  Nennen Sie drei Vorteile von VoIP gegenüber klassischer
    Festnetztelefonie (ISDN, analog).

- Geringere Kosten (insbesondere bei internationalen Gesprächen)  
- Nutzung über bestehende IP-Netzwerke (keine separate Telefonleitung nötig)  
- Flexible Nutzung (Softphones, mobile Geräte, ortsunabhängig)  

<!-- -->

b)  Geben Sie für die folgenden Protokolle die jeweilige Funktion
    innerhalb einer VolP-Übertragung an.

    - SIP  
      Signalisierungsprotokoll zum Aufbau, Steuern und Beenden von Verbindungen

    - SIPS  
      SIP über TLS, verschlüsselte Signalisierung

    - RTP  
      Transportprotokoll für Audio- und Videodaten in Echtzeit

    - SDP  
      Beschreibung der Sitzungsparameter (Codecs, Ports, Medienarten)

    - MGCP  
      Steuerprotokoll zur zentralen Steuerung von Gateways durch Call-Controller

<!-- -->

c)  Nennen Sie je zwei Audio- und Video-Codecs Geben Sie für die
    Audio-Codecs an, ob diese komprimierend arbeiten.

Audio-Codecs:  
- G.711 – nicht komprimierend (PCM, hohe Bandbreite)  
- Opus – komprimierend (effizient, variabler Bitrate)

Video-Codecs:  
- H.264  
- VP8