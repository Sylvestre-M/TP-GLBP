# Gateway Load Balancing Protocol (GLBP)

## Définition

GLBP est un protocole propriétaire Cisco permettant de fournir :

- une passerelle virtuelle ;
- une redondance ;
- une répartition de charge entre plusieurs routeurs.

Contrairement à HSRP ou VRRP, GLBP permet d'utiliser plusieurs routeurs simultanément pour transférer le trafic.

---

## Fonctionnement

Chaque routeur possède :

- une adresse IP réelle ;
- une adresse MAC virtuelle.

Les clients utilisent uniquement la VIP.

Le protocole répartit automatiquement les réponses ARP afin de distribuer le trafic.

---

## Paramètres utilisés

Groupe :

1

VIP :

192.168.10.254

Priorités :

R2 : 120

R3 : 100

Mode :

Preempt activé

---

## Vérification

show glbp

show glbp brief

show glbp interface
