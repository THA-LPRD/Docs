# Praktische und Theoretische Grundlagen

## Recherchierte Technologien (nur vergleiche / kapitel 5 auswahl argumentieren)

## Mikrocontroller

## Stromsparende Display Technologien

## Akku Technologien

## Funktechnologien

## Bildverarbeitung 

## Energiemanagement
**Mario Wegmann**

Computer verbrauchen auch ohne aktive Aufgabe Strom. Ohne spzeielle Anweisungen an den Computer wird der Stromverbrauch nicht gedrosselt, wodurch Energie verschwendet wird. Bei PCs fallen hierbei ACPI Sleep States ein, ACPI steht dabei für Advanced Configuration and Power Interface und ist ein offener Industriestandard für die Energieverwaltung bei Computern [MW_02](Quellenverzeichnis.md). Die sogenannten ACPI sleep states ermöglichen es dem Betriebssystem zu steuern, welche Komponenten gedrosselt oder gar komplett abgeschaltet werden, um den Stromverbrauch zu minimieren. Auch bei Mikrocontrollern gibt es mehere Mechamisem, womit der Stromverbrauch reduziert werden kann. Da ein geringer Stromverbrauch eines der wichtigsten Kriterien diese Projekts ist, werden hier beispielhaft die Sleep States eines ESP32 erläutert. 

### Einfaches Delay

Die einfachste Möglichkeit einen ESP32 Mikrocontroller keine konkrete Aufgabe zu geben, ist mit einem Delay. Die Funktion heißt in der Arduino IDE `Delay()` und lässt einen Parameter zu, welcher angiebt, wie viele Mikrosekunden der Mikrocontroller warten soll. In der ESP-IDF heißt die Funktion `vTaskDelay()`, hier kann auch ein Parameter für die Wartedauer übergeben werden. Der Parameter nimmt jedoch nicht Millisekunden, sondern Ticks an. Die Ticks sind abhängig von der Tick Frequenz, daher müssen die Millisekunden mit der Funktion `pdMSTOTICKS()` in Ticks umgewandelt werden. Während dem aktiven warten werden jedoch keine Komponenten aktiv abgeschaltet oder gedrosselt, lediglich der Prozessor läuft nicht auf Vollast. 

### Der Light-sleep Modus

Deutlich besser ist da schon der Light-sleep. Wird dieser Modus aktiviert, so werden die teilweise Clock-Signale der digitale Peripherie, der meisten Teile des RAMs und der CPUs ausgeschalten und die Versorgungsspannung reduziert, dieses Verfahren nennt sich Clock-Gating [MW_03](Quellenverzeichnis.md). Dadurch kann der Stromverbrauch deutlich reduziert werden, wie hoch die Reduktion ist, wird im Kapitel [7.9 Strommessung von Mikrocontroller und Display](Hardware.md#strommessung-von-mikrocontroller-und-display) gemessen. Beim ESP32 gibt es nun verschiede Wakeup Sources um den Light-sleep wieder zu beenden. Unter anderem sind folgende Wakeup Sources möglich: 

* Timer
* Touchpad
* GPIO
* ULP Coprocessor (Ultra Low Power)
* UART

Nach einem Wakeup Event wird der State wiederhergestellt und der Mikrocontroller arbeitet an der Stelle weiter, wo er durch den Light-sleep aufgehört hat. 

### Der Deep-sleep Modus

Noch mehr Stromeinsparung kann mit dem Deep-sleep realisiert werden. Dabei werden die oben genannten Komponenten nicht nur clock-gated, sondern komplett abgeschaltet, somit bleibt nur noch der RTC Controller und dessen Memory und der ULP Coprocessor aktiv. Viele der zuvor genannten Wakeup Sources können auch verwendet werden um den ESP32 aus dem Deep-sleep heraus aufzuwecken, ausnahmen sind hierbei jedoch die meisten GPIO Pins und UART. Des weiteren ist anzumerken, dass nach dem Aufwecken aus dem Deep-sleep der ESP32 kein State wiederhergestellt wird. Die Firmware fängt also von vorne an und auch Daten die während dem Deep-sleep nicht verloren gehen dürfen müssen separat in nicht-flüchtigen Speicher abgelegt werden. 

## Firmwarebibliotheken

## Webanwendungen
**Mario Wegmann**

Aufgrund den anforderungen und der komplexität von Websiten ist es nicht mehr praktikabel Inhalte komplett händisch in HTML, CSS und JavaScript zu erstellen. Zu groß und fehleranfällig ist die Wartung eines solchen manuel erstellten Konstrukts. Ein Beispiel hierfür wäre das erweiteren einer neuen Unterseite in der Menüleiste. Hier müsste jede andere Unterseite anegpasst werden, um die neue Unterseite von allen anderen Unterseiten aus zu erreichen. 

Stattdessen hat es sich etabliert für Websiten mit viel statischen Inhalt sogenannte Static Site Generators zu nutzen. Hierbei liegt der Fokus nur noch auf die Erstellung des eigentlichen Inhalts über eine simple Textdatei. Nach Fertigstellung des Inhalts erzeugt der Generator dann das restliche Gerüst der Website, so werden die Unterseiten generiert, das Navigationsmenü erstellt, Bilder optimiert und das Layout anhand des angegebenen Themes angewendet. 

Neben Websiten mit statischen Inhalten gibt es auch Websiten, dessen Inhalt dynamisch erstellt wird. In Social Media ist die Anzahl an Inhalten so enorm, das es nicht praktikabel wäre allen Personen die gleiche Timeline anzuzeigen. Stattdessenn wird pro Benutzer eine auf Ihn spezialisierte Timeline beim Aufruf generiert. 

Zuletzt gibt es auch Anwendungen die über den Webbrowser laufen und somit keine lokale Installation benötigen, ein Beispiel wäre hierfür die NextCloud, womit sich Dateien abspeichern, erstellen, ordnen und teilen lassen. Dank vieler Erweiterungen 

Die letzen beiden genannten Kategorien erfordern viele Komponenten die zusammenarbeiten müssen um den Benutzer eine performante und benutzerfreundliche Erfahrung zu ermöglichen. Daher haben sich mehr und mehr verschiedene Technologien im Web entwickelt, die mit unterschiedlsichen Herangehensweisen versuchen die Anfoderungen zu erfüllen. 


### Webtechnologien

Moderne Webbrowser haben sich auf drei Programmiersprachen geeinigt um Websiten anzuzeigen. HTML beschreibt den Inhalt an sich, CSS beschreibt das aussehen und layout und JavaScript sorgt für die interaktivität im Browser beim Benutzer. Wie das Ergebnis in diesen drei Sprachen generiert wird bleibt dem Webserver überlassen. Prinzipiell lässt sich fast jede Programmiersprache verwenden um Websitecode zu erzeugen, beliebt sind jedoch PHP, Python, Ruby, C# und JavaScript (Node.JS) [MW_04](Quellenverzeichnis.md). 

Für die realisierung werden Frameworks genutzt, ähnlich wie bei Static Site Generators, unterstützen Frameworks bei der realisierung von Websiten, indem es wiederkehrende Aufgaben vereinfacht und die Wiederverwendung von Code fördert. Durch die Abstraktion und Strukturierung von Code sowie die Objektorientierung der Daten wird die Entwicklungszeit verkürzt und die Wartbarkeit großer Anwendungen erheblich verbessert. NextCloud verwendet beispielsweise das PHP Framework Symfony [MW_05](Quellenverzeichnis.md)


DOM Manipulation
EMS
TypeScript
React
Postgress und MySQL