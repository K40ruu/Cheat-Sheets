
# 🛠️ Cheat Sheet Avancée pour Hydra

> **Hydra** est un outil de force brute puissant et flexible, utilisé pour tester la robustesse des mots de passe sur divers services réseau.

## 📥 Installation

```bash
sudo apt-get install hydra
```

## ⚙️ Syntaxe de base

```bash
hydra [options] <cible> <service>
```

## 🧾 Options communes

| Option            | Description                                                                 |
|-------------------|-----------------------------------------------------------------------------|
| `-l <utilisateur>` | Nom d'utilisateur unique (ex. `-l admin`)                                  |
| `-L <fichier>`     | Liste des noms d'utilisateur (ex. `-L users.txt`)                          |
| `-p <motdepasse>`  | Mot de passe unique (ex. `-p password123`)                                 |
| `-P <fichier>`     | Liste des mots de passe (ex. `-P passwords.txt`)                           |
| `-s <port>`        | Port spécifique (ex. `-s 2222` pour SSH)                                   |
| `-t <nb_threads>`  | Nombre de threads parallèles (par défaut : 16)                             |
| `-v / -V`          | Mode verbeux (`-V` pour plus de détails)                                   |
| `-f`               | Arrête après la première réussite                                          |
| `-e nsr`           | Teste `n` (vide), `s` (identique à l'utilisateur), `r` (inverse)           |
| `-w <secondes>`    | Temps d'attente entre les tentatives (ex. `-w 5`)                          |
| `-o <fichier>`     | Enregistre les résultats dans un fichier                                   |

## 🌐 Exemples courants

### SSH
```bash
hydra -l root -P passwords.txt ssh://192.168.1.100
```

### FTP
```bash
hydra -L users.txt -P passwords.txt ftp://192.168.1.100
```

### HTTP POST avec cookies
```bash
hydra -L users.txt -P passwords.txt 192.168.1.100 http-post-form "/login.php:username=^USER^&password=^PASS^:F=Identifiants incorrects.:Cookie=PHPSESSID=abcdef1234567890"
```

### RDP
```bash
hydra -L users.txt -P passwords.txt rdp://192.168.1.100
```

## 🛠️ Création de wordlists personnalisées

### Crunch
```bash
crunch 8 12 abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789 -o wordlist.txt
```

### Cewl
```bash
cewl http://exemple.com -m 5 -w wordlist.txt
```

## 📝 Notes
- Wordlists comme `rockyou.txt` se trouvent dans `/usr/share/wordlists/` sur Kali Linux.
- N'utilisez Hydra que sur des systèmes pour lesquels vous avez l'autorisation.

---

*Sources : [Hydra Cheat Sheet - HackOps](https://hackops.fr/hydra-cheat-sheet/), [Hydra-Cheatsheet GitHub](https://github.com/frizb/Hydra-Cheatsheet), [freeCodeCamp Hydra Guide](https://www.freecodecamp.org/news/how-to-use-hydra-pentesting-tutorial/).*
