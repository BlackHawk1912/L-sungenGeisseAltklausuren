# Aufgabe 1
1. ja 
2. nein
3. ja
4. ja
5. ja
6. nein

# Aufgabe 2
*a)*
    Ein Eintrag Speichert nur den zur Seite gehörigen Rahmen, die Seitennummer selbst ist der Index der Tabelle. Demnach ist ein Eintrag auch nur 4 Byte größ.
    (Seitentabelle = Für jede Seite wird der Rahmen gespeichert, oder leer)

    32 KByte:
        Offset = log2(32*1024) = 15 Bit
        Also Seitennummern = 2^(40-15) = 33554432 Einträge
        Ein Eintrag speichert nur die Rahmennummer (4 Byte)
        also 33554432 * 4 Byte = 134217728 Byte = 131072 KByte = 128 MByte

    512 KByte:
        Offset = log2(512*1024) = 19 Bit
        Also Seitennummern = 2^(40-19) = 2097152 Einträge
        also 2097152 * 4 Byte = 8388608 Byte = 8192 KByte = 8 MByte

    8 MByte (8192 KByte):
        Offset = log2(8 * 1024 * 1024) = 23 Bit
        Also Seitennummern = 2^(40-23) = 131072 Einträge
        also 131072 * 4 Byte = 524288 Byte = 512 KByte = 0,5 MByte
        
*b)*
    32 * 1024 * 1024 = 33554432 Byte MAXIMAL
    33554432 Byte / 4 Byte = 8306688 Seiten
    log2(8388608) = 23 Bit Seitennummer
    40 - 23 = 17 Bit = Offset  
    2^17 = 131072 Byte = 128 KByte = Seitengröße

# Aufgabe 3
1. nein
2. ja
3. ja
4. nein
5. nein
6. ja

# Aufgabe 4
*a)* Ein Zombie ist ein Prozess, der bereits terminiert ist aber noch in der Prozesstabelle auftaucht. Dies passiert wenn der Vaterprozess noch läuft, das Kind aber schon terminiert hat. Er verschwindet wenn der Vater ein wait() ausführt oder selbst terminiert.

*b)* Ein Waise ist ein Prozess, dessen Vaterprozess bereits terminiert hat, er aber noch läuft. Er verschwindet wenn er vom init Prozess mit der PID 1 "adoptiert" wurde.

# Aufgabe 5 
Pro Block können (512 Bytes / 4 Bytes) Blöcke gespeichert werden = 128 Blöcke 
*a)* 2 * 512 Byte = 1 KiB
*b)* (2 * 512 Byte) + (128 * 512 Byte) = 1024 Byte + 65536 Byte = 66560 Byte = 65 KiB
*c)* 65 KiB + (128 * 128 * 512 Byte) = 65 KiB + 8192 KiB = 8257 KiB
*d)* 128 * 128 * 128 * 512 Byte = 1073741824 = 1048576 KiB = 1024 MiB = 1 GiB + 8257 KiB