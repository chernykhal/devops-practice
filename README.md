1. 
```
alexander@alexander:~$ ifconfig
enp3s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.2  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::fb63:3963:df8e:c05e  prefixlen 64  scopeid 0x20<link>
        ether f0:2f:74:cf:46:10  txqueuelen 1000  (Ethernet)
        RX packets 849163  bytes 1157511282 (1.1 GB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 370450  bytes 34588761 (34.5 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device memory 0xfc500000-fc51ffff  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 521  bytes 56320 (56.3 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 521  bytes 56320 (56.3 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```
Команды для просмотра сетевых интерфейсов в линуксе:
 - ifconfig
 - ip link show
Команды для просмотра сетевых интерфейсов в винде:
 - ipconfig /all

2. 
Протокол обнаружения соседей (англ. Neighbor Discovery Protocol, NDP)

Инструменты для работы с соседями:
 - ndptool 
 - ip
3. 
Для работы с виртуальными сетями есть инструмент vlan в линуксе

Пример конфигурации:
```
auto vlan1400
iface vlan1400 inet static
        address 192.168.1.1
        netmask 255.255.255.0
        vlan_raw_device eth0
```
4.
Виды агрегации сетевых интерфейсов:
 - статический (на Cisco mode on);
 - динамический (на Cisco mode active);

Опции балансировки:
 - по MAC-адресу отправителя или MAC-адресу получателя или учитывая оба адреса
 - по IP-адресу отправителя или IP-адресу получателя или учитывая оба адреса
 - по номеру порта отправителя или номеру порта получателя или учитывая оба порта

Пример конфигурации:
```
auto bond0

iface bond0 inet static
    address 10.31.1.5
    netmask 255.255.255.0
    network 10.31.1.0
    gateway 10.31.1.254
    bond-slaves eth0 eth1
    bond-mode active-backup
    bond-miimon 100
    bond-downdelay 200
    bond-updelay 200
```
5.
 - в сети с маской /29 всего может быть 6 адресов
 - 32 подсети можно получить с маской /29 внутри сети с маской /24
 - 10.10.10.0/29, 10.10.10.8/29, 10.10.10.16/29..10.10.10.248/29

6.
Подсети /26 по 64 хоста подойдут для этой задачи.

7.
Команды для просмотра ARP в линуксе:
 - arp
 
Команды для просмотра ARP в винде:
 - arp -a
 
Для удаления одной записи:
 - arp -d 192.168.5.254
 
Для удаления полной таблицы:
 - ip neigh flush all
