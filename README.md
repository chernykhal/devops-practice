## Решение задания к занятию "3.4. Операционные системы, лекция 2"
1.
unit-файл
```
vagrant@vagrant:~$ systemctl cat node_exporter
# /etc/systemd/system/node_exporter.service
[Unit]
Description=Node Exporter

[Service]
User=node_exporter
Group=node_exporter
EnvironmentFile=-/etc/sysconfig/node_exporter
ExecStart=/usr/local/bin/node_exporter $OPTIONS

[Install]
WantedBy=multi-user.target
vagrant@vagrant:~$             
```
остановка сервиса
```
vagrant@vagrant:~$ systemctl stop node_exporter
vagrant@vagrant:~$ systemctl status node_exporter
● node_exporter.service - Node Exporter
     Loaded: loaded (/etc/systemd/system/node_exporter.service; enabled; vendor preset: enabled)
     Active: inactive (dead) since Sun 2022-02-20 10:28:21 UTC; 3s ago
    Process: 1455 ExecStart=/usr/local/bin/node_exporter $OPTIONS (code=killed, signal=TERM)
   Main PID: 1455 (code=killed, signal=TERM)

Feb 20 10:28:05 vagrant node_exporter[1455]: level=info ts=2022-02-20T10:28:05.385Z caller=node_exporter.go:115 collect>
Feb 20 10:28:05 vagrant node_exporter[1455]: level=info ts=2022-02-20T10:28:05.385Z caller=node_exporter.go:115 collect>
Feb 20 10:28:05 vagrant node_exporter[1455]: level=info ts=2022-02-20T10:28:05.385Z caller=node_exporter.go:115 collect>
Feb 20 10:28:05 vagrant node_exporter[1455]: level=info ts=2022-02-20T10:28:05.385Z caller=node_exporter.go:115 collect>
Feb 20 10:28:05 vagrant node_exporter[1455]: level=info ts=2022-02-20T10:28:05.385Z caller=node_exporter.go:115 collect>
Feb 20 10:28:05 vagrant node_exporter[1455]: level=info ts=2022-02-20T10:28:05.385Z caller=node_exporter.go:199 msg="Li>
Feb 20 10:28:05 vagrant node_exporter[1455]: level=info ts=2022-02-20T10:28:05.388Z caller=tls_config.go:191 msg="TLS i>
Feb 20 10:28:21 vagrant systemd[1]: Stopping Node Exporter...
Feb 20 10:28:21 vagrant systemd[1]: node_exporter.service: Succeeded.
Feb 20 10:28:21 vagrant systemd[1]: Stopped Node Exporter.
lines 1-16/16 (END)                            
```
поднятие сервиса
```
vagrant@vagrant:~$ systemctl start node_exporter
vagrant@vagrant:~$ systemctl status node_exporter
● node_exporter.service - Node Exporter
     Loaded: loaded (/etc/systemd/system/node_exporter.service; enabled; vendor preset: enabled)
     Active: active (running) since Sun 2022-02-20 10:29:16 UTC; 1s ago
   Main PID: 1509 (node_exporter)
      Tasks: 4 (limit: 2279)
     Memory: 2.1M
     CGroup: /system.slice/node_exporter.service
             └─1509 /usr/local/bin/node_exporter

Feb 20 10:29:16 vagrant node_exporter[1509]: level=info ts=2022-02-20T10:29:16.041Z caller=node_exporter.go:115 collect>
Feb 20 10:29:16 vagrant node_exporter[1509]: level=info ts=2022-02-20T10:29:16.041Z caller=node_exporter.go:115 collect>
Feb 20 10:29:16 vagrant node_exporter[1509]: level=info ts=2022-02-20T10:29:16.041Z caller=node_exporter.go:115 collect>
Feb 20 10:29:16 vagrant node_exporter[1509]: level=info ts=2022-02-20T10:29:16.041Z caller=node_exporter.go:115 collect>
Feb 20 10:29:16 vagrant node_exporter[1509]: level=info ts=2022-02-20T10:29:16.041Z caller=node_exporter.go:115 collect>
Feb 20 10:29:16 vagrant node_exporter[1509]: level=info ts=2022-02-20T10:29:16.041Z caller=node_exporter.go:115 collect>
Feb 20 10:29:16 vagrant node_exporter[1509]: level=info ts=2022-02-20T10:29:16.041Z caller=node_exporter.go:115 collect>
Feb 20 10:29:16 vagrant node_exporter[1509]: level=info ts=2022-02-20T10:29:16.041Z caller=node_exporter.go:115 collect>
Feb 20 10:29:16 vagrant node_exporter[1509]: level=info ts=2022-02-20T10:29:16.042Z caller=node_exporter.go:199 msg="Li>
Feb 20 10:29:16 vagrant node_exporter[1509]: level=info ts=2022-02-20T10:29:16.042Z caller=tls_config.go:191 msg="TLS i>
lines 1-19/19 (END)    
```
перезагрузка сервиса
```
vagrant@vagrant:~$ systemctl restart node_exporter
vagrant@vagrant:~$ systemctl status node_exporter
● node_exporter.service - Node Exporter
     Loaded: loaded (/etc/systemd/system/node_exporter.service; enabled; vendor preset: enabled)
     Active: active (running) since Sun 2022-02-20 10:29:58 UTC; 3s ago
   Main PID: 1539 (node_exporter)
      Tasks: 5 (limit: 2279)
     Memory: 2.2M
     CGroup: /system.slice/node_exporter.service
             └─1539 /usr/local/bin/node_exporter

Feb 20 10:29:58 vagrant node_exporter[1539]: level=info ts=2022-02-20T10:29:58.389Z caller=node_exporter.go:115 collect>
Feb 20 10:29:58 vagrant node_exporter[1539]: level=info ts=2022-02-20T10:29:58.389Z caller=node_exporter.go:115 collect>
Feb 20 10:29:58 vagrant node_exporter[1539]: level=info ts=2022-02-20T10:29:58.389Z caller=node_exporter.go:115 collect>
Feb 20 10:29:58 vagrant node_exporter[1539]: level=info ts=2022-02-20T10:29:58.389Z caller=node_exporter.go:115 collect>
Feb 20 10:29:58 vagrant node_exporter[1539]: level=info ts=2022-02-20T10:29:58.389Z caller=node_exporter.go:115 collect>
Feb 20 10:29:58 vagrant node_exporter[1539]: level=info ts=2022-02-20T10:29:58.389Z caller=node_exporter.go:115 collect>
Feb 20 10:29:58 vagrant node_exporter[1539]: level=info ts=2022-02-20T10:29:58.389Z caller=node_exporter.go:115 collect>
Feb 20 10:29:58 vagrant node_exporter[1539]: level=info ts=2022-02-20T10:29:58.389Z caller=node_exporter.go:115 collect>
Feb 20 10:29:58 vagrant node_exporter[1539]: level=info ts=2022-02-20T10:29:58.389Z caller=node_exporter.go:199 msg="Li>
Feb 20 10:29:58 vagrant node_exporter[1539]: level=info ts=2022-02-20T10:29:58.392Z caller=tls_config.go:191 msg="TLS i>
lines 1-19/19 (END)            
```
2.
Процессор:
```
    node_cpu_seconds_total{cpu="0",mode="idle"} 2238.49
    node_cpu_seconds_total{cpu="0",mode="system"} 16.72
    node_cpu_seconds_total{cpu="0",mode="user"} 6.86
    process_cpu_seconds_total
```
Память:
```
    node_memory_MemAvailable_bytes 
    node_memory_MemFree_bytes
```   
Диск:
```
    node_disk_io_time_seconds_total{device="sda"} 
    node_disk_read_bytes_total{device="sda"} 
    node_disk_read_time_seconds_total{device="sda"} 
    node_disk_write_time_seconds_total{device="sda"}
```    
Сеть:
```
    node_network_receive_errs_total{device="eth0"} 
    node_network_receive_bytes_total{device="eth0"} 
    node_network_transmit_bytes_total{device="eth0"}
    node_network_transmit_errs_total{device="eth0"}
```
3. Успешно установил netdata
```
vagrant@vagrant:~$ systemctl status netdata
● netdata.service - netdata - Real-time performance monitoring
     Loaded: loaded (/lib/systemd/system/netdata.service; enabled; vendor preset: enabled)
     Active: active (running) since Sun 2022-02-20 12:41:41 UTC; 4s ago
       Docs: man:netdata
             file:///usr/share/doc/netdata/html/index.html
             https://github.com/netdata/netdata
   Main PID: 1511 (netdata)
      Tasks: 19 (limit: 2279)
     Memory: 22.2M
     CGroup: /system.slice/netdata.service
             ├─1511 /usr/sbin/netdata -D
             ├─1556 bash /usr/lib/netdata/plugins.d/tc-qos-helper.sh 1
             ├─1558 /usr/lib/netdata/plugins.d/apps.plugin 1
             └─1566 /usr/lib/netdata/plugins.d/nfacct.plugin 1

Feb 20 12:41:41 vagrant systemd[1]: Started netdata - Real-time performance monitoring.
Feb 20 12:41:41 vagrant netdata[1511]: SIGNAL: Not enabling reaper
Feb 20 12:41:41 vagrant netdata[1511]: 2022-02-20 12:41:41: netdata INFO  : MAIN : SIGNAL: Not enabling reaper
```
![image](https://user-images.githubusercontent.com/42215603/154842993-08910e00-6070-46cd-8f7b-81ee0ec6cb46.png)

4.
```
vagrant@vagrant:~$ dmesg | grep virtualization
[    0.372644] Performance Events: PMU not available due to virtualization, using software events only.
[    2.790776] systemd[1]: Detected virtualization oracle.
```
5.

