# ⚽ Tafelfussball

Ein digitales Quizspiel im Stil von „Tafelfussball" für den Unterricht — komplett clientseitig, kein Backend, keine Kosten. Läuft in jedem modernen Browser.

**Live:** https://manuel-benz.github.io/tafelfussball/

## Idee

Die Lehrperson stellt Fragen. Die richtig antwortende Mannschaft bewegt den Ball ein Feld Richtung gegnerisches Tor. Wer zuerst trifft, bekommt einen Punkt.

## Zwei Ansichten, ein Gerät

Öffne die App und wähle im Launcher eine Ansicht (jeweils in einem eigenen Fenster):

- **📺 Beamer-Ansicht** (`?view=beamer`) — für die Klasse auf dem Projektor. Zeigt Spielfeld, Ball, Punkte und Frage. **Nie die Lösung.**
- **🎛️ Lehrer-Ansicht** (`?view=lehrer`) — auf dem Laptop. Steuerung, Aufgabenverwaltung und die Lösung.

Beide Fenster synchronisieren sich live über `BroadcastChannel`, mit `localStorage` als Fallback und Persistenz.

## Aufgaben aus PDF importieren

1. Aufgabenblatt (PDF) in einem KI-Tool (Claude/ChatGPT) öffnen.
2. Diesen Prompt zusammen mit dem PDF einfügen:

   > Extrahiere alle Übungsaufgaben und deren Lösungen aus diesem PDF. Formatiere die Ausgabe exakt so: Für jede Aufgabe eine Zeile 'F: &lt;Frage&gt;', eine Zeile 'A: &lt;Antwort&gt;', dann eine Zeile mit nur '---' als Trennzeichen. Keine zusätzlichen Erklärungen oder Nummerierungen.

3. Die Ausgabe in der Lehrer-Ansicht unter „Import" einfügen — die Aufgaben werden automatisch angehängt.

Format:

```
F: Was ist die Hauptstadt der Schweiz?
A: Bern
---
F: Wie viel ist 7 × 8?
A: 56
---
```

## Lokal ausführen

Einfach `index.html` im Browser öffnen. Für die zuverlässigste Fenster-Synchronisation über einen lokalen Server starten:

```bash
python3 -m http.server 8000
# dann http://localhost:8000/
```

## Technik

Eine einzige `index.html` — Vanilla HTML/CSS/JS, keine Abhängigkeiten, kein Build-Schritt.
