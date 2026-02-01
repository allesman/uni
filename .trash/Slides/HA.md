# Füllen Sie die Tabellen so aus, dass sie die Tags nach den Speicherzugriffen zeigen.

a)
    # Cachezeilengröße:             32 Bytes
    # Anzahl an Zeilenmengen:       4
    # Assoziativität:               4-fach
    # Ersetzungsstrategie:          LRU

| Set | Tag 1      |     | Tag 2      |     | Tag 3      |     | Tag 4      |     |
| --- | ---------- | --- | ---------- | --- | ---------- | --- | ---------- | --- |
| 0   | 0x017FFFFE | 1   |            |     |            |     |            |     |
| 1   | 0x0000000B |     |            |     |            |     |            |     |
| 2   | 0x00000008 | 9   | 0x0000000B | 10  | 0x017FFFFD | 12  | 0x00AAAAAA | 11  |
| 3   | 0x017FFFFD | 3   |            |     |            |     |            |     |

b)
    # Cachezeilengröße:             32 Bytes
    # Anzahl an Zeilenmengen:       4
    # Assoziativität:               4-fach
    # Ersetzungsstrategie:          LFU


| Set | Tag 1   |     | Tag 2   |     | Tag 3 |     | Tag 4  |     |
| --- | ------- | --- | ------- | --- | ----- | --- | ------ | --- |
| 0   | 17FFFFE | 2   |         |     |       |     |        |     |
| 1   | B       | 1   |         |     |       |     |        |     |
| 2   | 8       | 3   | 17FFFFD | 6   | 9     | 2   | AAAAAA | 1   |
| 3   | 17FFFFD | 4   |         |     |       |     |        |     |


c)
    # Cachezeilengröße:             32 Bytes
    # Anzahl an Zeilenmengen:       4
    # Assoziativität:               4-fach
    # Ersetzungsstrategie:          FIFO

| Set | Tag 1   |     | Tag 2  |     | Tag 3   |     | Tag 4 |     |
| --- | ------- | --- | ------ | --- | ------- | --- | ----- | --- |
| 0   | 17FFFFE | 1   |        |     |         |     |       |     |
| 1   | B       | 9   |        |     |         |     |       |     |
| 2   | B       | 7   | AAAAAA | 8   | 17FFFFD | 9   | A     | 6   |
| 3   | 17FFFFD | 3   |        |     |         |     |       |     |


d)
    # Cachezeilengröße:             16 Bytes
    # Anzahl an Zeilenmengen:       8
    # Assoziativität:               2-fach
    # Ersetzungsstrategie:          LRU

| Set | Tag 1      |     | Tag 2      |     |
| --- | ---------- | --- | ---------- | --- |
| 0   | 0x017FFFFE | 1   |            |     |
| 1   |            |     |            |     |
| 2   | 0x0000000B |     |            |     |
| 3   |            |     |            |     |
| 4   | 0x0000000B | 7   | 0x017FFFFD | 8   |
| 5   | 0x00AAAAAA | 3   | 0x017FFFFD | 4   |
| 6   | 0x017FFFFD | 1   |            |     |
| 7   | 0x017FFFFD | 1   |            |     |

