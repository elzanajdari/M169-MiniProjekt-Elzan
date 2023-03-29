# M169-MiniProjekt-Elzan

[Link zum Video]()
 
Anleitung:

1. ## Dockerfile erstellen
Dockerfile in ein Ordner erstellen
Content: FROM httpd:2.4 (dies ist eine Kopie von httpd)

2. ## Docker Image Bauen
docker build -t imagename .
z.B. docker build -t webcontainer .
Achtung . = dockerfile ist im gleichen Ordner

3. ## Container mit Volumes starten
docker run -dit --name webcontainer -p 8080:80 -v page:/usr/local/apache2/htdocs/ -v logs:/usr/local/apache2/logs/ webcontainer

-v bedeuted Volume und Logs ist der Name
der Pfad /usr/local... ist der Pfad worauf alles dann gespiegelt wird.
Dies gilt alles für meine VM
Auf der rechten Seite sieht man das Ganze nochmals mit Page, dies gilt alles für mein Container.

4. ## Persistance vorzeigen

- Vorhandenen Portainer auf der VM löschen (webcontainer)
- Terminal öffnen
- Volume wird wieder erstellt mit neuem Namen und anderem Port: 
docker run -dit --name webcontainer2 -p 7777:80 -v page:/usr/local/apache2/htdocs/ -v logs:/usr/local/apache2/logs/ webcontainer
- Localhost:7777 öffnen in FIrefox
- Man sieht dass vorherige Änderungen bestehen bleiben durch der Persistance der Volumes. Der Inhalt des alten Volumes bleibt auf dem neuen Image bestehen.
