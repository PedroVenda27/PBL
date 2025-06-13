# PBL

# 1. Topologia física e lógica 

# 2. Endereçamento IPv4 

## SWITCHES

### SWITCHES – EDIFÍCIO A

| **Batidor** | **Switch** | **VLAN** | **Endereço IP**     | **Máscara**         | **Gateway**         |
|-------------|------------|----------|----------------------|---------------------|---------------------|
| 1           | BA1-S1     | 90       | 192.168.90.11        | 255.255.255.224     | 192.168.90.1        |
| 1           | BA1-S2     | 90       | 192.168.90.12        | 255.255.255.224     | 192.168.90.1        |
| 1           | BA1-S3     | 90       | 192.168.90.13        | 255.255.255.224     | 192.168.90.1        |
| 1           | BA1-S4     | 90       | 192.168.90.14        | 255.255.255.224     | 192.168.90.1        |
| 2           | BA2-S5     | 90       | 192.168.90.21        | 255.255.255.224     | 192.168.90.1        |
| 2           | BA2-S6     | 90       | 192.168.90.22        | 255.255.255.224     | 192.168.90.1        |

---

### SWITCHES – EDIFÍCIO B

| **Batidor** | **Switch** | **VLAN** | **Endereço IP**     | **Máscara**         | **Gateway**         |
|-------------|------------|----------|----------------------|---------------------|---------------------|
| 1           | BB1-S1     | 91       | 192.168.91.11        | 255.255.255.224     | 192.168.91.1        |
| 1           | BB1-S2     | 91       | 192.168.91.12        | 255.255.255.224     | 192.168.91.1        |
| 1           | BB1-S3     | 91       | 192.168.91.13        | 255.255.255.224     | 192.168.91.1        |
| 1           | BB1-S4     | 91       | 192.168.91.14        | 255.255.255.224     | 192.168.91.1        |
| 1           | BB1-S5     | 91       | 192.168.91.15        | 255.255.255.224     | 192.168.91.1        |
| 1           | BB1-S6     | 91       | 192.168.91.16        | 255.255.255.224     | 192.168.91.1        |
| 2           | BB2-S1     | 91       | 192.168.91.21        | 255.255.255.224     | 192.168.91.1        |
| 2           | BB2-S2     | 91       | 192.168.91.22        | 255.255.255.224     | 192.168.91.1        |
| 2           | BB2-S3     | 91       | 192.168.91.23        | 255.255.255.224     | 192.168.91.1        |
| 2           | BB2-S4     | 91       | 192.168.91.24        | 255.255.255.224     | 192.168.91.1        |
| 2           | BB2-S5     | 91       | 192.168.91.25        | 255.255.255.224     | 192.168.91.1        |
| 2           | BB2-S6     | 91       | 192.168.91.26        | 255.255.255.224     | 192.168.91.1        |

### SWITCHES – DATACENTER

| **Switch** | **VLAN** | **Endereço IP**     | **Máscara**         | **Gateway**         |
|------------|----------|----------------------|---------------------|---------------------|
| LAN-DATACENTER    | 92       | 192.168.92.2        | 255.255.255.224     | 192.168.92.1        |


## ROUTERS

| **Router**         | **Interface** | **Endereço IP** |
|--------------------|---------------|------------------|
| **ROUTER CENTRAL** | e0/0          | 10.0.1.2         |
|                    | e0/1          | 10.0.2.2         |
|                    | e0/2          | 10.0.3.2         |
|                    | e0/3          | 10.0.4.2         |
| **ROUTER A**       | e0/1          | 10.0.1.1         |
| **ROUTER B**       | e0/0          | 10.0.2.1         |
| **ROUTER DATABASE**| e0/0          | 10.0.3.1         |
|                    | e0/1.92       | 192.168.92.1     |
|                    | e0/1.93       | 192.168.93.1     |
| **ROUTER ISP**     | e0/0          | 10.0.4.1         |
|                    | e0/1          | 192.168.94.1     |

| VLAN ID | Nome VLAN                | Segmento             | Local        | Nº Hosts | Nº Hosts Reais | CIDR  | Sub-rede             | Gateway         | Máscara             | IPs utilizáveis     |
|---------|--------------------------|-----------------------|--------------|----------|-----------------|-------|-----------------------|------------------|----------------------|----------------------|
| 10      | VLAN_ALUNOS_A            | Alunos                | Edifício A   | 80       | 83              | /25   | 192.168.10.0/25       | 192.168.10.1     | 255.255.255.128      | .2 – .126            |
| 11      | VLAN_ALUNOS_B            | Alunos                | Edifício B   | 155      | 158             | /24   | 192.168.11.0/24       | 192.168.11.1     | 255.255.255.0        | .2 – .254            |
| 20      | VLAN_PROFESSORES_A       | Professores           | Edifício A   | 6        | 9               | /28   | 192.168.20.0/28       | 192.168.20.1     | 255.255.255.240      | .2 – .14             |
| 21      | VLAN_PROFESSORES_B       | Professores           | Edifício B   | 31       | 34              | /26   | 192.168.21.0/26       | 192.168.21.1     | 255.255.255.192      | .2 – .62             |
| 30      | VLAN_SERV_FINANCEIROS    | Serviços Financeiros  | Edifício B   | 10       | 13              | /28   | 192.168.30.0/28       | 192.168.30.1     | 255.255.255.240      | .2 – .14             |
| 40      | VLAN_SERV_ACADEMICOS     | Serviços Académicos   | Edifício B   | 16       | 19              | /27   | 192.168.40.0/27       | 192.168.40.1     | 255.255.255.224      | .2 – .30             |
| 50      | VLAN_SINFO               | Serviços Informática  | Edifício A   | 5        | 8               | /28   | 192.168.50.0/28       | 192.168.50.1     | 255.255.255.240      | .2 – .14             |
| 60      | VLAN_CONVIDADOS_A        | Convidados            | Edifício A   | 1        | 4               | /29   | 192.168.60.0/29       | 192.168.60.1     | 255.255.255.248      | .2 – .6              |
| 61      | VLAN_CONVIDADOS_B        | Convidados            | Edifício B   | 5        | 8               | /28   | 192.168.61.0/28       | 192.168.61.1     | 255.255.255.240      | .2 – .14             |
| 70      | VLAN_TELEFONES_A         | Telefones             | Edifício A   | 15       | 18              | /27   | 192.168.70.0/27       | 192.168.70.1     | 255.255.255.224      | .2 – .30             |
| 71      | VLAN_TELEFONES_B         | Telefones             | Edifício B   | 25       | 28              | /27   | 192.168.71.0/27       | 192.168.71.1     | 255.255.255.224      | .2 – .30             |
| 80      | VLAN_IMPRESSORAS_A       | Impressoras           | Edifício A   | 8        | 11              | /28   | 192.168.80.0/28       | 192.168.80.1     | 255.255.255.240      | .2 – .14             |
| 81      | VLAN_IMPRESSORAS_B       | Impressoras           | Edifício B   | 7        | 10              | /28   | 192.168.81.0/28       | 192.168.81.1     | 255.255.255.240      | .2 – .14             |
| 90      | VLAN_GESTAO_REDE_A       | Gestão equipamentos   | Edifício A   | 5        | 8               | /27   | 192.168.90.0/27       | 192.168.90.1     | 255.255.255.224      | .2 – .30             |
| 91      | VLAN_GESTAO_REDE_B       | Gestão equipamentos   | Edifício B   | 5        | 8               | /27   | 192.168.91.0/27       | 192.168.91.1     | 255.255.255.224      | .2 – .30             |
| 92      | VLAN_GESTAO_REDE_DATASET | Gestão equipamentos   | Datacenter   | 5        | 8               | /27   | 192.168.92.0/27       | 192.168.92.1     | 255.255.255.224      | .2 – .30             |
| 93      | DATACENTER               | Datacenter            | Datacenter   | 29       | 29              | /27   | 192.168.93.0/27       | 192.168.93.1     | 255.255.255.224      | .2 – .30             |
| 94      | ISP                      | ISP                   | Datacenter   | 29       | 29              | /27   | 192.168.94.0/27       | 192.168.94.1     | 255.255.255.224      | .2 – .30             |
| 99      | PARKING_LOT              | Parking               | Ambos        | -        | -               | -     | -                     | -                | -                    | -                    |


# 3. VLANs

## 3.1 CRIAR VLANS

## SWITCH EDIFICIO A
```
vlan 10
 name ALUNOS_A
vlan 20
 name PROFESSORES_A
vlan 50
 name SERV_INFO
vlan 60
 name CONVIDADOS_A
vlan 70
 name TELEFONES_A
vlan 80
 name IMPRESSORAS_A
vlan 90
 name GESTAO_REDE_A
vlan 99
 name PARKING_LOT
```


## SWITCH EDIFICIO B
``` 
vlan 11
 name ALUNOS_B
vlan 21
 name PROFESSORES_B
vlan 30
 name SERV_FINANCEIROS
vlan 40
 name SERV_ACADEMICOS
vlan 61
 name CONVIDADOS_B
vlan 71
 name TELEFONES_B
vlan 81
 name IMPRESSORAS_B
vlan 91
 name GESTAO_REDE_B
vlan 99
 name PARKING_LOT
```

## SWITCH DATACENTER
``` 
vlan 92
 name GESTAO_REDE_DATASET
vlan 93
 name DATACENTER
vlan 99
 name PARKING_LOT
```

## 3.1 TRUNK PORTS

## EDIFICIO A

```
------------ BASTIDOR 1 ------------
interface range ethernet0/0 - 2
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk native vlan 60
 switchport trunk allowed vlan 10,20,50,60,70,80,90
 
------------ BASTIDOR 2 ------------ 
interface range ethernet0/0
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk native vlan 60
 switchport trunk allowed vlan 10,20,50,60,70,80,90

------------ ENTREBASTIDORES ------------ 

interface range ethernet1/2
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk native vlan 60
 switchport trunk allowed vlan 10,20,50,60,70,80,90

interface range ethernet0/3
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk native vlan 60
 switchport trunk allowed vlan 10,20,50,60,70,80,90
 
interface range ethernet1/0
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk native vlan 60
 switchport trunk allowed vlan 10,20,50,60,70,80,90

```
 
## EDIFICIO B

```
interface range ethernet0/0 - 2
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk native vlan 61
 switchport trunk allowed vlan 11,21,30,40,50,61,71,81,91
 
interface range ethernet0/3
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk native vlan 61
 switchport trunk allowed vlan 11,21,30,40,50,61,71,81,91
 ```

## DATABASE 


```
------- LAN DATACENTER -------
interface Et0/0
 switchport trunk encapsulation dot1q     
 switchport mode trunk
 switchport trunk allowed vlan 92,93
exit

```

## 3.1 ACCESS PORTS

```
Interface <interface id>
Switchport mode access
Switchport access vlan <vlan id>
Exit
```

# 4. Routing estático 

# 5. Router on-a-stick (Edifício A) 

## ROUTER A 

```bash
interface e0/3
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk native vlan 60
 switchport trunk allowed vlan 10,20,50,60,70,80,90
 
 
! VLAN 10 - ALUNOS_A
interface Ethernet0/0.10
 encapsulation dot1Q 10
 ip address 192.168.10.1 255.255.255.128

! VLAN 20 - PROFESSORES_A
interface Ethernet0/0.20
 encapsulation dot1Q 20
 ip address 192.168.20.1 255.255.255.240

! VLAN 50 - SINFO
interface Ethernet0/0.50
 encapsulation dot1Q 50
 ip address 192.168.50.1 255.255.255.240 ---

! VLAN 60 - CONVIDADOS_A
interface Ethernet0/0.60
 encapsulation dot1Q 60
 ip address 192.168.60.1 255.255.255.248 ---

! VLAN 70 - TELEFONES_A
interface Ethernet0/0.70
 encapsulation dot1Q 70
 ip address 192.168.70.1 255.255.255.224

! VLAN 80 - IMPRESSORAS_A
interface Ethernet0/0.80
 encapsulation dot1Q 80
 ip address 192.168.80.1 255.255.255.240

! VLAN 90 - GESTÃO_REDE_A
interface Ethernet0/0.90
 encapsulation dot1Q 90
 ip address 192.168.90.1 255.255.255.224
```

# 6. Legacy Inter-VLAN Routing (Edifício B) 

## ROUTER B 

```bash
interface Ethernet0/3
 ip address 192.168.11.1 255.255.255.0
 no shutdown

interface Ethernet1/0
 ip address 192.168.21.1 255.255.255.192
 no shutdown

interface Ethernet1/1
 ip address 192.168.30.1 255.255.255.240
 no shutdown

interface Ethernet1/2
 ip address 192.168.40.1 255.255.255.224
 no shutdown

interface Ethernet1/3
 ip address 192.168.61.1 255.255.255.248
 no shutdown

interface Ethernet2/0
 ip address 192.168.71.1 255.255.255.224
 no shutdown

interface Ethernet2/1
 ip address 192.168.81.1 255.255.255.248
 no shutdown

interface Ethernet2/2
 ip address 192.168.91.1 255.255.255.224
 no shutdown
````

## SWITCH BB6 

```bash
interface Ethernet0/3
 switchport mode access
 switchport access vlan 11
exit
interface Ethernet1/0
 switchport mode access
 switchport access vlan 21
exit
interface Ethernet1/1
 switchport mode access
 switchport access vlan 30
exit
interface Ethernet1/2
 switchport mode access
 switchport access vlan 40
exit
interface Ethernet1/3
 switchport mode access
 switchport access vlan 61
exit
interface Ethernet2/0
 switchport mode access
 switchport access vlan 71
exit
interface Ethernet2/1
 switchport mode access
 switchport access vlan 81
exit
interface Ethernet2/2
 switchport mode access
 switchport access vlan 91
exit

interface vlan 91
 ip address 192.168.91.26 255.255.255.224
 no shutdown
exit

ip default-gateway 192.168.91.1

end
write memory
```

# 7. Servidor DHCP (Router Datacenter) 

## ROUTER DATABASE 

```bash
conf t
ip dhcp excluded-address 10.0.1.1 10.0.1.2
ip dhcp excluded-address 10.0.2.1 10.0.2.2
ip dhcp excluded-address 10.0.3.1 10.0.3.2
ip dhcp excluded-address 10.0.4.1 10.0.4.2

ip dhcp excluded-address 192.168.10.1
ip dhcp excluded-address 192.168.11.1
ip dhcp excluded-address 192.168.20.1
ip dhcp excluded-address 192.168.21.1
ip dhcp excluded-address 192.168.30.1
ip dhcp excluded-address 192.168.40.1
ip dhcp excluded-address 192.168.50.1
ip dhcp excluded-address 192.168.60.1
ip dhcp excluded-address 192.168.61.1
ip dhcp excluded-address 192.168.70.1
ip dhcp excluded-address 192.168.71.1
ip dhcp excluded-address 192.168.80.1
ip dhcp excluded-address 192.168.81.1
ip dhcp excluded-address 192.168.90.1
ip dhcp excluded-address 192.168.90.11 192.168.90.14
ip dhcp excluded-address 192.168.90.21 192.168.90.22
ip dhcp excluded-address 192.168.91.1
ip dhcp excluded-address 192.168.91.11 192.168.91.16
ip dhcp excluded-address 192.168.91.21 192.168.91.26
ip dhcp excluded-address 192.168.92.1
exit


conf t

ip dhcp pool POOL_ALUNOS_A
 network 192.168.10.0 255.255.255.128
 default-router 192.168.10.1
 dns-server 8.8.8.8

ip dhcp pool POOL_ALUNOS_B
 network 192.168.11.0 255.255.255.0
 default-router 192.168.11.1
 dns-server 8.8.8.8

ip dhcp pool POOL_PROF_A
 network 192.168.20.0 255.255.255.240
 default-router 192.168.20.1
 dns-server 8.8.8.8

ip dhcp pool POOL_PROF_B
 network 192.168.21.0 255.255.255.192
 default-router 192.168.21.1
 dns-server 8.8.8.8

ip dhcp pool POOL_FIN
 network 192.168.30.0 255.255.255.240
 default-router 192.168.30.1
 dns-server 8.8.8.8

ip dhcp pool POOL_ACA
 network 192.168.40.0 255.255.255.224
 default-router 192.168.40.1
 dns-server 8.8.8.8

ip dhcp pool POOL_SINFO
 network 192.168.50.0 255.255.255.240
 default-router 192.168.50.1
 dns-server 8.8.8.8

ip dhcp pool POOL_CONV_A
 network 192.168.60.0 255.255.255.248
 default-router 192.168.60.1
 dns-server 8.8.8.8

ip dhcp pool POOL_CONV_B
 network 192.168.61.0 255.255.255.240
 default-router 192.168.61.1
 dns-server 8.8.8.8

ip dhcp pool POOL_TEL_A
 network 192.168.70.0 255.255.255.224
 default-router 192.168.70.1
 dns-server 8.8.8.8

ip dhcp pool POOL_TEL_B
 network 192.168.71.0 255.255.255.224
 default-router 192.168.71.1
 dns-server 8.8.8.8

ip dhcp pool POOL_IMP_A
 network 192.168.80.0 255.255.255.240
 default-router 192.168.80.1
 dns-server 8.8.8.8

ip dhcp pool POOL_IMP_B
 network 192.168.81.0 255.255.255.240
 default-router 192.168.81.1
 dns-server 8.8.8.8

ip dhcp pool POOL_GEST_A
 network 192.168.90.0 255.255.255.224
 default-router 192.168.90.1
 dns-server 8.8.8.8

ip dhcp pool POOL_GEST_B
 network 192.168.91.0 255.255.255.224
 default-router 192.168.91.1
 dns-server 8.8.8.8

ip dhcp pool POOL_GEST_DATA
 network 192.168.92.0 255.255.255.224
 default-router 192.168.92.1
 dns-server 8.8.8.8

exit
```
 
## ROUTER A (Relay)

```bash
conf t

interface e0/0.10
 ip helper-address 10.0.3.1
exit

interface e0/0.20
 ip helper-address 10.0.3.1
exit

interface e0/0.50
 ip helper-address 10.0.3.1
exit

interface e0/0.60
 ip helper-address 10.0.3.1
exit

interface e0/0.70
 ip helper-address 10.0.3.1
exit

interface e0/0.80
 ip helper-address 10.0.3.1
exit

interface e0/0.90
 ip helper-address 10.0.3.1
exit

write memory
```
 
 
## ROUTER B (Relay)

 ```bash
conf t
interface range e0/3 e1/0 - 3 e2/0 - 2
 ip helper-address 10.0.3.1
exit
```

# 8. Redundância de L2 (Spanning Tree Protocol) 


## 8.1 EDIFICIO B 

## TODOS OS SWITCHS

```
configure terminal
spanning-tree vlan 11
spanning-tree vlan 21
spanning-tree vlan 30
spanning-tree vlan 40
spanning-tree vlan 61
spanning-tree vlan 71
spanning-tree vlan 81
spanning-tree vlan 91
exit
```


## BB2-S6 (ROOT BRIDGE)

```
configure terminal
spanning-tree vlan 11 priority 0
spanning-tree vlan 21 priority 0
spanning-tree vlan 30 priority 0
spanning-tree vlan 40 priority 0
spanning-tree vlan 61 priority 0
spanning-tree vlan 71 priority 0
spanning-tree vlan 81 priority 0
spanning-tree vlan 91 priority 0
exit
```

## BB1-S1 a S6, BB2-S1 a S5 (OUTROS)

```
configure terminal
spanning-tree vlan 11 priority 32768
spanning-tree vlan 21 priority 32768
spanning-tree vlan 30 priority 32768
spanning-tree vlan 40 priority 32768
spanning-tree vlan 61 priority 32768
spanning-tree vlan 71 priority 32768
spanning-tree vlan 81 priority 32768
spanning-tree vlan 91 priority 32768
exit
```


## 8.2 EDIFICIO A 


## TODOS OS SWITCHS

```
configure terminal
spanning-tree vlan 10
spanning-tree vlan 20
spanning-tree vlan 50
spanning-tree vlan 60
spanning-tree vlan 70
spanning-tree vlan 80
spanning-tree vlan 91
exit
```

## BA1-S1 (ROOT BRIDGE)

```
configure terminal
spanning-tree vlan 10 root primary
spanning-tree vlan 20 root primary
spanning-tree vlan 50 root primary
spanning-tree vlan 60 root primary
spanning-tree vlan 70 root primary
spanning-tree vlan 80 root primary
spanning-tree vlan 90 root primary
exit
```


## BA1-S3 (ROOT SECONDARY)

```
configure terminal
spanning-tree vlan 10 root secondary
spanning-tree vlan 20 root secondary
spanning-tree vlan 50 root secondary
spanning-tree vlan 60 root secondary
spanning-tree vlan 70 root secondary
spanning-tree vlan 80 root secondary
spanning-tree vlan 90 root secondary
exit
```

## BA1-S2, BA1-S4, BA2-S1, BA2-S2 (OUTROS)

```
configure terminal
spanning-tree vlan 10 priority 32768
spanning-tree vlan 20 priority 32768
spanning-tree vlan 50 priority 32768
spanning-tree vlan 60 priority 32768
spanning-tree vlan 70 priority 32768
spanning-tree vlan 80 priority 32768
spanning-tree vlan 90 priority 32768
exit
```

