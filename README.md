# Kolumbien bei Olympia (1896–2016)

**Kurs**: Applied AI with Python  
**Student**: Erika Diaz

## Forschungsfrage
Kolumbien bei Olympia (Sommer 1896–2016): Entwicklung der Teilnahme, Frauenanteil und Medaillenprofile nach Sportarten

## Datensatz
- athlete_events.csv
- noc_regions.csv  
(Quelle: Kaggle / Kursmaterialien)

## Repository-Struktur
- notebooks/      → Analyse-Notebooks
- src/            → Hilfsfunktionen (Daten laden, bereinigen)
- figures/        → exportierte Plots für das Poster
- poster/         → finales Poster als PDF (optional zusätzlich die editierbare Datei)

## Reproduktion
1. Dieses Repository als ZIP herunterladen und entpacken.
2. Im Projekt-Root einen Ordner data/ erstellen.
3. Die Datensatz-Dateien in data/ ablegen:
  -athlete_events.csv
  -noc_regions.csv
4. Abhängigkeiten installieren:
  -pip install -r requirements.txt
5. Jupyter starten:
  -jupyter notebook
6.Das Notebook in notebooks/ öffnen und die Zellen von oben nach unten ausführen.

> Hinweis: Der Ordner data/ wird von git ignoriert (siehe .gitignore) und nicht auf GitHub hochgeladen.

Methoden (kurz)
- Länderfilter: NOC == "COL" und Season == "Summer".
- Teamgröße: Anzahl einzigartiger Athlet:innen pro Jahr (nunique() über ID).
- Frauenanteil: F / (F + M) basierend auf einzigartigen Athlet:innen pro Jahr.
- Medaillen: gezählt als Zeilen mit nicht-null Medal (visualisiert nach Sportart und Jahr).

> Hinweis zu Ausreißer: Der Datensatz enthält einen Eintrag für 1900 (Tug-Of-War) mit NOC=COL. Wir kennzeichnen ihn als historischen Ausreißer und interpretieren Trends primär für 1932–2016.
