# Pflichtenheft
Belegarbeit Software-Engineering II

Sommersemester 2018

Thema: Entwicklung eines SW‐Systems zur Unterstützung der Planung von Präsentationen im Kontext des Moduls SE II

Bearbeitet von:
* Denis Keiling
* Fabian Krehnke
* Leo Lindhorst
* Đức Hùng Nguyễn
* Oliver von Seydlitz

Autraggeber: Prof. Dr. Hauptmann

## Problemstellung und Systemziel

### Problem
Die Terminbelegung für Prüfungspräsentationen über E-Mail und manuelles Editieren der Excel-Tabelle ist zeitaufwändig und kann zu Fehlern führen.

### Ziel
Es soll ein Software-System entwickelt werden, über das die Terminplanung geregelt wird. Es soll folgendes gewährleisten:
* Ein gleichzeitiges Buchen darf nicht möglich sein um Konflikte zu vermeiden
* Die Termine müssen vom Prüfer flexibel angegeben werden können
* Organisation muss dezentral sein um den Prüfer zu entlasten

## Systemkontext
![Kontexdiagramm](diagrams/kontext.jpg)

## Benutzerschnittstelle

## Anforderungen

### Funktionale Anforderungen

#### Überblick

Funktionale Anforderung | Auslöser (Eingabe) | Reaktion (Ausgabe)
------------------------|--------------------|------------------
**Prüfungstermine verwalten** | |
Termine generieren | Starttermin |
Termin als frei markieren | Termin |
Termin blockieren | Termin |
Termine anzeigen | | Terminübersicht
**Gruppen verwalten** (Lehrende)| |
Gruppe anlegen | Gruppenname |
Gruppe löschen | Gruppenname |
Gruppen anzeigen | | Gruppenübersicht
**Prüfungstermine anzeigen und buchen** | |
Termine anzeigen | | Terminübersicht
Termin reservieren | Reservierungswunsch |
Reservierten Termin stornieren | |
Termin verbindlich buchen | Buchungswunsch |

#### Prüfungstermine verwalten (Lehrende)
![AWF-Diagramm Termine verwalten Lehrende](diagrams/awf-termine-lehrende.jpg)
* Das System muss der Lehrenden die Möglichkeit bieten

#### Gruppen verwalten
![AWF-Diagramm Gruppen verwalten](diagrams/awf-gruppen.jpg)
* Das System bla

#### Prüfungstermine anzeigen und buchen
![AWF-Diagramm Termine anzeigen und buchen Studenten](diagrams/awf-termine-studenten.jpg)


### Qualitätsanforderungen
* Das System soll einen Kalender anbieten, in dem die Startzeiten der Doppelstundenraster bereits vorhanden sind.
* Die verschiedenen Zustände eines Termins sollen visuell voneinander unterscheidbar sein.

### Rahmenbedingungen

#### technisch/technologische Rahmenbedingungen
* Das System wird als Web-Anwendung realisiert.
* Das System wird auf http://www2.htw-dresden.de/~hauptmann installiert und muss mit den dort gegebenen technischen Möglichkeiten auskommen.
* Die technischen Abhängigkeiten sollen so gering wie möglich sein.

#### organisatorische Rahmenbedingungen
* Es wird davon ausgegangen, dass die Gruppen einander vertrauen und sich keine Gruppe als eine andere ausgibt.
* Es wird davon ausgegangen, dass sich eine Gruppe intern abspricht, bevor sie einen Termin reserviert oder bucht.
* Es findet höchstens eine Prüfung pro Tag statt.
* Die gebuchte Startzeit ist verbindlich. Die Gruppe muss beim Buchen selbst dafür sorgen, dass die Startzeit früh genug innerhalb des Zeitrahmens gewählt wird, sodass die komplette Prüfung im Zeitrahmen bleibt.
* Die Endzeit einer Prüfung wird von der Prüfenden eingetragen.
* Das System ist nicht für die Authentifizierung der Studierenden und Lehrenden zuständig. Diese wird von der Lehrenden über die Webserver-Einstellungen realisiert.

#### rechtliche Rahmenbedingungen
* Um dem Datenschutz gerecht zu werden, werden Gruppen nur über den Gruppennamen identifiziert.
