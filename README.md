# LAB-IP4/6

# Лабораторная работа: Архитектура сети IPv4/6.
# Задание:
- Разработать и задокументировать адресное пространство
- Настроить адреса на каждом активном порту
- Настроить каждый VPC в каждом офисе в своем VLAN
- Настроить VLAN управления для сетевых устройств

# Решение:
# 1. Документация адресного пространства.
Общая таблица адресов

Москва
| IP-адрес                   | Суперсеть     |   IPv6-адрес          | Суперсеть IPv6    | Описание    | Линк        |            
| :--------------------------|:-------------:| :--------------------:|:-----------------:|:-----------:|:------------|
| 152.95.0.0/20              | 152.95.0.0/19 | 200C:C0FE:AAAC:10::/64|200C:C0FE:AAAC::/48| Москва      | R13-SW5     |
| 152.95.0.0/20              | 152.95.0.0/19 | 200C:C0FE:AAAC:10::/64|200C:C0FE:AAAC::/48| Москва      | R12-SW4     |
| 152.95.16.0/22             | 152.95.0.0/19 | 200C:C0FE:AAAC:30::/64|200C:C0FE:AAAC::/48| Москва      | R19-local   |
| 152.95.20.0/22             | 152.95.0.0/19 | 200C:C0FE:AAAC:40::/64|200C:C0FE:AAAC::/48| Москва      | R20-local   |            
| 152.95.24.0/24             | 152.95.0.0/19 | 200C:C0FE:AAAC:50::/64|200C:C0FE:AAAC::/48| Москва      | PTP-линки   |
| 152.95.25.0/28             | 152.95.0.0/19 | 200C:C0FE:AAAC:60::/64|200C:C0FE:AAAC::/48| Москва      | LoopBack    |
| 152.95.25.16-152.95.31.254 | 152.95.0.0/19 |                       |200C:C0FE:AAAC::/48| Москва      | Резерв      |


С-Петербург
| IP-адрес                   | Суперсеть     |   IPv6-адрес          | Суперсеть IPv6    | Описание    | Линк        |            
| :--------------------------|:-------------:| :--------------------:|:-----------------:|:-----------:|:------------|
| 31.52.0.0/22               | 31.52.0.0/21  | 200C:C0FE:BBBC:10::/64|200C:C0FE:BBBC::/48| С-Петербург | R17-SW9     |
| 31.52.0.0/22               | 31.52.0.0/21  | 200C:C0FE:BBBC:10::/64|200C:C0FE:BBBC::/48| С-Петербург | R16-SW10    |
| 31.52.4.0/23               | 31.52.0.0/21  | 200C:C0FE:BBBC:30::/64|200C:C0FE:BBBC::/48| С-Петербург | R32-local   |
| 31.52.6.0/26               | 31.52.0.0/21  | 200C:C0FE:BBBC:40::/64|200C:C0FE:BBBC::/48| С-Петербург | PTP-линки   |            
| 31.52.6.64/28              | 31.52.0.0/21  | 200C:C0FE:BBBC:50::/64|200C:C0FE:BBBC::/48| С-Петербург | LoopBack    |
| 31.52.6.80-31.52.7.254     | 31.52.0.0/21  |                       |200C:C0FE:BBBC::/48| С-Петербург | Резерв      |



Триада
| IP-адрес                   | Суперсеть     |   IPv6-адрес          | Суперсеть IPv6    | Описание    | Линк        |            
| :--------------------------|:-------------:| :--------------------:|:-----------------:|:-----------:|:------------|
| 90.47.74.0/30              | 90.47.74.0/24 | 200C:C0FE:CCCC:10::/64|200C:C0FE:CCCC::/48| Триада      | R23-R25     |
| 90.47.74.4/30              | 90.47.74.0/24 | 200C:C0FE:CCCC:20::/64|200C:C0FE:CCCC::/48| Триада      | R25-R26     |
| 90.47.74.8/30              | 90.47.74.0/24 | 200C:C0FE:CCCC:30::/64|200C:C0FE:CCCC::/48| Триада      | R24-R26     |
| 90.47.74.12/30             | 90.47.74.0/24 | 200C:C0FE:CCCC:40::/64|200C:C0FE:CCCC::/48| Триада      | R23-R24     |            
| 90.47.74.16/28             | 90.47.74.0/24 | 200C:C0FE:CCCC:50::/64|200C:C0FE:CCCC::/48| Триада      | LoopBack    |
| 90.47.74.20-90.47.74.254   | 90.47.74.0/24 |                ,      |200C:C0FE:CCCC::/48| Триада      | Резерв      |


Чокурдах
| IP-адрес                      | Суперсеть       |   IPv6-адрес          | Суперсеть IPv6    | Описание    | Линк        |            
| :-----------------------------|:---------------:| :--------------------:|:-----------------:|:-----------:|:------------|
| 201.193.45.0/25               | 201.193.45.0/24 | 200C:C0FE:DDDC:10::/64|200C:C0FE:DDDC::/48| Чокурдах    | R28-SW29    |
| 201.193.45.128/29             | 201.193.45.0/24 | 200C:C0FE:DDDC:20::/64|200C:C0FE:DDDC::/48| Чокурдах    | LoopBack    |
| 201.193.45.136-201.193.45.254 | 201.193.45.0/24 |                       |200C:C0FE:DDDC::/48| Чокурдах    | Резерв      |


Лабытнанги
| IP-адрес                      | Суперсеть       |   IPv6-адрес          | Суперсеть IPv6    | Описание    | Линк        |            
| :-----------------------------|:---------------:| :--------------------:|:-----------------:|:-----------:|:------------|
| 47.84.51.0/25                 | 47.84.51.0/24   | 200C:C0FE:EEEC:10::/64|200C:C0FE:EEEC::/48| Лабытнанги  | R27-        |
| 47.84.51.128/29               | 47.84.51.0/24   | 200C:C0FE:EEEC:20::/64|200C:C0FE:EEEC::/48| Лабытнанги  | LoopBack    |
| 47.84.51.136-47.84.51.254     | 47.84.51.0/24   |                       |200C:C0FE:EEEC::/48| Лабытнанги  | Резерв      |


Ламас
| IP-адрес                      | Суперсеть       |   IPv6-адрес          | Суперсеть IPv6    | Описание    | Линк        |            
| :-----------------------------|:---------------:| :--------------------:|:-----------------:|:-----------:|:------------|
| 21.84.15.0/25                 | 21.84.15.0/24   | 200C:C0FE:FFFC:10::/64|200C:C0FE:FFFC::/48| Ламас       | R27-        |
| 21.84.15.128/29               | 21.84.15.0/24   | 200C:C0FE:FFFC:20::/64|200C:C0FE:FFFC::/48| Ламас       | LoopBack    |
| 21.84.15.136-21.84.15.254     | 21.84.15.0/24   |                       |200C:C0FE:FFFC::/48| Ламас       | Резерв      |


Киторн
| IP-адрес                      | Суперсеть       |   IPv6-адрес          | Суперсеть IPv6    | Описание    | Линк        |            
| :-----------------------------|:---------------:| :--------------------:|:-----------------:|:-----------:|:------------|
| 74.15.24.0/25                 | 74.15.24.0/24   | 200C:C0FE:FFFF:10::/64|200C:C0FE:FFFC::/48| Киторн      | R22-        |
| 74.15.24.128/29               | 74.15.24.0/24   | 200C:C0FE:FFFF:20::/64|200C:C0FE:FFFC::/48| Киторн      | LoopBack    |
| 74.15.24.136-74.15.24.254     | 74.15.24.0/24   |                       |200C:C0FE:FFFC::/48| Киторн      | Резерв      |


| IP-адрес                      | Описание                |           
| :-----------------------------|:-----------------------:|
| 194.14.123.0/26               | Прямые линки между AS   |
| 200C:C0FE:1111:10::/64        | R14-R22                 |
| 200C:C0FE:1111:20::/64        | R15-R21                 |
| 200C:C0FE:1111:30::/64        | R22-R23                 |
| 200C:C0FE:1111:40::/64        | R21-R24                 |
| 200C:C0FE:1111:50::/64        | R18-R24                 |
| 200C:C0FE:1111:60::/64        | R18-R26                 |
| 200C:C0FE:1111:70::/64        | R27-R25                 |
| 200C:C0FE:1111:80::/64        | R28-R25                 |
| 200C:C0FE:1111:90::/64        | R28-R26                 |
| 200C:C0FE:1111:A0::/64        | R21-R22                 |



# 2. Документация адресов для интерфейсов сетевых устройств.

| Устройство                 | Интерфейс     |  Тип IP-адреса       |  IP-адрес               | Сеть        | Описание    |            
| :--------------------------|:-------------:| :-------------------:|:-----------------------:|:-----------:|:------------|
| R14                        | e0/0          | IPv4                 |152.95.24.1/30              | Москва      | R14-R12     |
| R14                        | e0/0          | IPv6                 |  | Москва      | R14-R12     |
| R14                        | e0/0          | IPv6 Link-Lokal      |FF80::14                 | Москва      | R14-R12     |
| R14                        | e0/1          | IPv4                 |152.95.24.5/30              | Москва      | R14-R13     |
| R14                        | e0/1          | IPv6                 |  | Москва      | R14-R13     |
| R14                        | e0/1          | IPv6 Link-Lokal      |FF80::14                 | Москва      | R14-R13     |
| R14                        | e0/2          | IPv4                 |194.14.123.1/30             | Москва      | R14-R22     |
| R14                        | e0/2          | IPv6                 |                         | Москва      | R14-R22     |
| R14                        | e0/2          | IPv6 Link-Lokal      |FF80::14                 | Москва      | R14-R22     |
| R14                        | e0/3          | IPv4                 |152.95.24.9/30              | Москва      | R14-R19     |
| R14                        | e0/3          | IPv6                 |  | Москва      | R14-R19     |
| R14                        | e0/3          | IPv6 Link-Lokal      |FF80::14                 | Москва      | R14-R19     |
| R15                        | e0/0          | IPv4                 |152.95.24.13/30             | Москва      | R15-R13     |
| R15                        | e0/0          | IPv6                 |  | Москва      | R15-R13     |
| R15                        | e0/0          | IPv6 Link-Lokal      |FF80::15                 | Москва      | R15-R13     |
| R15                        | e0/1          | IPv4                 |152.95.24.17/30             | Москва      | R15-R12     |
| R15                        | e0/1          | IPv6                 |  | Москва      | R15-R12     |
| R15                        | e0/1          | IPv6 Link-Lokal      |FF80::15                 | Москва      | R15-R12     |
| R15                        | e0/2          | IPv4                 |194.14.123.5/30             | Москва      | R15-R21     |
| R15                        | e0/2          | IPv6                 |                         | Москва      | R15-R21     |
| R15                        | e0/2          | IPv6 Link-Lokal      |FF80::15                 | Москва      | R15-R21     |
| R15                        | e0/3          | IPv4                 |152.95.24.21/30             | Москва      | R15-R20     |
| R15                        | e0/3          | IPv6                 |  | Москва      | R15-R20     |
| R15                        | e0/3          | IPv6 Link-Lokal      |FF80::12                 | Москва      | R15-R20     |
| R12                        | e0/0          | IPv4                 |152.95.0.1/20               | Москва      | local       |
| R12                        | e0/0          | IPv6                 |      | Москва      | local       |
| R12                        | e0/0          | IPv6 Link-Lokal      |FF80::12                 | Москва      | local       |
| R12                        | e0/1          | IPv4                 |152.95.24.25/30             | Москва      | R12-R13     |
| R12                        | e0/1          | IPv6                 |  | Москва      | R12-R13     |
| R12                        | e0/1          | IPv6 Link-Lokal      |FF80::12                 | Москва      | R12-R13     |
| R12                        | e0/2          | IPv4                 |152.95.24.2/30              | Москва      | R12-R14     |
| R12                        | e0/2          | IPv6                 |  | Москва      | R12-R14     |
| R12                        | e0/2          | IPv6 Link-Lokal      |FF80::12                 | Москва      | R12-R14     |
| R12                        | e0/3          | IPv4                 |152.95.24.18/30             | Москва      | R12-R15     |
| R12                        | e0/3          | IPv6                 |  | Москва      | R12-R15     |
| R12                        | e0/3          | IPv6 Link-Lokal      |FF80::12                 | Москва      | R12-R15     |
| R13                        | e0/0          | IPv4                 |152.95.0.2/20               | Москва      | local       |
| R13                        | e0/0          | IPv6                 |      | Москва      | local       |
| R13                        | e0/0          | IPv6 Link-Lokal      |FF80::13                 | Москва      | local       |
| R13                        | e0/1          | IPv4                 |152.95.24.26/30             | Москва      | R13-R12     |
| R13                        | e0/1          | IPv6                 |  | Москва      | R13-R12     |
| R13                        | e0/1          | IPv6 Link-Lokal      |FF80::13                 | Москва      | R13-R12     |
| R13                        | e0/2          | IPv4                 |152.95.24.14/30             | Москва      | R13-R15     |
| R13                        | e0/2          | IPv6                 |  | Москва      | R13-R15     |
| R13                        | e0/2          | IPv6 Link-Lokal      |FF80::12                 | Москва      | R13-R15     |
| R13                        | e0/3          | IPv4                 |152.95.24.6/30              | Москва      | R13-R14     |
| R13                        | e0/3          | IPv6                 |  | Москва      | R13-R14     |
| R13                        | e0/3          | IPv6 Link-Lokal      |FF80::13                 | Москва      | R13-R14     |
| R19                        | e0/0          | IPv4                 |152.95.24.10/30             | Москва      | R19-R14     |
| R19                        | e0/0          | IPv6                 |  | Москва      | R19-R14     |
| R19                        | e0/0          | IPv6 Link-Lokal      |FF80::19                 | Москва      | R19-R14     |
| R20                        | e0/0          | IPv4                 |152.95.24.22/30             | Москва      | R20-R15     |
| R20                        | e0/0          | IPv6                 |  | Москва      | R20-R15     |
| R20                        | e0/0          | IPv6 Link-Lokal      |FF80::20                 | Москва      | R20-R15     |
| R18                        | e0/0          | IPv4                 |31.52.6.1/30              | Питер      | R18-R16     |
| R18                        | e0/0          | IPv6                 |                          | Питер      | R18-R16     |
| R18                        | e0/0          | IPv6 Link-Lokal      |FF80::18                  | Питер      | R18-R16     |
| R18                        | e0/1          | IPv4                 |31.52.6.5/30              | Питер      | R18-R17     |
| R18                        | e0/1          | IPv6                 |                          | Питер      | R18-R17     |
| R18                        | e0/1          | IPv6 Link-Lokal      |FF80::18                  | Питер      | R18-R17     |
| R18                        | e0/2          | IPv4                 |194.14.123.9/30           | Питер      | R18-R24     |
| R18                        | e0/2          | IPv6                 |                          | Питер      | R18-R24     |
| R18                        | e0/2          | IPv6 Link-Lokal      |FF80::18                  | Питер      | R18-R24     |
| R18                        | e0/3          | IPv4                 |194.14.123.13/30          | Питер      | R18-R26     |
| R18                        | e0/3          | IPv6                 |                          | Питер      | R18-R26     |
| R18                        | e0/3          | IPv6 Link-Lokal      |FF80::18                  | Питер      | R18-R26     |
| R16                        | e0/0          | IPv4                 |31.52.0.1/22              | Питер      | local     |
| R16                        | e0/0          | IPv6                 |                          | Питер      | local     |
| R16                        | e0/0          | IPv6 Link-Lokal      |FF80::16                  | Питер      | local     |
| R16                        | e0/1          | IPv4                 |31.52.6.2/30              | Питер      | R16-R18     |
| R16                        | e0/1          | IPv6                 |                          | Питер      | R16-R18     |
| R16                        | e0/1          | IPv6 Link-Lokal      |FF80::16                  | Питер      | R16-R18     |
| R16                        | e0/2          | IPv4                 |31.52.6.9/30              | Питер      | R16-R17     |
| R16                        | e0/2          | IPv6                 |                          | Питер      | R16-R17     |
| R16                        | e0/2          | IPv6 Link-Lokal      |FF80::16                  | Питер      | R16-R17     |
| R16                        | e0/3          | IPv4                 |31.52.6.13/30             | Питер      | R16-R32     |
| R16                        | e0/3          | IPv6                 |                          | Питер      | R16-R32     |
| R16                        | e0/3          | IPv6 Link-Lokal      |FF80::16                  | Питер      | R16-R32     |
| R17                        | e0/0          | IPv4                 |31.52.0.2/22              | Питер      | local     |
| R17                        | e0/0          | IPv6                 |                          | Питер      | local     |
| R17                        | e0/0          | IPv6 Link-Lokal      |FF80::17                  | Питер      | local     |
| R17                        | e0/1          | IPv4                 |31.52.6.6/30              | Питер      | R17-R18     |
| R17                        | e0/1          | IPv6                 |                          | Питер      | R17-R18     |
| R17                        | e0/1          | IPv6 Link-Lokal      |FF80::17                  | Питер      | R17-R18     |
| R17                        | e0/2          | IPv4                 |31.52.6.10/30             | Питер      | R17-R16     |
| R17                        | e0/2          | IPv6                 |                          | Питер      | R17-R16     |
| R17                        | e0/2          | IPv6 Link-Lokal      |FF80::17                  | Питер      | R17-R16     |
| R32                        | e0/0          | IPv4                 |31.52.6.14/30             | Питер      | R32-R16     |
| R32                        | e0/0          | IPv6                 |                          | Питер      | R32-R16     |
| R32                        | e0/0          | IPv6 Link-Lokal      |FF80::20                  | Питер      | R32-R16     |
| R23                        | e0/0          | IPv4                 |194.14.123.17/30          | Триада      | R23-R22     |
| R23                        | e0/0          | IPv6                 |                          | Триада      | R23-R22     |
| R23                        | e0/0          | IPv6 Link-Lokal      |FF80::23                  | Триада      | R23-R22     |
| R23                        | e0/1          | IPv4                 |90.47.74.1/30             | Триада      | R23-R25     |
| R23                        | e0/1          | IPv6                 |                          | Триада      | R23-R25     |
| R23                        | e0/1          | IPv6 Link-Lokal      |FF80::23                  | Триада      | R23-R25     |
| R23                        | e0/2          | IPv4                 |90.47.74.5/30             | Триада      | R23-R24     |
| R23                        | e0/2          | IPv6                 |                          | Триада      | R23-R24     |
| R23                        | e0/2          | IPv6 Link-Lokal      |FF80::23                  | Триада      | R23-R24     |
| R24                        | e0/0          | IPv4                 |194.14.123.21/30          | Триада      | R24-R21     |
| R24                        | e0/0          | IPv6                 |                          | Триада      | R24-R21     |
| R24                        | e0/0          | IPv6 Link-Lokal      |FF80::24                  | Триада      | R24-R21     |
| R24                        | e0/1          | IPv4                 |90.47.74.9/30             | Триада      | R24-R26     |
| R24                        | e0/1          | IPv6                 |                          | Триада      | R24-R26     |
| R24                        | e0/1          | IPv6 Link-Lokal      |FF80::24                  | Триада      | R24-R26     |
| R24                        | e0/2          | IPv4                 |90.47.74.6/30             | Триада      | R24-R23     |
| R24                        | e0/2          | IPv6                 |                          | Триада      | R24-R23     |
| R24                        | e0/2          | IPv6 Link-Lokal      |FF80::24                  | Триада      | R24-R23     |
| R24                        | e0/3          | IPv4                 |194.14.123.10/30          | Триада      | R24-R18     |
| R24                        | e0/3          | IPv6                 |                          | Триада      | R24-R18     |
| R24                        | e0/3          | IPv6 Link-Lokal      |FF80::24                  | Триада      | R24-R18     |
| R25                        | e0/0          | IPv4                 |90.47.74.2/30             | Триада      | R25-R23     |
| R25                        | e0/0          | IPv6                 |                          | Триада      | R25-R23     |
| R25                        | e0/0          | IPv6 Link-Lokal      |FF80::25                  | Триада      | R25-R23     |
| R25                        | e0/1          | IPv4                 |194.14.123.25/30          | Триада      | R25-R27     |
| R25                        | e0/1          | IPv6                 |                          | Триада      | R25-R27     |
| R25                        | e0/1          | IPv6 Link-Lokal      |FF80::25                  | Триада      | R25-R27     |
| R25                        | e0/2          | IPv4                 |90.47.74.13/30            | Триада      | R25-R26     |
| R25                        | e0/2          | IPv6                 |                          | Триада      | R25-R26     |
| R25                        | e0/2          | IPv6 Link-Lokal      |FF80::25                  | Триада      | R25-R26     |
| R25                        | e0/3          | IPv4                 |194.14.123.29/30          | Триада      | R25-R28     |
| R25                        | e0/3          | IPv6                 |                          | Триада      | R25-R28     |
| R25                        | e0/3          | IPv6 Link-Lokal      |FF80::25                  | Триада      | R25-R28     |
| R26                        | e0/0          | IPv4                 |90.47.74.10/30            | Триада      | R26-R24     |
| R26                        | e0/0          | IPv6                 |                          | Триада      | R26-R24     |
| R26                        | e0/0          | IPv6 Link-Lokal      |FF80::26                  | Триада      | R26-R24     |
| R26                        | e0/1          | IPv4                 |194.14.123.33/30          | Триада      | R26-R28     |
| R26                        | e0/1          | IPv6                 |                          | Триада      | R26-R28     |
| R26                        | e0/1          | IPv6 Link-Lokal      |FF80::26                  | Триада      | R26-R28     |
| R26                        | e0/2          | IPv4                 |90.47.74.14/30            | Триада      | R26-R25     |
| R26                        | e0/2          | IPv6                 |                          | Триада      | R26-R25     |
| R26                        | e0/2          | IPv6 Link-Lokal      |FF80::26                  | Триада      | R26-R25     |
| R26                        | e0/3          | IPv4                 |194.14.123.14/30          | Триада      | R26-R18     |
| R26                        | e0/3          | IPv6                 |                          | Триада      | R26-R18     |
| R26                        | e0/3          | IPv6 Link-Lokal      |FF80::26                  | Триада      | R26-R18     |
| R28                        | e0/0          | IPv4                 |194.14.123.34/30          | Чокурдах      | R28-R26     |
| R28                        | e0/0          | IPv6                 |                          | Чокурдах      | R28-R26     |
| R28                        | e0/0          | IPv6 Link-Lokal      |FF80::28                  | Чокурдах      | R28-R26     |
| R28                        | e0/1          | IPv4                 |194.14.123.30/30          | Чокурдах      | R28-R25     |
| R28                        | e0/1          | IPv6                 |                          | Чокурдах      | R28-R25     |
| R28                        | e0/1          | IPv6 Link-Lokal      |FF80::28                  | Чокурдах      | R28-R25     |
| R28                        | e0/2          | IPv4                 |201.193.45.0/25           | Чокурдах      | local       |
| R28                        | e0/2          | IPv6                 |                          | Чокурдах      | local       |
| R28                        | e0/2          | IPv6 Link-Lokal      |FF80::28                  | Чокурдах      | local       |
| R27                        | e0/0          | IPv4                 |194.14.123.26/30          | Лабытнанги      | R27-R25     |
| R27                        | e0/0          | IPv6                 |                          | Лабытнанги      | R27-R25     |
| R27                        | e0/0          | IPv6 Link-Lokal      |FF80::27                  | Лабытнанги      | R27-R25     |
| R22                        | e0/0          | IPv4                 |194.14.123.2/30           | Киторн      | R22-R14     |
| R22                        | e0/0          | IPv6                 |                          | Киторн      | R22-R14     |
| R22                        | e0/0          | IPv6 Link-Lokal      |FF80::22                  | Киторн      | R22-R14     |
| R22                        | e0/1          | IPv4                 |194.14.123.35/30          | Киторн      | R22-R21     |
| R22                        | e0/1          | IPv6                 |                          | Киторн      | R22-R21     |
| R22                        | e0/1          | IPv6 Link-Lokal      |FF80::22                  | Киторн      | R22-R21     |
| R22                        | e0/2          | IPv4                 |194.14.123.18/30          | Киторн      | R22-R23     |
| R22                        | e0/2          | IPv6                 |                          | Киторн      | R22-R23     |
| R22                        | e0/2          | IPv6 Link-Lokal      |FF80::22                  | Киторн      | R22-R23     |
| R21                        | e0/0          | IPv4                 |194.14.123.6/30           | Ламас      | R21-R15     |
| R21                        | e0/0          | IPv6                 |                          | Ламас      | R21-R15     |
| R21                        | e0/0          | IPv6 Link-Lokal      |FF80::21                  | Ламас      | R21-R15     |
| R21                        | e0/1          | IPv4                 |194.14.123.36/30          | Ламас      | R21-R22     |
| R21                        | e0/1          | IPv6                 |                          | Ламас      | R21-R22     |
| R21                        | e0/1          | IPv6 Link-Lokal      |FF80::21                  | Ламас      | R21-R22     |
| R21                        | e0/2          | IPv4                 |194.14.123.22/30          | Ламас      | R21-R24     |
| R21                        | e0/2          | IPv6                 |                          | Ламас      | R21-R24     |
| R21                        | e0/2          | IPv6 Link-Lokal      |FF80::21                  | Ламас      | R21-R24     |





# Схема сети Москва
![](https://github.com/dmitriyklimenkov/LAB-IP4-6/blob/main/%D0%A1%D1%85%D0%B5%D0%BC%D0%B0%20%D1%81%D0%B5%D1%82%D0%B8%20%D0%9C%D0%BE%D1%81%D0%BA%D0%B2%D0%B0.png)
