# Write Up Jarkom Modul 5 Kelompok IT33

| Nama | NRP |
|----------|----------|
| Ricko Mianto Jaya Saputra | 5027231031 |
| Tsaldia Hukma Cita | 5027231036 | 

# Daftar Isi
1. [IP Prefix](#ip-prefix)
2. [Spreadsheet Pembagian IP](#spreadsheet-pembagian-ip)
3. [Topology & Pembagian Subnet](#topology--pembagian-subnet)
4. [Tree Pembagian IP](#tree-pembagian-ip)
5. [Subnetting](#subnetting)
6. 

# IP Prefix
| Kelompok | Prefix IP |
|----------|----------|
| IT33 | 192.233 |   

# Spreadsheet Pembagian IP VLSM
[Spreadsheet Pembagian IP VLSM](https://docs.google.com/spreadsheets/d/16DfK6t9ueHe_vSlGAyjtVtIh90lcJA3qZ7Dzj-ddH78/edit?usp=sharing)

# Topology & Pembagian Subnet
![Add a little bit of body text (1)](https://github.com/user-attachments/assets/76c5cfcf-ca90-497f-a222-2cb9eefb5917)

> Keterangan:   
HDD: Berfungsi sebagai DNS Server.   
Fairy: Berfungsi sebagai DHCP Server.   
Web Servers: HIA, HollowZero.

> Client:   
Burnice: Memiliki 5 host.   
Lycaon: Memiliki 20 host.   
Policeboo: Memiliki 30 host.   
Caesar: Memiliki 50 host.   
Ellen: Memiliki 100 host.  
Jane: Memiliki 200 host.

# Tree Pembagian IP
![image](https://github.com/user-attachments/assets/bdf5ddf6-2858-4f3c-8cda-d34e3900cff3)

## Subnetting

### NewEridu
```
#NAT
auto eth0
iface eth0 inet dhcp
#A1
auto eth1
iface eth1 inet static
	address 192.233.1.217
	netmask 255.255.255.252
#A5
auto eth2
iface eth2 inet static
	address 192.233.1.221
	netmask 255.255.255.252
```

### LuminaSquare
```
#A1
auto eth0
iface eth0 inet static
	address 192.233.1.218
	netmask 255.255.255.252
	gateway 192.233.1.217
#A4
auto eth1
iface eth1 inet static
	address 192.233.0.1
	netmask 255.255.255.0
#A2
auto eth2
iface eth2 inet static
	address 192.233.1.193
	netmask 255.255.255.248
```

### Jane
```
auto eth0
iface eth0 inet dhcp
```

### Policeboo
```
auto eth0
iface eth0 inet dhcp
```

### HIA
```
#A2
auto eth0
iface eth0 inet static
	address 192.233.1.194
	netmask 255.255.255.248
  	gateway 192.233.1.193
```

### BalletTwins
```
#A2
auto eth0
iface eth0 inet static
	address 192.233.1.195
	netmask 255.255.255.248
  	gateway 192.233.1.193
#A3
auto eth1
iface eth1 inet static
  	address 192.233.1.1
	netmask 255.255.255.128
```

### Ellen
```
auto eth0
iface eth0 inet dhcp
```

### Lycaon
```
auto eth0
iface eth0 inet dhcp
```

### SixStreet
```
#A5
auto eth0
iface eth0 inet static
	address 192.233.1.222
	netmask 255.255.255.252
	gateway 192.233.1.221
#A9
auto eth1
iface eth1 inet static
	address 192.233.1.209
	netmask 255.255.255.248
#A6
auto eth2
iface eth2 inet static
	address 192.233.1.201
	netmask 255.255.255.248
```

### Fairy
```
#A9
auto eth0
iface eth0 inet static
	address 192.233.1.211
	netmask 255.255.255.248
	gateway 192.233.1.209
```

### HDD
```
#A9
auto eth0
iface eth0 inet static
	address 192.233.1.210
	netmask 255.255.255.248
	gateway 192.233.1.209
```

### OuterRing
```
#A6
auto eth2
iface eth2 inet static
	address 192.233.1.202
	netmask 255.255.255.248
	gateway 192.233.1.201
#A8
auto eth2
iface eth2 inet static
	address 192.233.1.129
	netmask 255.255.255.192
```

### Caesar
```
auto eth0
iface eth0 inet dhcp
```

### Burnice
```
auto eth0
iface eth0 inet dhcp
```

### ScootOutpost
```
#A6
auto eth2
iface eth2 inet static
	address 192.233.1.203
	netmask 255.255.255.248
	gateway 192.233.1.201
#A7
auto eth0
iface eth0 inet static
	address 192.233.1.225
	netmask 255.255.255.252
```

### HollowZero
```
#A7
auto eth0
iface eth0 inet static
	address 192.233.1.226
	netmask 255.255.255.252
	gateway 192.233.1.225
```

## Routing

### NewEridu
```
#A2
route add -net 192.233.1.192 netmask 255.255.255.248 gw 192.233.1.218

#A3
route add -net 192.233.1.0 netmask 255.255.255.128 gw 192.233.1.218

#A4
route add -net 192.233.0.0 netmask 255.255.255.0 gw 192.233.1.218

#A6
route add -net 192.233.1.200 netmask 255.255.255.248 gw 192.233.1.222

#A7
route add -net 192.233.1.224 netmask 255.255.255.252 gw 192.233.1.222

#A8
route add -net 192.233.1.128 netmask 255.255.255.192 gw 192.233.1.222

#A9
route add -net 192.233.1.208 netmask 255.255.255.248 gw 192.233.1.222

#Otomasi iptables awal
IP_ETH0=$(ip -4 addr show eth0 | grep -oP '(?<=inet\s)\d+(\.\d+){3}')
iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to-source $IP_ETH0
```

### LuminaSquare
```
#A3
route add -net 192.233.1.0 netmask 255.255.255.128 gw 192.233.1.195

#A7
route add -net 192.233.1.224 netmask 255.255.255.252 gw 192.233.1.217

#A8
route add -net 192.233.1.128 netmask 255.255.255.192 gw 192.233.1.217

#A9
route add -net 192.233.1.208 netmask 255.255.255.248 gw 192.233.1.217

echo 'nameserver 192.168.122.1' > /etc/resolv.conf
apt-get update
apt install isc-dhcp-relay -y

echo 'SERVERS="192.233.1.211"
INTERFACES="eth0 eth1 eth2 eth3"
OPTIONS=""
' > /etc/default/isc-dhcp-relay

echo 'net.ipv4.ip_forward=1' >> /etc/sysctl.conf

service isc-dhcp-relay restart
```

### BalletTwins
```
#A4
route add -net 192.233.0.0 netmask 255.255.255.0 gw 192.233.1.193

#A7
route add -net 192.233.1.224 netmask 255.255.255.252 gw 192.233.1.193

#A8
route add -net 192.233.1.128 netmask 255.255.255.192 gw 192.233.1.193

#A9
route add -net 192.233.1.208 netmask 255.255.255.248 gw 192.233.1.193

echo 'nameserver 192.168.122.1' > /etc/resolv.conf
apt-get update
apt install isc-dhcp-relay -y

echo 'SERVERS="192.233.1.211"
INTERFACES="eth0 eth1 eth2 eth3"
OPTIONS=""
' > /etc/default/isc-dhcp-relay

echo 'net.ipv4.ip_forward=1' >> /etc/sysctl.conf

service isc-dhcp-relay restart
```

### SiXStreet
```
#A2
route add -net 192.233.1.192 netmask 255.255.255.248 gw 192.233.1.221

#A3
route add -net 192.233.1.0 netmask 255.255.255.128 gw 192.233.1.221

#A4
route add -net 192.233.0.0 netmask 255.255.255.0 gw 192.233.1.221

#A7
route add -net 192.233.1.224 netmask 255.255.255.252 gw 192.233.1.203

#A8
route add -net 192.233.1.128 netmask 255.255.255.192 gw 192.233.1.202

echo 'nameserver 192.168.122.1' > /etc/resolv.conf
apt-get update
apt install isc-dhcp-relay -y

echo 'SERVERS="192.233.1.211"
INTERFACES="eth0 eth1 eth2 eth3"
OPTIONS=""
' > /etc/default/isc-dhcp-relay

echo 'net.ipv4.ip_forward=1' >> /etc/sysctl.conf

service isc-dhcp-relay restart
```

### OuterRing
```
#A2
route add -net 192.233.1.192 netmask 255.255.255.248 gw 192.233.1.201

#A3
route add -net 192.233.1.0 netmask 255.255.255.128 gw 192.233.1.201

#A4
route add -net 192.233.0.0 netmask 255.255.255.0 gw 192.233.1.201

#A7
route add -net 192.233.1.224 netmask 255.255.255.252 gw 192.233.1.203

#A9
route add -net 192.233.1.208 netmask 255.255.255.248 gw 192.233.1.201

echo 'nameserver 192.168.122.1' > /etc/resolv.conf
apt-get update
apt install isc-dhcp-relay -y

echo 'SERVERS="192.233.1.211"
INTERFACES="eth0 eth1 eth2 eth3"
OPTIONS=""
' > /etc/default/isc-dhcp-relay

echo 'net.ipv4.ip_forward=1' >> /etc/sysctl.conf

service isc-dhcp-relay restart
```

### ScootOutpost
```
#A2
route add -net 192.233.1.192 netmask 255.255.255.248 gw 192.233.1.201

#A3
route add -net 192.233.1.0 netmask 255.255.255.128 gw 192.233.1.201

#A4
route add -net 192.233.0.0 netmask 255.255.255.0 gw 192.233.1.201

#A8
route add -net 192.233.1.128 netmask 255.255.255.192 gw 192.233.1.202

#A9
route add -net 192.233.1.208 netmask 255.255.255.248 gw 192.233.1.201

echo 'nameserver 192.168.122.1' > /etc/resolv.conf
```

### Fairy
```
echo 'nameserver 192.168.122.1' > /etc/resolv.conf
apt-get update
apt-get install isc-dhcp-server netcat -y

echo 'INTERFACESv4="eth0"' > /etc/default/isc-dhcp-server

echo '#A8
subnet 192.233.1.128 netmask 255.255.255.192 {
        range 192.233.1.130 192.233.1.190;
        option routers 192.233.1.129; # Gateway
        option broadcast-address 192.233.1.191;
        option domain-name-servers 192.233.1.210; #IP HDD
        default-lease-time 600;
        max-lease-time 7200;
}

#A4
subnet 192.233.0.0 netmask 255.255.255.0 {
        range 192.233.0.2 192.233.0.254;
        option routers 192.233.0.1;
        option broadcast-address 192.233.0.255;
        option domain-name-servers 192.233.1.210;
        default-lease-time 600;
        max-lease-time 7200;
}

#A3
subnet 192.233.1.0 netmask 255.255.255.128 {
        range 192.233.1.2 192.233.1.126;
        option routers 192.233.1.1;
        option broadcast-address 192.233.1.127;
        option domain-name-servers 192.233.1.210;
        default-lease-time 600;
        max-lease-time 7200;
}

subnet 192.233.1.216 netmask 255.255.255.252 {}
subnet 192.233.1.192 netmask 255.255.255.248 {}
subnet 192.233.1.220 netmask 255.255.255.252 {}
subnet 192.233.1.200 netmask 255.255.255.248 {}
subnet 192.233.1.224 netmask 255.255.255.252 {}
subnet 192.233.1.208 netmask 255.255.255.248 {}
' > /etc/dhcp/dhcpd.conf

service isc-dhcp-server restart
```

### HDD
```
echo 'nameserver 192.168.122.1' > /etc/resolv.conf
apt-get update
apt-get install bind9 netcat -y

echo 'options {
        directory "/var/cache/bind";

        forwarders {
                192.168.122.1;
        };

        // dnssec-validation auto;
        allow-query{any;};
        auth-nxdomain no;
        listen-on-v6 { any; };
}; ' >/etc/bind/named.conf.options

service bind9 restart
```

### HIA & HollowZero
```
echo 'nameserver 192.168.122.1' > /etc/resolv.conf
apt-get update
apt-get install apache2 netcat -y

service apache2 start

echo 'Welcome to {hostname}' > /var/www/html/index.html

service apache2 restart
```

