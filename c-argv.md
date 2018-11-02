

| Memory address|    Value at that memory address|
|-----|----|
|0x1000:            | 0x1010                        |
|0x1010:            | 0x1020                        |
|0x1014:            | 0x1023                        |
|0x1018:            | 0x0000 // NULL                |
|0x1020:            | 'a'                           |
|0x1021:            | 'b'                           |
|0x1022:            | 'c'                           |
|0x1023:            | NUL                           |
|0x1024:            | 'd'                           |
|0x1025:            | 'e'                           |
|0x1026:            | 'f'                           |
|0x1027:            | NUL                           |




| Memory address|    Value at that memory address|
|-----|----|
| | |
|&argv              | 0x1000  // no memory for this |
| | |
|0x1000            | 0x1010                        |
|argv               | 0x1010                        |
|&argv[0]           | 0x1010                        |
| | |
|0x1010            | 0x1020                        |
|argv[0]            | 0x1020                        |
|*argv              | 0x1020                        |
|&argv[0][0]        | 0x1020                        |
| | |                                               
|0x1014            | 0x1023                        |
|argv[1]            | 0x1023                        |
|*(argv+1)          | 0x1023                        |
|&argv[1][0]        | 0x1023                        |
| | |                                               
|0x1018            | 0x0000 // NULL                |
|argv[2]            | 0x0000 // NULL                |
|*(argv+2)          | 0x0000 // NULL                |
| | |                                               
|0x1020            | 'a'                           |
|argv[0][0]         | 'a'                           |
|0x1021            | 'b'                           |
||argv[0][1]        |  'b'                          |
|0x1022            | 'c'                           |
|0x1023            | NUL                           |
|0x1024            | 'd'                           |
|argv[1][0]         | 'd'                           |
|0x1025            | 'e'                           |
|0x1026            | 'f'                           |
|0x1027            | NUL                           |


| Memory address|    Value at that memory address|
|-----|----|
| | |
|&argv = 0xffffd01c | 0xffffd010  // the value in argv is 0ffffd0010
                                   // argv  AKA  &argv[0]  AKA  &(*(argv+0)) |
| | |
|(the address of argv[0] is 0fffd0010)| |
|&argv[0] = 0xffffd010: |0xffffd000 // the value in argv[0] is 0fffd000
                                  // argv[0], AKA *argv       AKA  &argv[0][0]   |
|&argv[1] = 0xffffd014: |0xffffd006 // argv[1], AKA *(argv + 1) AKA  &argv[0][1]|
|&argv[2] = 0xffffd018: |0x00000000 // argv[2], AKA *(argv + 2)|
| | |
|&argv[0][0] = 0xffffd000: |a // argv[0][0], AKA **argv    AKA  *(*(argv+0)+0)  |
|&argv[0][1] = 0xffffd001: |p // argv[0][1], AKA *(*(argv+0) + 1)|
|&argv[0][2] = 0xffffd002: |p|
|&argv[0][3] = 0xffffd003: |l|
|&argv[0][4] = 0xffffd004: |e|
|&argv[0][5] = 0xffffd005: |NUL|
| | |
|(the address of argv[1][0] is 0xffffd006 )| |
|&argv[1][0] = 0xffffd006: |b // argv[1][0], AKA **(argv + 1)  AKA   *(argv[1]+0)  AKA   *(*(argv+1)+0)  |
|&argv[1][1] = 0xffffd007: |a   |
|0xffffd008:| n      |
|0xffffd009:| a     |
|0xffffd00a:| n     |
|0xffffd00b:| a     |
|0xffffd00c:| NUL  |
