# Uitspraak Coach

Persönliche Sprech- und Aussprache-App von Justin (Deutsch → Niederländisch, A2). Live: https://timely-semolina-81b8d0.netlify.app (Netlify baut automatisch aus `main`).

## Dateien
- `index.html` – die komplette App (ein File, kein Build). Azure Speech (Aussprache + Stimmen), Gemini (Rollenspiel + KI-Coach, der die WAV-Aufnahme anhört und gesprochen auf Deutsch erklärt); Mikrofon-Verstärkung einstellbar. Schlüssel liegen nur im Browser.
- `lessons.json` – alle Lektionen. Die App lädt sie bei jedem Öffnen. **Neue Lektion = hier ein Pack ergänzen und auf `main` pushen.**
- `progress/` im Branch **`progress`** – Ergebnisse, die die App hochlädt (ein JSON pro Sync, Feld `records`). Nicht in `main` mergen.

## Lektions-Pack
```json
{"id":"les7","title":"Les 7 · Thema (TT.MM.)",
 "items":[["NL-Satz","DE-Übersetzung","Aussprache-/Grammatiktipp","BE·to·nung  WOR·ter"]],
 "scene":{"name":"Kurzname","who":"Rollenname","role":"English: scene for the AI partner",
          "goal":"Deutsch: Ziel für Justin","open":["erster Satz NL","DE"],"hint":"Deutsch: Tipp"}}
```
Betonung: Silben mit `·`, betonte Silbe GROSS, Wörter mit zwei Leerzeichen. Neueste Lektion vorne im Array einfügen, „Klanken“ bleibt hinten, `updated` auf das Datum setzen.

## Fortschritt lesen
`git fetch origin progress` und alle Dateien unter `progress/` in `origin/progress` lesen. Record-Typen: `talk` (Rollenspiel: turns mit you/better/notes/pron, weakWords, sounds), `pron` (Satz, score, weak = Wort:Punkte [schwache Laute]), `pron-basic`, `coach` (KI-Erklärung: verdict, words), `fail` (keine Bewertung: reason nomatch/noscore/…, gain).
Daraus Wiederholung und Klanken-Übungen der nächsten Lektion ableiten.
