# 🏅 Kolumbien bei Olympia (1896–2016)

**Kurs**: Applied AI with Python 
**Kursleitung**: Prof. DI Martin Uray
**Studentin**: Erika Diaz
**Institution**: Paris Lodron Universität Salzburg
**Semester**: WS 2025/26

## 📋Forschungsfrage

Wie hat sich Kolumbiens Teilnahme an den Olympischen Sommerspielen entwickelt?
Diese Analyse untersucht die olympische Entwicklung Kolumbiens von 1896 bis 2016 mit Fokus auf:
- 📈Teamwachstum: Entwicklung der Delegationsgröße über 120 Jahre
- 👥Geschlechterparität: Integration und Anteil weiblicher Athlet:innen
- 🥇Medaillenprofile: Erfolge nach Sportarten und zeitliche Trends

## 📊Datensatz

Die Analyse basiert auf dem 120 Years of Olympic History Dataset:

Datei                   Beschreibung                                    Quelle
__________________________________________________________________________________________
athlete_events.csv      Individuelle Athlet:innen und ihre Events       Kaggle
                        (271.116 Zeilen)
noc_regions.csv         NOC-Codes und Länderzuordnung (230 Regionen)    Kursmaterialien

Filterkriterien für diese Analyse:
- NOC == 'COL' (nur Kolumbien)
- Season == 'Summer' (nur Sommerspiele)

## 📁Repository-Struktur

Project-Applied-AI-with-Python/
│
├── notebooks/   
│   └── FinalProject.ipynb
│
├── figures/               
│   ├── 01_team_size.pdf
│   ├── 01_team_size.png
│   ├── 02_gender_composition_area.pdf
│   |── 02_gender_composition_area.png
|   ├── 03_medals_heatmap.pdf
|   ├── 03_medals_heatmap.png
│   ├── 04_medals_typeofmedal.pdf
│   ├── 04_medals_typeofmedal.png
│   |── 05_host_cities_withmedals_colored.pdf
|   └── 05_host_cities_withmedals_colored.png
│
├── poster/                 
│   |── Poster_Project.pdf
|   └── Poster_Project.pptx
│
├── data/                   # ⚠️ NICHT im Repository (siehe .gitignore)
│   ├── athlete_events.csv
│   └── noc_regions.csv
│
├── requirements.txt        
├── .gitignore          
└── README.md  
- notebooks/      → Analyse-Notebooks
- src/            → Hilfsfunktionen (Daten laden, bereinigen)
- figures/        → exportierte Plots für das Poster
- poster/         → finales Poster als PDF (optional zusätzlich die editierbare Datei)

## 🔬Methodik

Datenfilterung

df_colombia = df[(df['NOC']=='COL')&(df['Season']=='Summer')]

Metriken

Metrik                Berechnung                       Code-Beispiel
__________________________________________________________________________________________
Teamgröße             Anzahl eindeutiger               df.groupby('Year')['ID'].nunique()
                      Athlet:innen pro Jahr
Frauenanteil          Verhältnis F/(F+M) pro Jahr      female / (female + male)
Medaillen             Deduplizierte Medal-Events       df.drop_duplicates(subset=                                                                       ['Year','Sport','Event','Medal'])

Deduplikation von Medaillen

Um Team-Medaillen (z.B.Fußball) nicht mehrfach zu zählen, werden Duplikate entfernt:
cols = ['Year', 'City', 'Sport', 'Event', 'NOC', 'Medal']
Ergebnis: 27 eindeutige Medaillen-Events

Historicher Ausreißer

1900 Paris – Tug-Of-War (Silber):
Der Datensatz enthält einen Eintrag mit NOC=COL für das Team "Racing Club de France". Dies ist eine historische Anomalie (französisches Team mit kolumbianischem Sportler).
✅ Dokumentiert
❌ Nicht in Trendinterpretarionen einbezogen
📊 Hauptanalyse-Zeitraum: 1932-2016

## 📈Hauptergebnisse

1. Teamwachstum (71-facher Anstieg)

Jahr            Athlet:innen            Bemerkung
__________________________________________________________________________________________
1932            2                       Erste reguläre Teilnahme
1968            10                      Erste weibliche Athlet:innen
2012            101                     Größer relativer Sprung
2016            143                     Historisches Maximum

Interpretation: Exponentielle Beschleunigung ab den 1990er-Jahren deutet auf institutionelle Sportreformen und gezielte Investitionen hin.

2. Geschlechterparität
   
1932-1964:       0% Frauen (ausschließlich männliche Teilnahme)
1968:            33% Frauen (5 von 15 Athlet:innen)
2012:            55% Frauen (56 von 101) <- Historicher Höhepunkt
2016:            49% Frauen (70 von 143)
Meilenstein: 2012 markiert erstmals weibliche Mehrheit in der Delegation

3. Medaillenprofile

Gesamt: 27 deduplizierte Medaillen-Events(1932-2016)
Zeitliche Konzentration:
  - 2012-2016: 16 Medaillen (59% des Gesamterfolgs)
  - Peak-Jahre: London 2012 und Rio 2016 (je 8 Events)

Top-Sportarten:
1. 🚴Cycling
2. 🏃Athletics
3. 🥊Boxing
4. 🏋️Weighlifting
5. 🥋Taekwondo, Wrestling, Judo
6. 🎯Shooting

Geographische Verteilung:
- London 2012: 8 Medaillen
- Rio 2016: 8 Medaillen
- München 1972: 3 Medaillen
- Athen 2004, Beijing 2008: je 2 Medaillen

 ## 📚Weiterführende Ressourcen
 Datensatz
 - Kaggle: 120 Years of Olimpic History
 - Olympic.org: Offizielle Statisken

Tutorials
- pandas Documentation
- seaborn Tutorial
- geopandas User Guide

Wissenschaftliches Poster Desing
- Better Posters Blog
- Scientific Poster Desing Guide
