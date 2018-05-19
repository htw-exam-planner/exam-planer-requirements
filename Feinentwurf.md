# 2.0 Feinentwurf

In diesem Abschnitt soll der Feinentwurf beschrieben werden. Dazu wird das Pflichtenheft als Basis genommen.

## 2.1 Programmiersprache

Als Programmiersprache standen PHP und Java zur Verfügung. Aufgrund der kurzfristigen Änderung seitens Frau Prof. Dr.-Ing. Hauptmann , dass es sich um einen lokalen Client handeln soll, wurde sich im Team für die Programmiersprache Java entschieden.

## 2.2 Qualitätsanforderungen an den Quellcode

WIP

Damit das Softwaresystem von allen Projektmitgliedern leicht verstanden werden kann wurden folgende Maßnahmen zur Qualitätsssicherung vorgenommen.

* Kommentare und Variablendeklarationen werden in Englisch verfasst.
* Einheitliche Namenskonvention: der Erste Buchstabe einer Variable wird groß geschrieben. Kommentare werden in der Form `// summary: ... Input: ... Output:...` festgelegt.
* Funktionen werden mit zwei Tabstops, der Rest des Quellcodes mit einem Tabstop eingerückt.
* In Funktionen werden Rückgabewerte immer geprüft, bevor ein Wert zurück gegeben wird.
* Eingaben werden immer überprüft und mögliche Fehler durch Exceptions abgefangen.
* Der Quellcode folgt dem Prinzip KISS (Keep it stupid simple) und DRY (Don't repeat yourself).
* Das Umbrechen einer Quellcodezeile ist zu vermeiden.Dadurch wird der Quellcode gut lesbar.
* Die Implementierung muss jederzeit durch andere Projektmitglieder verstanden werden können.
* Es finden regelmäßig gemeinsame Codereviws statt um die Qualität des Quellcodes hoch zu halten.
* Das Softwaresystem besitzt mehrere Klassen, die nach Modulen unterteilt sind.
* Der Quellcode des Softwaresystems wird versioniert und auf Github allen Mitgliedern zugänglich gemacht.

## 2.3 funktionale Anforderungen

Folgende Anforderungen sind für das Softwaresystem wichtig:

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

## 2.4 Ausgaben des Softwaresystems

Die Ausgaben des Clients erfolgen grafisch. 

Dafür gibt es drei Ausgabelevel:



| Ausgabelevel | Beschreibung 
| -------- | -------- |
| Information    | Die Ausgabe hat ledeglich informativen Chrakter. Sie bestätigt Aktionen, die vom Benutzer ausgewählt wurden.    |
| Warnung   | Hier teilt der Client dem Benutzer mit, dass es eventuell zu Fehlern kommen kann, wenn ein bestimmter Wert vom Benutzer nicht mitgeteilt wird. Der Benutzer sollte hier sorgfältig arbeiten.  |
| Fehler   |Hier teilt das Softwaresystem mit, dass eine bestimmte Aktion nicht ausgeführt werden kann. Hier muss der Benutzer oder Administrator eingreifen, um den FEhler zu beheben.    |


## 2.5 Konfiguration

Da das Softwaresystem eine Verbindung zur Datenbank erhalten wird, benötigt es Informationen um sich mit dieser zu verbinden. 
Da es sich hierbei um kritische Informationen (Benutzername,Passwort) handelt, ist es ratsam, diese Informationen zumindest gesalzen (gehasht) dem Programm zu übergeben, da sont eine Manipulation der Datenbank möglich wäre, falls jemand, diese Informationen in einer Datei findet.
Alternativ könnte die Information zur Verbindung der Datenbank auf in einer Maske eingestellt werden, die nur dem Administrator zugänglich ist.

Um die Software nicht unnötig aufzublähen und sie einfach zu halten, wird die Konfiguration über eine Maske eingestellt, die nur dem Administrator zugänglich ist.
