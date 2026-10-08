# Datenmodell

Alle Inhalte der Reise stehen in **einem** Datenobjekt. In `index.html` ist es als Konstante `DATA` eingebettet; dieselbe Struktur speist WhatsApp-Texte, Word-Dokument und Markdown. Änderungen werden nur an einer Stelle gemacht.

## Oberste Ebene

| Schlüssel | Typ | Inhalt |
|---|---|---|
| `START` | Text | Standard-Startpunkt für Routen (ein bekannter Platz, nicht die Wohnung) |
| `days` | Liste | Tage in Reihenfolge, siehe unten |
| `prep` | Liste | Vorbereitungspunkte `{ id, text }`, in der Seite abhakbar |
| `tarife` | Objekt | `rows[{ name, preis, note }]`, `tipp`, `kauf`, `rechnung` |
| `verdunBackground` | Objekt | Hintergrund zu einem Thema: `fakten[]`, `begriffe[{ fr, de, ety }]`, `literatur[]` (optional, je Reise ersetzbar) |
| `sources` | Liste | Quellen der Seite als `[Titel, URL]` |
| `stations` | Liste | Haltestellen rund um die Unterkunft `{ name, lines, m, note }` |

## Tag (`days[]`)

| Schlüssel | Bedeutung |
|---|---|
| `id` | Kurzname, z. B. `p1` |
| `badge` | Tagesmarke `{ label, kind, bg, fg, sym }` (Nummer, Typ `day` oder `travel`, Farben, Symbol) |
| `tag`, `date`, `short`, `name`, `title`, `lead` | Beschriftungen, Datum (ISO), Kurzform mit Wochentag, Überschrift, Einleitung |
| `line` | Hauptverkehrslinie `{ label, kind, bg, fg, caption }` |
| `leave` | frühester Aufbruch (`"10:30"`), optional |
| `sunset` | Sonnenuntergang |
| `stops` | Stationen, siehe unten |
| `kids` | Aufgabe für die Kinder |
| `fallbackLabel`, `fallback` | Plan B (Standard-Beschriftung „Bei Regen“) |
| `legs` | Teilstrecken, siehe unten |

## Station (`stops[]`)

| Schlüssel | Bedeutung |
|---|---|
| `t` | Uhrzeit |
| `name`, `q` | Anzeigename, Suchbegriff für den Karten-Link |
| `mode` | Weg dorthin, beginnt mit „Metro“, „RER“, „zu Fuß“ oder „Auto“ (steuert das Symbol im WhatsApp-Text) |
| `hook` | Neugier-Frage, die zuerst sichtbar ist |
| `info` | Kurzinfo zum Aufklappen |
| `tip`, `cost` | Tipp und Preis, optional |
| `optional` | `true` markiert „optional“ |
| `closedOn` | Liste von Ruhetagen (`["Mo"]`) für die Prüfung gegen die Wochentage |
| `deep` | Vertiefung, siehe unten |

## Vertiefung (`deep`)

| Schlüssel | Bedeutung |
|---|---|
| `lage` | Ort, Stadtbezirk |
| `history` | Absätze (zusammen 250 bis 350 Wörter): Geschichte, Stadt- und Sozialgeschichte, Einordnung zur Gegenwart |
| `terms` | Begriffe `{ fr, de, ety }` mit Übersetzung und Herkunft |
| `kids` | 3 bis 4 Sätze für die Kinderbox |
| `quiz` | 2 bis 3 Fragen `{ q, a }`, Antwort in der Seite eingeklappt |
| `sources` | `{ title, url }`; Bücher ohne URL erlaubt |

## Teilstrecke (`legs[]`)

| Schlüssel | Bedeutung |
|---|---|
| `from`, `to` | Start und Ziel |
| `m`, `min` | Fußweg in Metern und Minuten (4,5 km/h); `null`, wenn nicht gemessen (z. B. Anreise nach Versailles) |
| `rec` | Empfehlung: `walk`, `metro` oder `either` |
| `mixM` | Fußmeter, wenn die Empfehlung befolgt wird (Metro-Tipp: nur der Weg zur Station) |
| `metroMin`, `via`, `metro` | Fahrzeit, Stationen, ausführliche Beschreibung (bei `metro` und `either`) |
| `note` | Hinweis (z. B. „Bergauf, viele Stufen“) |

Regel zur Wahl von `rec`: unter 800 m immer `walk`; ab etwa 1,5 km oder über 20 Gehminuten `metro`; dazwischen `either`, wenn eine Metro-Alternative besteht. Die Summen „alles zu Fuß“ und „mit Metro-Tipps“ errechnet die Seite aus `m` und `mixM`.

## Erzeugte Formate

| Format | Quelle | Besonderheit |
|---|---|---|
| Seite (PWA) | `days`, `prep`, `tarife`, `stations`, `sources` | Tabs je Tag, Kopier-Buttons |
| WhatsApp-Text | Funktionen `dayText`, `overviewText`, `ticketsText` | 1 Nachricht je Tag, ohne Vertiefung; dieselben Funktionen laufen im Build und im Browser |
| Word | alle Felder inkl. `deep` | Vertiefung je Station |
| Markdown | alle Felder inkl. `deep`, Quellenabschnitt | für Dokumentation und Archiv |
