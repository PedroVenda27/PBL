# ACL necesarias por VLAN
1. Alunos

| PERMIT | DENY |
| :---: | :---: |
| HTTP institucional | HTTP |
| Internet | FTP |
| DHCP |  |
| Interedificios |  |
| Impresoras edificio propio |  |

2. Professores
   
| PERMIT | DENY |
| :---: | :---: |
| HTTP institucional | FTP |
| Internet |  |
| DHCP |  |
| Interedificios |  |
| Impresoras edificio propio |  |
|  HTTP |  |

3. Serviços Financieiros
   

| PERMIT | DENY |
| :---: | :---: |
| HTTP institucional | HTTP |
| Internet | FTP |
| DHCP | Interedificios |
| Impresoras edificio propio |  |

4. Serviços Academicos
   
| PERMIT | DENY |
| :---: | :---: |
| HTTP institucional | FTP |
| Internet | Interedificios |
| DHCP |  |
| Impresoras edificio propio |  |
|  HTTP |  |

5. Informática -> Permit All

6. Convidados -> Deny All + Permit Internet + Permit DHCP

7. Impresoras -> Deny All + Permit DHCP
8. Telefones -> Deny All + Permit Interedificios + Permit DHCP

9. Gestao Equipamentos -> Deny All + Permit Interedificios + Permit DHCP


## Reglas necesarias
### Deny any
- permit tcp any host [IP_INST] eq 80 ! HTTP inst
- permit tcp any host [IP_HTTP_SERVER] eq 80 ! HTTP
- permit tcp any host [IP_FTP] eq 21 ! FTP
- permit tcp any host [IP_INTERNET] eq 80 ! Internet 1
- permit tcp any host [IP_INTERNET] eq 443 ! Internet 2
- permit udp any host [IP_ROUTER_DATACENTER] eq 67 ! DHCP
- permit ip [IP_REDE_ORIGEN + MASCARA_INVERTIDA] [IP_REDE_DESTINO + MASCARA_INVERTIDA] ! Interedificios
- permit ip [IP_REDE_ORIGEN + MASCARA_INVERTIDA] [IP_REDE_IMPRESORAS_EDIFICIO + MASCARA_INVERTIDA]
- deny any any

## SCRIPTS ACL

### GENERAL
#### GESTAO

permit udp any host 10.0.3.1 eq 67 ! DHCP

permit ip [IP_REDE_ORIGEN + MASCARA_INVERTIDA] [IP_REDE_DESTINO + MASCARA_INVERTIDA] ! Interedificios

¿How can we set in single point?

### EDIFICIO A
#### ALUNOS

permit tcp any host 192.168.93.3 eq 80 ! HTTP inst

permit tcp any host 192.168.94.1 eq 80 ! Internet 1

permit tcp any host 192.168.94.1 eq 443 ! Internet 2

permit udp any host 10.0.3.1 eq 67 ! DHCP

permit ip 192.168.10.0 0.0.0.127 192.168.80.0 0.0.0.15 ! Impresoras

permit ip 192.168.10.0 0.0.0.127 192.168.11.0 0.0.0.255 ! Interedificios

#### PROFESORES

permit tcp any host 192.168.93.3 eq 80 ! HTTP inst

permit tcp any host 192.168.94.1 eq 80 ! Internet 1

permit tcp any host 192.168.94.1 eq 443 ! Internet 2

permit udp any host 10.0.3.1 eq 67 ! DHCP

permit tcp any host 192.168.93.4 eq 80 ! HTTP

permit ip 192.168.20.0 0.0.0.15 192.168.80.0 0.0.0.15 ! Impresoras

permit ip 192.168.20.0 0.0.0.15 192.168.21.0 0.0.0.63 ! Interedificios

#### INFORMATICA

permit tcp any host 192.168.93.3 eq 80 ! HTTP inst

permit tcp any host 192.168.94.1 eq 80 ! Internet 1

permit tcp any host 192.168.94.1 eq 443 ! Internet 2

permit udp any host 10.0.3.1 eq 67 ! DHCP

permit tcp any host 192.168.93.4 eq 80 ! HTTP

permit ip 192.168.50.0 0.0.0.15 192.168.80.0 0.0.0.15 ! Impresoras

permit tcp any host 192.168.93.5 eq 21 ! FTP

#### CONVIDADOS

permit tcp any host 192.168.94.1 eq 80 ! Internet 1

permit tcp any host 192.168.94.1 eq 443 ! Internet 2

permit udp any host 10.0.3.1 eq 67 ! DHCP

#### IMPRESORAS

permit udp any host 10.0.3.1 eq 67 ! DHCP

#### TELEFONES

permit udp any host 10.0.3.1 eq 67 ! DHCP

permit ip 192.168.70.0 0.0.0.31 192.168.71.0 0.0.0.31 ! Interedificios


### EDIFICIO B

#### ALUNOS

permit tcp any host 192.168.93.3 eq 80 ! HTTP inst

permit tcp any host 192.168.94.1 eq 80 ! Internet 1

permit tcp any host 192.168.94.1 eq 443 ! Internet 2

permit udp any host 10.0.3.1 eq 67 ! DHCP

permit ip 192.168.11.0 0.0.0.255 192.168.80.0 0.0.0.15 ! Impresoras

permit ip 192.168.11.0 0.0.0.255 192.168.10.0 0.0.0.127 ! Interedificios

#### PROFESORES

permit tcp any host 192.168.93.3 eq 80 ! HTTP inst

permit tcp any host 192.168.94.1 eq 80 ! Internet 1

permit tcp any host 192.168.94.1 eq 443 ! Internet 2

permit udp any host 10.0.3.1 eq 67 ! DHCP

permit tcp any host 192.168.93.4 eq 80 ! HTTP

permit ip 192.168.21.0 0.0.0.63 192.168.81.0 0.0.0.15 ! Impresoras

permit ip 192.168.21.0 0.0.0.63 192.168.20.0 0.0.0.15 ! Interedificios

#### FINANCIEROS

permit tcp any host 192.168.93.3 eq 80 ! HTTP inst

permit tcp any host 192.168.94.1 eq 80 ! Internet 1

permit tcp any host 192.168.94.1 eq 443 ! Internet 2

permit udp any host 10.0.3.1 eq 67 ! DHCP

permit ip 192.168.30.0 0.0.0.15 192.168.81.0 0.0.0.15 ! Impresoras

#### ACADEMICOS

permit tcp any host 192.168.93.3 eq 80 ! HTTP inst

permit tcp any host 192.168.94.1 eq 80 ! Internet 1

permit tcp any host 192.168.94.1 eq 443 ! Internet 2

permit udp any host 10.0.3.1 eq 67 ! DHCP

permit tcp any host 192.168.93.4 eq 80 ! HTTP

permit ip 192.168.40.0 0.0.0.31 192.168.81.0 0.0.0.15 ! Impresoras

#### CONVIDADOS

permit tcp any host 192.168.94.1 eq 80 ! Internet 1

permit tcp any host 192.168.94.1 eq 443 ! Internet 2

permit udp any host 10.0.3.1 eq 67 ! DHCP

#### IMPRESORAS

permit udp any host 10.0.3.1 eq 67 ! DHCP

#### TELEFONES

permit udp any host 10.0.3.1 eq 67 ! DHCP

permit ip 192.168.71.0 0.0.0.31 192.168.70.0 0.0.0.31 ! Interedificios
