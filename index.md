# 🛗 SOD 4G FUSION — Gestionnaire de Programmation VoIP

<div align="center">

![SOD 4G FUSION](https://img.shields.io/badge/SOD%204G%20FUSION-v2.0-15803d?style=for-the-badge&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0id2hpdGUiIGQ9Ik0xMiAyQzYuNDggMiAyIDYuNDggMiAxMnM0LjQ4IDEwIDEwIDEwIDEwLTQuNDggMTAtMTBTMTcuNTIgMiAxMiAyem0tMiAxNGwtNC00IDEuNDEtMS40MUwxMCAxMy4xN2w2LjU5LTYuNTlMMTggOGwtOCA4eiIvPjwvc3ZnPg==)
![HTML](https://img.shields.io/badge/HTML5-Single%20File-E34F26?style=for-the-badge&logo=html5)
![License](https://img.shields.io/badge/Licence-Propriétaire-red?style=for-the-badge)

**Application web de gestion et programmation VoIP pour ascenseurs GSM SOD 4G Fusion**

[📥 Télécharger](#installation) • [📖 Documentation](#utilisation) • [📱 SMS Gateway](#sms-gateway)

</div>

---

## ✨ Fonctionnalités

| Fonctionnalité | Description |
|----------------|-------------|
| 📊 **Tableau de bord** | Gestion complète des appareils VoIP avec filtres et recherche |
| 📱 **SMS en masse** | Envoi via Mobile Link (Windows), HTTP Gateway Android ou fichier Manuel |
| 📋 **QR Code** | Génération de QR codes de configuration VoIP |
| 📥 **Import Excel** | Import multi-onglets depuis fichiers .xlsx |
| 📤 **Export Excel** | Export complet avec statuts et résumé |
| ☁️ **Google Sheets** | Synchronisation bidirectionnelle avec Google Sheets / AppSheet |
| 🔑 **Licences** | Système de gestion des licences clients |
| 🌙 **Thèmes** | Mode sombre / clair + 6 couleurs d'accentuation |
| 📱 **Responsive** | Compatible PC, tablette et smartphone |
| 🔒 **Authentification** | Système de rôles (Admin / Responsable / Technicien) |

---

## 🚀 Installation

Aucune installation requise — c'est un fichier HTML autonome.

1. **Télécharger** le fichier `index.html`
2. **Double-cliquer** pour l'ouvrir dans votre navigateur
3. **Se connecter** avec vos identifiants

> ✅ Fonctionne hors ligne — toutes les données sont stockées localement (localStorage)

---

## 🔐 Connexion

| Identifiant | Mot de passe | Rôle |
|-------------|-------------|------|
| `admin` | `admin1234` | Administrateur |
| `responsable` | `resp1234` | Responsable |
| `technicien` | `tech1234` | Technicien |

> ⚠️ Changez les mots de passe après la première connexion dans **Paramètres → Utilisateurs**

---

## 📖 Utilisation

### Importer des données
1. Cliquer **Importer Excel** dans la sidebar
2. Sélectionner votre fichier `.xlsx`
3. Les données s'affichent dans le tableau de bord

### Statuts VoIP
| Statut | Couleur | Description |
|--------|---------|-------------|
| ✓ PROGRAMMÉ | 🟢 Vert | VoIP configuré avec succès |
| ✗ NON PROGRAMMÉ | 🔴 Rouge | Problème de configuration |
| 📅 PLANIFIÉ | ⚫ Gris | En attente de programmation |

### Envoi SMS en masse
1. **Cocher** les appareils dans le tableau
2. Cliquer **📱 SMS** dans la barre d'actions
3. Choisir la méthode :
   - 🪟 **Mobile Link** — via Windows Phone Link (recommandé)
   - 📡 **HTTP Gateway** — via app Android
   - 📋 **Manuel** — fichier .txt

---

## 📱 SMS Gateway Android

Pour envoyer des SMS automatiquement depuis votre PC via votre smartphone :

1. Installer **[SMS Gateway for Android](https://play.google.com/store/apps/details?id=capcom6.android.smsgateway)** sur votre téléphone
2. Lancer l'app → activer le serveur local
3. Dans SOD 4G → **Paramètres → SMS Gateway** → entrer l'IP affichée
4. Cliquer **🧪 Tester** pour vérifier la connexion

**Format API utilisé :**
```json
POST http://192.168.X.X:8080/message
Authorization: Basic username:password

{
  "textMessage": { "text": "SO-FU1*0#VOIP:1,..." },
  "phoneNumbers": ["+33612345678"]
}
```

---

## ☁️ Synchronisation Google Sheets / AppSheet

1. Créer un Google Sheet nommé **"SOD 4G FUSION"**
2. Aller dans **Extensions → Apps Script**
3. Copier le script depuis **Paramètres → 📋 Copier le script Apps Script**
4. Déployer comme **Application Web** (accès : Tout le monde)
5. Coller l'URL dans **Paramètres → Google Sheets**

**Boutons disponibles :**
- ⬆ **Envoyer** → SOD 4G → Google Sheets → AppSheet
- ⬇ **Récupérer** → Google Sheets → SOD 4G

---

## 🔑 Système de Licences

L'application inclut un système de licences pour la commercialisation :

- **Générer** des clés clients depuis **Sidebar → Licences** (admin uniquement)
- Format : `SOD-TYPE-CLIENT-XXXX`
- Durée configurable : 30j / 6 mois / 1 an / 2 ans / 10 ans
- **Révoquer** une licence = accès bloqué immédiatement

---

## 📋 Structure des données

| Colonne | Description |
|---------|-------------|
| `numeroAppareil` | Numéro identifiant de l'ascenseur |
| `adresse` | Adresse d'installation |
| `id` | Identifiant VoIP (Num PROM) |
| `mdp` | Mot de passe VoIP |
| `ligne` | Numéro de téléphone de la ligne |
| `serveur` | Serveur SIP (domaine) |
| `port` | Port SIP |
| `technicien` | Technicien assigné |
| `voip` | Statut VoIP (true/false) |
| `voipComment` | Commentaire de programmation |
| `voipSimNumber` | Numéro de SIM |
| `voipIccid` | Numéro ICCID de la SIM |

---

## 🛠️ Technologies

- **HTML5 / CSS3 / JavaScript** — Application monofichier, aucune dépendance serveur
- **XLSX.js** — Import/Export Excel
- **QRCode.js** — Génération QR codes
- **Google Fonts** — Inter + JetBrains Mono
- **localStorage** — Stockage local des données

---

## 📄 Licence

Ce logiciel est propriétaire. Tous droits réservés.  
Pour obtenir une licence commerciale : contactez l'auteur.

---

<div align="center">
  <strong>© 2026 SOD 4G FUSION — Développé pour SODIMAS SECORDUPE</strong>
</div>
