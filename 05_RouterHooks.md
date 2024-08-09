# Chapitre : ROUTER HOOKS

## Router hooks

La bibliothèque React Router exploite la puissance des hooks depuis la cinquième version et introduit quatre hooks différents pour aider notre routage.

* utiliserNavigate()
* utiliserLocation()
* utiliserParams()
* utiliserRouteMatch()

Nous allons explorer chacun de ces crochets dans les prochaines diapositives

# useNavigate() et useLocation()

* useNavigate est un hook qui renvoie une fonction nous permettant de changer l'url quand nous le souhaitons. Il donne le même résultat que le lien mais la fonction browse peut être utilisée à l'intérieur d'une autre fonction.

Voyons l'exemple ci-dessous, où la page de profil naviguera vers la page d'accueil pendant 5 secondes

```

import { useEffect, useState } from 'react';
import { Route, Routes, useNavigate } from 'react-router-dom';
import './App.css';

const Home = () => {
 const navigate = useNavigate();
 return (
   <div>
     <h1>
       Home page
     </h1>
     {/*
     When we click this button the navigate function will change the url to
     `/profile` and render the profile component
      */}
     <button onClick={() => navigate('/profile')}>Navigate to Profile </button>
   </div>
 )
}
const Profile = () => {
 const navigate = useNavigate();
 const [timer, setTimer] = useState(0)
 useEffect(() => {
   setInterval(() => {
     setTimer(timer + 1)
   }, 1000);
 })
 /*
 After the 5 second the function navigate will change the url into `/`
 and the home page will be rendered
 */
 useEffect(() => {
   setTimeout(() => {
     navigate('/')
   }, 5000);
 }, [])
 return (
   <div>
     <h1>Profile Page</h1>
     <p>
       Count down: <span>{timer}</span>
     </p>
   </div>
 )
}
function App() {
 return (
   <div className="App">
     <Routes>
       <Route path='/' element={<Home />}></Route>
       <Route index path='/profile' element={<Profile />}></Route>
     </Routes>
   </div>
 );
}

export default App;
```

* useLocation : Ce hook renvoie l'objet de localisation utilisé par le routeur react. Cet objet représente l'URL actuelle et est immuable. Chaque fois que l'URL change, le hook useLocation() renvoie un objet de localisation nouvellement mis à jour. Certaines de ses utilisations incluent l'extraction des paramètres de requête de l'URL

Dans l'exemple ci-dessous, nous créons une nouvelle route `about`où l'élément à restituer est la page À propos

```
import { useEffect } from 'react'
import { useLocation } from 'react-router-dom'
const About = () => {
   const location = useLocation()
   useEffect(() => {
       console.log("🚀 ~ file: About.js ~ line 5 ~ About ~ history", location)

   }, [])
   return (
       <div>
           <h1>
               About Page
           </h1>
       </div>
   )
}

export default About
```

La sortie de la fonction useEffect est l'image ci-dessous :

![](https://i.imgur.com/a3kH6Ok.png)

# useParams() et useMatchRoute()

* useParams() : ce hook renvoie un objet composé de tous les paramètres de l'URL.

Dans l'exemple ci-dessous, nous naviguons jusqu'à `/profile/admin`l'endroit où admin est l'identifiant de l'utilisateur

```
import { useEffect } from 'react';
import { Route, Routes, useNavigate, useParams } from 'react-router-dom';
import './App.css';

const Home = () => {
 const navigate = useNavigate();
 return (
   <div>
     <h1>
       Home page
     </h1>
     <button onClick={() => navigate('/profile/John')}>Navigate to Profile </button>
   </div>
 )
}
const Profile = () => {
 const params = useParams();
 useEffect(() => {
   console.log("🚀 ~ file: App.js ~ line 23 ~ Profile ~ params", params)

 })
 return (
   <div>
     <h1>Profile Page</h1>
     <p>
       this page is for {params.name}
     </p>
   </div>
 )
}
function App() {
 return (
   <div className="App">
     <Routes>
       <Route path='/' element={<Home />}></Route>
       {/* Here the parameter is the url is called `name`
       so the param that will be injected in useParams hook will be `name`  */}
       <Route index path='/profile/:name' element={<Profile />}></Route>
     </Routes>
   </div>
 );
}

export default App;
```

Le résultat `console.log`sera le suivant :

![](https://i.imgur.com/dLB2S1Z.png)

* useMatchRoute : renvoie des données de correspondance sur un itinéraire au chemin donné par rapport à l'emplacement actuel.

Prenons un exemple pour que ce soit plus clair.

```
import { useEffect } from 'react';
import { Route, Routes, useMatch, useNavigate } from 'react-router-dom';
import './App.css';

const Home = () => {
 const navigate = useNavigate();
 return (
   <div>
     <h1>
       Home page
     </h1>
     <button onClick={() => navigate('/profile/John')}>Navigate to Profile </button>
   </div>
 )
}
const Profile = () => {
 const match = useMatch('/profile/:name');
 useEffect(() => {
   console.log("🚀 ~ file: App.js ~ line 23 ~ Profile ~ params", match)

 })
 return (
   <div>
     <h1>Profile Page</h1>
     <p>
       this page is for {match.params.name}
     </p>
   </div>
 )
}
function App() {
 return (
   <div className="App">
     <Routes>
       <Route path='/' element={<Home />}></Route>
       <Route index path='/profile/:name' element={<Profile />}></Route>
     </Routes>
   </div>
 );
}

export default App;
```

Le résultat `console.log`sera le suivant :

![](https://i.imgur.com/iPq90vp.png)
