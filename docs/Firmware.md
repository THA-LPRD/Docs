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

- [`Application`](#application): Die Hauptklasse der Applikation. Sie ist eine Schnittstelle, die von den verschiedenen Betriebsmodi implementiert wird.
- [`AppStandalone`](#standalone-modus): Der Standalone-Betriebsmodus. Das Displaymodul funktioniert ohne ein bestehendes WLAN.
- [`AppNetwork`](#netzwerkmodus): Der Netzwerk-Betriebsmodus. Das Displaymodul funktioniert mit einem bestehenden WLAN.
- [`AppServer`](#servermodus): Der Server-Betriebsmodus. Das Displaymodul wird von einem zentralen Server gesteuert.
- [`AppDefault`](#standardmodus): Der Standard-Betriebsmodus. Das Displaymodul befindet sich im Standardmodus, wenn es zum ersten Mal eingeschaltet wird oder wenn ein nicht behebbarer Fehler auftritt.
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

The HTTP-Server is responsible for handling incoming HTTP requests. The server is implemented using the [`PsychicHttp`](https://github.com/hoeken/PsychicHttp) library, which is a lightweight and easy-to-use HTTP server library for the ESP32. We are using fallowing features from the library:

- HTTP requests such as GET and POST with file upload support
- Basic authentication
- HTTPS support

### HTTP Requests

HTTP defines methods to indicate the desired action to be performed for a given resource. The methode names are case-sensitive and must be written in uppercase unlike the header names. These methods can be safe meaning they won't change anything on the server or idempotent meaning they can be called multiple times and the result will be the same, and finally they can be cacheable meaning the response can be stored and reused later.

#### Get Request

The GET method requests a representation of the specified resource. Requests using GET should only retrieve data and should have no other effect on the data. For example when entered to a website the browser sends a GET request to the server to get the HTML file of the website.

The request [below](#__codelineno-0-1) is a simple GET request to get the index.html file from the server. This should return the main page of the website.

```http
GET /index.html HTTP/1.1
Host: 192.168.4.1
```

[Another simple GET request](#__codelineno-1-1) to get the current configuration of the device, which should return in plain text the operating mode of the device such as `Standalone`, `Network`, or `Server`.

```http
GET /api/v1/GetOpMode HTTP/1.1
Host: 192.168.4.1
```

Currently, the server has fallowing endpoints:

<ul style="list-style-type: none; padding: 0;">
    <li style="margin-left: -5px;">
        <div style="background-color: var(--md-code-bg-color); padding: 10px; border-radius: 5px; color: var(--md-code-fg-color);">
            <strong style="color: var(--md-code-hl-keyword-color);">GET
                <code>/api/v1/GetDisplayModule</code></strong><br>
            <p style="margin: 5px 0;">Returns the attached E-Paper display model.</p>
            <p style="margin: 5px 0;"><strong>Possible return values:</strong></p>
            <ul style="margin-left: 20px;">
                <li><code style="color: var(--md-code-hl-string-color);">WS_7IN3G</code></li>
                <li><code style="color: var(--md-code-hl-string-color);">WS_9IN7</code></li>
            </ul>
        </div>
    </li>
    <li style="margin-left: -5px;">
        <div style="background-color: var(--md-code-bg-color); padding: 10px; border-radius: 5px; color: var(--md-code-fg-color);">
            <strong style="color: var(--md-code-hl-keyword-color);">GET <code>/api/v1/GetOpMode</code></strong><br>
            <p style="margin: 5px 0;">Returns the current operating mode of the device.</p>
            <p style="margin: 5px 0;"><strong>Possible return values:</strong></p>
            <ul style="margin-left: 20px;">
                <li><code style="color: var(--md-code-hl-string-color);">Standalone</code></li>
                <li><code style="color: var(--md-code-hl-string-color);">Network</code></li>
                <li><code style="color: var(--md-code-hl-string-color);">Server</code></li>
            </ul>
        </div>
    </li>
    <li style="margin-left: -5px;">
        <div style="background-color: var(--md-code-bg-color); padding: 10px; border-radius: 5px; color: var(--md-code-fg-color);">
            <strong style="color: var(--md-code-hl-keyword-color);">GET <code>/api/v1/GetDisplayWidth</code></strong><br>
            <p style="margin: 5px 0;">Returns the width of the attached E-Paper display in pixels.</p>
            <p style="margin: 5px 0;"><strong>Possible return values:</strong></p>
            <ul style="margin-left: 20px;">
                <li><code style="color: var(--md-code-hl-string-color);">Positive integer</code></li>
            </ul>
        </div>
    </li>
    <li style="margin-left: -5px;">
        <div style="background-color: var(--md-code-bg-color); padding: 10px; border-radius: 5px; color: var(--md-code-fg-color);">
            <strong style="color: var(--md-code-hl-keyword-color);">GET <code>/api/v1/GetDisplayHeight</code></strong><br>
            <p style="margin: 5px 0;">Returns the height of the attached E-Paper display in pixels.</p>
            <p style="margin: 5px 0;"><strong>Possible return values:</strong></p>
            <ul style="margin-left: 20px;">
                <li><code style="color: var(--md-code-hl-string-color);">Positive integer</code></li>
            </ul>
        </div>
    </li>
    <li style="margin-left: -5px;">
        <div style="background-color: var(--md-code-bg-color); padding: 10px; border-radius: 5px; color: var(--md-code-fg-color);">
            <strong style="color: var(--md-code-hl-keyword-color);">GET <code>/api/v1/GetLogLevel</code></strong><br>
            <p style="margin: 5px 0;">Returns the current log level of the device.</p>
            <p style="margin: 5px 0;"><strong>Possible return values:</strong></p>
            <ul style="margin-left: 20px;">
                <li><code style="color: var(--md-code-hl-string-color);">Trace</code></li>
                <li><code style="color: var(--md-code-hl-string-color);">Debug</code></li>
                <li><code style="color: var(--md-code-hl-string-color);">Info</code></li>
                <li><code style="color: var(--md-code-hl-string-color);">Warn</code></li>
                <li><code style="color: var(--md-code-hl-string-color);">Error</code></li>
                <li><code style="color: var(--md-code-hl-string-color);">Fatal</code></li>
            </ul>
        </div>
    </li>
    <li style="margin-left: -5px;">
        <div style="background-color: var(--md-code-bg-color); padding: 10px; border-radius: 5px; color: var(--md-code-fg-color);">
            <strong style="color: var(--md-code-hl-keyword-color);">GET <code>/api/v1/GetHTTPS</code></strong><br>
            <p style="margin: 5px 0;">Returns whether the device is using HTTPS or not.</p>
            <p style="margin: 5px 0;"><strong>Possible return values:</strong></p>
            <ul style="margin-left: 20px;">
                <li><code style="color: var(--md-code-hl-string-color);">true</code></li>
                <li><code style="color: var(--md-code-hl-string-color);">false</code></li>
            </ul>
        </div>
    </li>
</ul>

And these files are currently available on the server:

<ul style="list-style-type: none; padding: 0;">
    <li style="margin-left: -5px;">
        <div style="background-color: var(--md-code-bg-color); padding: 10px; border-radius: 5px; color: var(--md-code-fg-color);">
            <strong style="color: var(--md-code-hl-keyword-color);">GET
                <code>/index.html</code></strong><br>
            <p style="margin: 5px 0;">Returns the main page of the website.</p>
        </div>
    </li>
    <li style="margin-left: -5px;">
        <div style="background-color: var(--md-code-bg-color); padding: 10px; border-radius: 5px; color: var(--md-code-fg-color);">
            <strong style="color: var(--md-code-hl-keyword-color);">GET
                <code>/settings.html</code></strong><br>
            <p style="margin: 5px 0;">Returns the settings page of the website.</p>
        </div>
    </li>
    <li style="margin-left: -5px;">
        <div style="background-color: var(--md-code-bg-color); padding: 10px; border-radius: 5px; color: var(--md-code-fg-color);">
            <strong style="color: var(--md-code-hl-keyword-color);">GET
                <code>/utils.js</code></strong><br>
            <p style="margin: 5px 0;">Returns the utility JavaScript file.</p>
        </div>
    </li>
    <li style="margin-left: -5px;">
        <div style="background-color: var(--md-code-bg-color); padding: 10px; border-radius: 5px; color: var(--md-code-fg-color);">
            <strong style="color: var(--md-code-hl-keyword-color);">GET
                <code>/LPRD-Logo.webp</code></strong><br>
            <p style="margin: 5px 0;">Returns the LPRD logo image.</p>
        </div>
    </li>
    <li style="margin-left: -5px;">
        <div style="background-color: var(--md-code-bg-color); padding: 10px; border-radius: 5px; color: var(--md-code-fg-color);">
            <strong style="color: var(--md-code-hl-keyword-color);">GET
                <code>/html2canvas.min.js</code></strong><br>
            <p style="margin: 5px 0;">Returns the html2canvas library.</p>
        </div>
    </li>
    <li style="margin-left: -5px;">
        <div style="background-color: var(--md-code-bg-color); padding: 10px; border-radius: 5px; color: var(--md-code-fg-color);">
            <strong style="color: var(--md-code-hl-keyword-color);">GET
                <code>/icons88-settings-25-w.png</code></strong><br>
            <p style="margin: 5px 0;">Returns the settings icon image.</p>
        </div>
    </li>
    <li style="margin-left: -5px;">
        <div style="background-color: var(--md-code-bg-color); padding: 10px; border-radius: 5px; color: var(--md-code-fg-color);">
            <strong style="color: var(--md-code-hl-keyword-color);">GET
                <code>/script.js</code></strong><br>
            <p style="margin: 5px 0;">Returns the main JavaScript file.</p>
        </div>
    </li>
    <li style="margin-left: -5px;">
        <div style="background-color: var(--md-code-bg-color); padding: 10px; border-radius: 5px; color: var(--md-code-fg-color);">
            <strong style="color: var(--md-code-hl-keyword-color);">GET
                <code>/style.css</code></strong><br>
            <p style="margin: 5px 0;">Returns the main CSS file.</p>
        </div>
    </li>
    <li style="margin-left: -5px;">
        <div style="background-color: var(--md-code-bg-color); padding: 10px; border-radius: 5px; color: var(--md-code-fg-color);">
            <strong style="color: var(--md-code-hl-keyword-color);">GET 
                <code>/layouts/various_templates</code></strong><br>
            <p style="margin: 5px 0;">Returns the various templates page of the website.</p>
            <p style="margin: 5px 0;"><strong>Note:</strong> This directory contains multiple HTML templates used for generating images, not for direct page serving.</p>
        </div>
    </li>
</ul>

#### Post Request

The POST method is used to submit an entity to the specified resource, often causing a change in state on the server. For example, when a user submits a form on a website, the browser sends a POST request to the server with the form data. The typo of the request is defined by the `Content-Type` header.

The request [below](#__codelineno-2-1) is a simple POST request to set the operating mode of the device. The body of the request should contain the new operating mode of the device such as `Standalone`, `Network`, or `Server`. The server should respond with a success message or an error message if the given mode is invalid.

```http
POST /api/v1/SetOpMode HTTP/1.1
Host: 192.168.4.1
Content-Type: application/x-www-form-urlencoded
Content-Length: 16

mode=Standalone
```

Currently, the server has fallowing endpoints:

<ul style="list-style-type: none; padding: 0;">
    <li style="margin-left: -5px;">
        <div style="background-color: var(--md-code-bg-color); padding: 10px; border-radius: 5px; color: var(--md-code-fg-color);">
            <strong style="color: var(--md-code-hl-keyword-color);">POST
                <code>/api/v1/SetOpMode</code></strong><br>
            <p style="margin: 5px 0;">Sets the operating mode of the device.</p>
            <p style="margin: 5px 0;"><strong>Request body:</strong></p>
            <ul style="margin-left: 20px;">
                <li><code style="color: var(--md-code-hl-string-color);">mode</code> - The new operating mode of the device.</li>
            </ul>
            <p style="margin: 5px 0;"><strong>Possible values:</strong></p>
            <ul style="margin-left: 20px;">
                <li><code style="color: var(--md-code-hl-string-color);">Standalone</code></li>
                <li><code style="color: var(--md-code-hl-string-color);">Network</code></li>
                <li><code style="color: var(--md-code-hl-string-color);">Server</code></li>
            </ul>
        </div>
    </li>
    <li style="margin-left: -5px;">
        <div style="background-color: var(--md-code-bg-color); padding: 10px; border-radius: 5px; color: var(--md-code-fg-color);">
            <strong style="color: var(--md-code-hl-keyword-color);">POST
                <code>/api/v1/SetWiFiCred</code></strong><br>
            <p style="margin: 5px 0;">Sets the Wi-Fi credentials of the device.</p>
            <p style="margin: 5px 0;"><strong>Request body:</strong></p>
            <ul style="margin-left: 20px;">
                <li><code style="color: var(--md-code-hl-string-color);">ssid</code> - The SSID of the Wi-Fi network.</li>
                <li><code style="color: var(--md-code-hl-string-color);">password</code> - The password of the Wi-Fi network.</li>
            </ul>
        </div>
    </li>
    <li style="margin-left: -5px;">
        <div style="background-color: var(--md-code-bg-color); padding: 10px; border-radius: 5px; color: var(--md-code-fg-color);">
            <strong style="color: var(--md-code-hl-keyword-color);">POST
                <code>/api/v1/SetServerURL</code></strong><br>
            <p style="margin: 5px 0;">Sets the server URL of the device.</p>
            <p style="margin: 5px 0;"><strong>Request body:</strong></p>
            <ul style="margin-left: 20px;">
                <li><code style="color: var(--md-code-hl-string-color);">url</code> - The URL of the server.</li>
            </ul>
        </div>
    </li>
    <li style="margin-left: -5px;">
        <div style="background-color: var(--md-code-bg-color); padding: 10px; border-radius: 5px; color: var(--md-code-fg-color);">
            <strong style="color: var(--md-code-hl-keyword-color);">POST
                <code>/api/v1/SetDisplayModule</code></strong><br>
            <p style="margin: 5px 0;">Sets the attached E-Paper display model of the device.</p>
            <p style="margin: 5px 0;"><strong>Request body:</strong></p>
            <ul style="margin-left: 20px;">
                <li><code style="color: var(--md-code-hl-string-color);">model</code> - The model of the E-Paper display.</li>
            </ul>
            <p style="margin: 5px 0;"><strong>Possible values:</strong></p>
            <ul style="margin-left: 20px;">
                <li><code style="color: var(--md-code-hl-string-color);">WS_7IN3G</code></li>
                <li><code style="color: var(--md-code-hl-string-color);">WS_9IN7</code></li>
            </ul>
        </div>
    </li>
    <li style="margin-left: -5px;">
        <div style="background-color: var(--md-code-bg-color); padding: 10px; border-radius: 5px; color: var(--md-code-fg-color);">
            <strong style="color: var(--md-code-hl-keyword-color);">POST
                <code>/api/v1/restart</code></strong><br>
            <p style="margin: 5px 0;">Restarts the device.</p>
        </div>
    </li>
    <li style="margin-left: -5px;">
        <div style="background-color: var(--md-code-bg-color); padding: 10px; border-radius: 5px; color: var(--md-code-fg-color);">
            <strong style="color: var(--md-code-hl-keyword-color);">POST
                <code>/api/v1/SetLogLevel</code></strong><br>
            <p style="margin: 5px 0;">Sets the log level of the device.</p>
            <p style="margin: 5px 0;"><strong>Request body:</strong></p>
            <ul style="margin-left: 20px;">
                <li><code style="color: var(--md-code-hl-string-color);">level</code> - The log level of the device.</li>
            </ul>
            <p style="margin: 5px 0;"><strong>Possible values:</strong></p>
            <ul style="margin-left: 20px;">
                <li><code style="color: var(--md-code-hl-string-color);">Trace</code></li>
                <li><code style="color: var(--md-code-hl-string-color);">Debug</code></li>
                <li><code style="color: var(--md-code-hl-string-color);">Info</code></li>
                <li><code style="color: var(--md-code-hl-string-color);">Warn</code></li>
                <li><code style="color: var(--md-code-hl-string-color);">Error</code></li>
                <li><code style="color: var(--md-code-hl-string-color);">Fatal</code></li>
            </ul>
        </div>
    </li>
    <li style="margin-left: -5px;">
        <div style="background-color: var(--md-code-bg-color); padding: 10px; border-radius: 5px; color: var(--md-code-fg-color);">
            <strong style="color: var(--md-code-hl-keyword-color);">POST
                <code>/api/v1/SetHTTPAuth</code></strong><br>
            <p style="margin: 5px 0;">Sets the HTTP authentication of the device.</p>
            <p style="margin: 5px 0;"><strong>Request body:</strong></p>
            <ul style="margin-left: 20px;">
                <li><code style="color: var(--md-code-hl-string-color);">username</code> - The username for HTTP authentication.</li>
                <li><code style="color: var(--md-code-hl-string-color);">password</code> - The password for HTTP authentication.</li>
            </ul>
        </div>
    </li>
    <li style="margin-left: -5px;">
        <div style="background-color: var(--md-code-bg-color); padding: 10px; border-radius: 5px; color: var(--md-code-fg-color);">
            <strong style="color: var(--md-code-hl-keyword-color);">POST
                <code>/api/v1/SetHTTPS</code></strong><br>
            <p style="margin: 5px 0;">Sets whether the device is using HTTPS or not.</p>
            <p style="margin: 5px 0;"><strong>Request body:</strong></p>
            <ul style="margin-left: 20px;">
                <li><code style="color: var(--md-code-hl-string-color);">https</code> - Whether the device is using HTTPS or not.</li>
            </ul>
            <p style="margin: 5px 0;"><strong>Possible values:</strong></p>
            <ul style="margin-left: 20px;">
                <li><code style="color: var(--md-code-hl-string-color);">true</code></li>
                <li><code style="color: var(--md-code-hl-string-color);">false</code></li>
            </ul>
        </div>
    </li>
    <li style="margin-left: -5px;">
        <div style="background-color: var(--md-code-bg-color); padding: 10px; border-radius: 5px; color: var(--md-code-fg-color);">
            <strong style="color: var(--md-code-hl-keyword-color);">POST
                <code>/api/v1/mkdir</code></strong><br>
            <p style="margin: 5px 0;">Creates a new directory in the file system.</p>
            <p style="margin: 5px 0;"><strong>Request body:</strong></p>
            <ul style="margin-left: 20px;">
                <li><code style="color: var(--md-code-hl-string-color);">path</code> - The path of the new directory.</li>
            </ul>
            <p style="margin: 5px 0;"><strong>Note:</strong> This endpoint only for debugging purposes and it's not included in the final version.</p>
        </div>
    </li>
    <li style="margin-left: -5px;">
        <div style="background-color: var(--md-code-bg-color); padding: 10px; border-radius: 5px; color: var(--md-code-fg-color);">
            <strong style="color: var(--md-code-hl-keyword-color);">POST
                <code>/api/v1/ls</code></strong><br>
            <p style="margin: 5px 0;">Lists the files in the specified directory.</p>
            <p style="margin: 5px 0;"><strong>Request body:</strong></p>
            <ul style="margin-left: 20px;">
                <li><code style="color: var(--md-code-hl-string-color);">path</code> - The path of the directory.</li>
            </ul>
            <p style="margin: 5px 0;"><strong>Note:</strong> This endpoint only for debugging purposes and it's not included in the final version.</p>
        </div>
    </li>
    <li style="margin-left: -5px;">
        <div style="background-color: var(--md-code-bg-color); padding: 10px; border-radius: 5px; color: var(--md-code-fg-color);">
            <strong style="color: var(--md-code-hl-keyword-color);">POST
                <code>/api/v1/rm</code></strong><br>
            <p style="margin: 5px 0;">Removes the specified file from the file system.</p>
            <p style="margin: 5px 0;"><strong>Request body:</strong></p>
            <ul style="margin-left: 20px;">
                <li><code style="color: var(--md-code-hl-string-color);">path</code> - The path of the file to be removed.</li>
            </ul>
            <p style="margin: 5px 0;"><strong>Note:</strong> This endpoint only for debugging purposes and it's not included in the final version.</p>
        </div>
    </li>
</ul>

### File Upload

### Basic Authentication

### HTTPS Support

## Systemansteuerung

## E-Paper Display API
