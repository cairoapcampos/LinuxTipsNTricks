# LinuxTipsNTricks! ![status](https://img.shields.io/readthedocs/pip.svg)
### Using iptables ###

| Command line | Description |
| --- | --- |
| `iptables -L` <br> `iptables -t filter -L` | shows rules of filter tables |
| `iptables -t nat -L` | shows rules of nat tables |
| `iptables -t mangle -L` | shows rules of mangle tables |
| `iptables -t raw -L` | shows rules of raw tables |
| `iptables -t security -L` | shows rules of security tables |
| `iptables -F` <br> `iptables -t filter -F` | deletes rules of filter tables |
| `iptables -X` | deletes custom chains |
| `iptables -t nat -Z` <br> `iptables -t mangle -Z` <br> `iptables -t filter -Z` | clears chain counters |
| `iptables -P INPUT DROP` <br> `iptables -P OUTPUT DROP` <br> `iptables -P FORWARD DROP` | **default policies**: DROP |
| `iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 81 -j DNAT --to 10.0.0.17:8081` | **port forwarding**: from eth0 interface; tcp protocol; from port 81 to IP:port 10.0.0.17:8081 |
| `iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE` | **NAT** - IP masquerade; output interface: eth0 |
| `iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT` | **ALLOWS input** connection with states: established and related |
| `iptables -A OUTPUT -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT` | **ALLOWS output** connection with states: new, established and related |
| `iptables -A FORWARD -i eth0 -o eth1 -m mac --mac-source 00:11:22:33:44:55 -p tcp -s 10.0.0.17 -d 200.200.200.200 --sport 1030 --dport 541 -j ACCEPT` | **ALLOWS the forwarding of packets**: from eth0 interface to eth1 interface; source MAC 00:11:22:33:44:55; tcp protocol; source IP:port 10.0.0.17:1030; destination IP:port 200.200.200.200:541 |


