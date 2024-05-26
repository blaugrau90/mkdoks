# Installation von Docker

## Dependencies

Die Umgebung basiert auf einer Debian-VM. Diese muss zunächst installiert und konfiguriert werden. Eine statische IP-Adresse ist hier unbedingt erforderlich. Um die Namensauflösung korrekt durchzuführen, sollte auch ein Nameserver und eine entsprechende Domain, falls vorhanden, konfiguriert werden. Um die Umgebung auf Basis von Docker einzurichten, werden zunächst die Docker-Pakete wie folgt installiert.


## 1. Docker Installation


:::info
**Hinweis:** Diese Dokumentation bezieht sich auf die Docker-Installation auf einem Debian 11 Linux

:::


Entfernen Sie zunächst alle Docker-Pakete, die möglicherweise veraltet sind.

`sudo apt-get remove docker docker-engine docker.io containerd runc`


Bevor Sie die Docker-Engine zum ersten Mal auf einem neuen Host-Rechner installieren, müssen Sie das Docker-Repository einrichten. Danach installieren und aktualisieren Sie Docker aus dem Repository. Fügen Sie den offiziellen GPG-Schlüssel von Docker hinzu. Mit dem Befehl echo wird die herunterzuladende Version auf **stable** gesetzt.

```bash
sudo apt-get update

sudo apt-get install \
 apt-transport-https \
 ca-certificates \
 curl \
 gnupg \
 lsb-release

curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

echo \
  "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/debian \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```


Die Installation von Docker ist dann sehr einfach und erfolgt mit zwei Befehlen.

```bash
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
```


## 2. Docker-Compose Installation

Docker Compose kommt standardmäßig mit der normalen Docker Installation mit. Die unten stehenden Befehle sind für die Standalone Docker Compose Installation und sind nicht zwingend erforderlich.

Für die Installation von Docker Compose benötigen Sie ebenfalls nur zwei kleine Befehle.

```bash
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
```