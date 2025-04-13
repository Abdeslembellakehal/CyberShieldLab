# 📘 Étapes techniques réalisées – CyberShieldLab

---

## ✅ 1. Création des machines virtuelles

- Création de 4 machines virtuelles sous VMware :
  - Kali Linux (attaquant)
  - Ubuntu Server (serveur cible avec Snort)
  - Ubuntu Desktop (analyste réseau)
  - Windows 10 (poste utilisateur)
- Configuration d’un réseau privé : `192.168.192.0/24`
- Vérification de la connectivité avec `ping` entre Ubuntu Desktop et Ubuntu Server

---

## ✅ 2. Installation de Snort sur Ubuntu Server

Installation du système de détection d’intrusion (IDS) :

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install -y snort
✅ 3. Lancement de Snort et détection d’attaque
Lancer Snort pour écouter le trafic :

bash
Copier
Modifier
sudo snort -i ens33 -A console -c /etc/snort/snort.conf
Puis, depuis Kali Linux, effectuer un scan réseau :

bash
Copier
Modifier
nmap 192.168.192.147
Snort affiche les alertes en temps réel.

✅ 4. Création du script d’automatisation block_ip.sh
Ce script récupère automatiquement l’IP depuis les logs de Snort et la bloque avec iptables.

✅ 5. Test manuel du script block_ip.sh
Exécuter manuellement le script pour vérifier qu’il détecte et bloque correctement une IP après une alerte Snort.

✅ 6. Création d’un fichier log /var/log/ip_bloquees.log
Ce fichier sert à journaliser les IP bloquées automatiquement par le script.

✅ 7. Ajout de la tâche automatique avec crontab
Planifier l’exécution automatique du script toutes les 5 minutes avec la commande suivante :

bash
Copier
Modifier
*/5 * * * * sudo /home/adminlab/block_ip.sh
🎯 Conclusion

Ces étapes m'ont permis de simuler un environnement de détection d'intrusion, de créer un script de blocage automatisé, et de configurer une tâche planifiée pour sécuriser un serveur avec Snort et iptables.
