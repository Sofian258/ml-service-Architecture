# Modular ML Service Architecture

Modulare Python-Architektur für wiederverwendbare Machine-Learning-Services zur Anomalieerkennung.

Das Projekt entstand im Rahmen meiner Bachelorarbeit und zeigt, wie ML-Services als wiederverwendbare Backend-Module aufgebaut werden können. Fokus liegt auf klarer Trennung von Input, Verarbeitung und Output sowie auf erweiterbarer Systemarchitektur.

## Architektur

Die Pipeline folgt dem EVA-Prinzip:

- Input: Daten einlesen und normalisieren (Adapter Pattern)
- Processing: Feature Engineering, Modelllogik und Pipeline-Steuerung
- Output: Vorhersagen und Weitergabe an Zielsysteme

Die Module sind lose gekoppelt und können unabhängig erweitert oder ersetzt werden.

## Verwendete Design Patterns

- Adapter Pattern für Datenquellen und Ausgabeformate  
- Strategy Pattern für ML-Modelle  
- Observer Pattern für Ereignisse in der Pipeline  
- Chain of Responsibility für flexible Verarbeitungsschritte  

Ziel ist eine wiederverwendbare ML-Service-Struktur statt eines einmaligen Skripts.

## Tech Stack

- Python  
- Pandas  
- Scikit-learn  
- Matplotlib  
- Objektorientierte Architektur  



## Projektstruktur

ml-service-architecture/
├─ ml_modular_system/
│  ├─ input/
│  │  ├─ data_reader.py        # Abstrakte Schnittstelle für Datenquellen
│  │  ├─ excel_adapter.py      # Adapter für Excel-Dateien
│  │  └─ preprocessing.py     # Datenbereinigung und Vorbereitung
│  │
│  ├─ processing/
│  │  ├─ rules.py              # Regelbasierte Feature-Berechnung
│  │  ├─ feature_engineering.py# Feature Engineering
│  │  ├─ ml_strategies.py      # ML-Strategien (z.B. Isolation Forest)
│  │  ├─ chain_handler.py      # Chain-of-Responsibility für ML-Pipeline
│  │  └─ pipeline.py           # Zentrale Verarbeitungspipeline
│  │
│  ├─ output/
│  │  ├─ observers.py          # Observer für Visualisierung und Export
│  │  ├─ plot_adapter.py       # Plot-Logik (Matplotlib)
│  │  └─ sink_adapter.py       # Adapter für Ausgabekanäle
│  │
│  ├─ subject.py               # Zentrales Subject (Observer Pattern)
│  └─ main.py                  # Einstiegspunkt / Orchestrierung
│
├─ docs/
│  └─ architecture.png         # Architekturdiagramm (EVA + Patterns)
│
├─ requirements.txt            # Python-Abhängigkeiten
└─ README.md                   # Projektbeschreibung
