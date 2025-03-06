
# 🛠️ Cheat Sheet Nikto

> **Nikto** est un scanner de vulnérabilités web open-source qui effectue des tests pour identifier des failles potentielles.

## 📥 Installation

```bash
git clone https://github.com/sullo/nikto
cd nikto/program
chmod +x nikto.pl
./nikto.pl -h http://www.example.com
```

## ⚙️ Syntaxe de base

```bash
nikto -h <cible>
```

## 🧾 Options communes

| Option              | Description                                              |
|---------------------|----------------------------------------------------------|
| -h <hôte>          | Spécifie l'hôte cible                                    |
| -p <ports>         | Spécifie le(s) port(s) à scanner                        |
| -ssl               | Force l'utilisation de SSL                              |
| -Tuning <options>  | Affine les tests à effectuer                            |
| -output <fichier>  | Sauvegarde les résultats dans un fichier                |
| -Format <format>   | Format de sortie (`csv`, `html`, `txt`, `xml`)          |
| -Plugins <liste>   | Liste des plugins à exécuter                            |
| -list-plugins      | Liste tous les plugins disponibles                      |
| -update            | Met à jour les bases de données et plugins              |
| -useproxy          | Utilise le proxy défini dans `nikto.conf`               |
| -config <fichier>  | Utilise un fichier de configuration spécifique          |
| -dbcheck           | Vérifie la base de données et fichiers clés             |
| -timeout <sec>     | Définit le délai d'attente des requêtes                 |
| -vhost <hôte>      | Définit l'hôte virtuel (en-tête Host)                   |

## 🔄 Tuning des tests

| Option | Description                                  |
|--------|----------------------------------------------|
| 0      | Téléchargement de fichiers                  |
| 1      | Fichiers intéressants                       |
| 2      | Mauvaise configuration / Défauts           |
| 3      | Divulgation d’informations                  |
| 4      | Injections (XSS, HTML)                      |
| 5      | Fichiers à distance (racine web)           |
| 6      | Déni de service                            |
| 7      | Fichiers à distance (serveur complet)      |
| 8      | Commandes/Shell à distance                  |
| 9      | Injection SQL                              |
| a      | Contournement d’authentification            |
| b      | Identification de logiciels                |
| c      | Inclusion de source à distance             |
| x      | Inverse la sélection (tout sauf spécifié)  |

Exemple :
```bash
nikto -h http://www.example.com -Tuning 9a
```

## 🌐 Exemples d'utilisation

### Scan basique :
```bash
nikto -h http://www.example.com
```

### Scan d'un port spécifique :
```bash
nikto -h http://www.example.com -p 8080
```

### Scan SSL :
```bash
nikto -h http://www.example.com -ssl
```

### Sauvegarder les résultats :
```bash
nikto -h http://www.example.com -output resultats.html -Format html
```

### Utiliser un proxy :
```bash
nikto -h http://www.example.com -useproxy
```

### Lister les plugins :
```bash
nikto -list-plugins
```

## 📝 Notes

- Mettez à jour régulièrement les plugins avec :
  ```bash
  nikto -update
  ```

- **Attention légale** : Utilisez Nikto uniquement sur des systèmes que vous êtes autorisé à scanner.

---

*Sources : [Comparitech](https://www.comparitech.com/net-admin/nikto-cheat-sheet/), [Highon.coffee](https://highon.coffee/blog/nikto-cheat-sheet/), [Nikto GitHub](https://github.com/sullo/nikto).*
