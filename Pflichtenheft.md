# Pflichtenheft
Belegarbeit Software-Engineering II

Thema: Entwicklung eines SW‐Systems zur Unterstützung der Planung von Präsentationen im Kontext des Moduls SE II

Bearbeitet von:
* Denis Keiling
* Fabian Krehnke
* Leo Lindhorst
* Đức Hùng Nguyễn
* Oliver von Seydlitz

Autraggeber: Prof. Dr. Hauptmann

## Problemstellung und Systemziel

## Anforderungen

### Funktionale Anforderungen

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
