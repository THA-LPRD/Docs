# Hardware

## Auswahl des Mikrocontrollers

## Auswahl der Displaytechnologie

## Zusammenbau der Akkupacks
**Mario Wegmann**
//TODO
Warum Nickelband?
Grafiken Aufbau Akkuzellen
Quellen
Nickelband
Punktverschweißen

### Konzeptioneller Aufbau

Bei der Auswahl der Akkukomponenten wurde die Entscheidung getroffen mehere Lithium-Ionen Zellen zu verwenden. Da die Kapazität des Akkupackts vergrößert werden, die Batteriespannung jedoch weiterhin zwischen 2,5 V und 4,2 V liegen soll, werden die beiden Lithium-Ionen Zellen parallel mit einander verbunden. Dadurch verdoppelt sich die Kapazität, während die Spannung gleich bleibt. Zudem wird der gemeinsame Pluspol mit dem Plus des Battery Management System verbunden und ebenso mit dem Minuspolen verfahren. Zum verbinden von den Akkuzellen untereinander und mit dem BMS eignet sich ein Nickelband, welches auch als Hiluminband bekannt ist.

### Battery Management System anschließen
Als erstes sollte das BMS verdrahtet werden. In diesem Projekt wurde sich dafür entschieden, dass das Akkupack über einen Stecker mit dem Mainboard verbunden werden kann und somit modular ist. Somit wurde an den Ausgängen des BMS ein 2 Pin JST-X2 Stecker gelötet. Hierbei wurde sich im Team intern darauf geeinigt, das der Pluspol rechts ist, wenn von der Drahtseite auf den Stecker geschaut wird und die Nase des Steckers nach oben zeigt. An den Pads für die Batteriepole wurde das Nickelband ebenso verlötet. 

### Vorbereiten der Lithium-Ionen Zellen
Für einen sicheren Umgang mit Lithium-Ionen Zellen ist es wichtig mehere Dinge zu beachten, bevor mehere Zellen miteinander verbunden werden können. 
Bereits beim beschaffen von den Zellen sollte darauf geachtet werden das identische Modell und eine gleiche Charge zu verwenden. 
Zudem sollten Zellen, die verbunden werden sollen, möglichst gleich alt und auch gleich belastet werden oder im optimalfall komplett neu sein. 
Zuletzt sollte vor dem Verbinden darauf geachtet werden, dass die Zellen die gleiche Zellspannung aufweisen um einen schlagartigen Ladungswechsel beim verbinden vorzubeugen.

Nachdem die einzelnen Zellen vorbereitet waren, wurden diese in die Plastikhalter eingelegt. Diese Plastikabstandshalter ergeben zusammen mit den Zellen ein stabiles Gesamtsytem und halten die Zellen davor ab sich direkt zu berühren.  

### Punktschweißverfahren bei Lithium-Ionen Zellen
Lithium-Ionen Zellen sind wärmeempfindlich und daher ist Weichlöten kein geeignetes Verfahren um die Zellen mit dem Hiluminband zu verbinden, stattdessen eignet sich das Punktschweißverfahren. Hierbei wird das Nickelband an einem Pol einer Zelle gepresst und dann die zwei Elektroden des Punktschweißgerätes auf das Nickelband gedrückt. Durch die beiden Elektroden fließen //TODO Ampere bei Volt, dieser hohe Strom führt zu einem Schweißpunkt, welcher das Nickelband und den Pol fest verbindet, jedoch aufgrund der kurzen Dauer des Prozesses von //TODO Sekunden kaum eine Wärmebelastung für die Akkuzelle darstellt. Das Nickelband, welches bereits mit dem BMS verbunden ist, wurde um ein weiteres Nckelband orthogonal dazu erweitert. Dadurch ergibt sich eine Nickelverbindung in T-Form. An beiden offenen Enden wurde jeweils ein Batteriepol angeschlossen. Dies wurde für die andere Polseite wiederholt. 

### Isolieren des Akkupacks
Abschlißend wurde Kapton Klebeband verwendet um das Akkupack mit einer isolierenden Schicht zu umhüllen. Dadurch wird vermieden, dass unkontrolliert die Batteriepole mit anderen leitfähigen Materialen in berührung kommen und sämtlicher Strom über das BMS geleitet wird. 

## Auswahl der PCB-Komponenten

## Platinen Design

## Zusammenbau der PCBs

## Gehäuse

## Zusammenbau des Displaymoduls

## Strommessung von Mikrocontroller und Display

## ADC Messung