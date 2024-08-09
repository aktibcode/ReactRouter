# Chapitre : DEMO 1 - ROUTAGE DE BASE


# Démo 1 : routage de base

Nous avons couvert tout ce que vous devez savoir pour créer un routeur de base. Essayons d'en construire un :

### src/App.js

```
import {Routes, Route, Link } from "react-router-dom";
import "./styles.css";

/* Home component */
const Home = () => (
 <div>
   <h2>Home</h2>
 </div>
);

/* Category component */
const Category = () => (
 <div>
   <h2>Category</h2>
 </div>
);

/* Products component */
const Products = () => (
 <div>
   <h2>Products</h2>
 </div>
);

/* App component */
const App = () => {
 return (
   <>
     <div>
       <nav className="navbar navbar-light">
         <ul className="nav navbar-nav">
           {/*  Link components are used for linking to other views */}
           <li>
             {" "}
             <Link to="/">Homes</Link>
           </li>
           <li>
             <Link to="/category">Category</Link>
           </li>
           <li>
             <Link to="/products">Products</Link>
           </li>
         </ul>
       </nav>
       {/*  Route components are rendered if the path prop matches the current URL  */}
       <Routes>
         <Route path="/" element={<Home />} />
         <Route path="/category" element={<Category />} />
         <Route path="/products" element={<Products />} />
       </Routes>
     </div>
   </>
 );
};
export default App;
```

# Démo 1 : routage de base

Nous avons déclaré les composants pour Home, Category et Products dans App.js. Cela suffit pour l'instant, mais lorsque les composants commencent à grossir, il est préférable d'avoir un fichier séparé pour chaque composant. En règle générale, nous créons généralement un nouveau fichier pour un composant s'il occupe plus de 10 lignes de code. (À partir de la deuxième démo, nous créerons un fichier séparé pour les composants qui sont devenus trop gros pour tenir dans le fichier App.js).
À l'intérieur du composant App, nous avons écrit la logique de routage. Le chemin de `<Route>` correspond à l'emplacement actuel et un composant est rendu. Le composant qui doit être rendu est transmis en tant que `element`prop.
Ici, `/`correspond à la fois à `/`et à `/category`. Dans la version précédente de react-router-dom, nous devons passer un prop appelé `exact`pour éviter que les deux composants ne soient rendus.

```
<Route exact  path="/" … />
```

Dans la version **actuelle de ****react-router-dom (V6),** nous n'avons plus besoin de cela. Tous les chemins sont par défaut exacts.

Lien vers le premier projet

[Ouvrir le lien](https://codesandbox.io/s/sharp-torvalds-25bm9?file=/src/App.js)
