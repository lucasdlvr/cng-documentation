# Procédure : Dépannage - Utilisateur n'a pas accès Internet

**Numéro procédure :** P001  
**Date création :** Juin 2026  
**Niveau :** Support L1 (Niveau 1)

---

## 🎯 Objectif

Diagnostiquer et résoudre rapidement un problème de connectivité Internet ou réseau.

---

## 📋 Symptômes (le client signale)

Cochez le symptôme correspondant :

- [ ] "Je n'ai pas Internet"
- [ ] "Je ne peux pas me connecter au Wi-Fi"
- [ ] "Le réseau est très lent"
- [ ] "Je ne vois pas le Wi-Fi disponible"
- [ ] "Internet marche par moments, puis coupe"

---

## 🔧 Diagnostic (Étapes)

**ÉTAPE 1 : Vérifier le statut du réseau (2 min)**

Windows 10/11 :
- En Bas à droite → Icône réseau → Qu'est-ce qu'on voit?
  - ✅ Connecté à Wi-Fi = probablement bon
  - ❌ "Pas de connexion" = problème
  - ❌ "!" jaune = problème de connexion

MacOS :
- En Haut à droite → Icône Wi-Fi → Quels réseaux disponibles ?

**Action :** Redémarrer la carte réseau

Windows :
1. Clic droit sur icône réseau → Paramètres réseau avancés
2. Paramètres réseau avancés → Paramètres d'adaptateur
3. Clic droit sur "Wi-Fi" ou "Ethernet" → Désactiver
4. Attendre 5 sec → Réactiver
5. Attendre 30 sec

---

**ÉTAPE 2 : Tester la connectivité (2 min)**

Ouvrir Command Prompt (ou Terminal) :

Windows : Win + R → tape "cmd" → Entrée
Mac : Cmd + Espace → tape "terminal" → Entrée

Tape la commande :
```
ping 8.8.8.8
```

**Résultat ?**
- ✅ `Reply from 8.8.8.8: bytes=32 time=xx ms` → Internet OK, DNS possiblement en cause
- ❌ `Request timed out` → Pas de connexion Internet, vérifier routeur/Wi-Fi

---

**ÉTAPE 3 : Vérifier DNS (2 min)**

Toujours dans le terminal/cmd :

```
nslookup google.com
```

**Résultat ?**
- ✅ `Address: 142.250.x.x` (un truc qui s'affiche) → DNS OK
- ❌ `Can't find server` → DNS cassé

**Fix DNS :**

Windows :
1. Panneau de configuration → Réseau → Paramètres adaptateur
2. Clic droit Wi-Fi → Propriétés
3. IPv4 → Propriétés
4. Cocher "Utiliser les serveurs DNS suivants"
5. DNS primaire: 8.8.8.8
6. DNS secondaire: 1.1.1.1
7. OK → Redémarrer

---

**ÉTAPE 4 : Vérifier le routeur (2 min)**

Si ping et DNS OK mais toujours pas Internet :

```
ping 192.168.1.1
```

(ou 192.168.0.1 selon votre réseau)

- ✅ Répond → Routeur OK, problème en amont
- ❌ Request timed out → Routeur OFF ou problème Wi-Fi

**Fix :**
- Éteindre routeur 30 sec
- Redémarrer
- Vérifier voyants (Internet = vert)

---

## ✅ Solutions rapides (par ordre de fréquence)

| Problème | Solution | Temps |
|----------|----------|-------|
| Wi-Fi pas vu | Redémarrer routeur | 2 min |
| Internet lent | Redémarrer PC | 3 min |
| Pas de connexion | Vérifier DNS | 5 min |
| Connexion intermittente | Redémarrer adaptateur réseau | 2 min |
| Toujours rien | Contacter responsable réseau | - |

---

## 📞 Quand escalader (contacter responsable réseau) ?

- ✅ Vous avez suivi tout et ça marche pas
- ✅ Le problème affecte plusieurs postes
- ✅ Le routeur ne répond pas
- ✅ Suspect problème câble/infrastructure physique

**Contacter :** [Nom responsable réseau] — [email/phone]

---

## 📝 Traçabilité (À documenter après intervention)

- Numéro ticket : ____________
- Date intervention : ____________
- Utilisateur : ____________
- Symptôme initial : ____________
- Étapes effectuées :
1. ___________________
2. ___________________
3. ___________________

- Solution appliquée : ____________
- Résultat : ✅ Résolu / ❌ Escaladé
- Temps total : ____________ min
- Notes additionnelles : ____________

---

**Version :** 1.0  
**Auteur :** Lucas De Oliveira  
