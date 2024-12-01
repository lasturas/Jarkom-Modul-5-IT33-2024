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
5. [Konfigurasi](#konfigurasi-ip-address)
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
	address 192.233.1.195
	netmask 255.255.255.248
  	gateway 192.233.1.193
```

### BalletTwins
```
#A2
auto eth0
iface eth0 inet static
	address 192.233.1.194
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
	address 192.233.1.210
	netmask 255.255.255.248
	gateway 192.233.1.209
```

### HDD
```
#A9
auto eth0
iface eth0 inet static
	address 192.233.1.211
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


