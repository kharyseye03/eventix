# Eventix

**Eventix** est une application mobile pour découvrir les concerts, festivals et spectacles près de chez soi, acheter ses billets en quelques secondes avec **Mobile Money**, et les présenter le jour J grâce à un QR code.

> Projet en cours de développement : l'interface est construite écran par écran à partir d'une maquette Figma, sur des données fictives en attendant l'API.

## Fonctionnalités prévues

- **Connexion par téléphone** : numéro + code de vérification reçu par SMS, sans mot de passe.
- **Découverte** : événements autour de soi (Dakar par défaut), recherche et filtres par catégorie (concerts, festivals, spectacles).
- **Fiche événement** : date, lieu, description, événements payants ou en entrée gratuite.
- **Choix des billets** : plusieurs catégories (Standard, Premium, VIP…) et choix de la quantité.
- **Paiement Mobile Money** : récapitulatif de la commande puis paiement avec son numéro.
- **Billets** : billet électronique avec QR code, téléchargeable, et liste des billets à venir ou passés.
- **Favoris** : garder de côté les événements qui intéressent.
- **Profil** : informations personnelles, moyens de paiement, notifications et aide.

## Stack technique

- [Flutter](https://flutter.dev) / Dart
- [go_router](https://pub.dev/packages/go_router) pour la navigation
- Icônes Material (version arrondie)

## Architecture

Le code suit une organisation **par fonctionnalité** (feature-based) :

```
lib/
├── main.dart
├── core/          → les fondations, rien de visible
│   ├── constants/ → couleurs, typographie, dimensions, textes, assets, durées
│   ├── theme/     → thème global de l'app
│   └── router/    → toutes les routes (go_router)
├── shared/        → widgets et formatters réutilisés partout
└── features/      → un dossier par fonctionnalité
    └── <feature>/
        ├── data/          → modèles et données fictives
        └── presentation/  → écrans et widgets propres à la feature
```

En résumé : `core/` dit comment l'app doit être, `shared/` fournit les briques, `features/` construit les écrans avec.

### Conventions

- Aucune valeur en dur dans les écrans : on passe toujours par `AppColors`, `AppDimens`, `AppStrings`, `AppAssets`…
- Navigation uniquement via `go_router`, avec les chemins déclarés dans `AppRoutes`.
- `shared/` ne dépend d'aucune feature : un widget partagé reçoit ses données en paramètres.
- Les raccourcis temporaires sont signalés par un commentaire `// shortcut: <la limite>, <quand le remplacer>`.
- Les animations restent discrètes et respectent le réglage « réduire les animations » du téléphone.

## Démarrer

Prérequis : Flutter (canal stable) installé.

```bash
flutter pub get
flutter run
```

Vérifications avant chaque contribution :

```bash
flutter analyze
flutter test
```

## Workflow Git

- `main` : version stable
- `develop` : intégration
- `feature/<nom>` : une branche par fonctionnalité, créée depuis `develop`

## Avancement

- [x] Fondations (thème, constantes, routeur)
- [ ] Onboarding
- [ ] Connexion par téléphone et vérification SMS
- [ ] Accueil
- [ ] Fiche événement
- [ ] Choix des billets et paiement
- [ ] Billet et mes billets
- [ ] Favoris
- [ ] Profil
