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
