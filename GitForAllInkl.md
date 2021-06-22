# Github bei All-Inkl33
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

### Zugang über SSH-key anlegen
Damit nicht vor jedem `push` oder `pull` zum remote Repository die Github Zugangsdaten eingegeben werden müssen, kann ein Schlüsselpaar erzeugt und der `public_key` in github.com gespeichert werden. Alle `privat_keys` liegen auf dem Server im Verzeichnis `~/.ssh`.  
`ls -lah ~/.ssh`  

Der Schlüssel muss mit der LogIn Emailadresse von github generiert werden:  
`ssh-keygen -t rsa -b 4096 -C "your_email@example.com"`  
Das Speichern des `privat_key` (id_rsa) mit Enter bestätigen und zweimal dieselbe Passphrase eingeben (gut merken, wird immer mal wieder gebraucht).  

Den `ssh-agent` starten und den Schlüssel übergeben, dabei nocheinmal die Passphrase eingeben:  
`eval "$(ssh-agent -s)"`  
`ssh-add ~/.ssh/id_rsa`  

Wenn die Ausgabe `Identity added: ...` ausgibt, den `privat_key` auslesen und kopieren:  
`cat ~/.ssh/id_rsa.pub`

Dann auf github.com unter `Settings` - `SSH and GPG keys` - `New SSH key` den `privat_key` unter Angabe eines sinnvollen Titels einfügen.  

Zur Kontrolle den Zugang testen (ggf mit Enter bestätigen):   
`ssh -T git@github.com`  



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
`git remote add origin https://github.com/Username/Repository`  

Wenn der Zugang über `SSH Keys` erfolgen soll, muss auch der `SSH`-Link verwendet werden:  
`git remote add origin git@github.com:Username/Repository.git`   

Von dem lokalen Repo in den `main` Branch des remote Repos pushen:  
`git push origin main`   
Username und Password von github eingeben

## ein Repository clonen

In einem Repository auf github den `SSH`-Link hinter dem grünen `Code` Button kopieren, in der Konsole in das Verzeichnis wechseln, in welches das Repo hinengeklont werden soll und den `SSH`-Link einfügen:
`git@github.com:Username/Repository.git`


## Änderungen dem lokalen Repository committen 

`git add .`  
`git commit -m "first commit"` 

## lokales Repository auf github pushen
`git push origin main` 


### noch unsortiert

### Fehlermeldungen

`fatal: remote origin already exists.`  

Das Problem tritt auf, weil eine falsche Reihenfolge der Git-Konfiguration befolgt wird, oder wenn ein Repository geklont wird.
Entweder das `origin` auf github vom lokalen Repository lösen:   
`git remote remove origin`   

Oder das `origin`auf dem lokalen Repository neu festlegen: (funktionierte nicht)  
`git remote set-url origin git@github.com:Username/Repository.git`  

