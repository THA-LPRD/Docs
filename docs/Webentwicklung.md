# Webentwicklung

## Framework und Library Auswahl
**Julia Reuter**

Die Interaktion zwischen Benutzer und Raumanzeige soll so einfach und unkompliziert wie möglich gehalten werden und dennoch genügend Funktionalitäten unterstützen.
Sie erfolgt deshalb über eine selbsterstellte Webseite, die mithilfe von HTML5, CSS und JavaScript designt wurde und über den ESP32-Webserver gehostet wird. 
Als externe Bibliothek verwendet die Benutzerwebseite nur die Javascript Library Html2Canvas.

## Webseitenaufbau und -funktionalitäten
**Julia Reuter**

Eine zentrale Funktion ist das Hochladen von PNG-Dateien. Nutzer können PNG-Bilder hochladen, die exakt auf die Pixeldimensionen des Displays abgestimmt sind. Vor jedem Upload überprüft die Webseite, ob das Bild die korrekten Dimensionen hat. Falls die Abmessungen nicht stimmen, wird der Upload abgelehnt und der Nutzer erhält eine entsprechende Fehlermeldung. Erst wenn die Bildgröße korrekt ist, wird die Datei mittels HTTP POST an den Server gesendet.

Ein weiteres Highlight ist die Möglichkeit, HTML-Designs hochzuladen. Nutzer können HTML-Code eingeben und in Echtzeit eine Vorschau anzeigen lassen. Der Ablauf beginnt mit der Eingabe des HTML-Codes in ein Textfeld. Die Webseite rendert diesen Code und zeigt eine Vorschau des Designs an. Anschließend wird der HTML-Code in ein Bild umgewandelt und erneut auf die korrekten Dimensionen überprüft. Wenn die Abmessungen stimmen, wird das Bild mittels HTTP POST an den Server gesendet.

Zusätzlich stehen vordefinierte HTML-Vorlagen zur Auswahl. Nutzer können eine Vorlage wählen, anpassen und in einer Vorschau anzeigen lassen. Das modifizierte Design wird in ein Bild umgewandelt, überprüft und bei korrekten Dimensionen an den Server gesendet.

Die Einstellungsseite der Low-Power-Raumanzeige bietet umfassende Konfigurationsmöglichkeiten. Nutzer können den Betriebsmodus der Anzeige (Standalone, Netzwerk, Server) ändern. Sie wählen den gewünschten Modus aus einem Dropdown-Menü, und die Auswahl wird mittels HTTP POST an den Server gesendet. Der Server bestätigt die Änderung und die Webseite zeigt eine entsprechende Rückmeldung an.

Ebenso können Nutzer das Display-Modul konfigurieren, indem sie es aus einem Dropdown-Menü auswählen. Die Auswahl wird wiederum mittels HTTP POST an den Server gesendet und der Server bestätigt die Änderung.

Für die WiFi-Konfiguration können Nutzer die SSID und das Passwort eingeben. Diese Daten werden mittels HTTP POST an den Server gesendet, und der Server bestätigt die Änderung. Nutzer können auch das Log Level für die serielle Konsole einstellen, indem sie das gewünschte Level aus einem Dropdown-Menü wählen und die Auswahl an den Server senden.

Für die HTTP-Authentifizierung können Benutzer Zugangsdaten eingeben und speichern. Diese Daten werden mittels HTTP POST an den Server gesendet und vom Server bestätigt. Die HTTPS-Einstellungen erlauben es den Nutzern, HTTPS zu aktivieren und die entsprechenden Zertifikatsdateien hochzuladen. Wenn HTTPS aktiviert ist, werden die Felder zum Hochladen der Zertifikats- und Schlüsseldateien sichtbar. Die Dateien werden dann ebenfalls mittels HTTP POST an den Server gesendet.

### Datenübertragung zwischen Webseite und Server
Die Kommunikation mit dem Server erfolgt über asynchrone HTTP-Anfragen, auch bekannt als AJAX (Asynchronous JavaScript and XML). 

HTTP (Hypertext Transfer Protocol) ist das grundlegende Protokoll für die Datenübertragung im Web. Es definiert, wie Nachrichten formatiert und übertragen werden und wie Webserver und -browser auf verschiedene Befehle reagieren. In diesem Kontext werden Daten wie Formularinhalte über HTTP POST-Anfragen an den Server gesendet. Diese Anfragen beinhalten die Daten im Nachrichtentext, wodurch sie für den Server zugänglich gemacht werden.

AJAX erweitert diese Funktionalität, indem es ermöglicht, HTTP-Anfragen asynchron zu senden. Das bedeutet, dass Daten im Hintergrund ausgetauscht werden können, ohne die Benutzeroberfläche zu unterbrechen. Dies wird durch die Verwendung von JavaScript erreicht, das HTTP-Anfragen erstellt und verarbeitet. Der Server antwortet auf diese Anfragen mit Daten, die dann vom JavaScript in der Webseite verarbeitet und angezeigt werden. Diese Methode verbessert die Benutzerfreundlichkeit und Reaktionsfähigkeit der Webseite erheblich.

Diese Technologie ermöglicht es, Daten mit dem Server auszutauschen und die Webseite zu aktualisieren, ohne die gesamte Seite neu zu laden. Dies sorgt für eine reibungslose und effiziente Benutzererfahrung.


## Linux Server
**Mario Wegmann**

### Verwendete Technologien

Wie im Kapitel [3.9.1 Webtechnologien](PraktischeUTheoretischeGrund.md#webtechnologien) bereits erläutert ist es für die Entwicklung einer Webanwendung sehr sinnvoll ein Webframework einzusetzen. 
Hierbei gibt es eine große Auswahl an möglichen Frameworks und auch Serverseitigen Programmiersprachen. Da JavaScript bereits im Standalone-Modus, wie auch im Netzwerk-Modus, verwendet wird um die Interaktion mit dem Displaymodul zu realisieren, ist es naheliegend, auch auf dem Server JavaScript zu nutzen. Diese Entscheidung ermöglichte eine einheitliche Codebasis sowohl im Frontend als auch im Backend, was die Entwicklung effizienter und die Wartung der Anwendung einfacher macht und zuletzt auch das erlernen neuer Programmiersprachen auf eine reduziert. Zudem wurde die Möglichkeit genutzt TypeScript anstatt Vanilla JavaScript zu verwenden, um die Vorteile zu nutzen, welche ebenso bereits im Kapitel [3.9.1 Webtechnologien](PraktischeUTheoretischeGrund.md#webtechnologien) erwähnt wurden. 

Für das Frontend wurde React ausgewählt. Durch React lassen sich Komponenten realisieren, welche modular wiederverwendet werden können. Dadurch wird es vermieden doppelten Code zu verfassen und Änderungen an einer Komponente werden global in der gesamten Webanwendung wiedergespiegelt. 

Als Webframework wurde Next.js ausgewählt, da es React unter anderem um serverseitiges Rendering erweitert. Darüber hinaus bietet Next.js eine nahtlose Integration von API-Routen und Middleware, was die Entwicklung von Full-Stack-Anwendungen erleichtert. 

Für das speichern der Daten wurde PostgresSQL als Datenbank ausgewählt. Als ORM wurde Prisma gewählt.  //TODO
Prisma ist ein Object-Relational-Mapper (ORM). ORMs ermöglichen das typensichere Arbeiten in objektroientierten Programmiersprachen 


Prisma ORM ist nützlich, weil es die Arbeit mit Datenbanken durch typsichere, deklarative Datenmodellierung und effiziente Datenbankmigrationen erheblich vereinfacht und optimiert. Es generiert automatisch TypeScript-Typen, was zu umfassender Typsicherheit und intelligenter Autovervollständigung in IDEs führt, wodurch die Produktivität und Codequalität verbessert werden. Prisma abstrahiert komplexe SQL-Abfragen und ermöglicht einfache CRUD-Operationen, reduziert die Notwendigkeit für manuelles SQL-Schreiben und minimiert potenzielle Fehler. Zudem unterstützt es verschiedene Datenbanksysteme und verfügt über eine starke Community sowie umfangreiche Dokumentation, was den Einstieg und die kontinuierliche Nutzung erleichtert.

Für den Webserver wurden Linux und Docker verwendet. Das quelloffene Linux ist bekannt für seine Stabilität, Sicherheit und Performance, was es zu einer idealen Wahl für den Einsatz als Webserver macht. Docker ergänzt diese Vorteile durch die Bereitstellung einer containerisierten Umgebung, die eine konsistente und isolierte Ausführung von Anwendungen ermöglicht. Dies erleichtert die Skalierung und Verwaltung der Anwendung erheblich und sorgt dafür, dass sie in unterschiedlichen Umgebungen gleichbleibend funktioniert. Docker-Container bieten zudem eine einfache Möglichkeit, Abhängigkeiten zu verwalten und die Bereitstellung von Updates zu automatisieren. 

Die Kombination dieser Technologien ermöglich effizient eine benutzerfreundliche, performante und wartbare Webanwendung zu entwicklen. 

### Testumgebung

Als Testumgebung wurde beim Rechenzentrum (RZ) eine Linux VM beantragt. Die vom Rechenzentrum erhaltene VM weißt die in []( #_tab_MW_01 ) genannten Eigenschaften auf

Table: Die Systemeigenschaften der vom RZ erhaltenen VM.  { #_tab_MW_01 }

| Eigenschaft | Wert |
|-------|------|
| Betriebssysrtem | Debian 12 (bookworm) |
| Prozessor-Cores | 2x 2,9 GHz |
| Arbeitsspeicher | 2 GB |
| Hauptspeicher | 30 GB |
| Hostname | lprd |

Zudem wurde vom RZ auch gleich ein DNS Eintrag gesetzt und die Domain lprd.informatik.tha.de verweist auf diese VM. 
Neben dem Betriebssystem liefert die VM auch gleich noch eine Firewall standardmäßig mit, hier setzt das RZ die Variante arno-iptables ein [[MW_01]](Quellenverzeichnis.md#MW_01). 

### Ersteinrichtung

Der administrative Zugriff auf die VM erfolgt über SSH. 
Nach der Übergabe wurden zuerst die standard Zugangsdaten der VM durch neue Zugangsdaten ersetzt und die SSH Anmeldung des root Benutzer gesperrt. Ebenso wurden für die Personen, welche Zugriff auf die VM benötigen jeweils neue Benuzter angelegt. Dabei wurde als Benutzerauthentifizierung SSH-Keys als Authentifizierungsmethode verwendet. 
Anschließend wurden die installierten Pakete mit dem Advanced Packaging Tool (apt) Paketmanager auf die neuste Version aktualisiert. 

Damit die VM während der Dauer des Projekts zuverlässig läuft und Probleme frühzeitig erkannt werden wurde eine Monitoring Lösung aufgesetzt und mit dem Discord Server der Projektgruppe verbunden. Die hier eingesetzte Lösung nennt sich Netdata. Der Netdata Agent ist opensource und kann kostenlos eingesetzt werden, dieser bringt von Haus aus viele Vorlagen mit um das Gesamtsystem gut zu überwachen und Warnungen, sowie Fehler proaktiv an die Administratoren zu melden. Taucht ein Fehler auf dem Server auf, so wird in der hier verwendenten Konfiguration, direkt eine Nachricht auf dem Discord der Projektgruppe gesendet.  

### Einrichtung der Webanwendung

Nach der erfolgreichen Grundinstallation kann mit dem Aufsetzen der Testumgebung der Webanwendung begonnen werden. 
Dafür werden zuerst die Pakete git und docker über den apt Packetmanager installiert. 


Docker

### Datensicherung
Der Zweck der VM ist primär die Entwicklung der Webanwendung und somit nicht der produktive Einsatz. Da der Quellcode der Webanwendung über Git verwaltet wird und die Daten innerhalb der Datenbank reine Testdaten sind, wurde auf das einrichten einer Datensicherung verzichtet. 

Für eine produktive Umgebung ist eine sorgfältig überlegte Backupstrategie unabdingbar. Hierbei sollte genaustens überlegt werden, wie der Backupprozess implementiert und automatisiert wird und wie erstellte Backups auf Konsistenz und wiederherstellbarkeit überprüft werden können. Auch der Speicherort von Backups sollte bedacht werden und der 3-2-1 Regel folgen. 

//TODO
Grafik Techstack



Wie im Kapitel //TODO bereits erläutert ist es für die Entwicklung einer Webanwendung sehr sinnvoll ein Webframework einzusetzen. Hierbei gibt es eine große Auswahl an möglichen Frameworks und auch Serverseitigen Programmiersprachen. Da für Funktionen wie 
Es bietet sich an im Rahmen der Projektarbeit für die Serverseitige Programmiersprache auch JavaScript einzusetzen, da bereits ein großteil des Websitecodes vom Standalone und Netzwerkmodus auf JavaScript setzt, damit dieser im Webbrowser des zugreifenden Benutzers ausgeführt werden kann. Für das Front

