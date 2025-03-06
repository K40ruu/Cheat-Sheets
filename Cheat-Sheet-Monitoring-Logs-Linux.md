# 📜 Cheat Sheet Monitoring Logs Linux

Cette cheat sheet te permet de surveiller efficacement ton système Linux pour identifier rapidement les tentatives d'intrusion (bruteforce), les connexions suspectes ou vérifier ce qui se passe sur ta machine en temps réel ou différé.

---

## 🚀 Surveillance des logs en temps réel

| Objectif                               | Commande                                  | Exemple concret                                                  |
|----------------------------------------|-------------------------------------------|------------------------------------------------------------------|
| Surveiller toutes les connexions SSH   | `tail -f /var/log/auth.log`               | Vérifier tentative d'attaques bruteforce SSH en direct           |
| Surveillance globale des logs système  | `journalctl -f`                           | Voir en direct tout ce qui se passe sur le système               |
| Surveillance d'accès Apache/Nginx      | `tail -f /var/log/apache2/access.log`     | Voir en temps réel qui visite ton site web                       |
| Surveillance des erreurs Apache/Nginx  | `tail -f /var/log/apache2/error.log`      | Identifier immédiatement les erreurs serveur web                 |

---

## 🕑 Analyse des logs en différé

| Objectif                             | Commande                                                | Exemple concret                                                          |
|--------------------------------------|---------------------------------------------------------|--------------------------------------------------------------------------|
| Voir les connexions réussies (SSH)   | `grep "Accepted" /var/log/auth.log`                    | Vérifier qui s'est connecté avec succès                                  |
| Voir les échecs d'authentification   | `grep "Failed" /var/log/auth.log`                      | Identifier les tentatives de bruteforce ratées                           |
| Historique des connexions SSH        | `last`                                                  | Lister les dernières connexions à ton système                            |
| Historique des connexions échouées   | `lastb`                                                 | Lister uniquement les connexions échouées                                |

---

## 🔍 Filtrage avancé des logs

| Objectif                                  | Commande                                                        | Exemple concret                                                  |
|-------------------------------------------|-----------------------------------------------------------------|------------------------------------------------------------------|
| Filtrer par IP précise                    | `grep "192.168.1.10" /var/log/auth.log`                        | Voir activités spécifiques d'une IP                              |
| Rechercher une date précise dans les logs | `grep "Mar 10" /var/log/auth.log`                              | Voir ce qui s'est passé à une date précise                       |
| Utiliser journalctl pour filtrer SSH      | `journalctl -u ssh.service`                                     | Logs spécifiques du service SSH                                  |
| Voir les logs kernel uniquement           | `journalctl -k`                                                 | Vérifier uniquement les alertes ou erreurs du noyau              |

---

## ⚙️ Exemple pratique (bruteforce SSH)

**Contexte :**
Tu soupçonnes une tentative de bruteforce SSH sur ta machine.

- Vérification en direct :

```bash
sudo tail -f /var/log/auth.log | grep "Failed"
```

- Analyse post-attaque :

```bash
sudo grep "Failed password" /var/log/auth.log | awk '{print $(NF-3)}' | sort | uniq -c | sort -nr | head -5
```

Cette commande affiche les 5 IP ayant le plus tenté de bruteforce ton serveur SSH.

---

## 🔐 Bonnes pratiques complémentaires

- Installer et configurer **fail2ban** pour bloquer automatiquement les attaques par bruteforce.

```bash
sudo apt install fail2ban
```

Logs de fail2ban :

```bash
sudo tail -f /var/log/fail2ban.log
```

---

## 📚 Ressources complémentaires

- [Documentation Journalctl](https://man7.org/linux/man-pages/man1/journalctl.1.html)
- [Fail2Ban GitHub](https://github.com/fail2ban/fail2ban)
