## Part 1.
* The network address 192.167.38.54/13 is defined as 192.160.0.0 ![](Screen%20Shot%202022-07-30%20at%203.42.24%20PM.png)
* Mask 255.255.255.0 is converted to /24 and 1111111111.11111111.111111.00000000 ![](Screen%20Shot%202022-07-30%20at%204.44.14%20PM.png)
* Mask /15 is converted to 255.254.0.0 and 1111111111.11111110.00000000.00000000 ![](Screen%20Shot%202022-07-30%20at%204.47.32%20PM.png)
* Mask 1111111111.11111111.11111111.11110000 is converted to 255.255.255.240 and /28 ![](Screen%20Shot%202022-07-30%20at%204.52.07%20PM.png)
* Minimum and maximum host in 12.167.38.4/8 network defined as 12.0.0.1 and 12.255.255.254 ![](Screen%20Shot%202022-07-30%20at%204.55.06%20PM.png)
* Minimum and maximum host in 12.167.38.4/11111111.11111111.00000000.00000000 network defined as 12.167.0.1 and 12.167.255.254 
![](Screen%20Shot%202022-08-02%20at%207.48.11%20PM.png)
* Minimum and maximum host in 12.167.38.4/255.255.254.0 network defined as 12.167.38.1 and 12.167.39.254 ![](Screen%20Shot%202022-07-30%20at%205.00.49%20PM.png) 
* Minimum and maximum host in 12.167.38.4/4 network defined as 0.0.0.1 and 15.255.255.254 ![](Screen%20Shot%202022-07-30%20at%205.01.52%20PM.png)
* localhost application can be accessed with 127.0.0.2, 127.1.0.1, and can’t with 194.34.23.100, 128.0.0.1
* IP 10.0.0.45 is private, 134.43.0.2 is public, 192.168.4.2 is private, 172.20.250.4 is private, 172.0.2.1 is public, 192.172.0.1 is public, 172.68.0.2 is public, 172.16.255.255 is private, 10.10.10.10 is private, 192.169.168.1 is public
* network 10.10.0.0/18 can’t have an IP address of gateways 10.0.0.1, 10.10.100.1 and can have 10.10.0.2, 10.10.10.10, 10.10.1.255

## Part 2.

![](Screen%20Shot%202022-07-31%20at%201.57.23%20PM.png)
* addresses: [192.168.100.10/16] ![](Screen%20Shot%202022-07-30%20at%205.53.56%20PM.png)
* addresses: [172.24.116.8/12] ![](Screen%20Shot%202022-07-30%20at%206.10.25%20PM.png)
* sudo apt install net-tools
* screenshot with the call and output of command
![](Screen%20Shot%202022-07-30%20at%205.58.08%20PM.png)
* screenshot with the call and output of ip r add 192.168.100.10 dev [network address] and ip r add 172.24.116.8 dev [network address] commands ![](Screen%20Shot%202022-07-30%20at%206.29.54%20PM.png) ![](Screen%20Shot%202022-07-30%20at%206.30.53%20PM.png)
* In settings of VirtualBOX: Network: Attached to: Internal Network
![](Screen%20Shot%202022-07-30%20at%209.27.09%20PM.png)
![](Screen%20Shot%202022-07-30%20at%209.27.50%20PM.png)
* the /etc/netplan/00-installer-config.yaml file with lines: - to: 192.168.100.10, via: 172.24.116.8 and - to: 172.24.116.8, via: 192.168.100.10
* screenshot with the call and output of ping 192.168.100.10 and ping 172.24.116.8 commands 
![](Screen%20Shot%202022-07-30%20at%207.17.30%20PM.png)
![](Screen%20Shot%202022-07-30%20at%207.15.31%20PM.png)

## Part 3.
* 8 Мегабит/с == 8 / 1 == 1 МегаБайт/с
* 100 МегаБайт/с == 100 * 8 * 1024 == 819200 Килобит/с
* 1 Гигабит/с == 1* 1024 == 1024 Мегабит/с
* sudo apt install iperf
* On the first machine iperf3 -s, on second iperf3 -c 192.168.100.10 
![](Screen%20Shot%202022-07-30%20at%209.22.31%20PM.png)
![](Screen%20Shot%202022-07-30%20at%209.23.07%20PM.png)

## Part 4.
* screenshot of a file simulating the firewall, screenshots of files that are run with /etc/firewall 
![](Screen%20Shot%202022-07-31%20at%2012.34.45%20PM.png)
* If the deny rule is first, it is not overwritten by the allow rule.
* screenshot with the call and output of ping and nmap commands
![](Screen%20Shot%202022-07-31%20at%201.20.47%20PM.png)
* The most common usage of nmap is to scan a system with hostname or IP address: nmap 172.24.116.8

## Part 5.
* Setup netplan setting of all machine ![](Screen%20Shot%202022-07-31%20at%207.09.49%20PM.png)
* screenshot with the call and output of netplan apply, ip -4 a, ping 10.10.0.2 and ping 10.20.0.10 commands ![](Screen%20Shot%202022-07-31%20at%207.13.00%20PM.png)
* screenshot with the call and output of net.ipv4.ip_forward = 1 command 
![](Screen%20Shot%202022-07-31%20at%207.29.57%20PM.png)
* screenshot of the /etc/sysctl.conf file with the line: net.ipv4.ip_forward = 1 
![](Screen%20Shot%202022-07-31%20at%207.33.16%20PM.png)
* screenshots of /etc/netplan/00-installer-config.yaml file with lines: gateway4: 10.10.0.1, gateway4: 10.20.0.1 and gateway4: 10.20.0.1 
![](Screen%20Shot%202022-08-01%20at%201.26.19%20PM.png)
* screenshot with the call and output of the ip r command 
![](Screen%20Shot%202022-08-01%20at%201.35.36%20PM.png)
* screenshot with the call and output of the tcpdump -tn -i [2nd network adress] and ping 10.100.0.12 commands
![](Screen%20Shot%202022-08-01%20at%201.55.07%20PM.png)
* screenshots of the /etc/netplan/00-installer-config.yaml file with lines: - to: 10.20.0.0, via: 10.100.0.12 and - to: 10.10.0.0, via: 10.100.0.11
![](Screen%20Shot%202022-08-01%20at%202.48.05%20PM.png)
* screenshot with the call and output of the ip r list 10.10.0.0/18 and ip r list 0.0.0.0/0 commands
![](Screen%20Shot%202022-08-01%20at%202.54.56%20PM.png)
* Для 0.0.0.0 выбран другой маршрут, потому что он более точный.
* screenshot with the call and output of the tcpdump -tnv -i [network adress] and traceroute 10.20.0.10 commands. The traceroute utility prints out each node a packet passes through.
![](Screen%20Shot%202022-08-01%20at%203.33.59%20PM.png)
* screenshot with the call and output of the tcpdump -n -i [network adress] icmp and ping -c 1 [random address] commands 
![](Screen%20Shot%202022-08-01%20at%203.45.03%20PM.png)

## Part 6.
* screenshot of the /etc/dhcp/dhcpd.conf file 
![](Screen%20Shot%202022-08-01%20at%204.52.28%20PM.png)
* screenshot of the resolv.conf file with nameserver 8.8.8.8.
 ![](Screen%20Shot%202022-08-01%20at%204.58.41%20PM.png)
* screenshot with the call and output of the service dhcp-server restart, ip a, ping commands 
![](Screen%20Shot%202022-08-01%20at%205.48.53%20PM.png)
* screenshot of the /etc/netplan/00-installer-config.yaml file 
![](Screen%20Shot%202022-08-01%20at%205.52.27%20PM.png)
* The first 3 points are repeated for the second virtual machine
 ![](Screen%20Shot%202022-08-01%20at%207.03.21%20PM.png)
* Использовал dhclient -r, dhclient
![](Screen%20Shot%202022-08-01%20at%209.15.51%20PM.png)

## Part 7.
* screenshot of the /etc/apache2/ports.conf file with the line: Listen 0.0.0.0:80
![](Screen%20Shot%202022-08-01%20at%2010.09.05%20PM.png)
* screenshot with the call and output of service apache2 start command 
 ![](Screen%20Shot%202022-08-01%20at%2010.12.02%20PM.png)
* screenshot with the call and output of chmod +x /etc/firewall.sh and /etc/firewall.sh commands 
![](Screen%20Shot%202022-08-01%20at%2010.25.16%20PM.png)
* Настройки /etc/firewall.sh
![](Screen%20Shot%202022-08-01%20at%2010.58.10%20PM.png)
* Add to two rules:
* screenshot with the call and output of two telnet [адрес] [порт] commands
![](Screen%20Shot%202022-08-02%20at%206.30.27%20PM.png)

## Part 8.
* screenshot with the call and output of the command that looks like: ssh -L [local port]:localhost:[Apache web server port] [ws22 host] and screenshot with the call and output of the command that looks like: ssh -R [local port]:localhost:[Apache web server port] [ws11 host] 
![](Screen%20Shot%202022-08-02%20at%207.32.41%20PM.png)
* screenshot with the call and output of both commands that look like: telnet 127.0.0.1 [local port from the previous command] 
![](Screen%20Shot%202022-08-02%20at%207.29.08%20PM.png)