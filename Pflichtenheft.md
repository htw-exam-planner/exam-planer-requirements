# Pflichtenheft
Belegarbeit Software-Engineering II

Sommersemester 2018

Thema: Entwicklung eines SW‐Systems zur Unterstützung der Planung von Präsentationen im Kontext des Moduls SE II

Bearbeitet von:
* Denis Keiling
* Fabian Krehnke
* Leo Lindhorst
* Đức Hùng Nguyễn
* Oliver von Seydlitz

Auftraggeber: Prof. Dr. Hauptmann

## Problemstellung und Systemziel

### Problem
Die Terminbelegung für Prüfungspräsentationen über E-Mail und manuelles Editieren der Excel-Tabelle ist zeitaufwändig und kann zu Fehlern führen.

### Ziel
Es soll ein Software-System entwickelt werden, über das die Terminplanung geregelt wird. Es soll folgendes gewährleisten:
* Ein gleichzeitiges Buchen darf nicht möglich sein um Konflikte zu vermeiden
* Die Termine müssen vom Prüfer flexibel angegeben werden können
* Organisation muss dezentral sein um den Prüfer zu entlasten

## Systemkontext
Der Kontext des Systems wird durch folgendes Diagramm beschrieben:

![Kontexdiagramm](diagrams/awf-kontext.jpg)

## Benutzerschnittstelle
### Startbildschirm - Rollenauswahl
Auf dem Startbildschirm kann der Benutzer auswählen, ob die Anwendung im Administrator- oder im Studentenmodus genutzt werden soll.
![Rollenauswahl](ui-prototypes/exports/Role%20selection.png)
 
### Studentenansicht
#### Gruppenauswahl
In der Gruppenauswahl kann der Student die Gruppe auswählen, für die er die Buchung durchführen möchte.
![Gruppenauswahl](ui-prototypes/exports/Group%20selection.png)

#### Terminansicht
In der Terminansicht kann sich der Student eine Übersicht über die verfügbaren Termine veschaffen und Buchungen/Reservierungen verwalten.
![Terminansicht](ui-prototypes/exports/Date%20management.png)

##### Buchung durchführen
Nach dem Drücken des "Buchen" Knopfes muss der Student die Startzeit für die Prüfung eingeben.
![Buchung durchführen](ui-prototypes/exports/Date%20management%20\(Book%20Button%20pressed\).png)

### Administratoransicht
#### Gruppen und Termine anlegen
Mithilfe des Formulars kann der Administrator die initialen Gruppen und Termine anlegen.
![Gruppen und Termine anlegen](ui-prototypes/exports/Setup.png)

#### Terminansicht
In der Terminansicht kann sich der Administrator eine Übersicht über die verfügbaren Termine veschaffen, Termine editieren und Buchungen/Reservierungen verwalten.
![Terminansicht](ui-prototypes/exports/Date%20management%20Admin.png)

##### Termin bearbeiten
Durch die Schaltfläche "Bearbeiten", kann der Administrator den Zeitraum und den Kommentar des Termins bearbeiten und den Termin deaktivieren.
![Termin bearbeiten](ui-prototypes/exports/Date%20management%20Admin%20\(Edit%20Button%20pressed,%20no%20Booking\).png)

Falls eine Buchung für den Termin besteht, kann der Administrator die Buchung stornieren oder den Zeitraum sowie Prüfungsraum der Buchung festlegen.
![Termin bearbeiten - Buchung](ui-prototypes/exports/Date%20management%20Admin%20\(Edit%20Button%20pressed,%20Booking%20present\).png)

Falls eine Reservierung für den Termin besteht, kann der Administrator die Reservierung stornieren.
![Termin bearbeiten - Reservierung](ui-prototypes/exports/Date%20management%20Admin%20\(Edit%20Button%20pressed,%20Reservation%20present\).png)

Falls der Termin deaktiviert ist, kann der Administrator den Termin wieder aktivieren.
![Termin bearbeiten - Deaktiviert](ui-prototypes/exports/Date%20management%20Admin%20\(Edit%20Button%20pressed,%20Deactivated\).png)

#### Gruppenansicht
In der Gruppenansicht kann sich der Administrator einen Überblick über den Zustand der Gruppen verschaffen, sowie Gruppen mithilfe der entsprechenden Schaltflächen anlegen und löschen.
![Gruppenansicht](ui-prototypes/exports/Group%20management.png)

## Anforderungen

### Funktionale Anforderungen

#### Überblick
Die folgende Tabelle gibt einen Überblick über die essentiellen Gruppen und essentiellen Funktionen, sowie deren Auslöser und Reaktionen:

Anwendungsfall | Auslöser/Eingabe | Reaktion/Ausgabe
---------------|----------|---------
**Prüfungstermine verwalten** | |
Termine und Gruppen generieren | Startdatum + Anzahl Gruppen | Termine + Gruppen
Termin bearbeiten | Termin | Termine bzw. Warnhinweis
Termin als frei markieren | Termin | Termine
Termin deaktivieren | Termin | Termine
Zeitfenster bearbeiten | Termin | Termine bzw. Warnhinweis
Bemerkung bearbeiten | Termin | Termine
Raum und Endzeit festlegen | Termin | Termine bzw. Warnhinweis
Termine exportieren | | Termine
**Termine anzeigen** | |
Termine anzeigen | | Termine
**Gruppen verwalten** | |
Gruppe anlegen | Gruppenname | Gruppe
Gruppe löschen | Gruppe | Gruppen (neu)
Gruppen anzeigen | | Gruppen
**Prüfungstermine anzeigen und buchen** | |
Als Gruppe anmelden | Gruppe | Termine
Termin reservieren | Gruppe + Termin | ggf. Warnhinweis
Reservierten Termin stornieren | Termin | ggf. Warnhinweis
Termin buchen | Gruppe + Termin + Startzeit | ggf. Warnhinweis

Die essentiellen Gruppen sind ferner in folgendem Anwendungsfalldiagramm dargestellt. Abstrakte Anwendungsfälle sind dabei kursiv geschrieben.

![AWF-Diagramm Überblick](diagrams/awf-ueberblick.jpg)

##### Struktur der Auslöser und Reaktionen
Termin =
  Datum
  \+ Zeitfenster
  \+ Terminzustand
  \+ Bemerkung
  \+ \(
    Reservierung
    | Buchung
    \)

Termine = {Termin}

Zeitfenster = Startzeit \+ Endzeit

Terminzustand = frei | deaktiviert | reserviert | gebucht

Reservierung = Gruppe

Buchung = Gruppe \+ Startzeit \+ \(Endzeit\) \+ \(Raum\)

Gruppe = Gruppenname \+ Buchungsstatus

Buchungsstatus = gebucht | noch nicht gebucht

Gruppen = {Gruppe}

Die anderen Auslöser und Reaktionen sind atomare Werte.


Es folgen nun die Beschreibungen aller Anwendungsfälle.


#### Termine verwalten
Folgendes Anwendungsfalldiagramm gibt einen Überblick über die Anwendungsfälle der essentiellen Gruppe "Termine verwalten":

![AWF-Diagramm Termine verwalten Lehrende](diagrams/awf-termine-verwalten.jpg)

##### Termine und Gruppen generieren
Die Funktion "Termine und Gruppen generieren"
* muss dem Administrator die Möglichkeit bieten, die 15 Termine eines Prüfungszeitraums sowie die Gruppen dieses Zeitraums anzulegen.

Folgendes Aktivitätsdiagramm verdeutlicht dies:

![Aktivitätsdiagramm Termine und Gruppen generieren](diagrams/ad-termine-gruppen-generieren.jpg)

##### Termin bearbeiten
Die Funktion "Termin bearbeiten"
* muss dem Administrator die Möglichkeit bieten, eine der folgenden Aktionen durchzuführen:
 * Termin als frei markieren
 * Termin deaktivieren
 * Zeitfenster bearbeiten
 * Bemerkung bearbeiten
 * Raum und Endzeit festlegen

Folgendes Aktivitätsdiagramm verdeutlicht dies. Die möglichen Aktionen sind in ihren jeweiligen Aktivitätsdiagrammen beschrieben:

![Aktivitätsdiagramm Termin frei markieren](diagrams/ad-termin-bearbeiten.jpg)

##### Termin als frei markieren
Die Funktion "Termin als frei markieren"
* muss dem Administrator die Möglichkeit bieten, einen Termin als frei zu markieren.
* muss beim frei markieren eine ggf. vorhandene Reservierung oder Buchung löschen.

Folgendes Aktivitätsdiagramm verdeutlicht dies:

![Aktivitätsdiagramm Termin frei markieren](diagrams/ad-termin-frei-markieren.jpg)

##### Termin deaktivieren
Die Funktion "Termin deaktivieren"
* muss dem Administrator die Möglichkeit bieten, einen Termin zu deaktivieren.
* muss beim Deaktivieren eine ggf. vorhandene Reservierung oder Buchung löschen

Folgendes Aktivitätsdiagramm verdeutlicht dies:

![Aktivitätsdiagramm Termin deaktivieren](diagrams/ad-termin-deaktivieren.jpg)

##### Zeitfenster bearbeiten
Die Funktion "Zeitfenster bearbeiten"
* muss dem Administrator die Möglichkeit bieten, das Zeitfenster eines Termins zu bearbeiten.
* muss prüfen, ob beim angegebenen Zeitfenster die End- nach der Startzeit liegt.

Folgendes Aktivitätsdiagramm verdeutlicht dies:

![Aktivitätsdiagramm Zeitfenster bearbeiten](diagrams/ad-zeitfenster-bearbeiten.jpg)

##### Bemerkung bearbeiten
Die Funktion "Bemerkung bearbeiten"
* muss dem Administrator die Möglichkeit bieten, einem Termin eine Bemerkung hinzuzufügen.
* muss dem Administrator die Möglichkeit bieten, die Bemerkung eines Termins, sofern vorhanden, zu bearbeiten.

Folgendes Aktivitätsdiagramm verdeutlicht dies:

![Aktivitätsdiagramm Zeitfenster bearbeiten](diagrams/ad-bemerkung-bearbeiten.jpg)

##### Raum und Endzeit einer Buchung festlegen
Die Funktion "Raum und Endzeit einer Buchung festlegen"
* muss dem Administrator die Möglichkeit bieten, einem gebuchten Prüfungstermin den Prüfungsraum und die Endzeit der Prüfung zuzuordnen.
* muss sicherstellen, dass die Endzeit nach der Startzeit liegt.

Folgendes Aktivitätsdiagramm verdeutlicht dies:

![Aktivitätsdiagramm Raum und Endzeit festlegen](diagrams/ad-raum-endzeit-festlegen.jpg)

##### Termine exportieren
Die Funktion "Termine exportieren"
* sollte dem Administrator die Möglichkeit bieten, eine Übersicht der gebuchten Termine als PDF zu exportieren.
* sollte dem Administrator die Möglichkeit bieten, eine Übersicht der gebuchten Termine als Kalenderdaten zu exportieren.

Folgendes Aktivitätsdiagramm verdeutlicht dies:

![Aktivitätsdiagramm Termine exportieren](diagrams/ad-termine-exportieren.jpg)

#### Gruppen verwalten
Folgendes Anwendungsfalldiagramm gibt einen Überblick über die Anwendungsfälle der essentiellen Gruppe "Gruppen verwalten":

![AWF-Diagramm Gruppen verwalten](diagrams/awf-gruppen-verwalten.jpg)

##### Gruppe anlegen
Die Funktion "Gruppe anlegen"
* muss dem Administrator die Möglichkeit bieten, eine Gruppe anzulegen.

Folgendes Aktivitätsdiagramm verdeutlicht dies:

![Aktivitätsdiagramm Gruppe anlegen](diagrams/ad-gruppe-anlegen.jpg)

##### Gruppe löschen
Die Funktion "Gruppe löschen"
* muss dem Administrator die Möglichkeit bieten, eine Gruppe zu löschen.

Folgendes Aktivitätsdiagramm verdeutlicht dies:

![Aktivitätsdiagramm Gruppe löschen](diagrams/ad-gruppe-loeschen.jpg)

##### Gruppen anzeigen
Die Funktion "Gruppen anzeigen"
* muss dem Administrator die Möglichkeit bieten, alle Gruppen anzuzeigen.
* muss die Gruppen, die noch nicht gebucht haben, visuell hervorheben.

Folgendes Aktivitätsdiagramm verdeutlicht dies:

![Aktivitätsdiagramm Gruppen anzeigen](diagrams/ad-gruppen-anzeigen.jpg)


#### Termine anzeigen
Die Funktion "Termine anzeigen"
* muss dem Administrator und den Studenten die Möglichkeit bieten, die Termine anzuzeigen.

![AWF-Diagramm Termine anzeigen](diagrams/ad-termine-anzeigen.jpg)

#### Termine buchen und reservieren
Folgendes Anwendungsfalldiagramm gibt einen Überblick über die Anwendungsfälle der essentiellen Gruppe "Termine buchen und reservieren":

![AWF-Diagramm Termine buchen und reservieren](diagrams/awf-termine-reservieren-und-buchen.jpg)

##### Als Gruppe anmelden
Die Funktion "Als Gruppe anmelden"
* muss einem Studenten ermöglichen, sich unter Angabe seiner Gruppe am System anzumelden.

![Aktivitätsdiagramm Als Gruppe anmelden](diagrams/ad-gruppe-anmelden.jpg)

##### Termin reservieren
Die Funktion "Termin reservieren"
* muss einem Studenten die Möglichkeit bieten, einen Termin zu reservieren.
* muss sicherstellen, dass eine Gruppe nur eine Reservierung tätigen kann.
* muss sicherstellen, dass nur freie Termine reserviert werden können.
* muss sicherstellen, dass eine Gruppe, die bereits gebucht hat, keinen Termin mehr reservieren kann.

Folgendes Aktivitätsdiagramm verdeutlicht dies:

![Aktivitätsdiagramm Termin reservieren](diagrams/ad-termin-reservieren.jpg)

##### Reservierung stornieren
Die Funktion "Reservierung stornieren"
* muss einem Studenten die Möglichkeit bieten, die Reservierung eines Termins zu stornieren.

Folgendes Aktivitätsdiagramm verdeutlicht dies:

![Aktivitätsdiagramm Reservierung stornieren](diagrams/ad-reservierung-stornieren.jpg)

##### Termin buchen
Die Funktion "Termin buchen"
* muss einem Studenten die Möglichkeit bieten, einen Prüfungstermin zu buchen.
* muss sicherstellen, dass eine Gruppe nur einen Termin buchen kann.
* muss beim Buchen eine Reservierung der buchenden Gruppe, sofern vorhanden, entfernen.
* muss sicherstellen, dass nur freie Termine gebucht werden können.
* muss prüfen, ob die gewählte Startzeit im Zeitfenster des Termins liegt.

Folgendes Aktivitätsdiagramm verdeutlicht dies:

![Aktivitätsdiagramm Termin buchen](diagrams/ad-termin-buchen.jpg)

#### Zustandsdiagramm eines Termins
Folgendes Zustandsdiagramm gibt einen Überblick über die Zustände eines Termins und die möglichen Übergänge zwischen diesen Zuständen. Eine Erklärung der Bedeutung der Zustände findet sich im Glossar.

![Zustandsdiagramm Termine](diagrams/zd-termine.jpg)


### Qualitätsanforderungen
* Die verschiedenen Zustände eines Termins sollen visuell voneinander unterscheidbar sein.
* In der Gruppenübersicht sollen Gruppen, die noch nicht gebucht haben, visuell hervorgehoben werden.

### Rahmenbedingungen

#### technisch/technologische Rahmenbedingungen
* Das System wird mit Java als Desktop-App implementiert.
* Es wird ferner eine MySQL-Datenbank auf einem Hochschulserver verwendet. Der Auftraggeber beantragt diese bei der HTW.
* Die technischen Abhängigkeiten sollen so gering wie möglich sein.

#### organisatorische Rahmenbedingungen
* Es wird davon ausgegangen, dass die Gruppen einander vertrauen und sich keine Gruppe als eine andere ausgibt.
* Es wird davon ausgegangen, dass sich eine Gruppe intern abspricht, bevor sie einen Termin reserviert oder bucht.
* Es findet höchstens eine Prüfung pro Tag statt.
* Die gebuchte Startzeit ist verbindlich. Die Gruppe muss beim Buchen selbst dafür sorgen, dass die Startzeit früh genug innerhalb des Zeitrahmens gewählt wird, sodass die komplette Prüfung im Zeitrahmen bleibt.
* Die Endzeit einer Prüfung wird von der Prüfenden eingetragen.
* Das System ist nicht für die Authentifizierung der Studierenden und Lehrenden zuständig.

#### rechtliche Rahmenbedingungen
* Um dem Datenschutz gerecht zu werden, werden Gruppen nur über den Gruppennamen identifiziert.

## Glossar

Begriff | Bedeutung
--------|----------
Termin | Tag, Start-und Endzeit eines Zeitfensters, in dem eine Prüfung stattfinden kann. Innerhalb des Termins kann eine Reservierung bzw. Buchung gemacht werden
deaktivierter Termin | Ein Tag, an dem keine Prüfung stattfinden kann.
freier Termin | Ein Termin, an dem eine Prüfung stattfinden kann und der noch nicht reserviert oder gebucht ist.
Reservierung | nicht verbindliche Kennzeichnung einer Gruppe, dass sie einen Termin buchen möchte
Buchung | verbindliche Entscheidung einer Gruppe, einen bestimmten Termin als Prüfungstermin in Anspruch zu nehmen
Student | Studierende(r) des Moduls "Software-Engineering II", der/die in seiner/ihrer Gruppe in der Prüfungszeit geprüft werden muss
Administrator | Die Lehrende bzw. Prüfende des Moduls "Software-Engineering II", sowie der Praktikumsbetreuer, der ebenfalls bei einer Prüfung mitwirkt
