# Briefing-Vorlage für eine neue Städtereise

Diese Vorlage hält die Spezifikationen fest, aus denen die Paris-Reise entstanden ist. Ausfüllen, dann zusammen mit dem Arbeitsauftrag unten und [`DATENMODELL.md`](DATENMODELL.md) einem KI-Assistenten übergeben.

## 1. Angaben zur Reise

| Feld | Eintrag | Beispiel (Paris 2026) |
|---|---|---|
| Stadt / Region | | Verdun und Paris |
| Zeitraum, Wochentage | | Sa 10.10. bis So 18.10.2026 |
| Anreise / Abreise | | Auto; Abreise Sonntagvormittag |
| Reisegruppe, Alter | | 2 Erwachsene, Kinder 10 und 13 |
| Unterkunftsbereich (nur Stadtteil, keine Adresse im öffentlichen Repo) | | Montmartre, 18e |
| Interessen (max. 3) | | Geschichte und Architektur, Skurriles und Gruseliges, Aussicht und Action |
| Tempo | | entspannt, 2 bis 3 Stationen pro Tag |
| Frühester Aufbruch | | 10:30 Uhr an Programmtagen |
| Ausschlüsse | | kein Louvre, keine Luftbesichtigung |
| Verkehr vor Ort | | Metro/RER, Navigo-Woche; Auto im Parkhaus; Umweltplakette vorhanden |
| Tagesausflug außerhalb | | Versailles |
| Wegregel | | unter 800 m keine Metro; Gehtempo 4,5 km/h |
| Vertiefung | | je Station 250 bis 350 Wörter, Begriffe mit Herkunft, Kinderbox, Quiz mit eingeklappter Lösung, Quellen |
| Quellenpolitik | | offizielle Stellen zuerst; Wikipedia nur zur Orientierung |
| Ausgabeformate | | interaktive Seite (PWA), WhatsApp-Text je Tag, Word, Markdown |
| Sprache | | Deutsch; Fachbegriffe in der Landessprache mit Übersetzung und Etymologie |

## 2. Fragen zur Klärung vor dem Start

1. Gibt es feste Termine (Tickets, Check-in, Zugzeiten)?
2. Welche Orte sind gesetzt, welche ausgeschlossen?
3. Wie lange ist das Kind belastbar (Gehzeit pro Tag, Stufen, Dunkelheit, Gruseliges)?
4. Soll es einen Plan B bei Regen pro Tag geben?
5. Welche Ermäßigungen gelten (Alter, Wohnsitz, Ausweise)?
6. Soll die Seite öffentlich oder nur per Link erreichbar sein?

## 3. Arbeitsauftrag an den Assistenten (zum Kopieren)

```text
Erstelle auf Basis des ausgefüllten Briefings einen Reiseführer für [Stadt].

Vorgehen:
1. Schlage pro Tag 2 bis 3 Stationen vor, geografisch gebündelt, passend zu den Interessen.
   Prüfe Ruhetage gegen die Wochentage. Stimme die Auswahl mit mir ab, bevor du weiterarbeitest.
2. Recherchiere Öffnungszeiten, Preise, Ermäßigungen und Reservierungspflichten bei den Betreibern.
   Nenne Quelle und Stand. Was du nicht bestätigen kannst, markierst du mit "bitte prüfen".
3. Lege alle Inhalte in einem Datenobjekt nach DATENMODELL.md ab.
4. Messe die Fußwege zwischen allen Stationen (Geocoding, Fußrouting). Wende die Wegregel an.
5. Schreibe zu jeder Station die Vertiefung (Umfang, Begriffe, Kinderbox, Quiz, Quellen) und prüfe
   jede Zahl und jedes Datum gegen die Quellen. Streiche Unbelegtes oder kennzeichne es als Schätzung.
6. Erzeuge aus dem Datenobjekt alle gewünschten Formate. Die Kopier-Buttons der Seite verwenden dieselben
   Textfunktionen wie der Build.
7. Prüfe: Ruhetage, Wochentage, Aufbruchszeit, Überlauf auf dem Handy, Offline-Betrieb, keine privaten Daten.
8. Liefere die statischen Dateien (index.html, manifest.webmanifest, sw.js, Symbole) für GitHub Pages
   und eine README mit den Schritten.

Formatvorgaben: sachlich, präzise, ohne Werbesprache; Zahlen mit Quelle; Fachbegriffe in der Landessprache
mit Übersetzung und Etymologie; Hinweis auf nicht gesicherte Angaben im Text.
```

## 4. Ergebnis kontrollieren

Nutze die Prüfliste in der [README](README.md#prüfliste-vor-der-veröffentlichung). Stichproben: je Tag eine Zahl aus der Vertiefung gegen die verlinkte Quelle prüfen, zwei Wege in Google Maps gegenmessen, Offline-Test am eigenen Telefon.
