# Архитектура сети



##### Цель:

В данной самостоятельной работе необходимо распланировать адресное пространство
Настроить IP на всех активных портах для дальнейшей работы над проектом
Адресное пространство должно быть задокументировано

##### **Описание/Пошаговая инструкция выполнения домашнего задания:**

В этой самостоятельной работе мы самостоятельно:

1. Разработаем и задокументируете адресное пространство для лабораторного стенда.
2. Настроите ip адреса на каждом активном порту
3. Настроите каждый VPC в каждом офисе в своем VLAN.
4. Настроите VLAN/Loopback interface управления для сетевых устройств
5. Настроим сети офисов так, чтобы не возникало broadcast штормов, а использование линков было максимально оптимизировано
6. Используем IPv4. 



Задокументируем адресное пространство:

| Device | Inteface    | AddrType | Address         | SubNetwork     | Network        | Description                               |
| ------ | ----------- | -------- | --------------- | -------------- | -------------- | ----------------------------------------- |
| R14    | e0/3        | IPv4     | 100.1.2.0/31    | 100.1.2.0/31   | 100.1.2.0/24   | R14 to R19                                |
| R14    | e0/0        | IPv4     | 100.1.1.4/31    | 100.1.1.4/31   | 100.1.1.0/24   | R14 to R12                                |
| R14    | e0/1        | IPv4     | 100.1.1.2/31    | 100.1.1.2/31   | 100.1.1.0/24   | R14 to R13                                |
| R14    | e0/2        | IPv4     | 10.1.1.1/31     | 10.1.1.0/31    | 10.1.1.0/31    | R14 to R22(маленький  провайдер)          |
| R14    | loopback    | IPv4     | 100.1.0.14/32   | 100.1.0.14/32  | 100.1.0.0/24   | Loopback for Management                   |
| R14    | e1/0        | IPv4     | 100.1.1.0/31    | 100.1.1.0/31   | 100.1.1.0/24   | R14  to R15                               |
|        |             |          |                 |                |                |                                           |
| R19    | e0/0        | IPv4     | 100.1.2.1/31    | 100.1.2.0/31   | 100.1.2.0/24   | R19 to R14                                |
| R19    | loopback    | IPv4     | 100.1.0.19/32   | 100.1.0.19/32  | 100.1.0.0/24   | loopback                                  |
|        |             |          |                 |                |                |                                           |
| R20    | e0/0        | IPv4     | 100.1.3.1/31    | 100.1.3.0/31   | 100.1.3.0/24   | R20 to R15                                |
| R20    | loopback    | IPv4     | 100.1.0.20/32   | 100.1.0.20/32  | 100.1.0.0/24   | loopback                                  |
|        |             |          |                 |                |                |                                           |
| R15    | e0/3        | IPv4     | 100.1.3.0/31    | 100.1.3.0/31   | 100.1.3.0/24   | R15 to R20                                |
| R15    | e0/0        | IPv4     | 100.1.1.8/31    | 100.1.1.8/31   | 100.1.1.0/24   | R15 to R13                                |
| R15    | e0/1        | IPv4     | 100.1.1.6/31    | 100.1.1.6/31   | 100.1.1.0/24   | R15 to R12                                |
| R15    | e0/2        | IPv4     | 30.1.1.1/31     | 30.1.1.0/31    | 30.1.1.0/24    | R15 to R21(маленький  провайдер)          |
| R15    | loopback    | IPv4     | 100.1.0.15/32   | 100.1.0.15/32  | 100.1.0.0/24   | Loopback for Management                   |
| R15    | e1/0        | IPv4     | 100.1.1.1/31    | 100.1.1.0/31   | 100.1.1.0/24   | R15 to R14                                |
|        |             |          |                 |                |                |                                           |
| R12    | e0/3        | IPv4     | 100.1.1.7/31    | 100.1.1.6/31   | 100.1.1.0/24   | R12 to R15                                |
| R12    | e0/2        | IPv4     | 100.1.1.5/31    | 100.1.1.5/31   | 100.1.1.0/24   | R12 to R14                                |
| R12    | e0/1.2      | IPv4     | 100.1.1.18/31   | 100.1.1.18/31  | 100.1.1.0/24   | R12 to SW5                                |
| R12    | e0/0.3      | IPv4     | 100.1.1.16/31   | 100.1.1.16/31  | 100.1.1.0/24   | R12 to SW4                                |
| R12    | e1/0        | IPv4     | 100.1.1.10/31   | 100.1.1.10/31  | 100.1.1.0/24   | R12 to R15                                |
| R12    | loopback    | IPv4     | 100.1.0.12/32   | 100.1.0.12/32  | 100.1.0.0/24   | Loopback for Management                   |
|        |             |          |                 |                |                |                                           |
| R13    | e0/3        | IPv4     | 100.1.1.3/31    | 100.1.1.2/31   | 100.1.1.0/24   | R13 to R14                                |
| R13    | e0/2        | IPv4     | 100.1.1.9/31    | 100.1.1.9/31   | 100.1.1.0/24   | R13 to R15                                |
| R13    | e0/1.4      | IPv4     | 100.1.1.20/31   | 100.1.1.20/31  | 100.1.1.0/24   | R13 to SW4                                |
| R13    | e0/0.5      | IPv4     | 100.1.1.22/31   | 100.1.1.22/31  | 100.1.1.0/24   | R13 to SW5                                |
| R13    | loopback    | IPv4     | 100.1.0.13/32   | 100.1.0.13/32  | 100.1.0.0/24   | Loopback for Management                   |
| R13    | e1/0        | IPv4     | 100.1.1.11/31   | 100.1.1.10/31  | 100.1.1.0/24   | R13 to R12                                |
|        |             |          |                 |                |                |                                           |
| SW5    | Vlan 7      | IPv4     | 100.1.7.3/24    | 100.1.7.0/24   | 100.1.0.0/16   | Vlan 7 for e0/0 to SW 2                   |
| SW5    | Vlan 11     | IPv4     | 100.1.11.3/24   | 100.1.11.0/24  | 100.1.0.0/16   | Vlan 11 for e0/1 to SW3                   |
| SW5    | Vlan 9      | IPv4     | 100.1.1.25/31   | 100.1.1.24/31  | 100.1.0.0/16   | Vlan 9 for Ethechennel on e0/2-3 to SW4   |
| SW5    | Vlan 5      | IPv4     | 100.1.1.23/31   | 100.1.1.22/31  | 100.1.0.0/16   | Vlan 5 for e1/0 to R13                    |
| SW5    | Vlan 2      | IPv4     | 100.1.1.19/31   | 100.1.1.18/31  | 100.1.1.0/24   | Vlan 2 for e1/1 to R12                    |
| SW5    | Loopback    | IPv4     | 100.1.0.5/32    | 100.1.0.5/32   | 100.1.0.0/24   | Loopback for Management                   |
|        |             |          |                 |                |                |                                           |
| SW4    | Vlan 11     | IPv4     | 100.1.11.2/24   | 100.1.11.0/24  | 100.1.0.0/16   | Vlan 11 for e0/0 to SW3                   |
| SW4    | Vlan 7      | IPv4     | 100.1.7.2/24    | 100.1.7.0/24   | 100.1.0.0/16   | Vlan 7 for e0/1 to SW2                    |
| SW4    | Vlan 9      | IPv4     | 100.1.1.24/31   | 100.1.1.24/31  | 100.1.0.0/16   | Vlan 9 for Ethechennel on e0/2-3 to SW5   |
| SW4    | Vlan 3      | IPv4     | 100.1.1.17/31   | 100.1.1.16/31  | 100.1.1.0/24   | Vlan 3 for e1/0 to R12                    |
| SW4    | Vlan 4      | IPv4     | 100.1.1.21/31   | 100.1.1.20/31  | 100.1.1.0/24   | Vlan 4 for e1/1 to R13                    |
| SW4    | Loopback  0 | IPv4     | 100.1.0.4/32    | 100.1.0.4/32   | 100.1.0.0/24   | Loopback for Management                   |
|        |             |          |                 |                |                |                                           |
| SW3    | Vlan 10     | IPv4     | 100.1.11.4/24   | 100.1.11.0/24  | 100.1.0.0/16   | Management Vlan for SW3                   |
|        |             |          |                 |                |                |                                           |
| SW2    | Vlan 7      | IPv4     | 100.1.7.4/24    | 100.1.7.0/24   | 100.1.0.0/16   | Management Vlan for SW2                   |
|        |             |          |                 |                |                |                                           |
| VPC1   | e0          | IPv4     | 100.1.11.10/24  | 100.1.11.0/24  | 100.1.0.0/16   |                                           |
| VPC7   | e0          | IPv4     | 100.1.7.10/24   | 100.1.7.0/24   | 100.1.0.0/16   |                                           |
|        |             |          |                 |                |                |                                           |
| R21    | e0/0        | IPv4     | 30.1.1.0/31     | 30.1.1.0/31    | 100.1.0.0/16   | R21(AS301) to R15 (AS1001)                |
| R21    | e0/1        | IPv4     | 101.30.1.1/31   | 101.30.1.0/31  | 101.30.1.0/24  | R21(AS301) to R15 (AS101)                 |
| R21    | e0/2        | IPv4     | 30.15.20.1/31   | 30.15.20.0/31  | 30.15.20.0/24  | R21 (AS301) to R24(AS520)                 |
| R21    | loopback    | IPv4     | 30.1.0.21/32    | 30.1.0.21/32   |                | Loopback for Management                   |
|        |             |          |                 |                |                |                                           |
| R22    | e0/0        | IPv4     | 10.1.1.0/31     | 10.1.1.0/31    | 10.1.1.0/24    | R22 (AS101) to R14(AS1001)                |
| R22    | e0/1        | IPv4     | 101.30.1.0/31   | 101.30.1.0/31  | 101.30.1.0/24  | R22(AS101) to R21 (AS301)                 |
| R22    | e0/2        | IPv4     | 101.5.20.1/31   | 101.5.20.0/31  | 101.5.20.0/24  | R22 (AS101) to R23(AS520)                 |
| R22    | loopback    | IPv4     | 10.1.0.22/32    | 10.1.0.22/32   |                | Loopback for Management                   |
|        |             |          |                 |                |                |                                           |
| R23    | e0/0        | IPv4     | 101.5.20.0/31   | 101.5.20.0/31  | 101.5.20.0/24  | R22 (AS520) to R14(AS101)                 |
| R23    | e0/1        | IPv4     | 5.20.1.0/31     | 5.20.1.1/31    | 5.20.1.0/24    | R22(AS520) to R25 (AS520)                 |
| R23    | e0/2        | IPv4     | 5.20.1.2/31     | 5.20.1.2/31    | 5.20.1.0/24    | R23 (AS520) to R24(AS520)                 |
| R23    | e1/0        | IPv4     | 5.20.1.4/31     | 5.20.1.4/31    | 5.20.1.0/24    | R23 (AS520) to R26(AS520)                 |
| R23    | loopback    | IPv4     | 5.20.0.23/32    | 5.20.0.23/32   | 5.20.0.0/24    | Loopback for Management                   |
|        |             |          |                 |                |                |                                           |
| R24    | e0/0        | IPv4     | 30.15.20.0/31   | 30.15.20.0/31  | 30.15.20.0/24  | R24 (AS520) to R21(AS301)                 |
| R24    | e0/1        | IPv4     | 5.20.1.10/31    | 5.20.1.10/31   | 5.20.1.0/24    | R24(AS520) to R26 (AS520)                 |
| R24    | e0/2        | IPv4     | 5.20.1.3/31     | 5.20.1.2/31    | 5.20.1.0/24    | R24 (AS520) to R23(AS520)                 |
| R24    | e0/3        | IPv4     | 204.25.20.0/31  | 204.25.20.0/31 | 204.25.20.0/24 | R24 (AS520) to R18(AS2042)                |
| R24    | e1/0        | IPv4     | 5.20.1.7/31     | 5.20.1.6/31    | 5.20.1.0/24    | R24 (AS520) to R25(AS520)                 |
| R24    | loopback    | IPv4     | 5.20.0.24/32    | 5.20.0.24/32   | 5.20.0.0/24    | Loopback for Management                   |
|        |             |          |                 |                |                |                                           |
| R25    | e0/0        | IPv4     | 5.20.1.1/31     | 5.20.1.0/31    | 5.20.1.0/24    | R25 (AS520) to R23(AS520)                 |
| R25    | e0/1        | IPv4     | 100.15.20.4/31  | 100.15.20.4/31 | 100.15.20.0/24 | R25(AS520) to R27 (AS1001)                |
| R25    | e0/2        | IPv4     | 5.20.1.8/31     | 5.20.1.8/31    | 5.20.1.0/24    | R25 (AS520) to R26(AS520)                 |
| R25    | e0/3        | IPv4     | 100.15.20.2/31  | 100.15.20.2/31 | 100.15.20.0/24 | R25 (AS520) to R28(AS1001)                |
| R25    | e1/0        | IPv4     | 5.20.1.6/31     | 5.20.1.6/31    | 5.20.1.0/24    | R25 (AS520) to R24(AS520)                 |
| R25    | loopback    | IPv4     | 5.20.0.25/32    | 5.20.0.25/32   | 5.20.0.0/24    | Loopback for Management                   |
|        |             |          |                 |                |                |                                           |
| R26    | e0/0        | IPv4     | 5.20.1.11/31    | 5.20.1.10/31   | 5.20.1.0/24    | R26 (AS520) to R24(AS520)                 |
| R26    | e0/1        | IPv4     | 10.15.20.0/31   | 10.15.20.0/31  | 10.15.20.0/24  | R26(AS520) to R28 (AS1001)                |
| R26    | e0/2        | IPv4     | 5.20.1.9/31     | 5.20.1.8/31    | 5.20.1.0/24    | R26 (AS520) to R25(AS520)                 |
| R26    | e0/3        | IPv4     | 204.25.20.2/31  | 204.25.20.2/31 | 204.25.20.0/24 | R26 (AS520) to R18(AS2042)                |
| R26    | e1/0        | IPv4     | 5.20.1.5/31     | 5.20.1.4/31    | 5.20.1.0/24    | R26 (AS520) to R23(AS520)                 |
| R26    | loopback    | IPv4     | 5.20.0.26/32    | 5.20.0.26/32   | 5.20.0.0/24    | Loopback for Management                   |
|        |             |          |                 |                |                |                                           |
| R27    | e0/0        | IPv4     | 100.15.20.5/31  | 100.15.20.4/31 | 100.15.20.0/24 | R27 (AS1001) to R25(AS520)                |
| R27    | loopback    | IPv4     | 100.1.0.27/32   | 100.1.0.27/32  | 100.1.0.0/24   | Loopback for Management                   |
|        |             |          |                 |                |                |                                           |
| R28    | e0/0        | IPv4     | 100.15.20.1/31  | 100.15.20.0/31 | 100.15.20.0/24 | R28 (AS1001) to R26(AS520)                |
| R28    | e0/1        | IPv4     | 100.15.20.3/31  | 100.15.20.2/31 | 100.15.20.0/24 | R28 (AS1001) to R25(AS520)                |
| R28    | e0/2.30     | IPv4     | 100.1.30.1/24   | 100.1.30.0/24  | 100.1.0.0/16   | Sub From R28 for Vlan30 to SW29           |
| R28    | e0/2.31     | IPv4     | 100.1.31.1/24   | 100.1.31.0/24  | 100.1.0.0/16   | Sub From R28 for Vlan31 to SW29           |
| R28    | loopback    | IPv4     | 100.1.0.28/32   | 100.1.0.28/32  | 100.1.0.0/24   | Loopback for Management                   |
|        |             |          |                 |                |                |                                           |
| SW29   | Vlan 30     | IPv4     | 100.1.30.100/24 | 100.1.30.0/24  | 100.1.0.0/16   | Management Vlan For SW29                  |
|        |             |          |                 |                |                |                                           |
| VPC30  | e0          | IPv4     | 100.1.30.10/24  | 100.1.30.0/24  | 100.1.0.0/16   |                                           |
| VPC31  | e0          | IPv4     | 100.1.31.10/24  | 100.1.31.0/24  | 100.1.0.0/16   |                                           |
|        |             |          |                 |                |                |                                           |
| R18    | e0/0        | IPv4     | 204.2.2.2/31    | 204.2.2.2/31   | 204.2.2.0/24   | R18 (AS2042) to R16(AS2042)               |
| R18    | e0/1        | IPv4     | 204.2.2.0/31    | 204.2.2.0/31   | 204.2.2.0/24   | R18 (AS2042) to R17(AS2042)               |
| R18    | e0/2        | IPv4     | 204.25.20.1/31  | 204.25.20.0/31 | 204.25.20.0/24 | R18 (AS2042) to R24(AS520)                |
| R18    | e0/3        | IPv4     | 204.25.20.3/31  | 204.25.20.2/31 | 204.25.20.0/24 | R18 (AS2042) to R26(AS520)                |
| R18    | loopback    | IPv4     | 204.2.0.18/32   | 204.2.0.18/32  | 204.2.0.0/24   | Loopback for Management                   |
|        |             |          |                 |                |                |                                           |
| R17    | e0/0.6      | IPv4     | 204.2.3.0/31    | 204.2.3.0/31   | 204.2.3.0/24   | Sub R17 for Vlan 6 to  SW9                |
| R17    | e0/1        | IPv4     | 204.2.2.1/31    | 204.2.2.0/31   | 204.2.2.0/24   | R17(AS2042) to R18(AS2042)                |
| R17    | e0/2.10     | IPv4     | 204.2.3.2/31    | 204.2.3.2/31   | 204.2.3.0/24   | Sub R17 for Vlan 10 to  SW10              |
| R17    | loopback    | IPv4     | 204.2.0.17/32   | 204.2.0.17/32  | 204.2.0.0/24   | Loopback for Management                   |
|        |             |          |                 |                |                |                                           |
| R16    | e0/0.12     | IPv4     | 204.2.3.6/31    | 204.2.3.6/31   | 204.2.3.0/24   | Sub R16 for Vlan 12 to  SW10              |
| R16    | e0/1        | IPv4     | 204.2.2.3/31    | 204.2.2.2/31   | 204.2.2.0/24   | R16(AS2042) to R18(AS2042)                |
| R16    | e0/2.13     | IPv4     | 204.2.3.4/31    | 204.2.3.4/31   | 204.2.3.0/24   | Sub R16 for Vlan 13 to  SW9               |
| R16    | e0/3        | IPv4     | 204.2.1.0/31    | 204.2.1.0/31   | 204.2.1.0/24   | R16(AS2042) to R32(AS2042)                |
| R16    | loopback    | IPv4     | 204.2.0.16/32   | 204.2.0.16/32  | 204.2.0.0/24   | Loopback for Management                   |
|        |             |          |                 |                |                |                                           |
| R32    | e0/0        | IPv4     | 204.2.1.1/31    | 204.2.1.0/31   | 204.2.1.0/24   | R32 (AS2042) to R16(AS2042)               |
| R32    | loopback    | IPv4     | 204.2.0.32/32   | 204.2.0.32/32  | 204.2.0.0/24   | Loopback for Management                   |
|        |             |          |                 |                |                |                                           |
| SW9    | Vlan 14     | IPv4     | 204.2.3.8/31    | 204.2.3.8/31   | 204.2.3.0/24   | Vlan 14 for Ethechennel on e0/0-1 to SW10 |
| SW9    | Vlan 8      | IPv4     | 204.2.8.1/31    | 204.2.8.0/24   | 204.2.0.0/16   | Vlan 8 on e0/2 For VPC8                   |
| SW9    | Vlan 6      | IPv4     | 204.2.3.1/31    | 204.2.3.0/31   | 204.2.3.0/24   | Vlan 6 on e0/3 to R17                     |
| SW9    | Vlan 13     | IPv4     | 204.2.3.5/31    | 204.2.3.4/31   | 204.2.3.0/24   | Vlan 13 on e1/0 to R16                    |
| SW9    | loopback    | IPv4     | 204.2.0.9/32    | 204.2.0.9/32   | 204.2.0.0/24   | Loopback for Management                   |
|        |             |          |                 |                |                |                                           |
| SW10   | Vlan 14     | IPv4     | 204.2.3.9/31    | 204.2.3.8/31   | 204.2.3.0/24   | Vlan 14 for Ethechennel on e0/0-1 to SW9  |
| SW10   | Vlan 9      | IPv4     | 204.2.9.1/31    | 204.2.9.0/24   | 204.2.0.0/16   | Vlan 9 on e0/2 For VPC9                   |
| SW10   | Vlan 12     | IPv4     | 204.2.3.7/31    | 204.2.3.6/31   | 204.2.3.0/24   | Vlan 12 on e0/3 to R16                    |
| SW10   | Vlan 10     | IPv4     | 204.2.3.3/31    | 204.2.3.2/31   | 204.2.3.0/24   | Vlan 10 on e1/0 to R17                    |
| SW10   | loopback    | IPv4     | 204.2.0.10/32   | 204.2.0.10/32  | 204.2.0.0/24   | Loopback for Management                   |
|        |             |          |                 |                |                |                                           |
| VPC8   | e0          | IPv4     | 204.2.8.10/31   | 204.2.8.0/24   | 204.2.0.0/16   |                                           |
| VPC9   | e0          | IPv4     | 204.2.9.10/31   | 204.2.9.0/24   | 204.2.0.0/16   |                                           |



Архитектура сети с назначенными IP - адресами:



![image](https://github.com/SalminKHV/OTUS/assets/130359715/27969d3f-2f88-4980-aded-34fb462d60fd)





Настроим коммутаторы SW4 и SW5 на примере SW5

Соpдадим и подпишем Vlan's, создадим и назначим ip-адрес Loopback - интерфейсу, затем на Vlan-интерфейсах назначим IP-адреса, организуем Port-Channel по LACP и Настроим протокол hsrp для клиентских подсетей 100.1.11.0/24 и 100.1.7.0/24. Создадим Vlan 100 и переместим в него неиспользуемые порты коммутатора, переведем их в режим доступа и выключим их физически, Vlan 99 назначим нативным.

SW5(config)#vlan 2  
SW5(config-vlan)#name for_e1/1 to_R12   

SW5(config-vlan)#vlan 5  
SW5(config-vlan)#name for e1/0 to R13  
SW5(config-vlan)#vlan 7
SW5(config-vlan)#name  for e0/0 to SW2  
SW5(config-vlan)#vlan 9  
SW5(config-vlan)#name LACP e/02-3 to SW4  
SW5(config-vlan)#vlan 11  
SW5(config-vlan)#name for e0/1 to SW3    

SW5(config)#int loopback 0  

SW5(config-if)#ip address 100.1.0.5 255.255.255.255  

SW5(config-if)#int vlan 2  

SW5(config-if)#ip address 100.1.1.19 255.255.255.254  
% Warning: use /31 mask on non point-to-point interface cautiously  

SW5(config-if)#int vlan 5  
SW5(config-if)#ip add 100.2.2.23 255.255.255.254  

SW5(config-if-range)#no sh  
SW5(config-if-range)#exi    

Настроим HSRP для шлюза по умолчанию для устройств из пользовательских подсетей 100.1.9.0/24 и 100.1.11.0/24

SW5(config-if)#int vlan 7  

SW5(config-if)#ip add 100.1.7.3 255.255.255.0

SW5(config-if)#standby ver 2  
SW5(config-if)#stand 1 ip 100.1.7.1  
 SW5(config-if)#stand 1 priority 150  
SW5(config-if)#stand 1 preempt  
SW5(config-if)#no sh  
SW5(config-if)#int vlan 11
SW5(config-if)#ip add 100.1.11.3 255.255.255.0
SW5(config-if)#no sh 
SW5(config-if)#stand ver 2  
SW5(config-if)#stand 2 ip 100.1.11.1  
SW5(config-if)#no sh 

SW5(config)#int vlan 9  
SW5(config-if)#ip add 100.1.1.25 255.255.255.254  
% Warning: use /31 mask on non point-to-point interface cautiously  
SW5(config-if)#no sh  

SW5(config)#vlan 100  
SW5(config-vlan)#name Parking_Lot  
SW5(config-vlan)#vlan 99  
SW5(config-vlan)#name Native  
SW5(config-vlan)#exi  
SW5(config)#int ra e1/2-3  
SW5(config-if-range)#sw a vl 100  

Теперь настроим физические интерфейсы коммутатора, настроим port-channel:  



SW5(config)#int e0/0  
SW5(config-if)#sw t e d  
SW5(config-if)#sw m t  
SW5(config-if)#sw tr all vl 7  
SW5(config-if)#sw tr nativ vlan 99  

SW5(config-if)#int e0/1  
SW5(config-if)#sw tr e d  
SW5(config-if)#sw m tr  
SW5(config-if)#sw tr  
SW5(config-if)#sw tr all vl 11  
SW5(config-if)#sw tr nativ vlan 99  

SW5(config-if)#int e1/0  
SW5(config-if)#sw tr e d  
SW5(config-if)#sw m t  
SW5(config-if)#sw tr all vl 5  
SW5(config-if)#sw tr nativ vlan 99  

SW5(config-if)#int e1/1  
SW5(config-if)#sw tr e d  
SW5(config-if)#sw m t  
SW5(config-if)# sw tr all vl 2  
SW5(config-if)#sw tr nativ vlan 99  
SW5(config-if)#exi  

SW5(config)#int ra e0/2-3  
SW5(config-if-range)#sw tr e d  
SW5(config-if-range)#sw m tr  
SW5(config-if-range)#sw tr all vl 9  
SW5(config-if-range)#channel-group 1 mode act  
Creating a port-channel interface Port-channel 1  

SW5(config-if-range)#no sh  

  

Аналогично произведем настройку коммутатор SW4, а также настроим коммутаторы SW2 и SW3.  Все неиспользуемые порты добавим во vlan 100 и отключим физически. 

Switch(config)#host SW3  
SW3(config)#line con 0  
SW3(config-line)#logging syn  
SW3(config-line)#exec-time 300  

SW3(config)#do copy run st  
Destination filename [startup-config]?  
Building configuration...  
Compressed configuration from 822 bytes to 548 bytes[OK]  
SW3(config)#vlan 11  
SW3(config-vlan)#name Managment_Vlan  
SW3(config-vlan)#exi  
SW3(config)#int vlan 11  

SW3(config-if)#ip add 100.1.11.4 255.255.255.0 

SW3(config-if)#no sh

SW3(config-if)#int ra e0/0-1  
SW3(config-if-range)#sw tr e d  
SW3(config-if-range)#sw m tr  
SW3(config-if-range)#sw tr all vl 11  
SW3(config-if-range)#sw tr native vl 99  
SW3(config-if-range)#exi  
SW3(config)#vlan 99  
SW3(config-vlan)#name Native    

SW3(config-vlan)#exi

SW2(config)#int e0/2
SW2(config-if)#sw m a
SW2(config-if)#sw a vl 7

SW3(config)#vlan 100  
SW3(config-vlan)#name Parking_lot  
SW3(config-vlan)#exi  
SW3(config)#int ra e0/3, e1/0-3  
SW3(config-if-range)#sw a vl 100  

SW3(config)#ip default-gateway 100.1.11.1  

SW3(config)#ip route 0.0.0.0 0.0.0.0 100.1.11.1  
SW3(config)#do copy run st  

Проверим доступность соседних устройств SW4, SW5 и проверим правильность настройки hsrp ip 100.1.11.1:

![image](https://github.com/SalminKHV/OTUS/assets/130359715/558b7266-7797-4d0d-ae25-23822428458d)

![image](https://github.com/SalminKHV/OTUS/assets/130359715/e7790a36-8220-4308-98af-cf77369a29ae)





Настроим IP- адреса на VPC1 и VPC-7 и проверим доступность шлюза по умолчанию:

![image](https://github.com/SalminKHV/OTUS/assets/130359715/20906b2c-1332-4bda-b691-87d513d1ea44)



Рассмотрим настройку роутеров на примере R12 согласно таблицы адресации:

настроим имя роутера и время закрытия сессии при подключении по консоли:

Router>en  
Router#conf t  
Enter configuration commands, one per line.  End with CNTL/Z.  
Router(config)#host R12  
R12(config)#li con 0  
% Ambiguous command:  "li con 0"  
R12(config)#line con 0  
R12(config-line)#logg syn  
R12(config-line)#exec-time 300  
R12(config-line)#do copy run st  
Destination filename [startup-config]?  
Building configuration...  
[OK]   
R12(config-line)#exi  

Настроим SUB-интерфейсы для портов смотрящих в сторону L-3 коммутаторов (уровень агрегации), и поднимем физические порты, на которых настроили sub-интерфейсы:  

R12(config)#int e0/0.3  
R12(config-subif)#encapsulation dot1Q 3  
R12(config-subif)#ip address 100.1.1.16 255.255.255.254  
% Warning: use /31 mask on non point-to-point interface cautiously  
R12(config-subif)#des  
R12(config-subif)#description for VLAN3 to SW4  
R12(config-subif)#no sh   
R12(config-subif)#exi  
R12(config)#int e0/0  
R12(config-if)#no sh  
R12(config-if)#  
*Jul 22 00:46:55.933: %LINK-3-UPDOWN: Interface Ethernet0/0, changed state to up  
*Jul 22 00:46:56.933: %LINEPROTO-5-UPDOWN: Line protocol on Interface Ethernet0/0, changed state to up  
R12(config-if)#int e0/1.2  
R12(config-subif)#en  
R12(config-subif)#encapsulation dot 2  
R12(config-subif)#ip add 100.1.1.18 255.255.255.254  
% Warning: use /31 mask on non point-to-point interface cautiously  
R12(config-subif)#no sh  
R12(config-subif)#int e0/1  
R12(config-if)#no sh  
R12(config-if)#  
*Jul 22 00:48:18.563: %LINK-3-UPDOWN: Interface Ethernet0/1, changed state to up  
*Jul 22 00:48:19.563: %LINEPROTO-5-UPDOWN: Line protocol on Interface Ethernet0/1, changed state to up  
R12(config-if)#int e0/1.2  
R12(config-subif)#des  
R12(config-subif)#description For vlan 2 to SW5  
R12(config-subif)#exi  
R12(config)#int e0/2  
R12(config-if)#ip add 100.1.1.5 255.255.255.254  
% Warning: use /31 mask on non point-to-point interface cautiously  
R12(config-if)#des  
R12(config-if)#description to R14  
R12(config-if)#no sh  
R12(config-if)#  
*Jul 22 00:49:58.341: %LINK-3-UPDOWN: Interface Ethernet0/2, changed state to up  
*Jul 22 00:49:59.345: %LINEPROTO-5-UPDOWN: Line protocol on Interface Ethernet0/2, changed state to up   

Настроим физические интерфейсы роутера:    

R12(config)#int e0/3  
R12(config-if)#ip add 100.1.1.7 255.255.255.254  
% Warning: use /31 mask on non point-to-point interface cautiously  
R12(config-if)#des  
R12(config-if)#description to R15  
R12(config-if)#no sh  
R12(config-if)#  
*Jul 22 00:50:47.372: %LINK-3-UPDOWN: Interface Ethernet0/3, changed state to up  
*Jul 22 00:50:48.380: %LINEPROTO-5-UPDOWN: Line protocol on Interface Ethernet0/3, changed state to up  
R12(config-if)#int e1/0  
R12(config-if)#ip add 100.1.1.10 255.255.255.254  
% Warning: use /31 mask on non point-to-point interface cautiously  
R12(config-if)#des  
R12(config-if)#description to R13   

R12(config-if)#no sh  

R12(config-if)#exi  

Настроим Loopback - адрес для управления роутером:    



R12(config)#int loopback 0  
R12(config-if)#  
*Jul 22 00:52:04.867: %LINEPROTO-5-UPDOWN: Line protocol on Interface Loopback0, changed state to up  
R12(config-if)#ip add 100.1.0.12 255.255.255.255  

R12(config-if)#  
*Jul 22 00:52:42.792: %LINK-3-UPDOWN: Interface Ethernet1/0, changed state to up  
*Jul 22 00:52:43.796: %LINEPROTO-5-UPDOWN: Line protocol on Interface Ethernet1/0, changed state to up  

Сохраним все произведенные настройки:  

R12(config-if)#do copy run st  
Destination filename [startup-config]?  
Building configuration...  
[OK]  



На основе выше изложенных примерах настроим все остальное оборудование стенда.

Итак, мы имеем AS1001 г Москва коммутаторы SW2 и SW3 работают как коммутатор доступа, SW2 во vlan7, коммутаторо SW3 во vlan11. Коммутаторы SW4 и SW5 работают как коммутаторы уровеня агрегации с настроенным HSRP (для подсетей 100.1.11.0/24 и 100.1.7.0/24 ) и LACP (на портах E0/2-3). Для разных линков на портах созданы разные VLAN - интерфейсы, все порты SW4 и SW5 настроены для работы с разными подсетями для работы на L3 (с перспективой настройки на коммутаторах протоколов динамической маршрутизации). 

В Санкт-Петербурге коммутаторы SW9 и SW10 настроены как коммутаторы L3, т.к. офис не большой. Каждый из коммутаторов является шлюзом для каждой из клиентских подсетей(vlan8 и vlan9). 

В Чукордахе на коммутатор работает только на L2, на на порту e0/2 маршрутизатора R28 настроены sub-интерфейсы, которые являются шлюзами для подсетей vlan 30 и vlan 31.

На всех маршрутизаторах схемы настроены порты и Loopback- адреса в соответствии с таблицей адресации. Конфигурационные файлы прилагаю.





















