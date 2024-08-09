# Chapitre : NOTIONS DE BASE SUR LE REACT ROUTER


# Notions de base sur le routeur React

Voici un exemple de ce à quoi ressembleront nos itinéraires :

```
<Routes>
         <Route path="/" element={<Home />} />
         <Route path="/category" element={<Category />} />
         <Route path="/login" element={<Login />} />
         <Route path="/products" element={<Products />} />
</Routes>
```

# Routeur

Vous avez besoin d'un composant **routeur** et de plusieurs composants **route** pour configurer une route de base comme illustré dans l'écran précédent. Étant donné que nous créons une application basée sur un navigateur, nous pouvons utiliser deux types de routeurs de l'API React Router :

1. `<BrowserRouter>`
2. `<HashRouter>`

La principale différence entre eux est évidente dans les URL qu’ils créent :

```
// <BrowserRouter>
http://example.com/about

// <HashRouter>
http://example.com/#/about
```

# Routeur

Le `<BrowserRouter>`est le plus populaire des deux car il utilise l'API d'historique HTML5 pour suivre l'historique de votre routeur. Le `<HashRouter>`, d'autre part, utilise la partie hachage de l'URL ( `window.location.hash`) pour mémoriser des éléments. Si vous avez l'intention de prendre en charge les anciens navigateurs, vous devriez vous en tenir à `<HashRouter>`.

Enveloppez le `<BrowserRouter>`composant autour du composant App.

Dans **index.js** :

```
/* Import statements */
import React from 'react';
import ReactDOM from 'react-dom';

/* App is the entry point to the React code.*/
import App from './App';

/* import BrowserRouter from 'react-router-dom' */
import { BrowserRouter } from 'react-router-dom';

ReactDOM.render(
    <BrowserRouter>
        <App />
    </BrowserRouter>
    , document.getElementById('root'));
```

*Remarque : un composant routeur ne peut avoir qu'un seul élément enfant. L'élément enfant peut être un élément HTML (par exemple div) ou un composant React.*

Pour que React Router fonctionne, vous devez importer l'API appropriée depuis la `react-router-dom`bibliothèque. Ici, nous avons importé le `BrowserRouter`into `index.js`. Nous avons également importé le `App`composant from `App.js`. `App.js`, comme vous l'avez peut-être deviné, est le point d'entrée des composants React.
Le code ci-dessus crée une instance d'historique pour l'ensemble de notre composant App.

Nous allons maintenant vous présenter officiellement l’histoire.



### NavigateurRouteur

[Ouvrir le lien](https://reactrouter.com/web/api/BrowserRouter)

### Routeur de hachage

[Ouvrir le lien](https://reactrouter.com/web/api/HashRouter)
