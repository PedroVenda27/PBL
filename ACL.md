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
### Admit + permit
- Deny HTTP
- Deny FTP
- Deny interedificios -> No dar acceso a la red del otro edificio (out)
- Allow DHCP (esto va en todos, no hay ningúno prohibido)
- Allow Internet
- Allow Interedificios

### Admit all en todo
- Deny HTTP
- Deny FTP
- Deny interedificios
