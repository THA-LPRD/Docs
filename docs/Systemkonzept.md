# Systemkonzept
Basierend auf den Rechercheergebnissen aus Kapitel 3 hat das Team folgendes Systemkonzept für die Low-Power Raumanzeige entwickelt.

### 1. Grundaufbau der Hardware

Abbildung 1 veranschaulicht den allgemeinen Aufbau. Das Low-Power Display Modul besteht aus:

- Einem Akku, der die Stromversorgung des gesamten Systems gewährleistet.
- Einem Mikrocontroller, der die zentrale Steuereinheit bildet und die anzuzeigenden Informationen über WLAN empfängt, entsprechend aufbereitet und weitergibt.
- Einem E-Paper Display, das über eine geeignete Schnittstelle die Daten vom Mikrocontroller erhält und im Anschluss direkt anzeigen kann.

Angedacht sind zudem zwei Knöpfe, die Benutzerinteraktionen ermöglichen, wie zum Beispiel das System nach einem Fehler neu zu starten oder das angezeigte Bild zu ändern. All dies ist in einem kompakten 3D-gedruckten Gehäuse verpackt, sodass es einfach und ohne externe Kabel montiert werden kann.

### 2. Potentielle Einsatzgebiete und entsprechende Funktionalitäten

In der Projektdefinition ist die Hochschule als konkreter Kunde genannt, weshalb der Fokus vor allem auf diesen spezifischen Anwendungsfall gerichtet wird. Hier besteht die Hauptidee darin, die Raumverfügbarkeit in Echtzeit anzuzeigen und über das Stattfinden von Veranstaltungen, Vorlesungen und Seminaren zu informieren. 

Dies bedeutet, dass Studenten schnell und unkompliziert herausfinden können, welche Räume gerade frei sind, um ungestört zu lernen oder Gruppenarbeiten durchzuführen. Dozenten können sicherstellen, dass ihre geplanten Veranstaltungen in den vorgesehenen Räumen stattfinden und bei Bedarf kurzfristige Änderungen kommunizieren. Auch das Verwaltungspersonal profitiert von einer effizienten Raumverwaltung, die durch das Anzeigen zusätzlicher Informationen, wie beispielsweise das Melden defekter Beamer, die logistischen Abläufe verbessert.

Ein reibungsloser Betrieb erfordert die zentrale Verwaltung mehrerer Displays über eine Serverkomponente, wie es auch bei den Konkurrenzprodukten (vgl. Kapitel 3) der Fall ist. Es bietet sich an, je nach Standort bzw. Raum IDs zu vergeben, sodass auch spontane Raumbuchungen korrekt zugeordnet werden können. Über eine Schnittstelle zu gängigen Kalendersystemen wie ICS oder WebUntis wird nicht nur über die Verfügbarkeit informiert, sondern auch der gesamte Tagesstundenplan aller Räume ist sofort ersichtlich.

Das Einsatzgebiet der Low-Power Raumanzeige wird jedoch nicht nur auf den Hochschulbereich beschränkt. Vor allem für den mobilen Einsatz oder für Privatpersonen ist das Einrichten und Verwalten eines Servers unpraktisch und zeitaufwändig. Deshalb ist das System so flexibel und generisch gehalten, dass es die Bedürfnisse unterschiedlicher Benutzergruppen erfüllt. 

So kann es auch von kleineren Firmen zur effizienten Verwaltung von einzelnen Besprechungsräumen oder Shared-Desk-Systemen eingesetzt werden. Auch auf Messeständen oder in Tagungsräumen ist eine universelle Low-Power Anzeige denkbar. In diesen Anwendungsfällen ist häufig keine geeignete Infrastruktur vorhanden, um ein komplexes System zu integrieren. Deshalb ist es möglich, das Display sowohl im Standalone- als auch im Netzwerkmodus zu betreiben.

Im Standalone-Modus kann das Display am flexibelsten eingesetzt werden, da keinerlei Infrastruktur am Anzeigeort nötig ist. Der systemeigene Mikrocontroller öffnet einen WLAN Access-Point, sodass sich ein Client-Gerät, wie beispielsweise das eigene Handy, mit der Raumanzeige verbindet und der Benutzer direkt über sein Gerät den gewünschten Inhalt an das Display übermittelt. Dieser Modus erweitert das Low Power Raumdisplay zu einer völlig autarken Anzeige. 

Im Netzwerkmodus ist das Konzept ähnlich, mit dem Unterschied, dass sich sowohl das Displaymodul als auch das Client-Gerät im gleichen WLAN, wie zum Beispiel dem eigenen Heimnetzwerk, befinden.


![Standalone](img/Standalone.png){ width=100% }

![Netzwerk](img/netzwerk.png){ width=100% }

