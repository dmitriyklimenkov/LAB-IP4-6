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
| IP-адрес                   | Суперсеть     |   IPv6-адрес         | Суперсеть IPv6    | Описание    | Линк        |            
| :--------------------------|:-------------:| :-------------------:|:-----------------:|:-----------:|:------------|
| 152.95.0.0/20              | 152.95.0.0/19 | 200C:C0FE:AAAC:1::/64|200C:C0FE:AAAC::/48| Москва      | R13-SW5     |
| 152.95.0.0/20              | 152.95.0.0/19 | 200C:C0FE:AAAC:2::/64|200C:C0FE:AAAC::/48| Москва      | R12-SW4     |
| 152.95.16.0/22             | 152.95.0.0/19 | 200C:C0FE:AAAC:3::/64|200C:C0FE:AAAC::/48| Москва      | R14-R19     |
| 152.95.20.0/22             | 152.95.0.0/19 | 200C:C0FE:AAAC:4::/64|200C:C0FE:AAAC::/48| Москва      | R15-R20     |            
| 152.95.24.0/24             | 152.95.0.0/19 | 200C:C0FE:AAAC:5::/64|200C:C0FE:AAAC::/48| Москва      | PTP-линки   |
| 152.95.25.0/28             | 152.95.0.0/19 | 200C:C0FE:AAAC:6::/64|200C:C0FE:AAAC::/48| Москва      | LoopBack    |
| 152.95.25.16-152.95.31.254 | 152.95.0.0/19 |                      |200C:C0FE:AAAC::/48| Москва      | Резерв      |


С-Петербург
| IP-адрес                   | Суперсеть     |   IPv6-адрес         | Суперсеть IPv6    | Описание    | Линк        |            
| :--------------------------|:-------------:| :-------------------:|:-----------------:|:-----------:|:------------|
| 31.52.0.0/22               | 31.52.0.0/21  | 200C:C0FE:BBBC:1::/64|200C:C0FE:BBBC::/48| С-Петербург | R18-R17     |
| 31.52.0.0/22               | 31.52.0.0/21  | 200C:C0FE:BBBC:2::/64|200C:C0FE:BBBC::/48| С-Петербург | R18-R16     |
| 31.52.4.0/23               | 31.52.0.0/21  | 200C:C0FE:BBBC:3::/64|200C:C0FE:BBBC::/48| С-Петербург | R16-R32     |
| 31.52.6.0/26               | 31.52.0.0/21  | 200C:C0FE:BBBC:4::/64|200C:C0FE:BBBC::/48| С-Петербург | PTP-линки   |            
| 31.52.6.64/28              | 31.52.0.0/21  | 200C:C0FE:BBBC:5::/64|200C:C0FE:BBBC::/48| С-Петербург | LoopBack    |
| 31.52.6.80-31.52.7.254     | 31.52.0.0/21  |                      |200C:C0FE:BBBC::/48| С-Петербург | Резерв      |



Триада
| IP-адрес                   | Суперсеть     |   IPv6-адрес         | Суперсеть IPv6    | Описание    | Линк        |            
| :--------------------------|:-------------:| :-------------------:|:-----------------:|:-----------:|:------------|
| 90.47.74.0/30              | 90.47.74.0/24 | 200C:C0FE:CCCC:1::/64|200C:C0FE:CCCC::/48| Триада      | R23-R25     |
| 90.47.74.0/30              | 90.47.74.0/24 | 200C:C0FE:CCCC:2::/64|200C:C0FE:CCCC::/48| Триада      | R25-R26     |
| 90.47.74.4/30              | 90.47.74.0/24 | 200C:C0FE:CCCC:3::/64|200C:C0FE:CCCC::/48| Триада      | R24-R26     |
| 90.47.74.8/30              | 90.47.74.0/24 | 200C:C0FE:CCCC:4::/64|200C:C0FE:CCCC::/48| Триада      | R23-R24     |            
| 90.47.74.12/28             | 90.47.74.0/24 | 200C:C0FE:CCCC:5::/64|200C:C0FE:CCCC::/48| Триада      | LoopBack    |
| 90.47.74.16-90.47.74.254   | 90.47.74.0/24 |                      |200C:C0FE:CCCC::/48| Триада      | Резерв      |


Чокурдах
| IP-адрес                      | Суперсеть       |   IPv6-адрес         | Суперсеть IPv6    | Описание    | Линк        |            
| :-----------------------------|:---------------:| :-------------------:|:-----------------:|:-----------:|:------------|
| 201.193.45.0/25               | 201.193.45.0/24 | 200C:C0FE:DDDC:1::/64|200C:C0FE:DDDC::/48| Чокурдах    | R28-SW29    |
| 201.193.45.128/29             | 201.193.45.0/24 | 200C:C0FE:DDDC:2::/64|200C:C0FE:DDDC::/48| Чокурдах    | LoopBack    |
| 201.193.45.136-201.193.45.254 | 201.193.45.0/24 |                      |200C:C0FE:DDDC::/48| Чокурдах    | Резерв      |


Лабытнанги
| IP-адрес                      | Суперсеть       |   IPv6-адрес         | Суперсеть IPv6    | Описание    | Линк        |            
| :-----------------------------|:---------------:| :-------------------:|:-----------------:|:-----------:|:------------|
| 47.84.51.0/25                 | 47.84.51.0/24   | 200C:C0FE:EEEC:1::/64|200C:C0FE:EEEC::/48| Лабытнанги  | R27-        |
| 47.84.51.128/29               | 47.84.51.0/24   | 200C:C0FE:EEEC:2::/64|200C:C0FE:EEEC::/48| Лабытнанги  | LoopBack    |
| 47.84.51.136-47.84.51.254     | 47.84.51.0/24   |                      |200C:C0FE:EEEC::/48| Лабытнанги  | Резерв      |

Ламас
| IP-адрес                      | Суперсеть       |   IPv6-адрес         | Суперсеть IPv6    | Описание    | Линк        |            
| :-----------------------------|:---------------:| :-------------------:|:-----------------:|:-----------:|:------------|
| 21.84.15.0/25                 | 21.84.15.0/24   | 200C:C0FE:FFFC:1::/64|200C:C0FE:FFFC::/48| Ламас       | R27-        |
| 21.84.15.128/29               | 21.84.15.0/24   | 200C:C0FE:FFFC:2::/64|200C:C0FE:FFFC::/48| Ламас       | LoopBack    |
| 21.84.15.136-21.84.15.254     | 21.84.15.0/24   |                      |200C:C0FE:FFFC::/48| Ламас       | Резерв      |

