# Aufgbe 1
1. Hauptspeicher
2. CPU
3. Massenspeicher

4. I/O-Geräte
5. Netzwerkzugänge

# Aufgbe 2
1. nein
2. ja (kam nie dran)
3. ja
4. ja
5. nein
6. nein

# Aufgbe 3
1. ja
2. nein
3. nein
4. ja
5. nein
6. ja

# Aufgbe 4
*a)* Ein Zombie ist ein Prozess, der bereits terminiert ist aber noch in der Prozesstabelle auftaucht. Dies passiert wenn der Vaterprozess noch läuft, das Kind aber schon terminiert hat. Er verschwindet wenn der Vater ein wait() ausführt oder selbst terminiert.
*b)* Ein Waise ist ein Prozess, dessen Vaterprozess bereits terminiert hat, er aber noch in der Prozesstabelle auftaucht. Er wird von Prozess mit der PID 0 "adoptiert".

# Aufgbe 5
*a)* 2^m / 2^n -> Die Anzahl der Einträge ergibt sich aus der gesammten Größe des Speichers und der Größe der einzelnen Seiten 
*b)* (2^k * (2^m / 2^n)) / 2^n -> Die Anazhl der genutzten Seiten ergibt sich aus der Anzahl der Einträge geteilt durch die Seitengröße. 

# Aufgbe 6
1. ja
2. nein
3. nein
4. ja (?)
5. ja (?)
6. nein

# Aufgbe 7
Die 50% Regel besagt, dass ein drittel des Speichers nicht nutzbar sind. In dem Fall von 3 GiB sind 1/3 = 1GiB der wegen Fragmentierung nicht vergeben werden kann.

# Aufgbe 8
