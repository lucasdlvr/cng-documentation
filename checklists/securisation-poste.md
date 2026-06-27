# Checklist: Sécuriser un nouveau poste de travail

**Niveau:** Support L1  
**Durée:** 15-20 min par poste  
**Fréquence:** À chaque nouveau poste

---

## 🔐 Avant livraison à l'utilisateur

### Système d'exploitation

- [ ] **Windows Update:** Toutes les mises à jour appliquées
  Paramètres → Mise à jour et sécurité → Vérifier les mises à jour

- [ ] **Antivirus:** Activé et à jour
  - [ ] Windows Defender actif
  - [ ] Scan complet effectué
  - [ ] Signatures de virus à jour

- [ ] **Pare-feu Windows:** Activé
  Paramètres → Sécurité Windows → Pare-feu

### Authentification & Accès

- [ ] **Mot de passe utilisateur:** Fort (12+ caractères, majuscules, chiffres, spéciaux)
  ✅ Exemple: P@ss2024!CNG
  ❌ Mauvais: password123, azerty, 12345

- [ ] **BitLocker:** Activé (si disponible - Windows Pro+)
  Panneau de configuration → Chiffrer le lecteur BitLocker

- [ ] **Compte administrateur:** Désactivé ou mot de passe fort

- [ ] **Accès domaine:** Machine jointe au domaine CNG
  Propriétés système → Domaine: [CNG]

### Logiciels

- [ ] **Software bloatware:** Supprimé (jeux, trials, etc.)

- [ ] **Logiciels requis:** Installés et validés
  - [ ] Microsoft Office (si besoin)
  - [ ] Adobe Reader
  - [ ] VPN client (si besoin)
  - [ ] Logiciels métier

- [ ] **Licenses vérifiées:** Tous les logiciels payants activés

### Données & Sauvegarde

- [ ] **Sauvegarde configurée:**
  Paramètres → Mise à jour et sécurité → Sauvegarde
  Dossier de sauvegarde: [Serveur CNG]

- [ ] **Dossier utilisateur:** Créé et accessible
  \\serveur\users\prenom.nom

### Réseau & Connectivité

- [ ] **Wi-Fi/Ethernet:** Fonctionne
  Ping 8.8.8.8 + Vérifier connexion Internet

- [ ] **DNS:** Correct (8.8.8.8 ou DNS CNG)

- [ ] **Imprimante:** Configurée et testée
  Print test page depuis paramètres

- [ ] **VPN:** Configuré (si applicable)

### Matériel

- [ ] **Clavier/Souris:** Fonctionne
- [ ] **Webcam:** Fonctionne (si présente)
- [ ] **Microphone:** Fonctionne (si présent)
- [ ] **Batterie:** Charge OK (si portable)
- [ ] **Ports USB:** Tous fonctionnels

---

## 📋 Documentation & Traçabilité

- [ ] **Asset tag:** Collé et noté en inventaire
  GLPI: [Ajouter la machine]

- [ ] **Numéro de série:** Documenté
  Commande: systeminfo | find "Serial"

- [ ] **Configuration documentée:** Fiche technique complétée
  Processeur: ____________
  RAM: ____________
  Disque: ____________
  OS: ____________
  Logiciels: ____________

- [ ] **Utilisateur formé:** Baseline expliquée
  - [ ] Mot de passe robuste
  - [ ] Pas laisser déverrouillé
  - [ ] Signaler problèmes rapidement
  - [ ] Backups importants

---

## 🚀 Livraison à l'utilisateur

- [ ] Tous les points cochés ✅
- [ ] Utilisateur a reçu credential
- [ ] Utilisateur a changé mot de passe temporaire
- [ ] Support IT contacté et noté
- [ ] Ticket fermé

---

## 📝 Traçabilité

Date: ____________
Poste modèle: ____________
Numéro série: ____________
Utilisateur: ____________
Technicien: ____________
Validé par: ____________
Ticket #: ____________

---

**Version:** 1.0  
**Auteur:** Lucas De Oliveira  
**Dernière révision:** Décembre 2024
