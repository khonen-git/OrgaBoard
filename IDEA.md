# Dashboard personnel d’organisation intégrée ou Life Operating System locale (nom: OrgaBoard)

Une application desktop locale multiplateforme (Windows/Linux/Mac), sans nécessité de connexion internet, axée sur la sécurité et la confidentialité.

## Besoins

### Tableau de bord

- Vue d’ensemble des éléments clés : tâches en cours, projets actifs, habitudes (bonnes/mauvaises), humeur du jour, etc.
- Widgets ou cartes synthétiques avec graphiques (ex : courbe d’évolution des habitudes). 
- Visualisation de l’évolution : streak, heatmap, courbes temporelles.
- Affichage personnalisable : filtres, vues semaine/mois, choix des modules visibles.

### Agenda

- Affichage journalier, hebdomadaire, mensuel.
- Intégration des événements liés aux projets ou tâches.
- Ajout manuel d’événements personnels.
- Notifications et rappels locaux.

### Tâches et projets (style Trello)

- Système de cartes avec colonnes (To do, In progress, Done...).
- Possibilité de hiérarchiser les tâches (sous-tâches, dépendances).
- Ajout d’étiquettes, de dates limites, de notes/commentaires.

### Gestion des habitudes

- Liste personnalisable d’habitudes à suivre (positives ou négatives).
- Suivi par jour (coché / non coché ou avec des notes).
- Navigation temporelle

### Suivi psychologique

- Champs à remplir matin et soir tous les jours: humeur, motivation, environnement, énergie, stress, heure lever/coucher
- Possibilité illimités pour pouvoir les remplir n'importe quand et à quel heure, possibilité de pouvoir sélectionner le jour
- Navigation temporelle : jour précédent/suivant et date calendrier

### Exportation des données

- Export CSV complet ou filtré (ex : habitudes, suivi psychologiques, tâches, etc.).
- Option d’archivage périodique.

### Précisions

- Aucune restriction temporelle et fréquence pour compléter les données 

## Structure des données

### 📁 Projet (project)

| Champ         | Type         | Description                            |
|---------------|--------------|----------------------------------------|
| id            | string (UUID) | Identifiant unique                     |
| nom           | string       | Nom du projet                          |
| description   | string       | Description longue                     |
| date_creation | datetime     | Date de création                       |
| statut        | enum         | Actif / Archivé / Terminé              |
| date_echeance | date?        | Date butoir (optionnelle)             |

🔄 **Relation** : Un projet peut contenir plusieurs tâches.

### ✅ Tâche (task)

| Champ         | Type         | Description                            |
|---------------|--------------|----------------------------------------|
| id            | string (UUID) | Identifiant unique                     |
| titre         | string       | Titre court                            |
| description   | string       | Détail de la tâche                     |
| date_limite   | date?        | Date limite                            |
| statut        | enum         | À faire / En cours / Terminé           |
| projet_id     | string?      | Référence au projet (optionnelle)     |
| parent_id     | string?      | Sous-tâche de (référence récursive)    |
| etiquettes    | string[]     | Liste de tags                          |
| priorite      | int?         | Priorité (1 à 5)                     |

🔄 **Relation** : Une tâche peut appartenir à un projet et à une autre tâche (sous-tâche).

### 🔁 Habitude (habit)

| Champ       | Type         | Description                            |
|-------------|--------------|----------------------------------------|
| id          | string (UUID) | Identifiant unique                     |
| nom         | string       | Nom de l’habitude                      |
| type        | enum         | Positive / Négative                    |
| frequence   | enum         | Quotidienne / Hebdomadaire / 3 fois par semaine / etc |
| objectif    | int?         | Nombre de répétitions souhaité         |
| actif       | bool         | Si l’habitude est active ou non        |

### 📅 Enregistrement d’habitude (habit_log)

| Champ        | Type         | Description                            |
|--------------|--------------|----------------------------------------|
| id           | string (UUID) | Identifiant unique                    |
| habitude_id  | string       | Référence à l’habitude                 |
| date         | date         | Date de réalisation                    |
| realisee     | bool         | Réalisée ou non                        |
| commentaire  | string?      | Commentaire facultatif                 |

### 🧠 Suivi psychologique (psy_entry)

| Champ           | Type         | Description                            |
|------------------|--------------|----------------------------------------|
| id               | string (UUID) | Identifiant unique                    |
| date             | date         | Timestamp saisie (automatique)        |
| date             | date         | Date                                  |
| moment           | enum         | Matin / Soir                          |
| humeur           | int (0-10)   | Note de l’humeur                      |
| motivation       | int (0-10)   | Idem                                  |
| environnement    | int (0-10)   | Idem                                  |
| energie          | int (0-10)   | Idem                                  |
| stress           | int (0-10)   | Idem                                  |
| heure_lever_coucher | time      | Heure de lever (si moment = matin)   |
| commentaire      | string?      | Commentaire libre                     |

### 📆 Événement (agenda_event)

| Champ       | Type          | Description                              |
|-------------|---------------|------------------------------------------|
| id          | string (UUID) | Identifiant unique                       |
| titre       | string        | Nom court                                |
| description | string?       | Détail optionnel                         |
| date        | datetime      | Date et heure                            |
| lien_taches | string[]?     | Références à plusieurs tâches (optionnel) |
| rappel      | int?          | Minutes avant notification               |

## 📌 Relations principales

- `projet` → `tâches[]`
- `tâche` → `sous-tâches[]`
- `habitude` → `habit_log[]`
- `agenda_event` → `tâches[]?`

## Import / Export

- **Export CSV** : disponible pour toutes les entités (tâches, projets, habitudes, entrées psychologiques...).
- **Filtrage** : par date, catégorie, statut, période.
- **Import CSV** (optionnel) : envisagé pour l’ajout en masse d’habitudes, tâches ou projets.

## Stack technique

- **Frontend :** Electron + React
- **UI :** Tailwind CSS + Radix UI + ShadCN UI
- **Graphiques :** Chart.js
- **State management :** Zustand
- **Base de données locale :** Prisma + SQLite
- **Import/export CSV :** PapaParse
- **Packaging :** Electron Forge / Electron Builder
- **Tests :**
  - Vitest pour les tests unitaires
  - React Testing Library pour les tests de composants
  - Playwright pour les tests end-to-end

## Git

- .gitignore pour les données sensibles

##  Sécurité & Confidentialité

- Données uniquement en local.
- Aucun envoi vers des serveurs externes.

## Extensions possibles

- Programme sportif
- Gestionnaire de finances (compte courant, abonnements, etc)
- Recette cuisine et logistique des courses alimentaires