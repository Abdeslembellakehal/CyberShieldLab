# 📘 Étapes techniques réalisées – CyberShieldLab

---

## ✅ 1. Création des machines virtuelles

- Création de 4 VMs :
  - Kali Linux (attaquant)
  - Ubuntu Server (serveur cible)
  - Ubuntu Desktop (analyste)
  - Windows 10 (poste utilisateur)
- Réseau privé : `192.168.192.0/24`
- Test de communication avec `ping` entre Ubuntu Desktop et Ubuntu Server ✅

📸 ![Ping Ubuntu](../images/ping_ubuntu.png)

---

## ✅ 2. Installation de Snort sur Ubuntu Server

Commande utilisée :
```bash
sudo apt update && sudo apt upgrade -y
sudo apt install -y snort
## ✅ 3. Lancement de Snort et détection d'attaque
sudo snort -i ens33 -A console -c /etc/snort/snort.conf
Depuis Kali, scan Nmap exécuté :
nmap 192.168.192.147
Snort détecte l'activité réseau avec succees 
