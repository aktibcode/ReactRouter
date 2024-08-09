# Chapitre : LES ITINERAIRES IMBRIQUES


# Les itinéraires imbriqués

Jusqu'à présent, nous avons travaillé avec des routeurs suffisamment petits pour être entièrement rendus dans un seul fichier. Mais à mesure qu'une application prend de l'ampleur, il peut être utile de scinder le routeur et d'écrire des routes plus proches de l'endroit où la logique d'interface utilisateur associée est écrite.
En d'autres termes, les routes imbriquées nous permettent, au niveau de la route, de faire en sorte qu'un composant parent contrôle le rendu d'un composant enfant.

Le meilleur exemple ici est facebook.com/messages/<whatever_path>.
Si nous ouvrons facebook/messages et naviguons entre les messages, nous remarquerons que la première partie de l'URL (facebook.com/messages/t/) est toujours fixe, ce que nous appelons le chemin parent tandis que le reste de l'URL est appelé le chemin enfant.

La bibliothèque React Router V6 propose deux façons d'implémenter les routes imbriquées.
La première méthode consiste à utiliser le `<Route>`composant et `/*`dans le chemin.
Pour faciliter la compréhension, prenons un exemple.

```
import { Link, Route, Routes } from 'react-router-dom';
import './App.css';
// Component Home
const Home = () => (
 <>
   <h1>
     Home
   </h1>
 </>
)
// Component Profile
const Profile = () => (
 <>
   <h1>
     profile
   </h1>
 </>
)
// Component Account
const Account = () => (
 <>
   <h1>
     Account
   </h1>
 </>
)
// Component User
const User = () => {
 return (
   <div>
     <h1>User</h1>

     <nav>
       <Link to="profile">Profile</Link>
       <Link to="account">Account</Link>
     </nav>
     <Routes>
       <Route path="profile" element={<Profile />} />
       <Route path="account" element={<Account />} />
     </Routes>
   </div>
 );
};
const App = () => {
 return (
   <div className="App">
     <>
       <h1>React Router</h1>

       <nav>
         <Link to="/home">Home</Link>
         <Link to="/user">User</Link>
       </nav>

       <Routes>
         <Route index element={<Home />} />
         <Route path="home" element={<Home />} />
         {/* The `/*` means every route that is relative to the user must render the user component   */}
         <Route path="/user/*" element={<User />}>
         </Route>
       </Routes>
     </>
   </div>
 );
}

export default App;
```

# Routes imbriquées et dynamiques avec React Router

Dans cette vidéo, vous trouverez un aperçu de React Router et de la manière dont nous imbriquons les routes

<iframe allowfullscreen="true" frameborder="0" src="https://www.youtube.com/embed/lGjU0tBmP5M?list=PL-w_yrNy8uTaWNAYCFoyW0C0zPm4S9b3v"></iframe>

### Ces ressources peuvent vous aider

Routage imbriqué

[https://www.youtube.com/watch?v=PWi9V9d_Jsc](https://www.youtube.com/watch?v=PWi9V9d_Jsc)
