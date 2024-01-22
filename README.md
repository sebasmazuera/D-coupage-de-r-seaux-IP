# D-coupage-de-r-seaux-IP

Pour découper le réseau 172.16.1.0/24 de manière symétrique et asymétrique pour les quatre pôles informatiques, nous allons utiliser le CIDR (Classless Inter-Domain Routing) pour déterminer la plage d'adresses IP pour chaque pôle.

### Découpage Symétrique :
Pour un découpage symétrique, nous allons allouer des sous-réseaux égaux à chaque pôle.

1. **Pôle Informatique (PI) :**
   - Nombre d'équipements : 50
   - Nombre de sous-réseaux : 1  
   - Bits pour les hôtes : \( \lceil \log_2(50 + 6) \rceil = 6 \) bits
   - CIDR : /30 (4 adresses par sous-réseau)
   - Adresse réseau : 172.16.1.0/30
   - Adresse de diffusion (Broadcast) : 172.16.1.3

2. **Pôle Développement (PD) :**
   - Nombre d'équipements : 12
   - Nombre de sous-réseaux : 1
   - Bits pour les hôtes : \( \lceil \log_2(12 + 6) \rceil = 4 \) bits
   - CIDR : /28 (16 adresses par sous-réseau)
   - Adresse réseau : 172.16.1.4/28
   - Adresse de diffusion (Broadcast) : 172.16.1.15

3. **Pôle Administratif (PA) :**
   - Nombre d'équipements : 20
   - Nombre de sous-réseaux : 1
   - Bits pour les hôtes : \( \lceil \log_2(20 + 4) \rceil = 5 \) bits
   - CIDR : /29 (8 adresses par sous-réseau)
   - Adresse réseau : 172.16.1.16/29
   - Adresse de diffusion (Broadcast) : 172.16.1.23

4. **Pôle Technicien (PT) :**
   - Nombre d'équipements : 15
   - Nombre de sous-réseaux : 1
   - Bits pour les hôtes : \( \lceil \log_2(15 + 4) \rceil = 4 \) bits
   - CIDR : /28 (16 adresses par sous-réseau)
   - Adresse réseau : 172.16.1.24/28
   - Adresse de diffusion (Broadcast) : 172.16.1.39

### Découpage Asymétrique :
Pour un découpage asymétrique, nous allons allouer des sous-réseaux en fonction du nombre d'équipements prévus pour chaque pôle.

1. **Pôle Informatique (PI) :**
   - Nombre d'équipements : 50
   - Bits pour les hôtes : \( \lceil \log_2(50) \rceil = 6 \) bits
   - CIDR : /26 (64 adresses par sous-réseau)
   - Adresse réseau : 172.16.1.0/26
   - Adresse de diffusion (Broadcast) : 172.16.1.63

2. **Pôle Développement (PD) :**
   - Nombre d'équipements : 12
   - Bits pour les hôtes : \( \lceil \log_2(12) \rceil = 4 \) bits
   - CIDR : /28 (16 adresses par sous-réseau)
   - Adresse réseau : 172.16.1.64/28
   - Adresse de diffusion (Broadcast) : 172.16.1.79

3. **Pôle Administratif (PA) :**
   - Nombre d'équipements : 20
   - Bits pour les hôtes : \( \lceil \log_2(20) \rceil = 5 \) bits
   - CIDR : /29 (8 adresses par sous-réseau)
   - Adresse réseau : 172.16.1.80/29
   - Adresse de diffusion (Broadcast) : 172.16.1.87

4. **Pôle Technicien (PT) :**
   - Nombre d'équipements : 15
   - Bits pour les hôtes : \( \lceil \log_2(15) \rceil = 4 \) bits
   - CIDR : /28 (16 adresses par sous-réseau)
   - Adresse réseau : 172.16.1.88/28
   - Adresse de diffusion (Broadcast) : 172.16.1.103

### Tableau Récapitulatif :
| Pôle | Nombre d'équipements | CIDR | Adresse Réseau | Adresse de Diffusion |
|------|-----------------------|------|-----------------|-----------------------|
| PI   | 50                    | /30  | 172.16.1.0/30   | 172.16.1.3           |
| PD   | 12                    | /28  | 172.16.1.4/28   | 172.16.1.15          |
| PA   | 20                    | /29  | 172.16.1.16/29  | 172.16.1.23          |
| PT   | 15                    | /28  | 172.16.1.24/28  | 172.16.1.39          |
| PI   | 50                    | /26  | 172.16.1.0/26   | 172.16.1.63          |
| PD   | 12                    | /28  | 172.16.1.64/28  | 172.16.1.79          |
| PA   | 20                    | /29  | 172.16.1.80/29  | 172.16.1.87          |
| PT   | 15                    | /28  | 172.16.1.88/28  | 172.16.1.103         |

