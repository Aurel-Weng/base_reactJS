# Création et lacement d'un projet ReactJS avec vite

## Création

Utiliser la commande suivant : npm create vite@latest
Puis faire les choix de tech depuis le terminal.

## Lancement

Commandes : 
  - npm install : pour installer les dépendances
  - npm run dev : pour lancer le projet en mode dev
  - npm run build : pour build le projet (compile, créer un dosier avec les fichiers prêt à être déployés)
  - npm run preview : prévisualise le projet en simulant post mise en prod

# Structure du Projet React

## Vue d'ensemble

Ce projet React suit une architecture modulaire avec une séparation claire entre les composants de présentation et ceux contenant de la logique métier.

## Structure des dossiers

```
src/
├── assets/          # Ressources statiques
├── components/      # Composants réutilisables sans logique métier
├── containers/      # Composants avec logique métier
├── errors/          # Gestion des erreurs
├── hooks/           # Hooks personnalisés
├── Layout/          # Structure générale des pages
├── pages/           # Composants de pages/routes
├── services/        # Services externes (API, etc.)
├── style/           # Styles globaux et variables
└── utils/           # Fonctions utilitaires
```

## Description détaillée

### 📁 `assets/`
Contient toutes les ressources statiques du projet :
- Images (logos, icônes, illustrations)
- Fonts personnalisées
- Fichiers JSON de configuration
- Autres ressources médias

### 🧩 `components/`
Composants réutilisables **sans logique métier** :
- Elements d'interface pure (Button, Input, Modal)
- Composants de navigation (Header, Footer, Menu)
- Composants d'affichage (Card, Badge, Loader)

**Caractéristiques :**
- Reçoivent leurs données via les props
- Ne font pas d'appels API
- Peuvent être utilisés dans différents contextes
- Chaque composant a son fichier `.module.css` associé

### 📦 `containers/`
Composants avec **logique métier** :
- Gestion des données (fetch, mutations)
- Formulaires avec validation
- Listes avec filtrage/tri
- Composants connectés aux services

**Caractéristiques :**
- Contiennent la logique applicative
- Gèrent l'état local complexe
- Utilisent les hooks personnalisés
- Font appel aux services

### 🚨 `errors/`
Gestion centralisée des erreurs tel que :
- `ErrorBoundary.jsx` - Capture des erreurs React
- `errorHandler.js` - Traitement des erreurs
- `errorMessages.js` - Messages standardisés
- `apiErrorHandler.js` - Gestion des erreurs API
- `components/` - Composants d'affichage d'erreurs

### 🪝 `hooks/`
Hooks React personnalisés tel que :
- Logique réutilisable entre composants
- Gestion d'état complexe
- Intégration avec les services
- Hooks utilitaires (useLocalStorage, useDebounce, etc.)

### 🏗️ `Layout/`
Structure générale de l'application :
- `Layout.jsx` - Composant principal qui orchestre Header, Footer
- Gestion du layout global
- Structure commune à toutes les pages

### 📄 `pages/`
Composants représentant les pages/routes :
- HomePage, LoginPage, ProfilePage, etc.
- Point d'entrée des différentes sections
- Orchestrent containers et components

### 🔧 `services/`
Services externes et logique d'accès aux données :
- Configuration API
- Appels HTTP
- Authentification
- Services tiers (analytics, notifications)

### 🎨 `style/`
Styles globaux uniquement tel que :
- `globals.css` - Reset CSS, styles globaux
- `variables.css` - Variables CSS (couleurs, espacements)
- `themes/` - Gestion des thèmes
- `mixins.css` - Utilitaires CSS réutilisables

**Note :** Les styles spécifiques aux composants sont dans leurs dossiers respectifs (`.module.css`)

### 🛠️ `utils/`
Fonctions utilitaires réutilisables tel que :
- `formatters.js` - Formatage des données
- `validators.js` - Validation
- `helpers.js` - Fonctions d'aide générale
- `storage.js` - Gestion du localStorage
- `constants.js` - Constantes de l'application

## Conventions

### Composants vs Containers
- **Components** = Présentation pure (dumb components)
- **Containers** = Logique métier (smart components)

### Styles
- Styles globaux dans `style/`
- Styles de composants en `.module.css` à côté du composant

### Naming
- PascalCase pour les composants
- camelCase pour les fichiers utilitaires
- Descriptif et explicite

## Exemple d'utilisation

```jsx
// Page qui utilise un container
import UserListContainer from '../containers/UserListContainer'

// Container qui utilise des composants et services
import { Button, Input } from '../components'
import { userService } from '../services'
import { useUsers } from '../hooks'

// Component pur
export const Button = ({ onClick, children, variant }) => {
  return <button className={styles.button} onClick={onClick}>{children}</button>
}
```

Cette structure favorise la réutilisabilité, la maintenabilité et une séparation claire des responsabilités.