# Aufgabe 1
1. nein
2. > ???
3. nein
4. ja
5. nein
6. nein

# Aufgabe 2
*a)* 
    16 KiB: Offset = log2(16 * 1024) = 14 Bit -> 42 Bit für Seitennummer = 
        Einträge: 2^42
        Größe: 2^42 * 4 Byte = 16384 GiB

    256 KiB: Offset = log2(256 * 1024) = 18 Bit -> 38 Bit für Seitennummer = 
        Einträge: 2^38
        Größe: 2^38 * 4 Byte = 1024 GiB

    4 MiB: Offset = log2(4 * 1024 * 1024) = 22 Bit -> 34 Bit für Seitennummer = 
        Einträge:
        Größe: 2^34 * 4 Byte = 64 GiB
*b)* 
    64 MiB / 4 Byte = 64 * 1024 * 1024 Byte / 4 Byte = 67108864 -> log2(67108864) = 24; 56 - 24 = 32 Bit für den Offset = 4294967296  Byte = 4 GiB
    log2(4 * 1024 * 1024 * 1024) = 32 Bit -> 24 Bit für die Seitennummer =
        Einträge: 2^24
        Größe: 2^24 * 4 Byte = 64 MiB

# Aufgabe 3
1. nein
2. nein
3. nein
4. Ja
5. Nein
6. Ja

# Aufgabe 4
*a)* 7,0,1,4,3,0 = 6 Seitenfehler 
    Fifo:
       0 1 2
    7| 7 - - 
    0| 7 0 -
    1| 7 0 1
    2| 2 0 1
    0| 2 0 1
    3| 2 3 1
    0| 2 3 0
    4| 4 3 0
    2| 4 2 0
    3| 4 2 3

*b)* 
    LRU: 7,1,2,3,0 = 5 Seitenfehler
       0 1 2
    7| 7 - - | 7LRU
    0| 7 0 - | 7LRU
    1| 7 0 1 | 7LRU
    2| 2 0 1 | 7LRU
    0| 2 0 1 | 0LRU
    3| 2 0 3 | 1LRU
    0| 2 0 3 | 2LRU
    4| 4 0 3 | 3LRU
    2| 4 0 2 | 0LRU
    3| 4 3 2 | 4LRU

# Aufgabe 5
Pro Block können (8 KiB / 4 Byte) = 2048 Blocknummern gespeichert werden
*a)* 10 * 8 KiB = 80 KiB = 81920 Byte = 80 KiB
*b)* (2 * 2048 * 8 KiB) = 33554432 -> 33554432 + 81920 Byte = 33636352 Byte = 32848 KiB
*c)* (2048 * 2048 * 8192 Byte) = 34359738368 Byte -> 34359738368 Byte + 33636352 Byte = 34393374720 Byte = 33587280 KiB