# Checklist : Renouvellement matériel informatique

**Niveau :** Support L1/L2  
**Durée :** 30-45 min par poste  
**Fréquence :** Tous les 4-5 ans (selon âge/obsolescence)

---

## 🎯 Objectif

Remplacer un poste informatique vieillissant par un nouveau matériel, en **conservant les données**, en **transférant les configurations**, et en **documentant le processus**.

---

## 📋 Avant renouvellement

### Évaluation de l'équipement actuel

- [ ] **Âge du matériel :** _____ ans (ancien PC = candidate au renouvellement)
- [ ] **État physique :** Bon / Acceptable / Dégradé
- [ ] **Problèmes fréquents :** Lenteur ? Crash ? Problème matériel ?
- [ ] **Capacité actuelle :**
  - [ ] RAM: _____ GB (< 8 GB = renouveler)
  - [ ] Disque: _____ GB (< 256 GB SSD = renouveler)
  - [ ] Batterie (si portable): _____ % (< 50% = changer)

### Demande approuvée

- [ ] **Responsable IT :** Approuve le renouvellement
- [ ] **Budget :** Validé
- [ ] **Utilisateur :** Informé de la date de changement
- [ ] **Ticket GLPI :** Créé (numéro : ________)

---

## 🔄 Processus de renouvellement

### ÉTAPE 1 : Backup des données (J-2)

**C'est CRITIQUE - les données de l'utilisateur doivent pas se perdre !**

```
1. Connecter disque externe ou NAS
2. Copier dossiers utilisateur :
   - Documents
   - Bureau
   - Favoris navigateur (browser export)
   - Partages réseau (notes utilisateur)
   
3. Vérifier taille données :
   - Petit (< 50 GB) = USB/disque externe
   - Gros (> 100 GB) = NAS ou migration serveur
   
4. Valider le backup :
   - Vérifier intégrité fichiers
   - Tester quelques fichiers aléatoires
```

**Documentation :**
```
Utilisateur : _____________
Données backup : _________ GB
Localisation backup : _____________
Date backup : _____________
Validé : ✅ OK / ❌ ERREUR
```

---

### ÉTAPE 2 : Répertorier les logiciels (J-2)

Avant de perdre l'ancien PC, documenter ce qui est installé :

```
1. Win + R → "msinfo32" → Applications
   Ou : Panneau de configuration → Programmes et fonctionnalités
   
2. Lister :
   - Logiciels métier (applicatifs CNG)
   - Suite Office
   - Navigateurs
   - VPN / Tools réseau
   - Antivirus / Sécurité
```

**Fichier à créer :**
```
LOGICIELS ANCIEN PC :
- Microsoft Office 2021 (Licence n° __________)
- Adobe Reader DC
- VPN Pulse Secure
- GLPI
- [Autres]

LICENSES À TRANSFÉRER :
- [Listé ci-dessus]

LOGICIELS À RÉINSTALLER :
- [Ce qui est pas disponible]
```

---

### ÉTAPE 3 : Configuration utilisateur (J-1)

Sauvegarder aussi les configurations :

- [ ] **Favoris navigateur :** Exporter HTML (Firefox/Chrome)
- [ ] **Paramètres de messagerie :** Si email local
- [ ] **Imprimantes préférées :** Noter lesquelles
- [ ] **Lecteurs réseau mappés :** Lister (Z:\, X:\, etc.)
- [ ] **Raccourcis bureau/menu :** Prendre screenshot

---

### ÉTAPE 4 : Déploiement nouveau PC (J)

#### A) Installation OS + software de base

```
1. Démarrer le nouveau PC
2. Configuration Windows :
   - [ ] Langue : Français
   - [ ] Région : France
   - [ ] Updates : Tout mettre à jour
   - [ ] Antivirus : Activé
   - [ ] Nom machine : [Suivre naming CNG]
   
3. Joindre domaine CNG :
   - [ ] Domaine : CNG.local (ou valeur réelle)
   - [ ] Administrateur : (credentials IT)
   - [ ] Redémarrer
   
4. Réinstaller logiciels métier :
   - [ ] Office 365
   - [ ] VPN
   - [ ] Logiciels métier CNG
   - [ ] Drivers spécifiques
```

#### B) Restaurer données utilisateur

```
1. Connecter disque backup
2. Copier les données vers nouveau PC :
   C:\Users\[login]\Documents ← Documents backup
   C:\Users\[login]\Desktop ← Bureau backup
   
3. Vérifier accès aux partages réseau :
   - [ ] P:\ (Partage personnel)
   - [ ] G:\ (Partage groupe)
   - [ ] Autres lecteurs mappés
   
4. Restaurer favoris navigateur :
   - Importer fichier HTML
```

#### C) Paramétrer pour utilisateur

```
1. Configurer imprimantes :
   - [ ] Imprimante principale (défaut)
   - [ ] Autres imprimantes préférées
   
2. Configurer email :
   - [ ] Outlook synchronisé
   - [ ] Signature paramétrée
   
3. Lecteurs réseau :
   - [ ] Mapper lecteurs (script ou manuel)
   - [ ] Vérifier accès à chacun
   
4. Raccourcis bureau :
   - [ ] Recréer selon screenshot ancien PC
```

---

### ÉTAPE 5 : Validation utilisateur (J)

Avant de considérer ça comme "fini", tester avec l'utilisateur :

- [ ] Utilisateur peut se **connecter** (domaine + password)
- [ ] **Internet** fonctionne (test: ping 8.8.8.8)
- [ ] **Wi-Fi** OK (si portable)
- [ ] **Partages réseau** accessibles
- [ ] **Imprimantes** actives
- [ ] **Données** restaurées et accessibles
- [ ] **Logiciels critiques** fonctionnent
- [ ] **Vitesse acceptable** (pas de lag)
- [ ] **Batterie charge** (si portable)

**Signature utilisateur :** ✅ Je confirme que tout fonctionne

---

## 📦 Traitement de l'ancien PC

### Récupération données résiduelles

- [ ] **Vérifier :** Aucune donnée personnelle sur disque (surtout données CNG !)
- [ ] **Commande :** `cipher /w:C:` (sécurise suppression)
- [ ] **Formatage :** Disque complètement effacé

### Decommissioning

- [ ] **Inventaire GLPI :** Marquer comme "Retired"
- [ ] **Asset tag :** Retirer sticker physique
- [ ] **Documentation :** Archiver fiche technique
- [ ] **Recyclage :**
  - [ ] Contacter responsable matériel
  - [ ] Destruction confidentielle (si données sensibles)
  - [ ] Ou recyclage standard électronique

**Trace :**
```
Ancien PC retiré du service : [Date]
Numéro série : _____________
Destination: Recyclage / Destruction / Réaffectation
Responsable : _____________
```

---

## 📋 Traçabilité complète

```
========== RENOUVELLEMENT PC ==========

Utilisateur : _____________
Ancien PC :
  - Modèle : _____________
  - Âge : _____ ans
  - Numéro série : _____________

Nouveau PC :
  - Modèle : _____________
  - Numéro série : _____________
  - Config : RAM ____ / SSD ____ / OS _______

Données backup :
  - Taille : _________ GB
  - Localisation : _____________
  - Validé : ✅ OUI

Date renouvellement : _____________
Technicien : _____________
Utilisateur validation: ✅ OK

Ticket GLPI : ____________
```

---

## ✅ Checklist finale

Avant de cloturer le ticket :

- [ ] Ancien PC decommissionné (données sécurisées)
- [ ] Nouveau PC testé et validé par utilisateur
- [ ] Données complètement restaurées
- [ ] Logiciels réinstallés et fonctionnels
- [ ] Permissions/accès configurés
- [ ] Inventaire GLPI mis à jour
- [ ] Ticket fermé
- [ ] Utilisateur satisfait

---

## 📚 Ressources

- [Gestion des équipements GLPI](https://glpi-project.org)
- Responsable matériel : [Contact]
- Support IT : [Contact]

---

**Version :** 1.0  
**Auteur :** Lucas De Oliveira  
