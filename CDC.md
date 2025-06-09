# Cahier des Charges - OrgaBoard
*Dashboard personnel d'organisation intégrée / Life Operating System locale*

## 1. Présentation du Projet

### 1.1 Contexte
OrgaBoard est une application desktop multiplateforme conçue pour offrir une solution complète de gestion personnelle, fonctionnant entièrement en local et axée sur la confidentialité des données.

### 1.2 Objectifs
- Fournir un tableau de bord unifié pour la gestion des tâches, projets et habitudes
- Permettre un suivi psychologique quotidien
- Garantir la confidentialité totale des données
- Offrir une expérience utilisateur fluide et personnalisable

## 2. Spécifications Fonctionnelles

### 2.1 Modules Principaux

#### 2.1.1 Tableau de Bord
- Vue synthétique des informations clés
- Widgets personnalisables
- Graphiques d'évolution
- Filtres et vues temporelles configurables

#### 2.1.2 Gestion de Projets et Tâches
- Interface style Trello
- Système de colonnes (To do, In progress, Done)
- Hiérarchisation des tâches
- Étiquetage et dates limites
- Système de commentaires

#### 2.1.3 Suivi des Habitudes
- Création d'habitudes personnalisées
- Catégorisation (positives/négatives)
- Suivi quotidien
- Visualisation des streaks

#### 2.1.4 Suivi Psychologique
- Saisies quotidiennes (matin/soir)
- Métriques : humeur, motivation, environnement, énergie, stress
- Heures de lever/coucher
- Navigation temporelle flexible

#### 2.1.5 Agenda
- Vues multiples (jour/semaine/mois)
- Intégration avec les projets et tâches
- Système de notifications locales
- Gestion d'événements personnels

### 2.2 Fonctionnalités Transverses
- Export des données en CSV
- Système d'archivage
- Navigation temporelle dans tous les modules
- Personnalisation de l'interface

## 3. Spécifications Techniques

### 3.1 Architecture Technique
- **Frontend** : Electron + React
- **UI** : 
  - Tailwind CSS
  - Radix UI
  - ShadCN UI
- **Graphiques** : Chart.js
- **État** : Zustand
- **Base de données** : Prisma + SQLite
- **Utilitaires** : PapaParse (CSV)

### 3.2 Base de Données
Structures détaillées pour :
- Projets
- Tâches
- Habitudes
- Suivis psychologiques
- Événements agenda

### 3.3 Sécurité
- Stockage 100% local
- Aucune connexion externe
- Protection des données sensibles

## 4. Méthodologie de Développement

### 4.1 Approche TDD
15 étapes de développement :

1. **Configuration initiale**
   - Environnement de développement
   - Outils et dépendances
   - Structure du projet

2. **Base de données**
   - Modèles Prisma
   - Tests d'intégration
   - Migrations

3. **State Management**
   - Stores Zustand
   - Tests des actions
   - Persistance locale

4. **Interface de base**
   - Layout principal
   - Navigation
   - Tests d'accessibilité

5. **Module Projets**
   - CRUD
   - Interface Trello
   - Tests d'intégration

6. **Module Tâches**
   - Système de sous-tâches
   - Drag-and-drop
   - Relations projets-tâches

7. **Module Habitudes**
   - Système de tracking
   - Visualisations
   - Calculs statistiques

8. **Module Suivi Psychologique**
   - Formulaires
   - Navigation temporelle
   - Graphiques

9. **Module Agenda**
   - Vues calendrier
   - Intégration tâches
   - Notifications

10. **Dashboard Principal**
    - Widgets
    - Personnalisation
    - Graphiques synthétiques

11. **Système d'Export**
    - Export CSV
    - Formatage données
    - Interface utilisateur

12. **Tests End-to-End**
    - Scénarios Playwright
    - Tests multi-plateformes
    - Tests de flux

13. **Optimisation**
    - Performance
    - Requêtes
    - Mémoire

14. **Documentation**
    - Technique
    - Utilisateur
    - API

15. **Distribution**
    - Packaging
    - Installateurs
    - Déploiement

### 4.2 Cycle de Développement
Pour chaque étape :
1. Écriture des tests
2. Vérification des échecs
3. Implémentation
4. Refactoring
5. Validation

## 5. Livrables

### 5.1 Application
- Installateurs pour Windows, Linux, Mac
- Documentation utilisateur
- Documentation technique

### 5.2 Code Source
- Repository Git complet
- Tests unitaires et E2E
- Documentation API

## 6. Extensions Futures Envisagées
- Programme sportif
- Gestion des finances
- Gestion des recettes et courses

## 7. Critères de Qualité
- Tests couvrant >80% du code
- Performance optimale sur toutes les plateformes
- Interface responsive et accessible
- Zéro fuite de données personnelles 