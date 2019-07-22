# Aufgabe 1
*a)* 512 * 8KiB = 4096 KiB = 4 MiB
*b)* log2(8KiB) = 13
*c)* log2(40961024) = 22
*d)* 256 MiB = 262144 KiB -> 262144 KiB / 8 KiB = 32768 Rahmen
*e)* log2(32768) = 15 -> 15 Bit für die Rahmennummer + 13 Bit Offset = 28 Bit physikalische Adresse
*f)* 
Da es hier nur um Adressen (nicht Nummern) geht, muss einfach nur der Offset genullt werden. Dann wie gehabt in der Tabelle nachschauen, Rahmenadresse (auch mit genulltem offset) aus der Tabelle ziehen und den Offset wieder dranhängen. 
0x0EA470 -> 0000 1110 1010 0100 0111 0000 -> 0000 1110 1010 0000 0000 0000 = 0EA000 -> TLB Miss
0x0B134A -> 0000 1011 0001 0011 0100 1010 -> 0000 1011 0000 0000 0000 0000 = 0B0000 -> 0x40CE000 -> 0100 0000 1100 1111 0011 0100 1010 = 0x40CF34A 
0x00BA6B -> 0000 0000 1011 1010 0110 1011 -> 0000 0000 1010 0000 0000 0000 = 00A000 -> 0x841E000 -> 1000 0100 0001 1111 1010 0110 1011 = 0x841FA6B
0x223A25 -> 0010 0010 0011 1010 0010 0101 -> 0010 0010 0010 0000 0000 0000 = 222000 -> 0xD940000 -> 1101 1001 0100 0001 1010 0010 0101 = 0xD941A25

# Aufgabe 2
*a)* Optimal: 0,5
*b)* FiFo: 0,3,1
*c)* LRU: 0,1,7,5 
*d)* Second Chance: 0,7,3,5

# Aufgabe 3
Freiliste 0: 1 KiB Blöcke
Freiliste 1: 2 KiB Blöcke
Freiliste 2: 4 KiB Blöcke
Freiliste 3: 8 KiB Blöcke
Freiliste 4: 16 KiB Blöcke
Freiliste 5: 32 KiB Blöcke
Freiliste 6: 64 KiB Blöcke
Freiliste 7: 128 KiB Blöcke

*a)* Einziger BLock in der höchsten Freiliste (Freiliste 7), Blöcke in dieser Freiliste sind 128 KiB, also ist der gesammte Speicherbereich 128 KiB groß.
*b)*
    0: -
    1: -
    2: -
    3: 8 KiB ->  0x02000 (Erste 8er Block wird verwendet, hat die Adresse 0KiB bzw. 0x00000, kommt aber nicht auf die Liste)
    4: 16 KiB -> 0x04000
    5: 32 KiB -> 0x08000
    6: 64 KiB -> 0x10000
    7: -
*c)* 0x08C00 in Dec ist 35840. davor passen also noch ein 32KiB Block -> 35840-32*1024 = 3072. darein passen noch 2 Kib = 1024. darein passt also noch ein Block. Adresse des Buddys ist 0x08800, da links neben dem eig. Block ein 32er, ein 2er und ein 1er Block stehen.
*d)* 
    1. 0x05800 = 22528 / 1024 = 22 = 16+4+2 -> dieser Block ist ein rechter Buddy (weil davor ein Block mit gleicher größe steht (die +2))
    2. 0x04800 = 18432 / 1024 = 18 = 16+2 -> dieser Block ist ein rechter Buddy
    3. 0x05000 = 20480 / 1024 = 20 = 16+4 -> dieser Block ist ein LINKER Buddy (weil davor KEIN Block mit gleicher größe steht)
    Wir können nur zwei unterschiedliche Blocke verschmelzen (linker+rechter Buddy), also Block 3.(einziger linker Block) verschmelzen mit welchem?
    Wir wissen jetzt, dass 3. die Adresse vom linken ist, die Adresse vom Rechten muss also die von 3. + 2048 sein -> 20480 + 2048 = 22528,
    ALSO können Block 1. und 3. verschmolzen werden.

# Aufgabe 4
*a)* 8 * 512 Byte = 4096 Byte
*b)* 512 Byte / 2 Byte = 256 
*c)* 256 * 512 Byte = 131072 Byte = 128 KiB * 4 = 512 KiB
*d)* 2 * (256 * 256 * 512 Byte) = 2 * 33554432 Byte = 2 * 32768 KiB = 64 MiB 
    aber das würde wieder das maximum an mit 2 Byte adressierbaren Blöcken überschreiten 
*e)* THEORETISCH kann ein dreifach indirekter Blokck so groß sein: 256 * 256 * 256 * 512 Byte = 8589934592 Byte = 8388608 KiB = 8192 MiB = 8 GiB 
     Das Dateisystem hat allerdings nur 2 Byte für die Blockadressen, was bedeutet, dass es maximal 2^16 (65536) Blöcke geben kann, und nicht 16777216 Blöcke (256 * 256 * 256)
     Somit kann eine Datei aber nur MAXIMAL so groß werden: 65536 Blöcke - 1 Bootblock - 1 Superblock - 1 Inodeblock - 1 root dir Block = 65536 -4 = 65532 Blöcke -> 65532 * 512 Byte = 33552384 Byte = 32766 KByte