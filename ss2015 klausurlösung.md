# Aufgabe 1
(Diagramm aus Skript)
[blockiert] -Ereignis tritt ein-> [bereit] -CPU-Zuteilung-> [ausführend] -Warten auf Ereignis-> [blockiert]
[ausführend] -Verdrängung "Preemption"-> [bereit]
    1. CPU-Zuteilung: Der Scheduler erteilt die Kontrolle über die CPU an diesen Prozess
    2. Warten auf Ereignis: der prozess warten darauf, das es weitergehen kann, etwa auf Daten von der Festplatte oder Benutzereingabe
    3. Ereignis tritt ein: Das Ereignis auf das der Prozess gewartet hat, trifft ein. Etwa dei Bentuzereingabe 
    4. Verdrängung "Preemption": Der Scheduler vergibt die Kontrolle an einen anderen Prozess

# Aufgabe 2
Nein, sie gehören nicht zum Prozesskontekt, müssen aber trotzdem beim Kontextwechsel gerettet werden indem sie in den Prozessdeskriptor kopiert. 

# Aufgabe 3
*a)* 64KiB / 32 Byte = 2048 Seiten
*b)* 2^12 / 32 Byte = 128 Rahmen
*c)* 4 / 2048 = 1 / 512
*d)* 4 / 128 = 1 / 32
*e)* Offset = log2(32) = 5 Bit
    0x40F6 = 0100 0000 1111 0110 -> 0010 0000 0111 -> 0x207 -> 0x13 = 0001 0011 -> 0010 0111 0110 = 0x276
    0x0A19 = 0000 1010 0001 1001 -> 0000 0101 0000 -> 0x050 -> 0x22 = 0010 0010 -> 0100 0101 1001 = 0x459
    0x050A = 0000 0101 0000 1010 -> 0000 0010 1000 -> 0x028 -> TLB-Miss
    0x227E = 0010 0010 0111 1110 -> 0001 0001 0011 -> 0x113 -> 0x66 = 0110 0110 -> 1100 1101 1110 = 0xCDE

# Aufgabe 4
*a)* Wenn A und B die selbe Datei öffnen.
    ...
    FILE *a;
    pid = fork()
    if (pid == 0) { // Prozess B
        a = fopen(test.img);
    } else { //Prozess A
        a = fopen(test.img);
    }
    ...

*b)* Also wenn A und B die gleiche Datei öffnen aber an verschiedenen Positionen lesen
    ...
    FILE *a = fopen(test.img);
    pid = fork()
    if (pid == 0) { // Prozess B
        stelle = fseek(a+5);
    } else { //Prozess A
        stelle = fseek(a+23);
    }
    ...

*c)* Also wenn der Prozess die gleiche Datei zweimal öffnet.
    ...
    FILE *a = fopen(test.img);
    FILE *b = fopen(test.img);
    ...

# Aufgabe 5
*a)* 64 MiB / 1 KiB = 64 * 1024 / 1 = 65536 Blöcke
*b)* log2(65536) = 16 Bit
*c)* 1 KiB / log2(65536) = 1024 / 2 = 512 Blocknummern Pro indirektem Block
*d)* 3 * 1 KiB = 3 KiB
*e)* (3 * 1 KiB) + (3 * 512 * 1 KiB) = 3 KiB + 1536 KiB = 1539 KiB
*f)* (3 * 1 KiB) + (2 * 512 * 1 KiB) + (1 * 512 * 512 * 1 KiB) = 3 KiB + 1024 KiB + 262144 KiB = 263171 KiB 
     Aber ACHTUNG! das Dateisystem hat nur eine maximale Größe von 65536 KiB, 262144 KiB sind also nicht möglich.