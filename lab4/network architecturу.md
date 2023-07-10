| Device | Inteface   | AddrType | Address                        | Network                       | Description                      |
| ------ | ---------- | -------- | ------------------------------ | ----------------------------- | -------------------------------- |
| R14    | e0/3       | IPv4     | 10.3.0.1/31                    | 10.3.0.0/16                   | R14 to R19                       |
| R14    | e0/0       | IPv4     | 10.4.0.1/28                    | 10.4.0.0/16                   | R14 to R12                       |
| R14    | e0/1       | IPv4     | 10.4.0.3/28                    | 10.4.0.0/16                   | R14 to R13                       |
| R14    | e0/2       | IPv4     | 1.1.1.2/31                     | 1.1.1.0/31                    | R14 to R22(маленький провайдер)  |
| R14    | loopback   | IPv4     | 10.1.0.14/24                   | 10.1.0.0/24                   | Loopback for  Management         |
| R14    | e0/3       | IPv6     | 2001:AAAA:AAAA:1001::3/64      | 2001:AAAA:AAAA:1001::/64      | R14 to R19                       |
| R14    | e0/3       | IPv6     | FE08::14/10                    | FE08::/10                     | link-local for  Management       |
| R14    | e0/0       | IPv6     | 2001:AAAA:AAAA:1001::4/64      | 2001:AAAA:AAAA:1001::/64      | R14 to R12                       |
| R14    | e0/0       | IPv6     | FE08::14/10                    | FE08::/10                     | link-local for  Management       |
| R14    | e0/1       | IPv6     | 2001:AAAA:AAAA:1001::1/64      | 2001:AAAA:AAAA:1001::/64      | R14 to R13                       |
| R14    | e0/1       | IPv6     | FE08::14/10                    | FE08::/10                     | link-local for  Management       |
| R14    | e0/2       | IPv6     | 2001:AAAA:AAAA:1001:0101::2/80 | 2001:AAAA:AAAA:1001:0101::/80 | R14 to R22(маленький провайдер)  |
| R14    | e0/2       | IPv6     | FE08::14/10                    | FE08::/10                     | link-local for  Management       |
| R22    | e0/0       | IPv6     | 2001:AAAA:AAAA:1001:0101::1/80 | 2001:AAAA:AAAA:1001:0101::/80 | R22 to R14                       |
| R22    | e0/0       | IPv6     | FE08::22/10                    | FE08::/10                     | link-local                       |
| R22    | e0/0       | IPv4     | 1.1.1.1/31                     | 1.1.1.0/31                    | R22 to R14                       |
| R22    | loopback   | IPv4     | 101.1.1.1                      |                               |                                  |
|        |            |          |                                |                               |                                  |
|        |            |          |                                |                               |                                  |
|        |            |          |                                |                               |                                  |
|        |            |          |                                |                               |                                  |
|        |            |          |                                |                               |                                  |
|        |            |          |                                |                               |                                  |
| R19    | e0/0       | IPv4     | 10.3.0.2/31                    | 10.3.0.0/16                   | R19 to R14                       |
| R19    | loopback   | IPv4     | 10.1.0.19/24                   | 10.1.0.0/24                   | loopback                         |
| R19    | e0/0       | IPv4     | 2001:AAAA:AAAA:1001::19/64     | 2001:AAAA:AAAA:1001::/64      | R19 to R14                       |
| R19    | e0/0       | IPv4     | FE08::19/10                    | FE08::/10                     | link-local                       |
| R20    | e0/0       | IPv4     | 10.5.0.2/31                    | 10.5.0.0/16                   | R20 to R15                       |
| R20    | loopback   | IPv4     | 10.1.0.20/24                   | 10.1.0.0/24                   | loopback                         |
| R20    | e0/0       | IPv4     | 2001:AAAA:AAAA:1001::20/64     | 2001:AAAA:AAAA:1001::/64      | R20 to R15                       |
| R20    | e0/0       | IPv4     | FE08::20/10                    | FE08::/10                     | link-local                       |
| R15    | e0/3       | IPv4     | 10.5.0.1/31                    | 10.5.0.0/16                   | R14 to R19                       |
| R15    | e0/0       | IPv4     | 10.4.0.5/28                    | 10.4.0.0/16                   | R14 to R12                       |
| R15    | e0/1       | IPv4     | 10.4.0.7/28                    | 10.4.0.0/16                   | R14 to R13                       |
| R15    | e0/2       | IPv4     | 1.1.2.2/31                     | 1.1.2.0/31                    | R15 to R21(маленький провайдер)  |
| R15    | loopback   | IPv4     | 10.1.0.15/24                   | 10.1.0.0/24                   | Loopback for  Management         |
| R15    | e0/3       | IPv6     | 2001:AAAA:AAAA:1001::7/64      | 2001:AAAA:AAAA:1001::/64      | R14 to R19                       |
| R15    | e0/3       | IPv6     | FE08::15/10                    | FE08::/10                     | link-local for  Management       |
| R15    | e0/0       | IPv6     | 2001:AAAA:AAAA:1001::5/64      | 2001:AAAA:AAAA:1001::/64      | R14 to R12                       |
| R15    | e0/0       | IPv6     | FE08::15/10                    | FE08::/10                     | link-local for  Management       |
| R15    | e0/1       | IPv6     | 2001:AAAA:AAAA:1001::6/64      | 2001:AAAA:AAAA:1001::/64      | R14 to R13                       |
| R15    | e0/1       | IPv6     | FE08::15/10                    | FE08::/10                     | link-local for  Management       |
| R15    | e0/2       | IPv6     | 2001:AAAA:AAAA:1001:0301::2/80 | 2001:AAAA:AAAA:1001:0301::/80 | R14 to R21(маленький провайдер)  |
| R15    | e0/2       | IPv6     | FE08::15/10                    | FE08::/10                     | link-local for  Management       |
| R12    | e0/3       | IPv4     | 10.4.0.8/28                    | 10.4.0.0/16                   | R12 to R15                       |
| R12    | e0/3       | IPv6     | 2001:AAAA:AAAA:1001::11/64     | 2001:AAAA:AAAA:1001::/64      | R12 to R15                       |
| R12    | e0/3       | IPv6     | FE08::12/10                    | FE08::/10                     | link-local for  Management       |
| R12    | e0/2       | IPv4     | 10.4.0.2/28                    | 10.4.0.0/16                   | R12 to R14                       |
| R12    | e0/2       | IPv6     | 2001:AAAA:AAAA:1001::10/64     | 2001:AAAA:AAAA:1001::/64      | R12 to R14                       |
| R12    | e0/2       | IPv6     | FE08::12/10                    | FE08::/10                     | link-local for  Management       |
| R12    | e0/1.7     | IPv4     | 192.168.7.2/24                 | 192.168.7.0/24                | Sub for Vlan7                    |
| R12    | e0/1.10    | IPv4     | 10.1.0.12/24                   | 10.1.0.0/24                   | Sub for Vlan10 (Management Vlan) |
| R12    | e0/1.11    | IPv4     | 192.168.11.2/24                | 192.168.11.0/24               | Sub for Vlan11                   |
| R12    | e0/1.7     | IPv6     |                                |                               |                                  |
| R12    | e0/1.10    | IPv6     |                                |                               |                                  |
| R12    | e0/1.11    | IPv6     |                                |                               |                                  |
| R12    | e0/0.7     | IPv4     | 10.10.7.12/24                  | 10.10.7.0/24                  |                                  |
|        |            |          |                                |                               |                                  |
| R12    | e0/0.10    | IPv4     | 10.10.10.12/24                 | 10.10.0.0/16                  | R12 to SW4                       |
| R12    | e0/0.11    | IPv4     | 10.1.0.120/24                  | 10.10.0.0/16                  | R12 to SW5                       |
|        |            |          |                                |                               |                                  |
| R12    | loopback   | IPv4     | 10.1.0.12/24                   | 10.1.0.0/24                   | Loopback for  Management         |
|        |            |          |                                |                               | R14 to R19                       |
| R12    | e0/0       | IPv6     | 2001:AAAA:AAAA:1001::8/64      | 2001:AAAA:AAAA:1001::/64      | R14 to R12                       |
| R12    | e0/1       | IPv6     | 2001:AAAA:AAAA:1001::9/64      | 2001:AAAA:AAAA:1001::/64      | R14 to R13                       |
| R12    | e0/2       | IPv6     |                                |                               | R14 to R22(маленький провайдер)  |
| R12    | link-local | IPv6     | FE08::1/10                     | FE08::/10                     | link-local for  Management       |
|        |            |          |                                |                               |                                  |
|        |            |          |                                |                               |                                  |
|        |            |          |                                |                               |                                  |
|        |            |          |                                |                               |                                  |
|        |            |          |                                |                               |                                  |
|        |            |          |                                |                               |                                  |
|        |            |          |                                |                               |                                  |
|        |            |          |                                |                               |                                  |
|        |            |          |                                |                               |                                  |
|        |            |          |                                |                               |                                  |
|        |            |          |                                |                               |                                  |
|        |            |          |                                |                               |                                  |
|        |            |          |                                |                               |                                  |
|        |            |          |                                |                               |                                  |
|        |            |          |                                |                               |                                  |
|        |            |          |                                |                               |                                  |
|        |            |          |                                |                               |                                  |
|        |            |          |                                |                               |                                  |
|        |            |          |                                |                               |                                  |
|        |            |          |                                |                               |                                  |
|        |            |          |                                |                               |                                  |
|        |            |          |                                |                               |                                  |
|        |            |          |                                |                               |                                  |
|        |            |          |                                |                               |                                  |
|        |            |          |                                |                               |                                  |
|        |            |          |                                |                               |                                  |
|        |            |          |                                |                               |                                  |
|        |            |          |                                |                               |                                  |
|        |            |          |                                |                               |                                  |
