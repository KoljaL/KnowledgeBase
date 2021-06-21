# Github bei All-Inkl
Notwendig: All-Inkl SSH Zugang, Github.com Account

## auf dem Server anmelden
Terminal öffnen  
Mac: `Cmd`+`Space` type `Terminal`

Über SSH auf dem Server anmelden:  
`ssh ssh-w02c0548@w0584adb.kasserver.com`  
Passwort eingeben und Key akzeptieren

### bash Befehle
mit `ls` wird der Inhlat des Verzeichnisses angezeigt,  
`cd folder` wechselt in den Ordner `folder`,  
`cd ..` wechselt in den darüberliegenden Ordner.  

### User für Git anlegen
User global (für den ganzen Server) für Git festlegen:  
`git config --global user.name "name"`  
`git config --global user.email "mail@domain.com"`  
ohne `--global` auch innerhalb eines Reops möglich.  

## erstes Git-Repository anlegen
in das Vezeichnis wechseln, dass das neue Repository werden soll:  
`cd domain.com/folder`  

Git für das aktuelle Verzeichnis initialisieren:  
`git init .`  
und alle darin enthaltenen Dateien dem Repo hinzufügen:  
`git add .`  

Das erste Mal in das neue Repo committen:  
`git commit -m "first commit"`  

Auf github.com anmelden und ein neues Repo mit demselben Namen, wie der Ordner auf dem Server erstellen.

Das Repo auf Github mit dem lokalen Repo verbinden:  
`git remote add origin https://github.com/name/repo`

Von dem lokalen Repo in den `master` Branch des remote Repos pushen:  
`git push origin main`   
Username und Password von github eingeben

## Änderungen dem lokalen Repository `committen`

`git add .`  
`git commit -m "first commit"` 

## lokales Repository auf github `pushen`
`git push origin main` 
