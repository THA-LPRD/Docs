# Marktanalyse aktueller Trends und Technologien
**Julia Reuter**

Die Motivation des Projektteams lag bei erster Betrachtung des Projektes Low-Power Raumanzeige für die THA hauptsächlich in der Steigerung der Effizienz und des eigenen Komforts, wodurch das Projekt eher als Nischenprodukt für den internen Gebrauch angesehen wurde.
Diese Einstellung änderte sich jedoch schnell nach einiger Recherche.

Nicht nur ist der potenzielle Markt für eine Low-Power Raumanzeige aufgrund der vielfältigen Einsatzgebiete in Büroräumen, Krankenhäusern, Bildungseinrichtungen, usw. relativ groß, sondern auch im Hinblick auf das Thema Umwelt, Nachhaltigkeit und Digitalisierung, lange nicht ausgeschöpft.
So wird beispielsweise eine effiziente Nutzung von Räumen durch klare Erkennbarkeit der Belegung ermöglicht und durch intelligente Verwaltung können sogar unnötige Heiz- und Beleuchtungskosten reduziert werden, wenn der Raum gerade nicht genutzt wird. Darüber hinaus kann auf papierbasierte Stundenpläne und Türschilder verzichtet werden, was nicht nur den damit verbundenen personellen Verwaltungsaufwand zur Instandhaltung deutlich verringert, sondern auch die bislang verwendeten Ressourcen minimiert.

All dieses Aspekte sind Merkmale für ein durchaus zukunfttaugliches Produkt und gerade deshalb gibt es bereits einige Unternehmen, die dieses Potenzial erkannt und entsprechende Produkte entwickelt haben.

Im Folgenden werden nun vier hauptsächlich deutsche Unternehmen analysiert, welche als Inspiration für die eigene Raumanzeige dienten und durch ihr breites Spektrum dem Team zu neuen Ansätzen und Ideen verhalfen.

## Übersicht einiger Konkurrenzprodukte

Bei den ausgewählten Unternehmen und Produkten handelt es sich um:

- **Wizepanel** der Firma Wilke Technology in Aachen [[JR_01]](Quellenverzeichnis.md#jr_01)
- **Digitales Türschild** der Firma digitalSIGNAGE in Hamburg [[JR_02]](Quellenverzeichnis.md#jr_02)
- **Display** der Firma ROOMZ in Freiburg (Schweiz) [[JR_03]](Quellenverzeichnis.md#jr_03)
- **Touchscreen-Display** der Firma Beetronics in Düsseldorf [[JR_04]](Quellenverzeichnis.md#jr_04)

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
| **Wizepanel [[JR_05]](Quellenverzeichnis.md#jr_05)**          | E-Paper                | Schwarz-Weiß, 16 Graustufen | 868 MHz Ultra Low Power Funk, eigene Funksender | 10 x AA-Lithium-Primärzellen, bis zu 20 Jahre | Zentrale Serverkomponente: Inhaltsübertragung und Geräteverwaltung | Bereits in den Server integrierte Adapter für MS Exchange, iCal/ICS, Google Calendars, Excel,... Auch WebUntis wird unterstützt [[JR_08]](Quellenverzeichnis.md#jr_08)|
| **Digitales Türschild [[JR_06]](Quellenverzeichnis.md#jr_06)**| Touch-Screen (kein E-Paper) | Farbe                |  Ethernet, NFC-Option verfügbar               | Power over Ethernet (PoE) → Kabelanschluss nötig | Keine Angabe                           | LEDs rund um Display (rot, gelb, grün) zur Hervorhebung der Raumbelegung, Sofortbuchung über Touch/NFC      |
| **ROOMZ [[JR_03]](Quellenverzeichnis.md#jr_03)**              | E-Paper                | Schwarz-Weiß         | WLAN                                        | 8000mAh, 4 Jahre                      | MyRoomz-App zur Buchung einzelner definierter Arbeitsbereiche [[JR_10]](Quellenverzeichnis.md#jr_10) | MyRoomz-App bietet Lageplanansicht des Gebäudes mit Übersicht aller Räume mit Markierung ob sie belegt sind oder nicht [[JR_10]](Quellenverzeichnis.md#jr_10), ROOMZ Sensor zur Vermeidung von Ghost-Meetings [[JR_09]](Quellenverzeichnis.md#jr_09), Sofortbuchung über Touchleiste am Gehäuse |
| **Beetronics [[JR_07]](Quellenverzeichnis.md#jr_07)**         | High Brightness Full HD Touchscreen | Farbe                | Display Port, HDMI, VGA, USB-C, Unterstützung aller gängigen Betriebssysteme | Netzteil (d.h. Stromanschluss) denn braucht 12.7W (Betrieb)/0.4W (Standby) | Einfaches Plug-and-Play, sonst eigener Treiber für verschiedene Betriebssysteme verfügbar | Keine spezifischen Features angegeben, aber allgemein sehr vielfältig universell einsetzbar                                                                       |

## Auswertung der Rechercheergebnisse

### Vor- und Nachteile der einzelnen Produkte

Table: Vor-und Nachteile der vier Displayprodukte { #_tab_3.2 }

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
Denn auch wenn es sich um ein E-Paper Display handelt, besteht die Möglichkeit eine gewisse Benutzerinteraktion für zum Beispiel spontane Raumbuchung zu integrieren, die energiesparend und auch ohne Touchfunktion umsetzbar ist. Auch ein E-Paper-Display mit Farbunterstützung würde dazu beitragen das eher schlichtes Produkt für den Kunden optisch ansprechender zu gestalten und sich von der Masse abzuheben.

Das zentrale Alleinstellungsmerkmal ist jedoch das Entwickeln eines möglichst generischen Konzeptes, das sehr flexibel einsetzbar ist.
Denn eine Einschränkung der obigen Systeme ist, dass alle zentral über eine Serverkomponente gesteuert werden und teilweise sogar eigene Funkverteiler brauchen.
Dies ist für den Benutzer mit viel Aufwand und Kosten verbunden und lohnt sich nur für sehr große Organisationen. 

Zudem ist man stets von einer externen Softwarekomponente abhängig, denn die Display Ansteuerungsschnittstelle wird ebenfalls vom Hersteller in Form von einem Server (vgl. Wizepanel) oder einer App (vgl. ROOMZ) geliefert. So ist das System bei Ausfall oder Fehlverhalten nicht mehr einsatzfähig, bis das Problem durch eine externe Partie, sprich dem Hersteller behoben wurde.

Genau hier setzt das Projektteam an und entwickelt ein Konzept, indem die Raumanzeige nicht zwingend eine zusätzliche externe Infrastruktur benötigt. 
Es soll ein Option für eine Standalone-Funktionalität geben, sodass das Low-Power Display sowohl völlig unabhängig von jeglicher zusätzlicher Soft- und Hardware ist und autark funkionieren kann.
Gleichzeitig besteht weiterhin die Möglichkeit eine zentrale Verwaltungskomponente zu integrieren, um auch mehrere Displays verwalten zu können. 
Diese Flexibilität gekoppelt mit der Prämisse, das System Open-Source zu gestalten, sorgt für eine hohe Konkurrenzfähigkeit auf dem Markt. 

Der Kunde kann somit nach Belieben das System erweitern und anpassen, wodurch die Low-Power Raumanzeige nicht nur für die Hochschule attraktiv ist sondern auch in kleinern Kreisen und sogar im privaten Gebrauch eingesetzt werden kann.
