# Création d'une application avec React Router et Axios

## Sommaire :
1. [**🚀 Installation de React Router**](#1-installation-de-react-router)
   - [Commande d'installation](#commande-dinstallation)
   - [Importance de React Router dans une application React](#importance-de-react-router-dans-une-application-react)
2. [**🛣️ Création des routes de l'application**](#2-création-des-routes-de-lapplication)
   - [Structure du projet](#structure-du-projet)
   - [Création des composants de base](#création-des-composants-de-base)
     - [Home](#home)
     - [Users](#users)
     - [UserDetails](#userdetails)
   - [Configuration des routes dans App.jsx](#configuration-des-routes-dans-appjsx)
3. [**🌐 Appels à une API RESTful avec Axios**](#3-appels-à-une-api-restful-avec-axios)
   - [Installation d'Axios](#installation-daxios)
   - [Utilisation d'Axios pour effectuer des requêtes GET](#utilisation-daxios-pour-effectuer-des-requêtes-get)
   - [Gestion des données reçues de l'API](#gestion-des-données-reçues-de-lapi)
4. [**⚠️ Gestion des erreurs et des chargements**](#4-gestion-des-erreurs-et-des-chargements)
   - [Mise en place d'états pour le chargement et les erreurs](#mise-en-place-détats-pour-le-chargement-et-les-erreurs)
   - [Affichage de messages de chargement](#affichage-de-messages-de-chargement)
   - [Gestion et affichage des erreurs](#gestion-et-affichage-des-erreurs)
   - [Utilisation de try/catch pour gérer les exceptions](#utilisation-de-trycatch-pour-gérer-les-exceptions)
- [**🏁 Conclusion**](#conclusion)
- [🏠 retour à l'accueil du cours](./React-&-Vite-JS.md)
- [🏠 retour à l'accueil du repository](../README.md)

---

## 1. Installation de React Router

**React Router** est un package qui permet de gérer la navigation entre différentes pages dans une application React. Pour l'installer, procédez comme suit :

```bash
npm install react-router-dom
```

Une fois installé, vous pouvez commencer à configurer vos routes pour naviguer entre différentes pages dans votre application.

---

## 2. Création des routes de l’application

Après avoir installé **React Router**, nous devons définir les routes de l'application. Commençons par créer quelques composants pour représenter différentes pages de notre application :

## Exemple de structure de projet :
```
src/
  ├── components/
  │     ├── Home.jsx
  │     ├── Users.jsx
  │     └── UserDetails.jsx
  ├── App.jsx
  └── main.jsx
```

## `Home.jsx` (Composant d'accueil)
```jsx
import React from 'react';

const Home = () => {
  return (
    <div>
      <h1>Accueil</h1>
      <p>Bienvenue sur l'application React avec React Router et Axios.</p>
    </div>
  );
}

export default Home;
```

### `Users.jsx` (Liste des utilisateurs)
Nous allons utiliser Axios dans ce composant pour appeler une API RESTful plus tard.

```jsx
import React, { useState, useEffect } from 'react';
import { Link } from 'react-router-dom';

const Users = () => {
  return (
    <div>
      <h1>Liste des utilisateurs</h1>
      <p>Cette page affichera la liste des utilisateurs récupérés depuis l'API.</p>
    </div>
  );
}

export default Users;
```

### `UserDetails.jsx` (Détails d'un utilisateur)
Ce composant affichera des informations détaillées sur un utilisateur spécifique.

```jsx
import React from 'react';

const UserDetails = () => {
  return (
    <div>
      <h1>Détails de l'utilisateur</h1>
      <p>Cette page affichera les détails d'un utilisateur spécifique.</p>
    </div>
  );
}

export default UserDetails;
```

### Configuration du routeur dans `App.jsx`

Ensuite, configurez les routes dans le fichier `App.jsx` pour lier ces composants à des routes spécifiques :

```jsx
import React from 'react';
import { BrowserRouter as Router, Routes, Route, Link } from 'react-router-dom';
import Home from './components/Home';
import Users from './components/Users';
import UserDetails from './components/UserDetails';

function App() {
  return (
    <Router>
      <div>
        <nav>
          <ul>
            <li><Link to="/">Accueil</Link></li>
            <li><Link to="/users">Utilisateurs</Link></li>
          </ul>
        </nav>
        <Routes>
          <Route path="/" element={<Home />} />
          <Route path="/users" element={<Users />} />
          <Route path="/users/:id" element={<UserDetails />} />
        </Routes>
      </div>
    </Router>
  );
}

export default App;
```

---

## 3. Appels à une API RESTful avec Axios

Nous allons maintenant utiliser **Axios** pour faire des appels à une API RESTful. Installez Axios :

```bash
npm install axios
```

Nous allons mettre à jour les composants `Users` et `UserDetails` pour récupérer et afficher les données d'une API.

### `Users.jsx` (Récupération de la liste des utilisateurs avec Axios)

```jsx
import React, { useState, useEffect } from 'react';
import { Link } from 'react-router-dom';
import axios from 'axios';

const Users = () => {
  const [users, setUsers] = useState([]);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    axios.get('https://jsonplaceholder.typicode.com/users')
      .then(response => {
        setUsers(response.data);
        setLoading(false);
      })
      .catch(error => {
        setError('Erreur lors de la récupération des utilisateurs');
        setLoading(false);
      });
  }, []);

  if (loading) return <p>Chargement des utilisateurs...</p>;
  if (error) return <p>{error}</p>;

  return (
    <div>
      <h1>Liste des utilisateurs</h1>
      <ul>
        {users.map(user => (
          <li key={user.id}>
            <Link to={`/users/${user.id}`}>{user.name}</Link>
          </li>
        ))}
      </ul>
    </div>
  );
}

export default Users;
```

### `UserDetails.jsx` (Récupération des détails d'un utilisateur avec Axios)

```jsx
import React, { useState, useEffect } from 'react';
import { useParams } from 'react-router-dom';
import axios from 'axios';

const UserDetails = () => {
  const { id } = useParams();
  const [user, setUser] = useState(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    axios.get(`https://jsonplaceholder.typicode.com/users/${id}`)
      .then(response => {
        setUser(response.data);
        setLoading(false);
      })
      .catch(error => {
        setError("Erreur lors de la récupération de l'utilisateur");
        setLoading(false);
      });
  }, [id]);

  if (loading) return <p>Chargement des détails de l'utilisateur...</p>;
  if (error) return <p>{error}</p>;
  if (!user) return <p>Aucun utilisateur trouvé</p>;

  return (
    <div>
      <h1>Détails de {user.name}</h1>
      <p>Email : {user.email}</p>
      <p>Téléphone : {user.phone}</p>
      <p>Site web : {user.website}</p>
    </div>
  );
}

export default UserDetails;
```

---

## 4. Gestion des erreurs et des chargements

Dans les composants `Users` et `UserDetails`, nous avons utilisé des états pour gérer le **chargement** des données et les **erreurs** qui peuvent survenir lors des appels à l'API.

- **Chargement** : Nous utilisons `loading` pour afficher un message pendant que les données sont en cours de récupération.
- **Erreur** : Nous utilisons `error` pour afficher un message si la requête échoue (par exemple, si l'API est indisponible).

Voici un résumé de la gestion des états dans ces composants :

- Initialement, `loading` est à `true`.
- Lorsque les données sont récupérées avec succès, `loading` passe à `false` et les données sont affichées.
- En cas d'erreur, `loading` passe à `false` et un message d'erreur est affiché.

---

## Conclusion

Cette structure permet de créer une application React simple qui utilise **React Router** pour la navigation et **Axios** pour interagir avec une API RESTful. Vous pouvez maintenant enrichir cette application en ajoutant des fonctionnalités comme l'authentification, la gestion des états globaux (via Redux ou Context API), ou encore la gestion des formulaires pour soumettre des données à l'API.


[🔝 Retour en haut](#création-dune-application-avec-react-router-et-axios)

---

[🏠 retour à l'accueil du cours](./React-&-Vite-JS.md)
                                                                                                  [🏠 retour à l'accueil du repository](../README.md)
