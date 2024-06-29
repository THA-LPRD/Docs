# Firmware

**Ahmet Emirhan Göktas**

## Entwicklungsumgebung

[PlatformIO](PraktischeUTheoretischeGrund.md#platformio) wurde als Entwicklungsumgebung für die LPRD-Firmware ausgewählt. Da die [Arduino IDE](PraktischeUTheoretischeGrund.md#arduino) für die Komplexität des Projekts nicht geeignet ist, wird [PlatformIO](PraktischeUTheoretischeGrund.md#platformio) als fortschrittlichere Alternative verwendet.

### PlatformIO mit Visual Studio Code

Wie im Abschnitt [Grundlagen](PraktischeUTheoretischeGrund.md#firmwarebibliotheken) erwähnt, kann [PlatformIO](PraktischeUTheoretischeGrund.md#platformio) mit verschiedenen IDEs verwendet werden. Die meisten unserer Teammitglieder nutzen [Visual Studio Code](https://code.visualstudio.com/) als ihre IDE. Daher möchten wir zeigen, wie man [PlatformIO](PraktischeUTheoretischeGrund.md#platformio) für [Visual Studio Code](https://code.visualstudio.com/) einrichtet.

#### Installation

1. Installieren Sie [Visual Studio Code](https://code.visualstudio.com/).
2. Öffnen Sie das Erweiterungspanel entweder über die Seitenleiste oder durch Drücken von ++ctrl+shift+x++ und geben Sie `PlatformIO IDE` ein.
3. Klicken Sie auf die `Install`, um die PlatformIO IDE-Erweiterung zu installieren.
4. Nachdem die Erweiterung installiert ist, können Sie die PlatformIO-Seitenleiste öffnen, indem Sie auf das PlatformIO-Symbol in der Seitenleiste klicken. Dies kann einige Minuten dauern, da PlatformIO das Backend herunterlädt und die Umgebung einrichtet.

Figure: Abbildung 8.1: PlatformIO-Erweiterung in Visual Studio { #_abb8_1 }

![](img/PlatformIO-VSCode-Extension.webp){ width=60% }

#### Projekt erstellen

1. Öffnen Sie die VS Code-Befehlszeile durch Drücken von ++ctrl+shift+p++ und geben Sie `>PlatformIO:PlatformIO Home` ein.
2. Drücken Sie `Enter`, um die PlatformIO-Startseite zu öffnen.
3. Klicken Sie auf der linken Seite der PlatformIO-Startseite auf die Registerkarte `Projects`.
4. Klicken Sie auf die `New Project`.
5. Wählen Sie das Board, das Sie verwenden. In unserem Fall verwenden wir das Board `Seeed Studio XIAO ESP32S3`.
6. Wählen Sie das Framework. In unserem Fall verwenden wir das `Arduino`-Framework.
7. Drücken Sie abschließend die `Finish`, um das Projekt zu erstellen.

Figure: Abbildung 8.2: Neues PlatformIO-Projekt erstellen { #_abb8_2 }

![](img/PlatformIO-New-Project.webp){ width=60% }

#### Mikrocontroller flashen

1. Verbinden Sie den Mikrocontroller mit Ihrem Computer.
2. Öffnen Sie die PlatformIO-Seitenleiste, indem Sie auf das PlatformIO-Symbol in der Seitenleiste klicken.
3. Klicken Sie auf die Projektumgebung im Abschnitt `Project Tasks`.
4. Klicken Sie auf die `Upload` im Abschnitt `General`, um die Firmware auf den Mikrocontroller zu flashen.
5. Die `Upload File System Image` Taste im Abschnitt `Platform` kann verwendet werden, um das Dateisystem-Image auf den Mikrocontroller hochzuladen.

Figure: Abbildung 8.3: Firmware auf den Mikrocontroller hochladen { #_abb8_3 }

![](img/PlatformIO-Flashing.webp)

### Versionskontrolle

In diesem Projekt haben wir [git](https://git-scm.com/) als unser Versionskontrollsystem verwendet und dem Git-Flow-Modell gefolgt. Das Git-Flow-Modell ist ein von Vincent Driessen erstelltes Branching model für git. Es ist eine Reihe von Regeln, die verwendet werden, um die Verzweigungen in einem git-Repository zu verwalten. Die haupt Branches sind `master` und `dev`. Der `master`-Branch wird für produktionsbereiten Code verwendet, während der `dev`-Branch für Code verwendet wird, der sich in der Entwicklung befindet. Der `dev`-Branch wird abgezweigt, um Feature-Branches zu erstellen. Sobald das Feature abgeschlossen ist, wird der Feature-Branch wieder in den `dev`-Branch integriert. Wenn der Code im `dev`-Branch bereit für die Produktion ist, wird er in den `master`-Branch integriert.

## Anforderungen

Wie bereits erwähnt, muss das LPRD bestimmte Anforderungen erfüllen. Diese Anforderungen bilden die Grundlage für die Firmware-Entwicklung. Die folgenden Anforderungen ergeben sich aus den Hardwareanforderungen:

### Drahtlose Kommunikation

Das Gerät soll drahtlos gesteuert werden, um eine einfache Installation und Konfiguration zu ermöglichen und die Steuerung des Geräts von einem zentralen Server aus zu erlauben. Es gibt zwei Möglichkeiten, dies zu erreichen:

- Verbindung mit einem bestehenden drahtlosen Netzwerk.
- Erstellung eines eigenen drahtlosen Netzwerks.

### Dateisystem

Das Displaymodul benötigt einen nichtflüchtigen Speicher, um die angezeigten Bilder sowie die Konfigurationen wie Netzwerkeinstellungen und Betriebsmodi zu speichern. Der ESP32-S3-Mikrocontroller bietet 8 MB Flash-Speicher, der mit dem LittleFS-Dateisystem genutzt wird.

### Konfiguration

Das Displaymodul ist flexibel gestaltet und hat keine fest kodierte Konfiguration in der Firmware. Die Konfiguration kann vom Benutzer geändert werden und umfasst:

- WLAN-Netzwerkkonfiguration (SSID, Passwort)
- E-Paper-Display-Konfiguration (Modell)
- Betriebsmodus (Standalone, Netzwerk, Server)
- Serverkonfiguration (URL)
- Log-Level (für Debugging)
- HTTP-Server-Konfiguration (HTTP, HTTPS)
- Authentifizierung (Benutzername, Passwort)

### Betriebsmodi

Das Displaymodul unterstützt verschiedene Betriebsmodi:

- **Standalone**: Funktioniert ohne ein bestehendes WLAN-Netzwerk.
- **Netzwerk**: Funktioniert mit einem bestehenden WLAN-Netzwerk.
- **Server**: Wird von einem zentralen Server gesteuert.
- **Default**: Der Standardmodus bei der ersten Inbetriebnahme oder bei nicht behebbaren Fehlern. Dieser Modus entspricht dem Standalone-Modus mit fest kodierten Einstellungen.

### SPI-Schnittstelle

Das E-Paper-Display ist über die SPI-Schnittstelle mit dem ESP32-S3-Mikrocontroller verbunden. Diese Schnittstelle wird zur Kommunikation und Anzeige von Bildern auf dem E-Paper-Display genutzt und muss entsprechend initialisiert und konfiguriert werden.

### Niedriger Energieverbrauch

Die Akkulaufzeit ist ein wichtiger Faktor. Das Displaymodul muss in den Schlafmodus gehen können, wenn es nicht in Gebrauch ist, und bei Bedarf wieder aufwachen, um Energie zu sparen und die Akkulaufzeit zu verlängern.

## Klassendiagramm

figure: Abbildung 8.4: Klassendiagramm der Application { #_abb8_4 }

![](img/ClassDiagramApp.webp)

figure: Abbildung 8.5: Klassendiagramm der Systemansteuerung { #_abb8_5 }

![](img/ClassDiagramMCU.webp)

figure: Abbildung 8.6: Klassendiagramm der E-Paper-Display-Library { #_abb8_6 }

![](img/ClassDiagramEPDL.webp)

## Application

Die Applikation ist der Hauptteil der Firmware. Sie ist verantwortlich für die Konfiguration des Displaymoduls, die drahtlose Kommunikation, die Betriebsmodi und die SPI-Schnittstelle. Die Applikation ist in verschiedene Klassen unterteilt, die jeweils für unterschiedliche Teile der Applikation verantwortlich sind. Diese sind:

- [`Application`](#applikation): Die Hauptklasse der Applikation. Sie ist eine Schnittstelle, die von den verschiedenen Betriebsmodi implementiert wird.
- [`AppStandalone`](#standalone-mode): Der Standalone-Betriebsmodus. Das Displaymodul funktioniert ohne ein bestehendes WLAN.
- [`AppNetwork`](#network-mode): Der Netzwerk-Betriebsmodus. Das Displaymodul funktioniert mit einem bestehenden WLAN.
- [`AppServer`](#server-mode): Der Server-Betriebsmodus. Das Displaymodul wird von einem zentralen Server gesteuert.
- [`AppDefault`](#default-mode): Der Standard-Betriebsmodus. Das Displaymodul befindet sich im Standardmodus, wenn es zum ersten Mal eingeschaltet wird oder wenn ein nicht behebbarer Fehler auftritt.
- `Log`: Ein Namensraum, der für das Loggen von Nachrichten auf den seriellen Port verantwortlich ist.
- `Config`: Ein Namensraum, der für die Konfiguration des Displaymoduls verantwortlich ist.

### Ablauf der Applikation

Die `Application`-Klasse ist die Hauptklasse der Anwendung. Der grundlegende Ablauf der Anwendung ist wie folgt:

1. Initialisierung des Dateisystems.
2. Lesen der Konfiguration aus dem Dateisystem.
3. Initialisierung des entsprechenden Modus.
4. Ausführen der Anwendung.

### Betriebsmodi

#### Standardmodus

In diesem Modus wird das WLAN im Access-Point-Modus initialisiert, um dem Benutzer die direkte Verbindung mit dem Gerät zu ermöglichen. Nachdem das WLAN initialisiert ist, wird der HTTP-Server gestartet. Die Standardseite ist die Einstellungsseite, wobei keine Endpunkte für den Bild-Upload enthalten sind.

Der Zweck dieses Modus besteht darin, dem Benutzer die Konfiguration des Geräts zu ermöglichen, unabhängig davon, ob etwas schiefgelaufen ist oder ein Werksreset durchgeführt wurde.

#### Standalone-Modus

In diesem Modus arbeitet das Gerät unabhängig von bestehenden Infrastrukturen. Es beginnt mit der Initialisierung des WLANs im Access-Point-Modus. Anschließend wird der HTTP-Server mit Endpunkten für alle Einstellungen sowie für den Bild-Upload initialisiert. Eine Callback-Funktion wird übergeben, die aufgerufen wird, wenn ein Bild hochgeladen wird, sodass das Bild auf dem E-Paper-Display angezeigt werden kann. Schließlich wird das E-Paper-Display initialisiert, um bereit zu sein, die Bilder anzuzeigen.

Nachdem all diese Schritte erfolgreich abgeschlossen sind, ist das Gerät einsatzbereit. Man verbindet sich mit dem WLAN-Netzwerk des Geräts und ruft die Weboberfläche unter `http://192.168.4.1/index.html` auf. Das Gerät bleibt wach, bis ein Bild hochgeladen wird. Nach dem Hochladen wird das Bild auf dem E-Paper-Display angezeigt und das Modul geht in den Tiefschlaf, um die Akkulaufzeit zu verlängern und den Stromverbrauch zu minimieren.

#### Netzwerkmodus

Dieser Modus bietet einfachen Zugriff auf das Gerät, indem es sich mit einem bestehenden WLAN-Netzwerk verbindet. Das Gerät stellt die Verbindung zum WLAN-Netzwerk her, indem es die in der Konfigurationsdatei gespeicherten Anmeldeinformationen verwendet. Nach der Herstellung der Verbindung wird der HTTP-Server genauso wie im [Standalone-Modus](#standalone-modus) initialisiert. Nachdem das Gerät im Netzwerk gefunden wurde, kann es über die IP-Adresse des Geräts ähnlich wie im [Standalone-Modus](#standalone-modus) aufgerufen werden.

Wenn während der Initialisierung ein Fehler auftritt, wie z. B. falsche WLAN-Anmeldeinformationen, die dazu führen, dass das Gerät nicht mehr erreichbar ist, wechselt das Gerät zurück in den [Standardmodus](#standardmodus), um dem Benutzer die Neukonfiguration des Geräts zu ermöglichen. Andernfalls bleibt die Routine dieselbe wie im [Standalone-Modus](#standalone-modus).

#### Servermodus
**Mario Wegmann**

In diesem Modus wird mit einem Webbrowser nicht direkt auf das Displaymodul selbst zugegriffen, stattdessen holt sich jedes Displaymodul die notwendigen Informationen von einem zentralen Linux Webserver ab. Beim Konfigurieren im Standard-Modus wird neben den Zugangsdaten vom bestehenden WLAN Netzwerk auch eine Server URL mit angegeben. Beim jedem Aufweckend aus dem Deep-sleep verbindet sich das Displaymodul dann mit dem bestehenden WLAN und versucht den Server über HTTP(S) zu erreichen. Als erstes wird überprüft ob das Displaymodul dem Server bekannt ist, falls dies noch nicht der Fall ist, dann ruft das Displaymodul eine API-Route auf, um sich selbst als neues Display zu registrieren. Falls das Display bereits dem Server bekannt ist wird die API-Route aufgerufen, um eine neue Darstellungs-Konfiguration anzufragen. In dieser Konfiguration meldet der Server dem Displaymodul, unter welcher URL das Displaymodul das aktuelle Asset heruntergeladen werden kann und wie lange dieses Asset angezeigt werden soll. Nach der erfolgreichen Kommunikation mit dem Server setzt das Displaymodul einen Wakeup Timer auf die Dauer der übergebenen Anzeigedauer und geht in den Deep-sleep Modus. 

### Konfiguration

Der `Config`-Namensraum ist für die Konfiguration des Moduls verantwortlich. Die Konfiguration wird in einer JSON-Datei im Dateisystem gespeichert. Beim Booten wird die `Load`-Methode verwendet, um die Konfiguration aus dem Dateisystem zu laden, sodass die Konfiguration direkt aus dem RAM verfügbar ist. Die `Save`-Methode kann dann verwendet werden, um die Konfiguration zurück in das Dateisystem zu speichern.

### Logging

Der `Log`-Namensraum ist für das Loggen von Nachrichten auf den seriellen Port verantwortlich. Das Log-Level kann in der Konfigurationsdatei festgelegt werden. Die Protokollstufe kann auf `TRACE`, `DEBUG`, `INFO`, `WARN`, `ERROR` oder `FATAL` eingestellt werden. Das Log-Level wird über die Konfigurationsdatei festgelegt und die Nachrichten werden nur geloggt, wenn die Protokollstufe auf eine Stufe eingestellt ist, die gleich oder höher ist als die Stufe der Nachricht.

## HTTP-Server


## Systemansteuerung

## E-Paper Display API
