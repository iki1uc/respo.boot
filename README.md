# respo.boot — Vollkreis‑Engine

respo.boot ist ein modularer Response‑Generator, der mit der QI.engine arbeitet.  
Jedes Modul (1–9) erzeugt einen eigenen Respo, gesteuert durch den Team‑Work‑Koop‑Sequencer.

## Struktur

- **Public/**
  - 1 use.html
  - 2 user.html
  - 3 home.html
  - 4 ort.html
  - 5 markt.html
  - 6 industry.html
  - 7 work.html
  - 8 team.html
  - 9 koop.html
- **QI.engine/**
  - com.sys
  - 3.js
  - 9.sys
  - 81.sys
- **index.html** — Controller
- **stage.html** — Stage‑Layer
- **move.md** — Bewegungs‑Dokumentation
- **404.html** — Orbit‑Fehlerseite
- **LICENSE-CLOSED.txt**

## Team‑Work‑Koop‑Sequencer

- **Koop = 3 ↺** — Startimpuls, erzeugt tmp‑Signal  
- **Work = ▣** — stabilisiert und übersetzt  
- **Team = 27** — verteilt Last auf Beteiligte  

Sequenz: **3 ↺ → ▣ → 27**

## Nutzung

Öffne `index.html` im Browser.  
Die Buttons laden Module über die QI.engine.  
Orbit‑Routing steuert Fehler über `404.html`.

## Lizenz

Siehe `LICENSE-CLOSED.txt`.

## Maintainer

iki1uc
