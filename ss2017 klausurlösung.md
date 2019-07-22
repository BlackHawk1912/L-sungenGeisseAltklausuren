# Aufgabe 1
*a)* Big-Endian-Maschiene
Was beduetet das für die Speicherung der ganzen zahl 0x87654321 im hauptspeicher?
Die zahl liegt bei einer big endian maschiene richtig herum im hauptspeicher
bei einer little endian maschiene würde sie als 21 43 65 87 im speicher liegen.
*b)* Ein byte kann an jede adresse gespeichert werden, ein halbwort nur an gerade adressen und ein word nur an durch 4 teilbare adressen
bsp:
ausgerichtet: stw $8,$9,0x12
unausgerichtet: stw $8,$9,0x11
*c)* 
> ???

# Aufgabe 2 
*a)* Was ist ein TLB Miss?
wenn virtuelle adresse nicht im Buffer liegt und aus dem Speicher geladen werden muss.
Wenn der Translation Lookaside Buffer eine Rahmennummer nicht findet.
*b)* Was ist ein Seitenfehler?
Wenn eine benötigte Seite nicht im Hauptspeicher steht.
Wenn ein Prozess auf eine ausgelagerte Seite zugreifen will, nennt man das einen Seitenfehler.
*c)* 
1. Optimaler Fall Seite wurde gefunden Prozess läuft nathlos weiter
2. Seitenadresse steht nicht im Buffer wird aber in der Seitentabelle gefunden
3. Das kann nicht vorkommen da der TLB die Rahmennummer bereits gefunden hat. Somit kann es keinen Seitenfehler mehr geben.
4. Wenn die Seite nicht im TLB und nicht auf der Rahmentabelle gefunden wird. Muss der Prozess kurz unterbrochen werden und die Seite aus dem Virtuellen Adressraum geladen werden.

# Aufgabe 3
virtuelle Adressen = 24 Bit
Seitengröße = 1024 Byte = 1 KiB
physikalischer Speicher = 2 MiB = 2048 KiB

*a)* Adressraum = 2^24Bit = 16.777.216 Byte = 16.384 KiB = 16 MiB
Adressraum / Seitengröße
16.384 KiB / 1 KiB = 16.384 Seiten pro Prozess

*b)* Physikalischer Speicher / Seitengröße = Rahmengröße
2048 KiB / 1 KiB = 2048 Rahmen in diesem System

*c)* Log2(seitengröße) = Seitenoffset
log2(1024) = 10 Bit 
virtuelle Adresse - Seitenoffset = Seitennummern
24 Bit - 10 Bit = 14 Bit seitennummer
Der TLB vergleicht alle Einträge gleichzeit, also 8 * 14 Bit = 112 Bit

*d)* wieviele bits braucht die Rahmennummer = ld(2048) = 11

0x1E63BB
    0001.1110.0110.00 11.1011.1011
    00.0111.1001.1000
    0x0798
    Seitennummer = 0x0798 -> Rahmennummer = 0x6DE 
    0x6DE =
    110.1101.1110 + 11.1011.1011
    Pyhysikalische adresse = 1.1011.0111.1011.1011.1011 = 0x1B7BBB
    
0xDA14F0
    1101.1010.0001.01 00.1111.0000
    11.0110.1000.0101 
    0x3685
    0x3685 -> 0x2C9
    010.1100.1001 + 00.1111.0000
    Physikalische Adresse = 0.1011.0010.0100.1111.0000 = 0x0B24F0
    
0xAA7C16
    1010.1010.0111.11 00.0001.0110
    10.1010.1001.1111
    0x2A9F -> 0x0C1
    000.1100.0001 + 00.0001.0110
    Physikalische Adresse = 0.0011.0000.0100.0001.0110
 
# Aufgabe 4 
1. Lesen des Blocks 2, darin Inode 1 auswählen 
2. Aus inode 1 den ersten "direkt block" auslesen und diesen Block (26) als direktory interpretieren.
3. Hier im Block 26 nach dem string "bin" suchen und den inode (3) finden.
4. Wieder den Block 2 einlesen und Inode 3 auswählen.
5. Inode 3 auswerten und zu dessen ersten direkten block lesen = (28)
6. Im Block 28 nach dem String "prog" suchen den inode finden = (8).
7. block 2 auslesen und Inode 8 auswählen.
8. In Inode 8 ersten direkten block auslesen.