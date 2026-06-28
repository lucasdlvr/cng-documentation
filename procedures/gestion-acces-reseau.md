# Procédure : Gestion des demandes d'accès réseau au BSI

**Numéro procédure :** P003  
**Date création :** Juin 2026  
**Niveau :** Support L1/L2 + Sécurité  
**Prérequis :** Accès Active Directory + GLPI

---

## 🎯 Objectif

Gérer les demandes d'accès réseau (Wi-Fi, VPN, partages) de façon **sécurisée**, **tracée** et **conforme** aux exigences du CNG.

---

## 📋 Contexte

Le CNG gère des données sensibles (données praticiens, infos administratives). Chaque accès réseau doit être :
- ✅ **Autorisé** par la hiérarchie
- ✅ **Validé** par la sécu (principes du moindre privilège)
- ✅ **Tracé** (qui a quoi, quand, pourquoi)
- ✅ **Audité** régulièrement

---

## 🔧 Processus

### ÉTAPE 1 : Réception de la demande (Support L1)

L'utilisateur (ou son manager) soumet via ticket :

**Infos requises :**
- [ ] Demandeur (nom, département)
- [ ] Type d'accès (Wi-Fi ? VPN ? Partage ?)
- [ ] Durée (permanent ou temporaire ?)
- [ ] Justification (pour quel boulot ?)
- [ ] Manager qui valide

**Action :**
1. Vérifier que le ticket a TOUS les champs
2. Assigner à "Responsable Sécurité" si manque infos
3. Créer trace GLPI: "ACC-[DATE]-[NOM]"

---

### ÉTAPE 2 : Validation managériale (Manager de l'utilisateur)

Le manager reçoit notification → valide ou refuse

**À valider :**
- ✅ L'utilisateur a vraiment besoin ?
- ✅ Le type d'accès correspond au rôle ?
- ✅ Durée appropriée ?

Si OK → signe numériquement (ou email validation acceptée)

---

### ÉTAPE 3 : Évaluation de sécurité (Responsable Sécurité)

C'est **critique** pour CNG (données publiques).

**Questions à poser :**

| Question | Réponse attendue |
|----------|-----------------|
| Quel est le risque d'accès non-autorisé ? | Bas/Moyen/Haut |
| Faut-il 2FA / authentification forte ? | Oui/Non |
| Quelles données l'utilisateur va accéder ? | Types de données (praticiens, admin, etc.) |
| Accès sur quel réseau/serveur ? | Spécifier: réseau interne, VPN, partage X |
| Accès personnel ou service ? | (change le traitement) |

**Décision :**
- ✅ **Approuvé** → passer à étape 4
- ❌ **Refusé** → notifier demandeur + manager
- ⚠️ **Approuvé avec conditions** → ex : "2FA obligatoire", "durée 3 mois max", etc.

**Trace :** Signer/dater la validation

---

### ÉTAPE 4 : Configuration technique (Responsable Réseau/IT)

Maintenant que c'est approuvé, configurer l'accès.

**Par type d'accès :**

#### **Wi-Fi d'entreprise :**
1. Ajouter utilisateur au groupe AD "WiFi_Users"
2. Configurer 802.1X (certificat ou identifiant de domaine)
3. Envoyer SSID + instructions
4. Tester de proximité (demander à l'utilisateur de se connecter)

#### **VPN :**
1. Créer/activer VPN account dans serveur VPN
2. Assigner groupe "VPN_Users" (AD)
3. Installer client VPN sur poste utilisateur
4. Envoyer instructions + identifiants temporaires
5. Utilisateur change de mot de passe à première connexion
6. Tester une connexion VPN

#### **Partage réseau/NAS :**
1. Créer folder utilisateur (ou ajouter à existant)
2. Assigner permissions NTFS (Read/Write selon besoin)
3. Ajouter utilisateur au groupe de sécurité (ex : "ComptabiliteUsers")
4. Tester accès du poste utilisateur
5. Envoyer chemin réseau (ex : \\serveur\comptabilite\[nom])

**Trace :** Documenter dans GLPI :
- Quelle config appliquée
- Date/heure
- Qui a fait
- Test de validation effectué

---

### ÉTAPE 5: Notification et validation utilisateur

Email à l'utilisateur :

```
Sujet : Votre accès réseau est configuré

Bonjour [Prénom],

Votre accès [Wi-Fi/VPN/Partage] est maintenant actif.

Accès :
- Type : [Wi-Fi / VPN / Partage]
- Identifiant : [Si applicable]
- Chemin : [Si partage: \\serveur\dossier]

Instructions :
[Lien vers procédure / steps rapides]

Test :
Connectez-vous et vérifiez que vous pouvez accéder.
Si problème → répondre à ce mail ou ticket IT.

Sécurité :
- Ne partagez pas vos identifiants
- Changez votre mot de passe tous les 3 mois
- Signalez tout accès suspect

Support : [Email IT]

Cordialement,
[Nom Technicien]
```

**Utilisateur répond :** "✅ Accès OK" ou "❌ Ça marche pas"

---

### ÉTAPE 6 : Audit et révocation périodique

**Chaque trimestre :**
1. Lister tous les accès actifs (GLPI query)
2. Pour chaque accès, vérifier :
   - [ ] L'utilisateur toujours dans le département ?
   - [ ] Accès toujours nécessaire ?
   - [ ] Pas d'abus/accès anormal ?
3. Révoquer si : utilisateur parti, accès plus utile, inactivité 6 mois

**Révocation :**
1. Notifier manager + utilisateur
2. Supprimer accès (déjà groupes AD, partages, etc.)
3. Documenter dans GLPI : "Révoqué [date] - [raison]"

---

## ✅ Traçabilité complète

**Chaque demande d'accès doit avoir un dossier GLPI :**

```
Numéro : ACC-2024-12-OLIVEIRA
Demandeur : Lucas Oliveira
Type d'accès : VPN
Date demande : 2024-12-15
Manager validation : [Nom] - [Date]
Sécu validation : [Nom] - Approuvé - [Conditions?]
Configuration date : 2024-12-16
Config par : [Technicien]
Test validation : ✅ OK
Utilisateur notifié : 2024-12-16
Révocation plannifiée : 2025-03-16 (3 mois)
Statut : ACTIF
```

---

## 🔒 Checklist sécurité (à valider avant chaque accès)

- [ ] Demande **formelle** (ticket + signatures)
- [ ] Manager a **approuvé**
- [ ] Responsable sécu a **évalué le risque**
- [ ] Principe du **moindre privilège** appliqué (pas d'admin si juste user)
- [ ] **2FA** activé si données sensibles
- [ ] **Credentials temporaires** à 1ère connexion
- [ ] Accès **tracé** en GLPI
- [ ] **Audit** trimestriel effectué
- [ ] **Révocation** planifiée si temporaire

---

## 📞 Escalade

**Contacter responsable sécurité si :**
- ❓ Demande incohérente (ex: "accès VPN" pour quelqu'un qui n'en a pas besoin)
- ⚠️ Donnée sensible + accès non standard
- 🚨 Suspicion d'abus (utilisateur accède à data pas de son département)

**Contacter direction IT si :**
- 🔴 Incident sécurité détecté
- 🔴 Audit découvre faille majeure

---

## 📚 Ressources

- [RGPD et accès aux données](https://cnil.fr)
- [Guide sécurité accès réseau](https://anssi.gouv.fr)
- Serveurs/outils : [À remplir avec infra CNG réelle]
- Support : [Email responsable sécurité/IT]

---

**Version:** 1.0  
**Auteur:** Lucas De Oliveira  
**Basé sur:** Bonnes pratiques ANSSI + Expérience Crédit Agricole (gestion des risques, équipes cyber)
