# Git Workshop

## Was ist git?
git ist ein Tool zur Versionierung von Code, das auch gleichzeitiges Arbeiten von mehreren Personen an einer Codebase vereinfacht. Vereinfacht gesagt, ersetzt es das Anlegen von tausend Kopien mit neueren Arbeitsständen, wie wir es von Programmen wie der adobe cloud gewohnt sind. Wir können jederzeit einen zwischenstand (*commit*) unseres Codes speichern und jederzeit auf diesen zwischenstand zurückspringen. (Ähnlich wie bei figma). 

Darüber hinaus bietet git die funktion mithilfe von *branches*, vom gleichen Zwischenstand aus, parallel an verschiedenen Features/Änderungen etc. zu arbeiten und diese später dann (hoffentlich ohne große Probleme) wieder zu einem Stand zusammenzuführen. Dadurch können wir zu mehrt an einem Projekt arbeiten, ohne uns groß in die quere zu kommen.

Um mit mehreren Leuten zusammenzuarbeiten, oder auch um unseren Code öffentlich zugänglich zu machen, gibt es [git provider/hosting services](https://git-scm.com/tools/hosting), der bekannteste davon ist github (gehört den bösen (Microsoft)), andere sind gitlab, bitbucket, sourceforge, gitea etc.

Es gibt noch viele andere Features, die wir uns heute aber nicht so genau anschauen werden. Z.B. vergleichen von *commits* (*diff*), sehen wer welche Zeile code zuletzt bearbeitet hat (*blame*)...