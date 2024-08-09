# Chapitre : ROUTEUR REACT - PRESENTATION


# Introduction

[React Router](https://github.com/ReactTraining/react-router) est la bibliothèque de routage standard de React. Lorsque vous devez naviguer dans une application React avec plusieurs vues, vous aurez besoin d'un routeur pour gérer les URL. React Router fait cela tout en gardant l'interface utilisateur et l'URL de votre application synchronisées.

L'une des principales caractéristiques de React est qu'il permet la création d'applications monopages ( **SPA** ) qui sont rendues côté client. Une SPA peut avoir plusieurs **vues** (alias **pages** ) et, contrairement aux applications multipages classiques, la navigation dans ces vues ne doit pas entraîner le rechargement de la page entière. Au lieu de cela, nous voulons que les vues soient rendues en ligne dans la page actuelle. L'utilisateur final, habitué aux applications multipages, s'attend à ce que les fonctionnalités suivantes soient présentes dans une SPA :

* Chaque vue d'une application doit avoir une URL qui spécifie de manière unique cette vue. Cela permet à l'utilisateur de mettre l'URL en signet pour s'y référer ultérieurement, par exemple www.exemple.com/produits.
* Les boutons Précédent et Suivant du navigateur devraient fonctionner comme prévu.
* Les vues imbriquées générées dynamiquement doivent de préférence avoir leur propre URL également, par exemple www.exemple.com/products/shoes/101, où 101 est l'ID du produit.

# Introduction

**Le routage** est le processus qui consiste à synchroniser l'URL du navigateur avec ce qui est affiché sur la page. React Router vous permet de gérer le routage **de manière déclarative** . L'approche de routage déclaratif vous permet de contrôler le flux de données dans votre application, en disant « l'itinéraire doit ressembler à ceci » :

```
<Route path="/about" element={<About/>}/>
```

Vous pouvez placer votre `<Route>`composant à l'endroit où vous souhaitez que votre itinéraire soit rendu. Étant donné que `<Route>`React `<Link>`Router et toutes les autres API React Router que nous traiterons ne sont que des composants, vous pouvez facilement vous habituer au routage dans React.
Une remarque avant de commencer. Il existe une idée fausse courante selon laquelle React Router est une solution de routage officielle développée par Facebook. En réalité, il s'agit d'une bibliothèque tierce très appréciée pour sa conception et sa simplicité. Si vos besoins se limitent aux routeurs pour la navigation, vous pouvez implémenter un routeur personnalisé à partir de zéro sans aucun problème. Cependant, comprendre les bases de React Router vous donnera une meilleure idée du fonctionnement d'un routeur.

# Aperçu

![](https://daqxzxzy8xq3u.cloudfront.net/wp-content/uploads/2019/04/30123219/react-router-dom-feature-img.jpg)

Dans cette Super Skill, nous aborderons quatre sujets principaux. Tout d'abord, nous allons configurer React et React Router à l'aide de npm. Ensuite, nous passerons directement aux bases de React Router. Vous trouverez différentes démonstrations de code de React Router en action. Les exemples abordés incluent :

* Routage de navigation de base.
* Routage imbriqué.
* Routage imbriqué avec paramètres de chemin.
* Routage protégé.

Commençons!

# Configuration de React Router

Supposons que vous disposez déjà d'un environnement de développement opérationnel dans lequel vous avez utilisé Create React App pour générer les fichiers nécessaires à la création d'un projet React de base. La structure de répertoire par défaut générée par Create React App devrait ressembler à ceci :

```
react-routing-super-skill
├── README.md
├── node_modules
├── package.json
├── .gitignore
├── public
│   ├── favicon.ico
│   ├── index.html
│   ├── logo192.png
│   ├── logo512.png
│   ├── manifest.json
│   └── robots.txt
└── src
    ├── App.css
    ├── App.js
    ├── App.test.js
    ├── index.css
    ├── index.js
    ├── logo.svg
    └── serviceWorker.js
```

La bibliothèque React Router comprend trois packages : `react-router`, `react-router-dom`, et `react-router-native`. `react-router`est le package principal du routeur, tandis que les deux autres sont spécifiques à l'environnement. Vous devez l'utiliser `react-router-dom`si vous créez un site Web et `react-router-native`si vous utilisez un environnement de développement d'applications mobiles utilisant React Native.

Utilisons npm pour installer `react-router-dom`:

```
npm install --save react-router-dom
```

### Qu'est-ce que react-router-dom ?

[Ouvrir le lien](https://blog.logrocket.com/react-router-dom-set-up-essential-components-parameterized-routes-505dc93642f1/)

### React-routeur-dom

[Ouvrir le lien](https://www.npmjs.com/package/react-router-dom)
