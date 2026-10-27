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

## Git installieren
### MacOS
[Link zu git download](https://git-scm.com/install/mac)
Für macOS müssen wir git über den homebrew package manager installieren. Dafür erst homebrew installieren und dann folgendes im terminal eingeben:
```bash
brew install git
```

