
# Lab Petit Réseau d'entreprise ( commutation, routage et sécurité )

## 📌 À propos du projet
Ce projet personnel simule l'infrastructure réseau complète d'une PME ("Nova-Tech"). Il met en œuvre une architecture segmentée avec un routeur en mode **Router-on-a-Stick**, des mécanismes de sécurité avancés de niveau 2 et 3, ainsi qu'un contrôle strict des flux via des ACL et l'intégration d'un réseau Wi-Fi géré (WLC).

## 🛠️ Topologie du Réseau
- **Routeur :** RTR-Nova-Tech (Routage Inter-VLAN, NAT, ACLs, SSH, NTP, SYSLOG)
- **Switch d'accès :** SW-ACC-Nova-Tech (Vlan,Trunk, ACL, Port Security, DHCP Snooping, DAI, BPDU Guard, strom control)
- **Services :** Serveur centralisé (DHCP, DNS, Syslog, NTP) + WLC & Bornes d'accès (AP)
-
## [Topologie du réseau Nova-Tech](Topology/Nova-tech-1.png)

## 🔒 Fonctionnalités et Sécurité implémentées
1. **Segmentation VLAN :** 
   - VLAN 10 : IT (`10.1.1.0/27`)
   - VLAN 20 : DEV (`10.1.1.32/27`)
   - VLAN 30 : RH (`10.1.1.64/27`)
   - VLAN 40 : Administration (`10.1.1.96/27`)
   - VLAN 50 : Serveurs (`10.1.1.128/27`)
   - VLAN 60 : Imprimantes (`10.1.1.160/27`)
   - VLAN 70 : Management (`10.1.1.192/27`)
   - VLAN 80 : Guest (`192.168.10.0/24`)
2. **Sécurité de Niveau 2 (L2 Hardening) :** Activation du *Port Security* (Sticky MAC), *DHCP Snooping*, *Dynamic ARP Inspection (DAI)*, *BPDU Guard*, *strom control*.
3. **Filtrage de trafic (ACLs) :**
   - Isolation complète du réseau Guest (accès Internet/DNS/DHCP uniquement, pas de visibilité interne).
   - Restriction d'accès au WLC autorisée exclusivement au département IT.
   - Blocage des communications inter-départements non désirées.
   - Filtre de communication vers l'imprimante
4. **Sécurité des équipements :** Chiffrement des mots de passe, accès distant restreint en SSH v2, journalisation centralisée (Syslog) et authentification NTP.

## 📂 Fichiers de Configuration
Les configurations brutes des équipements sont disponibles dans le dossier `Configs/` :
- [`RTR-Nova-Tech.txt`](Configs/RTR-Nova-Tech_startup-config.txt)
- [`SW-ACC-Nova-tech.txt`](Configs/SW-ACC-Nova-tech_startup-config.txt)

## 📁 Retrouvez le fichier source du lab dans le dossier Topology

**NB: j'ai utilisé la version 9.0.1 de cisco packet tracer**
[Le Lab Nova-tech](Topology/projet-Nova-tech-1.pkt)





 
