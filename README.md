# 🤰 Mama — Application mobile de suivi de grossesse

**Mama** est une application Android qui accompagne les futures mamans au quotidien : suivi de la santé, nutrition, activité sportive, sommeil, rendez-vous médicaux, urgences et assistant conversationnel basé sur l'IA.

Projet réalisé en équipe en 4ème année du cycle ingénieur (option SLEAM) à l'ESPRIT.

## ✨ Fonctionnalités

### 🏠 Tableau de bord
Point d'entrée de l'application : accès rapide à tous les modules, aux urgences et au chatbot.

### 🩺 Santé
- Suivi des indicateurs de santé (saisie et graphiques d'évolution avec MPAndroidChart)
- Journal des symptômes
- Informations hebdomadaires sur l'évolution de la grossesse
- Suivi du sommeil avec enregistrement audio en arrière-plan (service au premier plan) et liste des enregistrements
- Météo et conseils d'activité adaptés

### 🥗 Nutrition
- Journal des repas (ajout, modification, suppression)
- Scan de codes-barres avec CameraX et ZXing, informations produit via l'API **Open Food Facts**
- Suivi de l'hydratation avec rappels et notifications
- Analyse nutritionnelle assistée par **Gemini**
- Rappels de repas

### 🏃‍♀️ Sport
- Tableau de bord d'activité et historique des séances (base **Room**)
- Bibliothèque d'exercices avec vidéos
- Courbes de tendance personnalisées

### 💊 Médicaments
Gestion des médicaments de la future maman.

### 📅 Rendez-vous
Gestion des rendez-vous médicaux avec notifications de rappel.

### 🚑 Urgences
Localisation de l'utilisateur et recherche des établissements de santé proches via **OpenStreetMap (Overpass API)**.

### 💬 Chatbot
Assistant conversationnel basé sur l'API **Google Gemini**, accessible depuis le tableau de bord.

### 🔐 Authentification
Inscription, connexion et récupération de mot de passe (stockage local SQLite).

## 🛠️ Stack technique

| Domaine | Technologies |
|---|---|
| Langage | Java |
| Plateforme | Android (minSdk 24, targetSdk 34) |
| UI | Material Components, ConstraintLayout |
| Persistance | SQLite (`SQLiteOpenHelper`), Room |
| Réseau | Retrofit 2, Gson |
| IA | Google Gemini API |
| Caméra / scan | CameraX, ZXing |
| Graphiques | MPAndroidChart |
| Localisation | Google Play Services Location |
| Build | Gradle (Kotlin DSL) |

## 📁 Structure du projet

```
app/src/main/java/com/example/mama/
├── (racine)      Authentification, dashboard, santé, sommeil, rendez-vous, urgences, chat
├── Nutrition/    Repas, hydratation, scan code-barres, Open Food Facts
├── sport/        Séances, exercices, historique (Room)
├── bot/          Client Gemini (requêtes, réponses, adaptateur de chat)
├── api/          Service Overpass (établissements de santé)
└── weather/      Modèles et API météo
```

## 🚀 Installation

### Prérequis
- Android Studio (version récente)
- JDK 8 ou plus
- Un appareil ou émulateur Android 7.0 (API 24) ou plus

### Étapes

```bash
git clone https://github.com/EmnaRiahi/ProjetMobile.git
cd ProjetMobile
```

1. Ouvrir le projet dans Android Studio.
2. Renseigner votre clé API Gemini (voir section suivante).
3. Laisser Gradle synchroniser les dépendances.
4. Lancer l'application (▶️) sur un appareil ou un émulateur.

## 🔑 Configuration des clés API

Le chatbot et l'analyse nutritionnelle utilisent l'API Gemini. Ne mettez **jamais** une clé directement dans le code source : ajoutez-la dans `local.properties` (non versionné) :

```properties
GEMINI_API_KEY=votre_cle_ici
```

puis exposez-la via `BuildConfig` dans `app/build.gradle.kts`. Une clé peut être obtenue sur [Google AI Studio](https://aistudio.google.com/).

## 🔒 Permissions

Internet, localisation (urgences), caméra (scan), micro (suivi du sommeil), notifications, alarmes exactes (rappels) et reconnaissance d'activité.

## 👥 Équipe

Projet réalisé par une équipe de cinq étudiants, avec une répartition par module :

- **Emna Riahi** — Gestion des urgences et chatbot
- **Rayen** — Nutrition
- **Nessim** — Santé
- **Moatez** — Sport
- **Ezzedine** — Gestion des médicaments

## 📄 Licence

Ce projet est distribué sous licence [MIT](LICENSE).
