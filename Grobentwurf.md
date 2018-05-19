# 1.0 Grobentwurf

Der Grobentwurf gibt in dem vorgestellten Projekt die Eckpunkte des Softwaresystems vor.

## 1.1 Ziel 

Es soll ein Software-System entwickelt werden, über das die Terminplanung geregelt wird. Es soll folgendes gewährleisten:

Ein gleichzeitiges Buchen darf nicht möglich sein um Konflikte zu vermeiden
Die Termine müssen vom Prüfer flexibel angegeben werden können
Organisation muss dezentral sein um den Prüfer zu entlasten
Dies wurde durch Frau Prof. Dr.-Ing. Hauptmann bestätigt.

## 1.2 Systemumgebung

Im Gespräch mit Frau Prof. Dr.-Ing. Hauptmann wurde herausgearbeitet, dass es sich um einen lokalen Client handeln soll, der durch die Studierenden sowie die Adminstratoren bedient werden soll.
Das Softwaresystem läuft damit auf einem Computer in dem PC-Kabinetten und auf den Arbeitsplatzrechner der Adminstratoren. Der Client liest und schreibt Daten in die Datenbank, sodass jederzeitein einheitlicher Stand auf allen Clients zu sehen ist.Eine umständliche manuelle Synchronisation der Daten entfällt damit.

## 1.3 Benutzerschnittstellen

Der Client soll mit einer Schnittstelle zur Datenbank und zum Exportieren der gesammelten Daten in eine PDF-Datei ausgestattet werden. Weiterhin nimmt er Eingaben der Gruppen und Administratoren entgegen.
Diese Schnittstellen betreffen im Studentenmodus:
* die Gruppenauswahl, welche die Buchung durchführen will
* die Terminansicht, bei der sich der Student eine Übersicht über die verfügbaren Termine veschaffen und Buchungen/Reservierungen verwalten kann
* die Möglichkeit eine Buchung durchzuführen und zwingend eine Startzeit anzugeben

Im Administratormodus werden folgende Schnittstellen benötigt:
* Anlegen der initialen Gruppen und Termine
* eine Übersicht über die verfügbaren Termine veschaffen, Termine editieren und Buchungen/Reservierungen verwalten
* das Bearbeiten des Zeitraumes, des Kommentares und das Deaktivieren des Termines
* bei einer Buchung kann der Termin storniert oder der Zeitraum sowie der Prüfungsraum festgelegt werden
* eine Reservierung stornieren
* einen deaktivierten Termin aktivieren
* Gruppen in der Gruppenansicht anlegen oder löschen

## 1.4 funktionale Anforderungen

Die funktionalen Anforderungen ergaben sich teilweise aus der Aufgabenstellung und wurden mit einer Auslöser-Reaktions-Tabelle ermittelt.
Weiterhin ergab die Analyse der Schnittstellen, dass es eine Einstellung bedarf, in der die Verbindungsdaten zu Datenbank stehen. 

## 1.5 Qualitätsanforderungen

Die Software soll: 
* lokal auf einem Client laufen
* einfach zu bedienen und robust sein
* ohne großen Aufwand wartbar sein
* eine schnelle Übersicht liefern, welche Gruppen bereits gebucht haben und welche Gruppen noch keine Buchung abgegeben haben
* welche Tage durch welche Gruppen belegt wurden

## 1.6 Rahmenbedingungen 

Die Software kann nur dann entsprechend den Qualitätsanforderungen funktionieren, wenn sie korrekt installiert und konfiguriert wurde. Dies wird in der Benutzerdokumentation beschrieben.

