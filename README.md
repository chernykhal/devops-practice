1.
2.
```
root@vagrant:/home/vagrant# echo "dummy" >> /etc/modules
        
root@vagrant:/home/vagrant# echo "options dummy numdummies=2" > /etc/modprobe.d/dummy.conf
        
root@vagrant:/home/vagrant# cat /etc/network/interfaces
	# interfaces(5) file used by ifup(8) and ifdown(8)
	# Include files from /etc/network/interfaces.d:
	source-directory /etc/network/interfaces.d
	
	auto dummy0
	iface dummy0 inet static
        address 10.2.2.2/32
        pre-up ip link add dummy0 type dummy
        post-down ip link del dummy0
        
systemctl restart networking

ip r a 192.168.10.0/24 dev dummy0
ip r a 192.168.11.0/24 via 10.2.2.2
ip r a 192.168.11.0/30 via 10.2.2.2	

root@vagrant:/home/vagrant# ip r s
	default via 10.0.2.2 dev eth0 proto dhcp src 10.0.2.15 metric 100 
	10.0.2.0/24 dev eth0 proto kernel scope link src 10.0.2.15 
	10.0.2.2 dev eth0 proto dhcp scope link src 10.0.2.15 metric 100 
	192.168.10.0/24 dev dummy0 scope link 
	192.168.11.0/30 via 10.2.2.2 dev dummy0 
	192.168.11.0/24 via 10.2.2.2 dev dummy0 
```
3.
```
root@vagrant:/home/vagrant# ss -npta
	State        Recv-Q       Send-Q              Local Address:Port               Peer Address:Port        Process                                                         
	LISTEN       0            4096                      0.0.0.0:111                     0.0.0.0:*            users:(("rpcbind",pid=591,fd=4),("systemd",pid=1,fd=71))       
	LISTEN       0            4096                127.0.0.53%lo:53                      0.0.0.0:*            users:(("systemd-resolve",pid=592,fd=13))                      
	LISTEN       0            128                       0.0.0.0:22                      0.0.0.0:*            users:(("sshd",pid=814,fd=3))                                  
	ESTAB        0            0                       10.0.2.15:22                     10.0.2.2:50748        users:(("sshd",pid=16914,fd=4),("sshd",pid=16865,fd=4))        
	LISTEN       0            4096                         [::]:111                        [::]:*            users:(("rpcbind",pid=591,fd=6),("systemd",pid=1,fd=78))       
	LISTEN       0            128                          [::]:22                         [::]:*            users:(("sshd",pid=814,fd=4)) 
```
Процесс с PID 591 rpcbind (демон, сопоставляющий универсальные адреса и номера программ RPC)  слушает на порту 111 (sunrpc) как по IPv4 так и IPv6.

4.
```
root@vagrant:/home/vagrant# ss -puan
	State        Recv-Q       Send-Q               Local Address:Port               Peer Address:Port       Process                                                         
	UNCONN       0            0                    127.0.0.53%lo:53                      0.0.0.0:*           users:(("systemd-resolve",pid=592,fd=12))                      
	UNCONN       0            0                   10.0.2.15%eth0:68                      0.0.0.0:*           users:(("systemd-network",pid=395,fd=15))                      
	UNCONN       0            0                          0.0.0.0:111                     0.0.0.0:*           users:(("rpcbind",pid=591,fd=5),("systemd",pid=1,fd=77))       
	UNCONN       0            0                             [::]:111                        [::]:*           users:(("rpcbind",pid=591,fd=7),("systemd",pid=1,fd=79))   
```

```
root@vagrant:/home/vagrant# ss -puan sport = 100
	State               Recv-Q              Send-Q                           Local Address:Port                           Peer Address:Port             Process             
	UNCONN              0                   0                                      0.0.0.0:100                                 0.0.0.0:*                 users:(("nc",pid=17781,fd=3))
```
5.
![screenshot](https://user-images.githubusercontent.com/42215603/159746513-def0b47c-23f5-4364-9734-608efcf727cf.png)

