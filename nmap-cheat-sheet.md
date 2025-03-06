# 🛡️ Cheat Sheet Nmap

## 🎯 Informations Générales

**Nmap** (Network Mapper) est un outil open-source de sécurité pour la découverte réseau et l'audit de sécurité.

Site officiel : [nmap.org](https://nmap.org/)

---

## 📌 Syntaxe de Base

```bash
nmap [options] <cible>
```

---

## 🎯 Scan de cibles

| Action                      | Commande                             | Exemple concret                                      |
|-----------------------------|--------------------------------------|------------------------------------------------------|
| Scan d'une IP unique        | `nmap 192.168.1.1`                   | `nmap 192.168.1.10` (serveur web interne)            |
| Scan d'une plage d'IP       | `nmap 192.168.1.1-100`               | `nmap 192.168.1.20-30` (recherche d'hôtes actifs)    |
| Scan d'un sous-réseau CIDR  | `nmap 192.168.1.0/24`                | `nmap 10.0.0.0/24` (scan réseau entreprise)          |
| Scan d'un domaine           | `nmap exemple.com`                   | `nmap google.com`                                    |
| Exclure des cibles          | `nmap 192.168.1.0/24 --exclude 192.168.1.5` | Exclure IP d'un serveur sensible pendant le scan |

---

## 🔎 Techniques de Scan

| Technique            | Commande                 | Mise en situation concrète                                  |
|----------------------|--------------------------|-------------------------------------------------------------|
| TCP SYN (discret)    | `nmap -sS <cible>`       | Scan discret d'une machine cible sans connexion complète    |
| TCP Connect (bruyant)| `nmap -sT <cible>`       | Scan classique pour vérifier rapidement un service SSH      |
| UDP                  | `nmap -sU <cible>`       | Vérifier les ports UDP comme DNS (port 53) sur un serveur   |
| TCP ACK (pare-feu)   | `nmap -sA <cible>`       | Identifier présence de firewall ou filtrage sur un serveur  |

---

## 📡 Découverte d'Hôtes

| Action                                  | Commande                           | Exemple concret                                      |
|-----------------------------------------|------------------------------------|------------------------------------------------------|
| Découverte sans scan de ports           | `nmap -sn <cible>`                 | Vérifier quels hôtes sont actifs sans alerter IDS    |
| Scan de ports sans découverte d'hôtes   | `nmap -Pn <cible>`                 | Scanner un hôte bloquant les requêtes ping           |
| Lister les cibles sans scan             | `nmap -sL <cible>`                 | Lister toutes les IP d'un domaine sans envoyer de paquets |

---

## 🎛️ Spécification des Ports

| Action                  | Commande                        | Exemple concret                                         |
|-------------------------|---------------------------------|---------------------------------------------------------|
| Ports spécifiques       | `nmap -p 22,80,443 <cible>`      | Vérifier SSH, HTTP, HTTPS sur serveur web interne       |
| Plage de ports          | `nmap -p 1-1024 <cible>`         | Scan rapide des ports standards sur une machine         |
| Tous les ports          | `nmap -p- <cible>`               | Scan complet pour audit exhaustif d'une cible           |
| Ports communs           | `nmap -F <cible>`                | Audit rapide pour les ports les plus fréquemment ouverts|

---

## 🧩 Détection avancée

| Action                            | Commande                   | Mise en situation concrète                                   |
|-----------------------------------|----------------------------|--------------------------------------------------------------|
| Détection version services        | `nmap -sV <cible>`         | Identifier les versions vulnérables des services actifs      |
| Détection OS                      | `nmap -O <cible>`          | Déterminer le système d'exploitation utilisé par une cible   |
| Détection complète                | `nmap -A <cible>`          | Réaliser un scan détaillé (OS, version, scripts, traceroute)|

---

## ⏱️ Optimisation du Timing

| Action                     | Commande                     | Exemple concret                                           |
|----------------------------|------------------------------|-----------------------------------------------------------|
| Rapide (par défaut)        | `nmap -T4 <cible>`           | Scan rapide pendant un pentest (par défaut)               |
| Plus discret               | `nmap -T2 <cible>`           | Scan discret contre des systèmes protégés par IDS         |
| Très agressif              | `nmap -T5 <cible>`           | Test de sécurité interne rapide pour une urgence          |

---

## 🥷 Évasion IDS / Firewall

| Action                       | Commande                                 | Mise en situation concrète                                   |
|------------------------------|------------------------------------------|--------------------------------------------------------------|
| Fragmenter paquets           | `nmap -f <cible>`                        | Échapper à la détection par certains systèmes de protection |
| Adresse IP leurre            | `nmap -D RND:10 <cible>`                 | Masquer le véritable IP pendant un pentest externe          |
| Spoofing d'adresse MAC       | `nmap --spoof-mac 00:11:22:33:44:55 <cible>`| Éviter le blocage MAC sur un réseau protégé                 |

---

## 📄 Sortie des Résultats

| Action                          | Commande                          | Exemple concret                                         |
|---------------------------------|-----------------------------------|---------------------------------------------------------|
| Format standard                  | `nmap -oN scan.txt <cible>`       | Sauvegarde simple pour revue manuelle rapide            |
| Format XML                       | `nmap -oX scan.xml <cible>`       | Intégration dans des outils tiers (ex: Metasploit)      |
| Tous les formats                 | `nmap -oA scan <cible>`           | Audit complet avec multiples formats exploitables       |

---

## 🧑‍💻 Nmap Scripting Engine (NSE)

| Action                             | Commande                                    | Mise en situation concrète                                  |
|------------------------------------|---------------------------------------------|-------------------------------------------------------------|
| Exécuter script spécifique         | `nmap --script=http-enum <cible>`           | Énumérer les répertoires et fichiers cachés d'un site web   |
| Scripts par défaut                 | `nmap -sC <cible>`                          | Automatisation rapide d'audit basique de sécurité           |

---

## 📚 Ressources

- [Documentation officielle](https://nmap.org/docs.html)
- [Scripts NSE](https://nmap.org/nsedoc/)
