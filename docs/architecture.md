# Architecture du réseau

## Description

Cette infrastructure met en œuvre le protocole **Gateway Load Balancing Protocol (GLBP)** afin d'assurer la redondance de la passerelle par défaut et la répartition de charge sur un réseau local.

L'architecture est composée de :

- 3 routeurs Cisco IOS
- 1 switch Ethernet
- 3 postes clients

Le routage entre les routeurs est assuré par des routes statiques.

---

## Topologie

                    R1
                 /      \
       10.0.0.0/30      10.0.1.0/30
              /            \
            R2------------R3
              \ 10.0.2.0/30 /
               \          /
                \        /
                 +------+
                 |  S1  |
                 +------+
               /    |     \
            PC1   PC2    PC3

---

## Rôle des équipements

### R1

- Routeur de transit
- Assure le routage WAN
- Ne participe pas au groupe GLBP

### R2

- Active Virtual Gateway (AVG)
- Priorité 120
- Fournit la passerelle virtuelle

### R3

- Backup Gateway
- Priorité 100
- Prend le relais en cas de défaillance

### Switch

- Relie tous les équipements du LAN
- Transporte les trames Ethernet

### PCs

- Utilisent la VIP GLBP comme passerelle par défaut.
