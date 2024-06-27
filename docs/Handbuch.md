# Handbuch

## Aufsetzen des Linux Servers
**Mario Wegmann**

In der folgenden Anleitung werden Platzhalter mit <Platzhaltername> markiert. 
### Grundinstallation
// TODO
NETDATA

sudo apt-get install git

### Testumgebung für Entwicklung
// TODO
Zu beginn muss Node.js installiert werden. 
Da über den apt Packetmanager nur veraltete Versionen von Node.js bereitgestellt werden, wird hier der Node Version Manager verwendet. 

Dieser lässt sich über folgendes Bash Skript installieren. 
`curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash`
Nach der Installation empfiehlt es sich die SSH Sitzung neu zu starten, damit der `nvm` Befehl auch erkannt wird. 
Anschließend kann mit `nvm install 20` die LTS-Version Node.js 20 installiert werden. 
Mit Node.js kommt auch der `npm` Packetmanager. Mit disem lässt sich React und Next.js installieren. 
`npm install next@latest react@latest react-dom@latest`

Als nächstes muss ein SSH Key für Github hinterlegt werden, damit das Repository geklont werden kann. 
Dafür wird als erstet ein SSH Key generiert. 
Es empfiehlt sich dabei auch ein Passphrase zu vergeben und beim Speicherort einen eindeutigen Namen zu vergeben. 
`ssh-keygen -t ed25519 -C "<Github E-Mail Adresse>"`
Als nächstes wird der SSH Agent einmal gestartet um anschließend den SSH Key beim SSH Agent hinterlegen zu können. 
`eval "$(ssh-agent -s)"`
Beim hinzufügen muss auch die zuvor festgelegte Passpharse eingegeben werden. 
`ssh-add <Speicherort des zuvor erstellten SSH Keys angeben>`

Der Public Teil des SSH Keys muss auch im Github Account hinterlegt werden. 
Dafür die URL https://github.com/settings/keys aufrufen und einen neuen SSH Key hinzufügen. 

Nun kann das Repository der Webanwendung geklont werden. 
`git clone git@github.com:THA-LPRD/web.git lprd`

Danach wird das Verzeichnis von der Next.js Anwendung betreten.
`cd lprd/lprd-server`

Die Anwendung verwendet die offizielle Schriftart der THA. Die Schriftart TWK Everett darf wegen der, von der THA erworbenen, Lizenz jedoch nur Studierenden und Mitarbeitern der Technischen Hochschule Augsburg zur verfügung gestellt werden. Die Schriftart lässt sich unter folgender URL herunterladen: https://www.tha.de/Kommunikation/Corporate-Design.page 
Anschließend müssen die zwei Schriftfamilien TWKEverett-Bold-web.ttf und TWKEverett-Medium-web.ttf TWKEverett-Medium-web.ttf müssen im Ordner lprd-server/components/fonts kopiert werden. 

Als nächstes kann die PostgreSQL Datenbank aufgesetzt werden. 
Dafür kann das Docker Image oder auch ein bestehender PostgreSQL Server verwendet werden. 
`sudo docker run --name lprd-postgres -p 5432:5432 -e POSTGRES_PASSWORD=<SicherersDatenbankPasswort> -d postgres`

Die URL der Datenbank muss auch noch der Next.js Anwendung bekannt gemacht werden, dies geschieht über die .env Datei. 
Diese sollte neue angelegt werden und den folgenden Inhalt enthalten: 
`DATABASE_URL="postgresql://<PostgresUser>:<PostgresUserPassword>@<PostgresServerIP/Hostname>:5432"`

Nach der Installation der Datenbank kann diese mit Prisma mit den notwendigen Tabellen befüllt werden. 

`npx prisma migrate dev --name init`

Die Vorbereitungen sind somit abgeschlossen und der Developmentserver kann gestartet werden.

`npm run dev`

Unter http://localhost:3000 ist der Server nun erreichbar. 

Der Developmentserver kann mit dem Tastenkürze Ctrl+C beendet werden. 

### Produktivumgebung bauen

// TODO Was mit Font?
docker build -t nextjs-docker .
docker run -p 80:3000 nextjs-docker

### Produktivumgebung starten

// TODO
CADDY
Cert

sudo apt-get install docker



## Quellen
https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent?platform=linux#generating-a-new-ssh-key 
https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account
