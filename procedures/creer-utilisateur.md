# Procédure : Créer un nouvel utilisateur Windows (Domaine)

**Numéro procédure :** P002  
**Niveau :** Support L1/L2  
**Prérequis :** Accès administrateur domaine

---

## 🎯 Objectif

Créer un compte utilisateur Windows dans le domaine CNG avec les droits appropriés.

---

## 📋 Informations requises

Avant de commencer, rassemblez :

- [ ] Nom complet de l'utilisateur
- [ ] Prénom
- [ ] Email professionnel
- [ ] Département/équipe
- [ ] Groupes de sécurité (Ex : "ComptabiliteUsers", "Admins", etc...)
- [ ] Responsable direct (qui approuve)

---

## 🔧 Étapes

### ÉTAPE 1 : Accéder à Active Directory

Sur un PC administrateur :

1. Win + R
2. Tape : dsa.msc
3. Entrée
4. Se connecter si demandé (admin identifiants)

### ÉTAPE 2 : Créer le compte

1. Ouvre le dossier "Users" (ou Users > [Département])
2. Clic droit → New → User
3. Remplir :
   - First Name : [Prénom]
   - Last Name : [Nom]
   - User logon name : prenom.nom (Ex : lucas.deoliveira)
4. Next
5. Tape mot de passe temporaire (complexe !)
   - ✅ "User must change password at next logon" (COCHER)
6. Next → Finish

### ÉTAPE 3 : Assigner aux groupes de sécurité

1. Ouvre le nouvel utilisateur (double-clique)
2. Onglet "Member Of"
3. Ajouter → Tape le groupe (Ex : "ComptabiliteUsers")
4. Chercher → OK
5. Appliquer

Groupes typiques (exemple) :
- `ComptabiliteUsers` — accès dossiers partagés
- `VPN_Users` — accès VPN
- `Printers_HP` — accès imprimantes

### ÉTAPE 4 : Configurer profil utilisateur

1. Onglet "Profile" du compte
2. Profile path : \\serveur\profiles\[prenom.nom]
3. Home folder : \\serveur\users\[prenom.nom]
4. Appliquer

### ÉTAPE 5 : Notifier l'utilisateur

Email template :

Sujet : Votre compte IT est créé

Bonjour [Prénom],

Votre compte IT est maintenant actif.

Identifiants de connexion:
- Identifiant : prenom.nom
- Mot de passe : [Temporaire, fourni en personne]

À votre première connexion, vous devrez changer ce mot de passe.

Besoins :
- VPN ? Contactez IT
- Imprimante ? Allez à [Lieu]

Support: [Email/Phone IT]

Cordialement,
[Ton nom]

---

## ✅ Checklist de validation

Après création, vérifier :

- [ ] Utilisateur peut se connecter au PC
- [ ] Accès aux dossiers partagés OK
- [ ] Imprimantes accessibles
- [ ] Email fonctionne
- [ ] VPN fonctionne (si applicable)

---

## 📝 Traçabilité

- Numéro ticket : ____________
- Date : ____________
- Utilisateur créé : ____________
- Groupes assignés : ____________
- Validé par : ____________
- Notes : ____________

---

**Version :** 1.0  
**Auteur :** Lucas De Oliveira
