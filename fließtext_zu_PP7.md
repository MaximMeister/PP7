Task 1:

1. Preprocess

In diesem Schritt werden die Informationen aus den verwendeten Bibliotheken (hier stdio.h) abgerufen und in die Datei sample.i eingefügt. Dabei werden die verwendeten Funktionen deklariert, würde dies nicht geschehen, müsste man dies für jede einzelne Funktion die man aus der Bibliothek verwendet, selbst tun.
Ebenso werden in dem Schritt des Preprocessing Makros definiert, diese haben in etwa die Funktion einer vordefinierten Anweisung, so kann über #define Pi 3,14159265, die Funktionen Pi erklärt werden. Bei späterer Verwendung von Pi wird immer der Zahlenwert von 3,14... verwendeten anstatt des Textes "Pi".

2. Compile to assembly

In diesem Schritt wird die Datei sample.c in die Form sample.s umgewandelt. Dabei ist .s deutlich kürzer als die .c Variante des ersten Schrittes.
In diesem Vorgang wandelt der compiler die Datei in eine für den Computer lesbare Form um. Dabei wird Assambly Code verwendet, dieser kann ebenfalls vom Personen gelesen werden, ist jedoch eine deutlich niedrigere Form einer Programmiersprache wie C oder Python. So wird zum Beispiel aus dem return 0 am Ende der Datei sample.i -> movl $0, %eax 

3. Assemble
Je nach Prozessorarchitektur fällt diese Datei von Pc zu Pc unterschiedlich aus, obwohl der gleiche Quellcode vorliegt.In diesem Schritt wird aus der Datei sample.c die Objektedatei sample.o gemacht. Dabei wird die Datei mit Assambly in Maschinensprache (0,1) übersetzt. 

4. Link to produce an executable

In dem Schritt des Linkens werden (falls nötig) mehrer o. Dateien zusammengefügt um daraus ein executable zu machen. Fehlende Funktionen werden dabei gesucht und verknüpft. Mit fällt es etwas schwer diesen Schritt zu erklären. Am einfachsten gesagt, hierbei wird alles an Unstimmigkeiten glatt gezogen. Erst dadurch wird das Programm ausführbar.

Task 2:

Copy

Der Befehl war mir bereits bekannt, dabei wird eine Datei ohne Veränderung in eine neue übernimmt und nichts ersetzt, außer wenn die Zieldatei existiert und dann überschrieben wird 

Grep

Mir grep lässt sich sehr einfach Texte nach Wörtern und einzelnen Buchstaben durchsuchen. Das nächste was mir in den Sinn gekommen ist das Strg + F aus Windows, hier kann man jedoch nur nach etwas suchen und die Inhalte nicht ersetzen.
In Task 2 wurde das Beispiel: grep -En "printf\s*\(" solutions/debug_sample.c verwendet. 
Die Zusätze -En stehen für die Erweiterung der Syntax (+,|,?...) und zur Angabe der Zeilennummer

Sed

Mit dem Befehl sed lassen sich Dateien durchsuchen und ebenso Änderungen vornehmen, dies geschieht "in place". Es werden jedoch alle Gesuchten Parameter abgeändert, in dem Beispiel, war dies noch sehr überschaubar. Sed legt gleichzeitig eine Backupdatei mit der Endung .bak an.


Awk

Das Werkzeug awk verhält sich recht ähnlich zu grep, jedoch ist awk komplexer und vielseitiger und kann beispielsweise bei Bedarf nur auf ausgewählte (einzelne) Zeilen angewendet werden.

grep "blau" logfile.txt - Zeigt alle Zeilen mit "blau".

awk '/blau/ { print $1, $3 }' logfile.txt - Zeigt aus Zeilen mit "blau" nur die erste und dritte Spalte.

Vim interactive

Dabei handelt es sich meiner Meinung nach um die beste und gleichzeitig einfachste Möglichkeit, Strings und Chars zu suchen und zu ersetzen. Mit unter liegt es daran, dass ich vim bereits kenne. Und die Suche mit /'gesucht' recht einfach durchgeführt werden kann. Ebenfalls ist das Ersetzen mit :%s/vorher/nachher/g recht einfach, sofern man das % oder g nicht vergisst.

Vim Cli (= Command Line Invocation

Vim Cli verhält sich genauso wie die oben stehenden Version, jedoch wird die Datei nicht mit vim geöffnet, sondern die Änderung erfolgt in dem Terminal; mit vim -c wird lediglich der nachfolgende Befehl in die Befehlszeile von vim geschrieben und ausgeführt, dies ist jedoch nicht interaktiv sichtbar.

Task 3:

Kurz zusammengefasst wurde in der Task 3 zwei verschiedene Dateien in einer ausführbaren .o Datei zusammengefügt.
Die beiden Funktionen in den Dateien main.c und add.c wurden erstellt. In der Datei main.c wurde über die Zeile " extern int add(int, int); " die externe Verknüpfung/Auslagerung der Datei add erklärt, so weiß der Compiler wo diese zufinden ist.
Im nächsten Schritt werden beide Dateien in das .o Format kompiliert. Danach wurden die beiden Datein manuell mit dem Befehl gcc zusammengefügt. Der Vorteil dieser Vorgehensweise kommt nur bei größeren Programmen oder vielen verschiedenen Funktionen zu tragen. So kann die Datei main noch recht übersichtlich gehalten werden. Bei Bedarf muss nur eine der "Nebendateien" wie add  angepasst werden.
