# Marktanalyse aktueller Trends und Technologien im Bereich digitaler Raumanzeigen @Julia Reuter

Die Motivation des Projektteams lag bei erster Betrachtung des Projektes Low-Power Raumanzeige für die THA hauptsächlich in der Steigerung der Effizienz und des eigenen Komforts, wodurch das Projekt eher als Nischenprodukt für den internen Gebrauch angesehen wurde.
Diese Einstellung änderte sich jedoch schnell nach einiger Recherche.

Nicht nur ist der potenzielle Markt für eine Low-Power Raumanzeige aufgrund der vielfältigen Einsatzgebiete in Büroräumen, Krankenhäusern, Bildungseinrichtungen, usw. relativ groß, sondern auch im Hinblick auf das Thema Umwelt, Nachhaltigkeit und Digitalisierung, lange nicht ausgeschöpft.
So wird beispielsweise eine effiziente Nutzung von Räumen durch klare Erkennbarkeit der Belegung ermöglicht und durch intelligente Verwaltung können sogar unnötige Heiz- und Beleuchtungskosten reduziert werden, wenn der Raum gerade nicht genutzt wird. Darüber hinaus kann auf papierbasierte Stundenpläne und Türschilder verzichtet werden, was nicht nur den damit verbundenen personellen Verwaltungsaufwand zur Instandhaltung deutlich verringert, sondern auch die bislang verwendeten Ressourcen minimiert.

All dieses Aspekte sind Merkmale für ein durchaus zukunfttaugliches Produkt und gerade deshalb gibt es bereits einige Unternehmen, die dieses Potenzial erkannt und entsprechende Produkte entwickelt haben.

Im Folgenden werden nun vier hauptsächlich deutsche Unternehmen analysiert, welche als Inspiration für die eigene Raumanzeige dienten und durch ihr breites Spektrum dem Team zu neuen Ansätzen und Ideen verhalfen.

## Analyse einiger Konkurrenzprodukte

Bei den ausgewählten Unternehmen und Produkten handelt es sich um:

- **Wizepanel** der Firma Wilke Technology in Aachen[^1]
- **Digitales Türschild** der Firma digitalSIGNAGE in Hamburg[^2]
- **Display** der Firma ROOMZ in Freiburg (Schweiz)[^3]
- **Touchscreen-Display** der Firma Beetronics in Düsseldorf[^4]

Im Hinblick auf das Projekt lag der Fokus der Recherche auf folgenden Aspekten, welche im Anschluss tabellarisch (s. [](#_tab_3.1)) aufgelistet werden: 

- Display Art (LCD oder E-Paper)
- Farbunterstützung
- Ansteuerung/Netzprotokoll
- Batterie und geschätzte Laufzeit
- Betrieb (Schnittstelle zum Kunden)
- Besondere Features

## Produktvergleich ausgewählter Unternehmen

Table: Übersicht und Vergleich der 4 ausgewählten Raumanzeigen { #_tab_3.1 }

| Produkt                | Display Art            | Farbunterstützung                | Ansteuerung/Netzprotokoll                    | Batterie und geschätzte Laufzeit           | Betrieb (Kundenschnittstelle)                                 | Besondere Features                                                                                         |
|------------------------|------------------------|----------------------|---------------------------------------------|--------------------------------------|-----------------------------------------|-----------------------------------------------------------------------------------------------------------|
| **Wizepanel[^5]**          | E-Paper                | Schwarz-Weiß, 16 Graustufen | 868 MHz Ultra Low Power Funk, eigene Funksender | 10 x AA-Lithium-Primärzellen, bis zu 20 Jahre | Zentrale Serverkomponente: Inhaltsübertragung und Geräteverwaltung | Bereits in den Server integrierte Adapter für MS Exchange, iCal/ICS, Google Calendars, Excel,... Auch WebUntis wird unterstütztENA[^8]|
| **Digitales Türschild[^6]**| Touch-Screen (kein E-Paper) | Farbe                |  Ethernet, NFC-Option verfügbar               | Power over Ethernet (PoE) → Kabelanschluss nötig | Keine Angabe                           | LEDs rund um Display (rot, gelb, grün) zur Hervorhebung der Raumbelegung, Sofortbuchung über Touch/NFC      |
| **ROOMZ[^3]**              | E-Paper                | Schwarz-Weiß         | WLAN                                        | 8000mAh, 4 Jahre                      | MyRoomz-App zur Buchung einzelner definierter Arbeitsbereiche[^10] | MyRoomz-App bietet Lageplanansicht des Gebäudes mit Übersicht aller Räume mit Markierung ob sie belegt sind oder nicht[^10], ROOMZ Sensor zur Vermeidung von Ghost-Meetings [^9], Sofortbuchung über Touchleiste am Gehäuse |
| **Beetronics[^7]**         | High Brightness Full HD Touchscreen | Farbe                | Display Port, HDMI, VGA, USB-C, Unterstützung aller gängigen Betriebssysteme | Netzteil (d.h. Stromanschluss) denn braucht 12.7W (Betrieb)/0.4W (Standby) | Einfaches Plug-and-Play, sonst eigener Treiber für verschiedene Betriebssysteme verfügbar | Keine spezifischen Features angegeben, aber allgemein sehr vielfältig universell einsetzbar                                                                       |

## Auswertung der Rechercheergebnisse

### Vor- und Nachteile der einzelnen Produkte

Table: Vor-und Nachteile der 4 Displayprodukte { #_tab_3.2 }

| Hersteller     | Vorteile                                                                                               | Nachteile                                                                                      |
| -------------- | ------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------- |
| **Wizepanel**  | - E-Paper-Technologie: Geringer Energieverbrauch                                                     | - Schwarz-weiß Display: Keine Farbdarstellung möglich                                        |
|                | - Lange Akkulaufzeit: Bis zu 20 Jahre                                                                | - Eigene Funksender zur Datenübertragung werden benötigt: Abhängigkeit von zusätzlicher Hardware                             |
|                | - Ultra Low Power Funk: Energiesparende und drahtlose Kommunikation                                                     |                                                                                               |
|                | - Serverintegration: Unterstützung für gängige Kalender- und Verwaltungssysteme               |                                                                                               |
| **digitalSIGNAGE** | - Touch-Screen und Farbe: Interaktive und ansprechende Benutzeroberfläche                         | - Power over Ethernet (PoE): Benötigt eine Kabelverbindung, externe Abhängigkeit      |
|                | - NFC-Option und Ethernet: Flexibilität bei der Ansteuerung                                           | - Keine Angaben zur Akku-Laufzeit: Unklarheit über Energieeffizienz vermutlich aber eher gering aufgrund der Displaytechnologie   |
|                | - LEDs zur Raumbelegung: Visuelle Hinweise zur Raumverfügbarkeit                        |                                                                                               |
| **ROOMZ**      | - E-Paper-Technologie: Geringer Energieverbrauch                                                      | - Schwarz-weiß Display: Keine Farbdarstellung möglich                                         |
|                | - WLAN: Einfache Integration in bestehende Netzwerke                                                  |                                                                                               |
|                | - Lange Akkulaufzeit: Bis zu 4 Jahre                                                                  |                                                                                               |
|                | - MyRoomz-App: Umfassende Funktionen zur Raumbuchung und -verwaltung, auch über mobile Endgeräte                                 |                                                                                               |
| **Beetronics** | - High Brightness Full HD Touchscreen: Hervorragende Bildqualität und interaktive Möglichkeiten       | - Verhältnismäßig sehr hoher Energieverbrauch        |
|                | - Vielseitige Anschlussmöglichkeiten: Unterstützung für Display Port, HDMI, VGA, USB-C; Flexibiliät in der Ansteuerung                | - Kabelgebunden: Abhängigkeit von ständiger Stromquelle.                                       |

### Abgeleitete Kriterien für das eigene Produkt

Basierend auf der Analyse der Vor- und Nachteile der Konkurrenzprodukte (vgl. [](#_tab_3.2)) sollten folgende Eigenschaften in die eigene Low-Power Raumanzeige integriert werden, um die grundlegenden Markanforderungen zu erfüllen:

1. **E-Paper-Technologie:** Für minimalen Energieverbrauch und lange Akkulaufzeit
2. **Lange Akkulaufzeit:** Nutzung von effizienten Batterien für eine wartungsarme Lösung und unabhängigen Betrieb
3. **Drahtlose Kommunikation:** WLAN oder Funk für flexible und einfache Installation sowie geringem Energieverbrauch
4. **Integration in bestehende Systeme:** Unterstützung für gängige Kalender- und Verwaltungssysteme (z.B. iCal/ICS oder WebUntis) über zentrale Serverkomponenten zur effizienten Verwaltung und Nutzung

### Ansätze zur Verbesserung der Konkurrenzfähigkeit auf dem Markt

Um sich von den zahlreichen Konkurrenzprodukten abzuheben, gibt es einige Ansätze.
Denn auch wenn es sich um ein E-Paper Display handelt, wäre es eine Idee eine gewisse Interaktion für zum Beispiel spontane Raumbuchung eingeplanen, die energiesparend und auch ohne Touchfunktion umsetzbar ist. Auch ein farbiges E-Paper-Display würde dazu beitragen das eher schlichtes Produkt für den Benutzer optisch ansprechender zu gestalten.
Das zentrale Alleinstellungsmerkmal ist jedoch das Entwickeln eines Konzeptes, indem keine zusätzliche externe Infrastruktur gebraucht wird. Denn alle obigen System werden zentral über eine Serverkomponente gesteuert und brauchen ggf. sogar eigene Funkverteiler. 
Dies ist für den Benutzer mit viel Aufwand und Kosten verbunden und lohnt sich nur für sehr große Organisationen. 

Zudem ist man stets von einer externen Softwarekomponente abhängig, denn die Display Ansteuerungsschnittstelle wird ebenfalls vom Hersteller in Form von einem Server (vgl. Wizepanel) oder einer App (vgl. ROOMZ) geliefert, sodass hier eine weitere große Abhängigkeit entsteht.

Genau hier sieht das Projektteam die potentielle Stärke ihrer Raumanzeige. Es soll ein standalone-System darstellen, dass sowohl völlig unabhängig von jeglicher zusätzlicher Soft- und Hardware ist und autark funkionieren kann.
Gleichzeitig besteht die Möglichkeit eine zentrale Verwaltungskomponente zu integrieren, um auch mehrere Displays verwalten zu können. 
Diese Flexibilität gekoppelt mit der Prämisse, das System Open-Source zu gestalten, sprich der Kunde kann nach Belieben das System erweitern und anpassen, sorgt für ein Alleinstellungsmerkmal auf dem Markt.

Die Low-Power Raumanzeige ist somit nicht nur für die Hochschule attraktiv sondern auch in kleinern Kreisen und sogar im privaten Gebrauch einsetzbar.

## Quellen

[^1]: [Wizepanel Wilke Technology (zuletzt aufgerufen am 25.06.24)](https://wizepanel.de/produkte/#schilder)
[^2]: [digitalSIGNAGE Digitale Türschilder (zuletzt aufgerufen am 25.06.24)](https://www.digitalsignage.de/digitale-tuerschilder.html)
[^3]: [ROOMZ Display (zuletzt aufgerufen am 25.06.24)](https://roomz.io/roomz_display)
[^4]: [Beetronics Touchscreen-Displays (zuletzt aufgerufen am 25.06.24)](https://www.beetronics.de/c-touchscreens)
[^5]: [Wizepanel 9"7 classic (zuletzt aufgerufen am 25.06.24)](https://wizepanel.de/downloads/DATA_Sheet_WizePanel_97_Classic_DE.pdf)
[^6]: [digitalSIGNAGE betrachtetes Digitales Türschild (zuletzt aufgerufen am 25.06.24)](https://www.digitalsignage.de/portfolio-hardware/xds-1078d-digital-signage-signboard.html)
[^7]: [Beetronics 10 Zoll Touchscreen Datenblatt (zuletzt aufgerufen am 25.06.24)](https://www.beetronics.de/datasheets/product/341)
[^8]: [Wizepanel Handbuch, S.52 (zuletzt aufgerufen am 25.06.24)](https://wizepanel.de/downloads/WizePanel_Manual_EN.pdf)
[^9]: [Roomz Sensor (zuletzt aufgerufen am 25.06.24)](https://roomz.io/roomz_sensor/?lang=de)
[^10]:[myRoomz App (zuletzt aufgerufen am 25.06.24)](https://roomz.io/myroomz-arbeitsplatzmanagement/?lang=de)

