# React & Vite JS

![React et Vite JS](./assets/imgs/react&viteJs.avif)

*Image illustrant React et Vite JS travaillant ensemble pour créer des applications web modernes et performantes.*

## Sommaire :

- [**🌟 Introduction**](#introduction)
  - [Qu'est-ce que React ?](#quest-ce-que-react-)
  - [Qu'est-ce que Vite JS ?](#quest-ce-que-vite-js-)
  - [Les grands principes de React en quelques mots](#les-grands-principes-de-react-en-quelques-mots)
    - [JSX](#jsx)
    - [Composants](#composants)
    - [State & Props](#state--props)
    - [Hooks](#hooks)
  - [Les grands principes de Vite JS en quelques mots](#les-grands-principes-de-vite-js-en-quelques-mots)
    - [Développement ultra-rapide](#développement-ultra-rapide)
    - [Build optimisé](#build-optimisé)
    - [HMR (Hot Module Replacement)](#hmr-hot-module-replacement)
- [**🚀 Initialisation d'un projet React avec Vite**](#initialisation-dun-projet-react-avec-vite)
  - [Prérequis](#prérequis)
  - [Création du projet](#création-du-projet)
  - [Structure du projet](#structure-du-projet)
  - [Lancement du serveur de développement](#lancement-du-serveur-de-développement)
- [**🏁 Conclusion**](#conclusion)
- [**📱 First app (liens vers fichier(First-app.md))**](./First-app.md)
  - [Installation de React Router](./First-app.md#1-installation-de-react-router)
  - [Création des routes de l'application](./First-app.md#2-création-des-routes-de-lapplication)
  - [Appels à une API RESTful avec Axios](./First-app.md#3-appels-à-une-api-restful-avec-axios)
  - [Gestion des erreurs et des chargements](./First-app.md#4-gestion-des-erreurs-et-des-chargements)
- [🏠 retour à l'accueil du repository](../README.md)
---

## Introduction

### Qu'est-ce que React ?

React est une bibliothèque JavaScript open-source, créée par Facebook en 2013, destinée à la création d'interfaces utilisateurs (UI). Elle permet de développer des applications web modernes avec une approche **composant** et un flux de données **unidirectionnel**.

**Caractéristiques principales :**

- **Composants réutilisables** : Les UIs sont découpées en composants indépendants et modulaires.
- **Virtual DOM** : Optimise les mises à jour du DOM réel en ne modifiant que les parties qui changent, ce qui améliore les performances.
- **Flux de données unidirectionnel** : Les données circulent du haut vers le bas, du parent vers l’enfant, ce qui rend le suivi des changements plus simple.

### Qu'est-ce que Vite JS ?

Vite est un **bundler** JavaScript de nouvelle génération, conçu pour être **rapide** et **léger**. Développé par Evan You (créateur de Vue.js), il est destiné aux projets modernes de développement web. Contrairement aux outils de bundling traditionnels comme Webpack, Vite adopte une approche différente : il utilise **ESM (Modules JavaScript natifs)** et traite les fichiers de manière individuelle, ce qui réduit considérablement le temps de démarrage.

**Caractéristiques principales de Vite JS :**

- **Développement ultra-rapide** : Grâce à un serveur de développement basé sur ES Modules, Vite charge instantanément les fichiers JavaScript.
- **Build optimisé** : Utilise Rollup pour la production, permettant des builds rapides et efficaces.
- **HMR (Hot Module Replacement)** : Rafraîchit instantanément les modules modifiés sans recharger toute la page, accélérant ainsi le cycle de développement.

### Les grands principes de React en quelques mots

1. **JSX (JavaScript XML)** : Syntaxe permettant de mélanger du HTML avec du JavaScript. 
   
   ```jsx
   const element = <h1>Hello, world!</h1>;
   ```

2. **Composants** : Les composants encapsulent des éléments réutilisables de l'interface utilisateur. 
   Exemple de composant fonctionnel :
   
   ```jsx
   function Welcome(props) {
     return <h1>Hello, {props.name}</h1>;
   }
   ```

3. **State & Props** : 
   
   - **State** : Gère les données locales d’un composant, déclenchant un re-rendu lorsqu’il change.
   - **Props** : Données passées d’un composant parent à un composant enfant pour les personnaliser.

4. **Hooks** : Fonctions permettant d’ajouter des fonctionnalités comme l’état et le cycle de vie dans les composants fonctionnels.
   
   ```jsx
   import { useState } from 'react';
   
   function Counter() {
     const [count, setCount] = useState(0);
     return (
       <div>
         <p>You clicked {count} times</p>
         <button onClick={() => setCount(count + 1)}>Click me</button>
       </div>
     );
   }
   ```

### Les grands principes de Vite JS en quelques mots

1. **ESM natif** : Vite exploite directement les modules JavaScript natifs (ESM) dans les navigateurs, supprimant le besoin de "bundler" tous les fichiers JavaScript dès le départ. Cela permet de **démarrer instantanément** les projets, même ceux comportant de nombreux modules.

2. **Serveur de développement rapide** : Vite analyse les fichiers JavaScript au moment où ils sont demandés par le navigateur, ce qui réduit considérablement le temps de démarrage.

3. **HMR (Hot Module Replacement)** : Vite permet de mettre à jour les modules modifiés en temps réel sans avoir à recharger toute l'application, améliorant ainsi le flux de travail pendant le développement.

4. **Build optimisé** : Pour la production, Vite utilise **Rollup**, un bundler puissant, qui effectue une compilation optimisée et crée un code performant et minifié.

---

## Initialisation d'un projet React avec Vite

### Étape 1 : Prérequis

Avant de commencer, assurez-vous d'avoir **Node.js** et **npm** installés sur votre machine.

Vérifiez les versions avec :

```bash
node -v
npm -v
```

### Étape 2 : Création d'un projet avec Vite

Pour initialiser un projet React avec Vite, utilisez la commande suivante :

```bash
npm create vite@latest
```

Ensuite, suivez les instructions :

1. Donnez un nom à votre projet (par exemple, `my-vite-react-app`).
2. Sélectionnez le framework `React`.
3. Sélectionnez si vous voulez utiliser TypeScript ou JavaScript (TypeScript est recommandé pour les projets à long terme).

Une fois ces étapes terminées, accédez à votre projet :

```bash
cd my-vite-react-app
```

Ensuite, installez les dépendances :

```bash
npm install
```

### Étape 3 : Démarrer le serveur de développement

Démarrez le serveur de développement avec la commande suivante :

```bash
npm run dev
```

Cela lancera votre application et l'ouvrira dans votre navigateur à l'adresse `http://localhost:5173`. Vite utilise par défaut un port différent de Webpack, mais vous pouvez configurer cela dans `vite.config.js` si nécessaire.

### Étape 4 : Structure du projet généré

Voici à quoi ressemble la structure de votre projet après son initialisation avec Vite :

```
my-vite-react-app/
  ├── node_modules/           # Dépendances du projet
  ├── public/                 # Fichiers publics (favicon, index.html)
  ├── src/                    # Code source de l'application
  │   ├── App.css             # Styles du composant App
  │   ├── App.jsx             # Composant principal
  │   ├── main.jsx            # Point d'entrée de l'application
  │   └── ...
  ├── index.html              # Point d’entrée HTML
  ├── package.json            # Informations sur le projet
  └── vite.config.js          # Configuration de Vite
```

### Étape 5 : Personnalisation de l'application

Le fichier `src/App.jsx` contient le composant principal de l'application. Vous pouvez modifier ce fichier pour commencer à développer votre interface React.

Exemple simple de modification de `App.jsx` :

```jsx
function App() {
  return (
    <div className="App">
      <h1>Bienvenue sur mon application React avec Vite</h1>
    </div>
  );
}

export default App;
```

## Conclusion

**React** et **Vite** forment un duo puissant pour le développement moderne d'applications web. React offre une structure basée sur des composants réutilisables et performants, tandis que Vite améliore considérablement la rapidité de développement grâce à son serveur de développement ultra-rapide et son système de build optimisé. Grâce à Vite, vous pouvez démarrer un projet React en quelques secondes, tout en bénéficiant d'une expérience de développement fluide et efficace.

---

[🔝 Retour en haut](#react--vite-js)

[🏠 retour à l'accueil du repository](../README.md)