# Aufgabe 1
Der Kernelmode kann jede Instruktion ausführen auf auf ALLE Speicherzellen zugreifen. Nach dem Start arbeitet die CPU in diesem Modus. 
Der User-Mode hat nur eingeschränkten Zugriff auf Speicherzellen und I/O-register.

# Aufgabe 2 
Die Grenze zwischen Code und Daten wird vom Binder auf eine Seitengrenze gelegt, damit der Code von mehreren Prozessen gemeinsam genutzt werden kann, während die Daten getrennt sind.

# Aufgabe 3
pid = fork();
if(pid == 0) { //Child 
    execvp("ls", "al");
} else { //Parent
    wait();
}

# Aufgabe 4
Threads haben einen zusammenhängenden Adressraum, Prozesse einen getrennten.
Dudurch ist der Zugriff auf gemeinsame Daten (wie Variablen) bei Threads direkt und ohne die Hilfe des BS möglich.

# Aufgabe 5
1. Ist ein Bereich wo zwei Threads, des selben Prozesses, pseudo-nebenlöufig auf gemeinsame Daten zugreifen wollen.
2. Besteht die Gefahr der Inkositenz der Daten durch gemeinsamen Zugriff. Dies kann durch verschiedene Implimentierungen verhindert werden, etwa Sephamoore oder Monitor.

# Aufgabe 6
Es muss "shared memory" implementieren und nutzen.
Die einzelnen Prozesse müssen synchronisiert werden.

# Aufgabe 7
(Starke) Fragmentierung des Speichers.
Kommt dadurch zu stande, das es potentiell zu vielen kleinen Clustern kommen kann, die nicht mehr für größere Anwendungsfälle genutzt werden können.

# Aufgabe 8
