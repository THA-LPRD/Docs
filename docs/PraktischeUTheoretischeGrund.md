# Praktische und Theoretische Grundlagen

## Recherchierte Technologien (nur vergleiche / kapitel 5 auswahl argumentieren)

## Mikrocontroller

## Stromsparende Display Technologien

## Akku Technologien

## Funktechnologien

## Bildverarbeitung

## Energiemanagement

## Firmwarebibliotheken

## Webframeworks

## Gehäuseentwicklung 
_Jannis Gröger_


Um das Gehäuse für ein elektronisches Gerät zu entwickeln, müssen zunächst die Anforderung festgelegt werden. Hierbei kann man in zwischen funktionalen und ästhtischen und ergonomischen Anforderungen unterscheiden. Grundsätzlich soll ein Gehäuse die Komponenten und die Elektronik nicht nur vor äußeren Einflüssen wie Staub, Schmutz oder mechanischen Stößen schützen, sondern trägt auch zur Wärmeableitung bei und spielt eine wichtige Rolle bei der Benutzung des Geräts. Im Folgenden werden die Grundlagen und die essentiellen Überlegungen bei der Entwicklung eines Gehäuses behandelt.

### Funktionale Anforderungen

Die Hauptfunktion eines Gehäuses ist der Schutz der einzelnen Bauteile, wobei hier auf verschiedene Faktoren zu achten ist. Zum einen muss das Gehäuse stabil genug sein, um die internen Komponenten vor mechanischen Einflüssen wie Stöße oder Druck zu schützen. Das Material muss dementsprechend passend ausgewählt werden, wobei auch die Geometrie des Gehäuses berücksichtigt werden muss. Häufig verwendete Materialien bei Elektrogeräten sind Kunststoffe oder Metalle wie bspw Aluminium. [[JG_01]](Quellenverzeichnis.md#jg_01)

Zudem ist das Gehäuse dazu da, die Elektronik darin vor so äußeren Einflüssen wie beispielsweise Staub oder Wasser zu bewahren. Bei der Frage, vor welchen sogenannten Umwelteinflüssen ein Gehäuse schützt, hilft die Einteilung in IP-Schutzklassen, wobei das IP für International Protection steht und die verschiedenen Klassen nach der DIN 60529 spezifiziert sind. Die Bezeichnung der Klassen besteht hierbei aus zwei Kennziffern nach der IP Abkürzung: Die erste Ziffer macht erkenntlich, gegen welche Arten von Berührung und Fremdkörpern das Gehäuse schützt, während die zweite Ziffer den Schutz gegen Wasser benennt. Eine Gehäuse mit IP68 Spezifikation ist beispielsweise vollständig gegen Staubeintritt und vor andauerndem Untertauchen geschützt. Eine solche Zertifizierung kann jedoch nur durch bestimmte Instititionen ausgestellt werden. [[JG_02]](Quellenverzeichnis.md#jg_02)

Ein weitere Funktion, der bei der Entwicklung des Gehäuses berücksichtigt werden muss, ist die Wärmeregulation, da die Elektronik sowohl vor Überhitzung, als auch vor zu starker Unterkühlung geschützt werden muss. Da elektronische Komponenten selbst Wärme erzeugen, spielt die Wärmeableitung eine größere Rolle, als der Schutz vor zu geringen Temperaturen. Diese kann durch Einsatz von Lüftern oder Kühlkörpern oder Einbau von Lüftungsschlitzen und die damit verbundene Konvektion bewerkstelligt werden. [[JG_02]](Quellenverzeichnis.md#jg_02)

Eine letzte funktionale Anforderung an das Gehäuse ist die elektromagnetische Verträglichkeit. Darunter versteht man, dass elektronische Geräte so aufgebaut sind, dass sie vor elektromagnetischer Störungen anderer Geräte geschützt sind und ihre eigenen elektromagnetischen Felder auf ein Minimum reduzieren, um selbst nicht andere Geräte zu stören. Dies kann durch die verwendung leitfähiger Materialien und speziellen Dichtungen erreicht werden. [[JG_02]](Quellenverzeichnis.md#jg_02)

### Ästhetische und ergonomische Anforderungen

Neben der Funktionalität stellen auch Ästhetik und Ergonomie gewisse Ansprüche an ein Gehäuse. Bei der Bedienung eines elektronischen Gerätes steht die Benutzerfreundlichkeit im Vordergrund, die bei tragbaren Geräten beispielsweise durch ein geringes Gewicht beeinflusst wird, wohingegen bei stationären Geräten eher auf Zugänglichkeit der Bedienelemente und Anschlüsse geachtet werden sollte. Des Weiteren beeinflusst das Design die Wahrnehmung und das Erscheinungsbild des Geräts, was maßgeblich zur Nutzung und Akzeptanz des Geräts beim Verbraucher beiträgt.  

### Auswahl des Materials und der Fertigungstechnik

Bei der Auswahl des Materials sind die oben genannten Aspekte von großer Bedeutung, da das verschiedene Materialen andere Eigenschaften besitzen und dementsprechend nicht jedes Material die gleichen Anforderungen erfüllt. Abhängig von der Materialauswahl ist im nöchsten Schritt dann die Auswahl der Fertigungstechnik, wobei hier zusätzlich auf die Anforderungen an die Geometrie des Gehäuses, die anzufertigende Stückzahl und der Material- sowie der Fertigungspreis geachtet werden muss.

### Design und Verfahren des Rapid Prototyping 

Sind Material und Fertigungstechnik gewählt, kann mit dem eigentlichen Design des Gehäuses begonnen werden. Heutzutage wird das Design häufig durch CAD-Software (computer-aided design Software) unterstützt, was Gehäuseentwicklern und -herstellern ermöglicht, ein präzises 3D-Modell des des gewünschten Produkts zu Erstellen. Durch Finite-Elemente-Modellierung, kurz FEM,  können Simulationen zum Testen der mechanischen oder thermischen Eigenschaften verwendet werden.[[JG_03]](Quellenverzeichnis.md#jg_03)

Nach dem Design folgt dann die Fertigung eines oder mehrerer Prototypen, die auf gewünschte Eigenschaften getestet werden, um eventuelle Schwachstellen auszumachen und Verbesserungen am Design vornehmen zu können. Hierbei werden immer häufiger Verfahren des Rapid Prototyping, im Folgenden auch RPT genannt, verwendet, was das "Erstellen von Prototypen aus einfach verarbeitbaren Materialien" [[JG_03]](Quellenverzeichnis.md#jg_03) bezeichnet. Hierbei wird das 3D-Modell aus der CAD-Software in ein "trianguliertes Oberflächenmodell überführt" [[JG_03]](Quellenverzeichnis.md#jg_03) und anschließend in einzelne Schichten mit einer festgelegten Dicke zerlegt. In unterschiedlichen Verfahren, von denen einige im Folgenden genannt werden, werden diese Schichten dann wieder zusammengefügt, wodurch ein Prototyp entsteht. [[JG_03]](Quellenverzeichnis.md#jg_03)

- Das Stereolithografie-Verfahren (STL-Verfahren) ist ein RPT-Verfahren, bei dem mit einem Laser in einem Bad aus "polymere[r] Flüssigkeit die Konturen der Scheiben des Modells schichtweise [...] nachgefahren [...] werden"[[JG_03]](Quellenverzeichnis.md#jg_03), wodurch ein räumliches Modell entsteht. 
- Beim Laminated Object Manufacturing Verfahren (LOM-Verfahren) dagegen, fährt der Laser die Konturen auf Papier nach, das die vorher festgelegte Dicke aufweist. Diese Papierschichten werden dann mittels eines "Schmelzkleber[s] aufeinander geklebt" [[JG_03]](Quellenverzeichnis.md#jg_03). Das entstehende Modell kann dann ähnlich "wie Holz nachbearbeitet werden" [[JG_03]](Quellenverzeichnis.md#jg_03).
- Das Fused Deposition Modelling-Verfahren (FDM-Verfahren) erstellt ein Prototyp, indem ein Kunststofffaden durch eine beheizbare Düse auf einer Plattform ausgelegt wird. Diese Plattform lässt sich dabei frei im Raum bewegen und der Durchmesser des Fadens entsricht dabei der vorher festgelegten Schichtdicke. [[JG_03]](Quellenverzeichnis.md#jg_03)
- Ein weiteres Verfahren ist das Solidier-Verfahren, auch Solid Ground Verfahren oder kurz SGC-Verfahren genannt. Das Modell entsteht hierbei aus mehreren dünnen Fotopolymerschichten, wovon jede einzelne "mit einer fotografischen Maskentechnik unter UV-Licht aushärtet" [[JG_03]](Quellenverzeichnis.md#jg_03). Um das fertige Modell herum wird ein Wachskörper gebildet, wodurch Überhänge nicht mit Stützen fixiert werden müssen. [[JG_03]](Quellenverzeichnis.md#jg_03)
- Auch das Selective Laser Sintering ist ein RPT-Verfahren, bei dem die einzelnen Schichten aus pulverförmigen Material mit einem Laser an gewollten Stellen geschmolzen wird. Durch schichtweises Herunterfahren der Fläche, worauf sich die unterste Pulverschicht befindet, liegt das fertige Modell dann in einem Pulverbett. [[JG_03]](Quellenverzeichnis.md#jg_03)
- Das 3D-Printing-Verfahren nutzt auch ein Schicht Pulver, wobei hier das Material mithilfe eines Binders verbunden wird. Auch hier wird das Modell an der obersten Schicht aufgebaut und der fertige Prototyp liegt in einem Pulverbett. [[JG_03]](Quellenverzeichnis.md#jg_03)

Die einzelnen RPT-Verfahren unterscheiden sich in den möglichen Materialien, der Genauigkeit der Modelle, der Qualität der Oberfläche und der verbundene Aufwand für die Nachbearbeitung. Diese Unterschiede sind der Abbildung [](#_JG_01) zu entnehmen.

Figure: Eigenschaften der verschiedenen Rapid-Prototyping-Verfahren [[JG_03]](Quellenverzeichnis.md#jg_03) { #_JG_01 }

![](img/rpt_unterschiede.png){width=80%}

Nach dem Prototyping und ausführlichen Testen, kann das überzeugende Modell schließlich in Serienproduktion übergehen womit die Entwicklung des Gehäuses ebenfalls abgeschlossen ist.