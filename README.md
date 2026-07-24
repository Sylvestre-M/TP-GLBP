# TP GLBP – Gateway Load Balancing Protocol

## Présentation

Ce projet présente la mise en œuvre du **Gateway Load Balancing Protocol (GLBP)** sur une infrastructure Cisco IOS.

L'objectif est de mettre en place une passerelle virtuelle offrant :

- la redondance de la passerelle par défaut ;
- la répartition de charge entre plusieurs routeurs ;
- la continuité de service en cas de défaillance d'un routeur.

Le routage entre les routeurs est réalisé à l'aide de **routes statiques**.

---

## Objectifs du TP

- Comprendre le fonctionnement de GLBP.
- Configurer un groupe GLBP.
- Mettre en œuvre le préemption (Preempt).
- Configurer les priorités des routeurs.
- Vérifier le fonctionnement du protocole.
- Tester la bascule en cas de panne.

---

## Topologie

```
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
```

---

## Plan d'adressage

### Réseau LAN

| Équipement | Adresse IP |
|------------|------------|
| VIP GLBP | 192.168.10.254 |
| R2 | 192.168.10.1 |
| R3 | 192.168.10.2 |

### Liaisons WAN

| Liaison | Réseau |
|---------|---------|
| R1 ↔ R2 | 10.0.0.0/30 |
| R1 ↔ R3 | 10.0.1.0/30 |
| R2 ↔ R3 | 10.0.2.0/30 |

---

## Configuration GLBP

### Groupe

- Groupe : **1**

### Passerelle virtuelle

```
192.168.10.254
```

### Priorités

| Routeur | Priorité | Rôle |
|----------|----------|------|
| R2 | 120 | Active Virtual Gateway (AVG) |
| R3 | 100 | Backup / Active Virtual Forwarder |

### Fonctionnalités

- Load Balancing
- Preempt
- Gateway virtuelle
- Haute disponibilité

---

## Routage

Le routage est réalisé à l'aide de **routes statiques**.

Aucun protocole de routage dynamique (OSPF, RIP, EIGRP) n'est utilisé.

---

## Arborescence du projet

```
TP-GLBP/
│
├── README.md
├── LICENSE
├── .gitignore
│
├── docs/
│   ├── architecture.md
│   ├── adressage.md
│   ├── glbp.md
│   └── tests.md
│
├── configs/
│   ├── R1.cfg
│   ├── R2.cfg
│   ├── R3.cfg
│   └── PCs.md
│
├── captures/
│   ├── show_glbp_R2.txt
│   ├── show_glbp_R3.txt
│   ├── show_ip_route_R1.txt
│   ├── show_ip_route_R2.txt
│   ├── show_ip_route_R3.txt
│   └── ping_tests.txt
│
└── scripts/
|    └── reset.txt
|
|── topology/
    └── topology.png
```

---

## Vérification

Sur les routeurs :

```bash
show glbp
show glbp brief
show ip interface brief
show ip route
```

Depuis les PC :

```bash
ping 192.168.10.254
ping 192.168.10.1
ping 192.168.10.2
```

---

## Tests réalisés

- Configuration des interfaces
- Configuration des routes statiques
- Configuration GLBP
- Vérification de la passerelle virtuelle
- Vérification des états GLBP
- Tests de connectivité
- Test de bascule (Failover)

---

## Technologies utilisées

- Cisco IOS
- GLBP
- Routage statique
- Ethernet
- IPv4

---

## Auteur

**Sylvestre Mouafo**

---

## Licence

Ce projet est distribué sous la licence **MIT**.
