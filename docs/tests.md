# Procédure de test

## Vérification des interfaces

show ip interface brief

---

## Vérification du routage

show ip route

---

## Vérification GLBP

show glbp

show glbp brief

---

## Test de connectivité

Depuis PC1

ping 192.168.10.254

ping 192.168.10.1

ping 192.168.10.2

---

## Test de bascule

1. Désactiver e0/2 sur R2

shutdown

2. Vérifier

show glbp brief

3. Vérifier la continuité

ping 192.168.10.254

Le trafic doit continuer à circuler via R3.
