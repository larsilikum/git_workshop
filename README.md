# Git Workshop und Terminal Einstieg

## Was ist git?
git ist ein Tool zur Versionierung von Code, das auch gleichzeitiges Arbeiten von mehreren Personen an einer Codebase vereinfacht. Vereinfacht gesagt, ersetzt es das Anlegen von tausend Kopien mit neueren Arbeitsständen, wie wir es von Programmen wie der adobe cloud gewohnt sind. Wir können jederzeit einen zwischenstand (*commit*) unseres Codes speichern und jederzeit auf diesen zwischenstand zurückspringen. (Ähnlich wie bei figma). 

Darüber hinaus bietet git die funktion mithilfe von *branches*, vom gleichen Zwischenstand aus, parallel an verschiedenen Features/Änderungen etc. zu arbeiten und diese später dann (hoffentlich ohne große Probleme) wieder zu einem Stand zusammenzuführen. Dadurch können wir zu mehrt an einem Projekt arbeiten, ohne uns groß in die quere zu kommen.

Um mit mehreren Leuten zusammenzuarbeiten, oder auch um unseren Code öffentlich zugänglich zu machen, gibt es [git provider/hosting services](https://git-scm.com/tools/hosting), der bekannteste davon ist github (gehört den bösen (Microsoft)), andere sind gitlab, bitbucket, sourceforge, gitea etc.

Es gibt noch viele andere Features, die wir uns heute aber nicht so genau anschauen werden. Z.B. vergleichen von *commits* (*diff*), sehen wer welche Zeile code zuletzt bearbeitet hat (*blame*)...

## Kurzer Exkurs ins Terminal (MacOS und Linux)
Das Terminal gibt uns zugriff auf unseren Computer ohne graphisches Interface, sondern Textbasiert.
[cheatsheet macos](https://www.geeksforgeeks.org/linux-unix/complete-mac-terminal-commands-cheat-sheet/)

### Öffnen
MacOS: cmd + t

### Abbrechen
Manchmal laufen irgendwelche prozesse sehr lange und ihr wollt sie einfach nur beenden. Dann strg + c drücken!

### Nutzung
Das Terminal kann viele Befehle ausführen. Diese werden immer als erstes geschrieben.
z.B. `cd ~`

`cd` (change directory) ist der Befehl in einen Ordner zu navigieren.
cd erwartet einen Pfad als Eingabe, hier: ~ (tilde steht für home directory). Dazu später mehr!

Leerzeichen trennen immer verschiedene arten von Eingaben voneinander.

Durch drücken der Enter-Taste wird der Befehl ausgeführt.

### Admin rechte
Manche Befehle benötigen Admin Rechte, diese können wir ausführen indem wir vor den Befehl den Befehl `sudo` schreiben (steht glaube für super user do...). Hier werden wir aufgefordert unser passwort einzugeben.

Beispiel:

`sudo ls /` (Hier sind eigentlich keine Adminrechte notwendig)

`ls` listet alle Dateien und Ordner in unserem derzeitigen working directory auf.

### Flags
Eine andere wichtige Eingabe sind flags.
Flags sind Optionen und Parameter die wir einem Befehl mitgeben (Ähnlich zu Parametern in Funktionen beim Programmieren). Diese unterscheiden sich natürlich auch von Befehl zu Befehl, wobei es auch überschneidungen gibt.
Diese sind entweder Optionen (heißt wenn wir sie dazuschreiben, wird der Befehl auf diese Weise ausgeführt):

`ls -a`: listet alle Dateien und Ordner (auch versteckte) auf

`ls -1`: formatiert den Output mit einer Datei/Ordner pro Zeile

Flags können aber auch inputs anzeigen z.B.

`ls -w 40`: -w (width) bestimmt die weite des Outputs im sinne von Zeichen. Also in diesem Falle höchstens 40 Zeichen pro Zeile

Bei Flags existieren oft zwei Formen (zumindest aber die lange Form).
Eine lange flag `--all` und eine kurze `-a`. (diese bewirken das gleiche)

Da kurze flags immer nur ein Zeichen sind (Achtung sie sind case-sensitive), können wir Options-flags auch kombinieren also z.B.
`ls -a1` oder `ls -1a` ist egal wierum.

### Hilfe
Meistens kennen wir nur ein paar flags etc. und das ist auch nicht schlimm. Jeder command hat eine `--help` flag. Diese gibt uns einen Überblick was der Befehl macht und zeigt uns welche Optionen/flags hierführ existieren.

Beispiel: `ls --help`

Sonst gibt es auch ein manual `man ls` zu jedem Command. Diese sind meistens seehr ausführlich.

Oder eine kurze Beschreibung mit `whatis ls`

### Navigation
Vor unserem cursor sehen wir unser working directory (der Ordner in dem wir uns befinden). Wenn wir das Terminal nicht direkt aus einem ordner öffnen, starten wir immer im home directory.

Mit `pwd` (print working directory) seht ihr in welchem Dateipfad ihr euch gerade befindet.

Wir kennen jetzt schon die wichtigsten Navigationsbefehle `cd` und `ls`. Für beide können wir einen Pfad angeben, bei `cd` müssen wir das auch.

Wir bauen einen Pfad wie beim Coden (z.B. im src attribut von img elementen) folgenderweise auf.

Der Pfad ist entweder:
1. relativ
wir beginnen mit einem ordner der sich in dem jetzigen working directory befindet (z.B. 'Documents')
2. absolut
der Pfad beginnt entweder mit einem / z.B. /home (hier starten wir vom obersten Ordner aus, dem root directory)
oder der Pfad beginnt mit einer tilde ~ z.B. ~/Documents (wir starten aus dem home directory)

Wichtige Zeichen:
`/` steht vor einem Unterordner (`~/Documents`: Documents ist unterodner vom home ordner)

`.` steht für den aktuellen Ordner (working directory)

`..` steht für den Ordner über dem aktuellen Ordner (demzufolge `../..` noch ein Ordner darüber)

`./` können wir weglassen (`cd Documents` ist das gleiche wie `cd ./Documents`)

Während ihr die Ordnernamen schreibt könnt ihr auch tab drücken zur automatischen vervollständigung. Funktioniert aber nur, wenn es nur einen ordner gibt der zu der aktuellen eingabe passt (falls nicht, werden bei erneutem tab drücken alle passenden Ordner angezeigt).

### Extra
Es gibt sehr viele Befehle und noch mehr die wir uns installieren können :)

hier noch ein paar essentielle:

`mkdir ordner_name` make directory, erstellt einen ordner (hier den ordner ordner_name)

`rm example.txt` remove, löschen von dateien oder ganzen ordnern: `rm -r example_folder` (-r steht hier für rekursiv, also alles was in dem Ordner ist, wird auch gelöscht)

`cp example.txt example_2.txt` copy, kopiert eine datei/ordner an einen neuen ort mit neuem namen

`mv -r example_folder ../example-folder` move, verschiebt datei oder ordner von angegebenen pfad zu neuem pfad (hier wird ein example_folder ordner in den Überordner verschoben), -r wird hier auch für ordner gebraucht. Dabei können diese aber auch umbenannt werden.

`touch example.txt` erstellt eine neue datei.

`cat example.txt` schreibt den inhalt der datei ins terminal

`nano example.txt` öffnet einen terminal basierten text editor.

## Git
### installieren
[Link zu git download](https://git-scm.com/install/mac)
Für macOS müssen wir git über den homebrew package manager installieren. Dafür erst homebrew installieren und dann folgendes im terminal eingeben:
```bash
brew install git
```

### Initialisierung
Es gibt zwei Wege ein git repository zu starten. Entweder wir kopieren ein existierendes Projekt oder initieren git in unserem (neuen oder bestehenden) Projekt.

*repository* steht für den gesamten Code + Dateien und Ordner die zu einem Coding Projekt gehören.

#### clone
Um ein bestehendes Projekt einfach auf unseren Computer zu laden gibt es den `clone` Befehl.

Hier wird das Projekt in das derzeitige working directory geladen! Also am besten nicht in eurem home directory ausführen :)

Der Befehl wird folgendermaßen ausgeführt:
`git clone <url-des-repositories>`

Die url findet ihr bei den jeweiligen git providern (hier github)
https://github.com/larsilikum/git_workshop

Diese Repository lässt sich also mit:
`git clone https://github.com/larsilikum/git_workshop.git` klonen.

Bei öffentlichen Repositories solltet ihr euch nicht anmelden müssen um sie zu klonen.

#### init
Habt ihr bereits ein Projekt, oder wollt komplett von vorne starten, gibt es den `init` Befehl.
Im Terminal navigiert ihr zu eurem Projektordner und gebt dort den Befehl `git init` ein. Damit ist git initiiert und ihr könnt weiter machen.

### staging
Wenn wir nun an unserem Projekt gearbeitet haben und einen Zwischenstand speichern möchten, müssen wir auswählen aus welchen Dateien wir die Änderungen abspeichern wollen. Das nennt sich *staging*. Meistens wollen wir einfach alle Änderungen übernehmen, aber es kann auch mal Ausnahmen geben.

Der Befehl um Dateien zu *stagen* ist `git add <pfad>`. 

Folglich benutzen wir `git add .` um unser ganzes working directory zu stagen. Achtung falls ihr zwischendurch in einen Unterordner navigiert seid wird nur dieser gestaged, da `.` ein relativer Pfad ist.

Nun sind alle geänderten Dateien gestaged und wir können unseren Zwischenstand speichern, dazu brauchen wir noch den `commit` Befehl.

### commit
Der `commit` Befehl speichert also alle Änderungen aus gestageten Dateien ab. Ein Commit hat dabei auch immer eine Commit-message. Dazu gibt es verschiedene Philosophien, aber meistens beschreibt sie was geändert wurde, damit wir im nachhinein besser nachvollziehen können was wann passiert ist, wenn wir einen bestimmten Zwischenstand suchen. 

**Ein Commit sollte keine schwerwiegenden Fehler haben. Also das Projekt sollte funktionieren wenn wir diesen Abspeichern.**

Der Befehl ist folgendermaßen aufgebaut:
`git commit -m "Das hier ist die commit message"`

Die `-m` flag gibt an, das danach die commit message folgt. Wenn ihr das nicht tut und nur `git commit` ausführt, werdet ihr gezwungen eine message einzugeben. Dabei wird nano geöffnet und ihr müsst dort die commit message eingeben, mit strg+o und dann enter abspeichern und dann mit strg+x verlassen, also einfach lieber direkt die message mit der flag angeben :)

Jetzt ist euer commit angelegt und ihr solltet eine Zeile im Terminal bekommen die irgendwie so ähnlich aussieht:

```bash
[main 14dbd9c] add staging and commit instructions
 1 file changed, 27 insertions(+), 1 deletion(-)
```

Hier sehen wir jetzt auf welchem branch der commit gespeichert wurde (in eckigen klammern) eure commit message dahinter und in der nächsten Zeile, wieviele Dateien und Zeilen sich geändert haben.

Eure letzten commits seht ihr auch z.B. mit `git log`.

### checkout
Der `checkout` befehl lässt uns zurückgehen zu alten commits oder auf andere branches wechseln.
*bevor wir auf einen anderen commit/branch wechseln sollten wir unsere Änderungen committen, stashen oder resetten*

Z.B. 
```bash
git checkout 7a6d51fc2838699a8f8c93c10c0b411870f2dd17
```

nach dem checkout Befehl schreiben wir den hash des commits (oder den namen des branches) zu dem wir zurückkehren wollen. Den findet ihr z.B. mit `git log`.
Da wir uns jetzt in einer alten version befinden können wir Änderungen von hier ausgehend nicht direkt abspeichern. Die automatisch angezeigte Hilfe nach diesem command gibt uns den Hinweis einen neuen Branch zu erstellen!

### branch
Ein Branch steht bei git analog zu einem paralleluniversum oder so. An einem gewissen Punkt (Commit) spaltet sich ein branch von einem anderen ab. Anders als bei echten Ästen und Bäumen können zwei Branches sich aber auch wieder *mergen*/kombinieren.

Wann genau wir branches anlegen ist auch uns überlassen. Oft starten wir einen neuen branch um Sachen auszuprobieren, die am Ende vielleicht gar nicht im Projekt auftauchen.

Oder wir Arbeiten mit issues und legen für jedes issue einen neuen Branch an. Z.B. wollen wir eine neue Unterseite in unsere Webseite einbauen. Da wir dafür wohl mehr als einen commit brauchen, legen wir einen neuen branch an. Bis die unterseite fertig ist arbeiten wir auf diesem branch und mergen ihn anschließend auf den main branch.

Oft haben git repos zumindest zwei branches. Einen *development* und einen *production* branch. Der *production* branch hat den stand der aktuell deployed ist, also auf dem server liegt. Der *development* branch hat den aktuellen stand der Entwicklung. Also neue Features, die aber noch nicht auf der Live Seite sind. Für ein Update wird dann der *development* branch in den *production* branch gemerget.

Es gibt mehrere Arten einen branch anzulegen.

`git checkout -b <branch-name>` mit checkout können wir mit der -b flag angeben das wir einen neuen branch anlegen wollen. Dabei startet dieser vom aktuell ausgecheckten commit (HEAD) und wir nehmen alle Änderungen die noch nicht commited wurden mit auf den neuen branch!

`git branch <branch-name>` hier erstellen wir vom aktuellen commit (HEAD) aus einen neuen branch. Wir wechseln aber im gegensatz zur checkout variante nicht dorthin. Dafür können wir `checkout` oder `switch`(ähnlich wie checkout, aber nur für branches) benutzen.

#### Andere wichtige branch befehle
`git branch -l` / `git branch --list` listet alle branches auf.

`git branch --show-current` zeigt den aktuellen branch.

`git branch -m <new-branch-name>` benennt den aktuellen branch um.

Wie auch bei allen anderen commands können wir natürlich auch immer die hilfe mit `git branch --help` öffnen.

### merge

### .gitignore?

### remote anbindung

### guis?


