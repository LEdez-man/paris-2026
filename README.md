# Familienreise Verdun und Paris 2026

Interaktiver Reiseführer für eine Familienreise (zwei Erwachsene, Kinder 10 und 13 Jahre) vom 10. bis 18. Oktober 2026: Verdun (Schlachtfeld-Klassiker) und sechs Tage Paris, Unterkunft in Montmartre (18e). Die Seite ist eine **Progressive Web App (PWA)**: Sie lässt sich auf dem Smartphone installieren und funktioniert danach auch ohne Netz.

**Live:** https://ledez-man.github.io/paris-2026/

Dieses Repository ist zugleich eine **Anleitung und Vorlage**, um denselben Ablauf für andere Städtereisen zu wiederholen (siehe [Auf eine andere Stadt übertragen](#auf-eine-andere-stadt-übertragen)).

## Inhalt des Repositories

| Datei | Zweck |
|---|---|
| `index.html` | Die gesamte App in einer Datei (HTML, CSS, JavaScript, alle Reisedaten eingebettet) |
| `manifest.webmanifest` | App-Metadaten für die Installation (Name, Farben, Symbole, Startseite) |
| `sw.js` | Service Worker: speichert die Seite für den Offline-Betrieb |
| `icon-192.png`, `icon-512.png` | App-Symbole (512 px auch als „maskable“) |
| `apple-touch-icon.png` | Symbol für iOS |
| `README.md` | Diese Dokumentation |
| `BRIEFING-VORLAGE.md` | Fragebogen und Arbeitsauftrag für eine neue Reise (Spezifikationsvorlage) |
| `DATENMODELL.md` | Aufbau der Reisedaten (Tage, Stationen, Wege, Vertiefung) |

## Die App installieren und nutzen

1. Die Live-Adresse einmal **mit Internet** im Browser öffnen (Android: Chrome).
2. Die Seite **ein zweites Mal neu laden**. Erst dann liegen auch die Schriftarten im Zwischenspeicher.
3. Chrome-Menü (drei Punkte) → **App installieren** (oder „Zum Startbildschirm hinzufügen“).
4. Danach öffnet sich die App im Vollbild und ohne Netz. Preise, Zeiten und Karten-Links brauchen unterwegs weiterhin Internet; die Kartenlinks öffnen Google Maps.

**iPhone/iPad:** Safari → Teilen → „Zum Home-Bildschirm“.

**Updates:** Der Service Worker lädt bei bestehender Verbindung zuerst die neue Version und fällt sonst auf den Zwischenspeicher zurück. Nach einer neuen Veröffentlichung genügt es, die App einmal mit Netz zu öffnen und einmal neu zu starten.

**Praktische Funktionen:** Tabs je Tag, Stationen mit Neugier-Frage zum Aufklappen, aufklappbare „Vertiefung“ (Geschichte, Begriffe, Kinderbox, Quiz mit eingeklappter Lösung, Quellen), Wege mit Entfernungen, Buttons „Für WhatsApp kopieren“ und „Route zum ersten Ziel“, abhakbare Vorbereitungsliste.

## Spezifikationen dieser Reise

Diese Vorgaben haben den Inhalt geprägt. Sie sind die Grundlage für das [Briefing](BRIEFING-VORLAGE.md) einer neuen Reise.

| Bereich | Vorgabe |
|---|---|
| Reisegruppe | 2 Erwachsene, Kinder 10 und 13 Jahre |
| Zeitraum und Ablauf | Sa 10.10. Verdun (1 Nacht), So 11.10. Verdun-Stätten, danach Paris, Mo 12. bis Sa 17.10. Programm, So 18.10. Abreise mit dem Auto |
| Unterkunft | Wohnung in Montmartre; die genaue Adresse steht **nicht** im öffentlichen Repository, die Routen starten am Place des Abbesses oder an einer lokal eingetragenen Adresse |
| Interessen | Geschichte und Architektur, Skurriles und Gruseliges, Aussicht und Action |
| Tempo | entspannt, 2 bis 3 Stationen pro Tag, Mittagspause, Plan B bei Regen |
| Ausschlüsse | kein Louvre-Besuch; keine Luftbesichtigung |
| Aufbruchszeit | in Paris an Programmtagen (Mo bis Sa) nicht vor 10:30 Uhr aus dem Haus |
| Verkehr | Auto steht eine Woche im Parkhaus; Crit’Air-Plakette vorhanden; Versailles wahlweise per Auto oder RER C; Navigo-Wochenkarte (Mo bis So) |
| Wege | pro Teilstrecke Entfernung in Metern ab Wohnung bzw. von Station zu Station; **unter 800 m wird keine Metro gerechnet**, ab etwa 1,5 km oder über 20 Gehminuten lohnt die Metro, dazwischen „zu Fuß oder Metro“; Gehtempo 4,5 km/h |
| Vertiefung je Station | 250 bis 350 Wörter: Geschichte, Stadtgeschichte, Sozialgeschichte, Einordnung zur Fünften Republik; Begriffe mit Herkunft; Kinderbox; Quiz (2 bis 3 Fragen, Lösung eingeklappt); Quellenliste |
| Quellenpolitik | zuerst offizielle Stellen (Betreiber, staatliche Museen, Denkmalbehörden, UNESCO, Ministerien), Wikipedia nur zur Orientierung; nicht Belegbares wird als „bitte prüfen“ markiert |
| Ausgabeformate | interaktive Seite (diese PWA), WhatsApp-Texte pro Tag, Word-Dokument, Markdown-Dokumentation |
| Visuelle Orientierung | farbige, nummerierte Tagesmarken (An, 1 bis 6, Ab) mit Themensymbol |

## Vorgehen in Schritten

Der Ablauf, nach dem dieses Projekt entstanden ist. Jeder Schritt hat ein überprüfbares Ergebnis.

1. **Briefing klären.** Reisegruppe, Termine, Interessen, Tempo, Ausschlüsse, Verkehrsmittel, Ausgabeformate. Ergebnis: ausgefülltes [Briefing](BRIEFING-VORLAGE.md).
2. **Orte auswählen.** Pro Tag 2 bis 3 Hauptstationen nach Interessen, geografisch gebündelt. Ruhetage der Häuser gegen die Wochentage prüfen (zum Beispiel Orsay und Katakomben montags geschlossen).
3. **Fakten recherchieren.** Öffnungszeiten, Preise, Ermäßigungen, Reservierungspflichten bei den Betreibern. Stand und Quelle festhalten, Unsicheres markieren.
4. **Daten strukturieren.** Alles in ein einziges Datenobjekt ([Datenmodell](DATENMODELL.md)), aus dem später alle Formate erzeugt werden. Keine Inhalte doppelt pflegen.
5. **Wege messen.** Orte geokodieren (Adress-Geocoder), Fußwege routen (OpenStreetMap-Fußrouting), Entfernung in Metern und Minuten je Teilstrecke; daraus die Regel „unter 800 m zu Fuß“ anwenden. Metro-Zeiten sind Schätzungen und als solche gekennzeichnet.
6. **Zeitplan bauen.** Startzeiten, Mittag, Puffer, Sonnenuntergang. Frühester Aufbruch als eigenes Feld, damit er in allen Formaten erscheint.
7. **Vertiefung schreiben.** Pro Station der aufklappbare Zusatztext mit Begriffen, Kinderbox, Quiz und Quellen. Faktenprüfung gegen die Quellen; nicht belegte Zahlen streichen oder als Schätzung kennzeichnen.
8. **Formate erzeugen.** Aus demselben Datenobjekt: HTML-Seite, WhatsApp-Texte (die Kopier-Buttons nutzen dieselben Textfunktionen wie der Build), Word-Dokument, Markdown.
9. **Prüfen.** Siehe [Prüfliste](#prüfliste-vor-der-veröffentlichung).
10. **Veröffentlichen.** Statische Dateien in ein öffentliches GitHub-Repository, GitHub Pages aktivieren (Branch `main`, Ordner `/ (root)`), Adresse auf dem Telefon öffnen und installieren.

## Auf eine andere Stadt übertragen

1. [`BRIEFING-VORLAGE.md`](BRIEFING-VORLAGE.md) ausfüllen (Stadt, Termine, Gruppe, Interessen, Tempo, Ausschlüsse, Verkehr, Unterkunftsbereich).
2. Das ausgefüllte Briefing zusammen mit [`DATENMODELL.md`](DATENMODELL.md) einem KI-Assistenten mit Recherche- und Dateifunktion übergeben (Arbeitsauftrag steht in der Vorlage). Der Auftrag verlangt, dass zuerst die Stationen abgestimmt werden, dann Recherche mit Quellen, dann die Formate.
3. Ergebnis gegen die [Prüfliste](#prüfliste-vor-der-veröffentlichung) kontrollieren.
4. Neues Repository anlegen, die erzeugten Dateien hochladen, GitHub Pages aktivieren.
5. Namen anpassen: `name`, `short_name`, `start_url`, Farben in `manifest.webmanifest`; Cache-Name in `sw.js` (`paris2026-…`), damit sich Reisen nicht gegenseitig überschreiben.

Der Generator (Node.js-Skripte, die aus dem Datenobjekt Seite, WhatsApp-Text, Word und Markdown bauen) liegt noch **nicht** in diesem Repository, weil er die private Unterkunftsadresse enthält. Er lässt sich bereinigt nachreichen.

## Prüfliste vor der Veröffentlichung

- Ruhetage gegen Wochentage geprüft; Datum und Wochentag passen zusammen.
- Preise und Zeiten mit Stand und Quelle; nicht Verifizierbares als „bitte prüfen“.
- Jede Station hat Neugier-Frage, Info, Weg, bei Bedarf Tipp und Preis.
- Jede Teilstrecke hat Entfernung und Empfehlung; Regel unter 800 m ohne Metro eingehalten.
- Frühester Aufbruch an Programmtagen eingehalten.
- Kein Überlauf auf dem Handy (Tabellen, lange Wörter), Bedienung mit dem Daumen.
- Offline-Test: Seite laden, Flugmodus, neu starten; alles außer externen Links muss funktionieren.
- Keine privaten Daten (Adresse, Namen, Buchungsnummern) im öffentlichen Repository.

## Technik der PWA

- **Eine Datei:** `index.html` enthält Layout, Logik und Daten; keine Abhängigkeit von Bibliotheken. Schriftarten werden zur Laufzeit von Google Fonts nachgeladen und zwischengespeichert, ohne sie bleibt die Seite lesbar.
- **Manifest:** `display: standalone`, `start_url: ./index.html`, Symbole 192 px und 512 px (maskable).
- **Service Worker:** Kernelemente werden beim Installieren zwischengespeichert; für Seiten derselben Herkunft gilt „Netz zuerst, bei Fehler Zwischenspeicher“; Schriftarten werden separat zwischengespeichert. Die Cache-Version ergibt sich aus einem Hash der Dateien, dadurch erscheinen Änderungen nach der nächsten Verbindung.
- **Speicher im Browser:** Abhakstatus der Vorbereitungsliste und die optional eingetragene Startadresse liegen nur im `localStorage` des eigenen Geräts.

## Datenschutz

Das Repository ist öffentlich. Es enthält keine Unterkunftsadresse, keine Namen und keine Buchungsdaten. Die Startadresse für die Routenbuttons wird nur lokal im Browser gespeichert und nirgendwohin gesendet.

## Hinweise zu den Inhalten

Preise, Öffnungszeiten und Ruhetage gelten laut den verlinkten Quellen mit Stand 8. Oktober 2026 und können sich ändern. Fahrzeiten der Metro sind grobe Schätzungen; die genaue Verbindung zeigt Google Maps oder die App von Île-de-France Mobilités. Die historischen Texte folgen den in jeder Vertiefung genannten Quellen; wo Quellen sich widersprechen, steht das im Text.

## Stand

Version vom 8. Oktober 2026.
