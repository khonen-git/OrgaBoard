# OrgaBoard

Un tableau de bord personnel d'organisation intégrée ou Life Operating System local.

## Description

OrgaBoard est une application desktop multiplateforme (Windows/Linux/Mac) conçue pour la gestion personnelle et l'organisation. Elle fonctionne localement, sans nécessité de connexion internet, en mettant l'accent sur la sécurité et la confidentialité.

## Fonctionnalités principales

- 📊 **Tableau de bord personnalisable**
- 📅 **Agenda intégré**
- ✅ **Gestion de tâches et projets**
- 🔄 **Suivi d'habitudes**
- 📈 **Suivi psychologique**
- 💾 **Export des données**

## Stack technique

- **Frontend :** Electron + React
- **UI :** Tailwind CSS + Radix UI + ShadCN UI
- **Graphiques :** Chart.js
- **State management :** Zustand
- **Base de données locale :** Prisma + SQLite
- **Tests :**
  - Vitest pour les tests unitaires
  - React Testing Library pour les tests de composants
  - Playwright pour les tests end-to-end

## Installation

```bash
# Cloner le repository
git clone https://github.com/khonen-git/OrgaBoard.git

# Installer les dépendances
npm install

# Lancer en mode développement
npm run dev
```

## Structure du projet

```
OrgaBoard/
├── src/
│   ├── main/           # Code Electron
│   ├── renderer/       # Code React
│   ├── shared/         # Code partagé
│   └── preload/        # Scripts de preload
├── prisma/             # Schémas et migrations
├── tests/              # Tests
└── electron/           # Configuration Electron
```

## Développement

Consultez le [DEVBOOK.md](DEVBOOK.md) pour plus de détails sur le développement et la progression du projet.

## Contribution

Les contributions sont les bienvenues ! Veuillez consulter le DEVBOOK.md pour comprendre la structure du projet et les conventions de code.

## Licence

MIT 