# Aufgabe 1
1. ja
2. > ??? nein 
3. > ??? ja
4. nein
5. ja
6. ja
7. nein
8. ja
9. nein
10. nein
11. ja
12. ja
13. nein
14. nein

# Aufgabe 2 
Zeitscheibe = Quantum
Bei einem kleinem Quantum werden Prozesse schneller gewechselt weil die Interupts schneller erfolgen
Quantum = Zeitintervalle der Interupts

*a)* Je kleiner das Quantum ist, desto schneller werden die Prozesse gewechselt
*b)* Kontextwechsel ist während des Prozesse und wenn die Zeitscheibe kleiner wäre als der Kontextwechsel, dann kommt es zu einem Overflow, weil das Zeitintervall kleiner ist als das was gemacht wird.
*c)* Prozesse werden seltener unterbrochen und dadurch schneller abgearbeitet
*d)* Weils dann zu verzögerungne im System kommen kann. Im Zweifel waretet man ewig auf das Ende eines Prozesses

# Aufgabe 3
Offset = 9
*a)* 4MiB = 4096 KiB = 4194304 B;  4194304 / 512 = 8192 Seiten
*b)* 2^18 = 262144 B; 262144 / 512 = 512 Rahmen
*c)* 8 / 8192 = 1/1024
*d)* 8 / 512 = 1/64
*e)*
123456 -> 0001 0010 0011 0100 0101 0110 
0001 0010 0011 010 - 0 0101 0110 = 000 1001 0001 1010 = 091A
091A-> 06E - 0000 0110 1101
06E = 00 1101 1100 0101 0110 
= 0DC56

00A97E -> 0000 0000 1010 1001 0111 1110
000 0000 0101 0100 = 0056 -> TLB MISS
= MISS

3D06A2 -> 0011 1101 0000 0110 1010 0010 -> 001 1110 1000 0011 = 1E83 -> 1AD
1AD = 0001 1010 1101 -> 011 0101 1010 1010 0010 
= 35AA2

215BC8 = 0010 0001 0101 1011 1100 1000 -> 001 0000 1010 1101 = 10AD -> 129
129 = 0001 0010 1001 -> 010 0101 0011 1100 1000 
= 253C8

# Aufgabe 4
*a)* 
    pid = fork();
    if(pid == 0) {
        exit(0);
    } else {
        /* Zombie hier*/
        while(1); 
    }
    
*b)*
    pid = fork();
    if(pid == 0) {
        while(1); 
        /* Waise hier, kind läuft noch, vater ist aber direkt tot*/
    } else {
        exit(0);
    }

# Aufgabe 5
*a)* 1 KiB / 4 Byte = 1024 / 4 = 256 Blocknummern
*b)* 256 * 1024 Byte = 256 KiB
*c)* 256 * 256 * 1024 Byte = 67108864 Byte = 65536 KiB = 64 MiB
*d)* kein doppelt indirekter, 4 einfach indirekte (und 12 direkte ???)
*e)* ein doppelt indirekter, acht einfach indirekte (und 3 direkte ???)
*f)* 16 doppelt indirekte Blöcke, keine einfach indirekte, keine direkten