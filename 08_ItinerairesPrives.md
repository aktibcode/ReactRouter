# Chapitre : ITINERAIRES PRIVES


# Itinéraires protégés

Souvent, lors de la création d'une application Web, vous devez protéger certaines routes de votre application contre les utilisateurs qui ne disposent pas de l'authentification appropriée. Les routes protégées nous permettent de choisir les routes que les utilisateurs peuvent visiter en fonction de leur connexion. Par exemple, vous pouvez avoir des routes publiques auxquelles vous souhaitez que tout le monde puisse accéder, comme une page de destination, une page de tarification et la page de connexion. Les routes protégées ne doivent être disponibles que pour les utilisateurs connectés, comme un tableau de bord ou une page de paramètres.
Bien que React Router ne fournisse aucune fonctionnalité prête à l'emploi pour cela, car il a été conçu dans un souci de composabilité, son ajout est assez simple.

![](https://i.ytimg.com/vi/0x8Dap2EIVE/maxresdefault.jpg)

# Le composant PrivateRoute

Ici, nous définissons un composant générique nommé PrivateRoute qui vérifiera si l'utilisateur est authentifié pour accéder à la route privée ou il redirigera l'utilisateur vers la page de connexion.
Le composant PrivateRoute prendra deux props, le premier prop est les enfants (ou nous pouvons dire quel composant nous allons protéger), l'autre prop est isAuth qui identifie si l'utilisateur est authentifié ou non

```
import { Navigate } from "react-router-dom"

const PrivateRoute = ({ children, isAuth }) => {
   return (
       isAuth === true ? children : <Navigate to='/login' replace />
   )
}

export default PrivateRoute
```

# Le composant PrivateRoute

Créons maintenant le reste de notre application. Dans cet exemple, nous allons les implémenter dans le même fichier (mais vous devez implémenter chaque composant dans un fichier séparé)

```
import { Link, Route, Routes } from "react-router-dom";
import PrivateRoute from "./Components/PrivateRoute";

const Home = () => <h1>Home (Public)</h1>;
const Pricing = () => <h1>Pricing (Public)</h1>;
const Dashboard = () => <h1>Dashboard (Private)</h1>;
const Settings = () => <h1>Settings (Private)</h1>;

const Login = () => <h1>TODO</h1>

function Nav() {
 return (
   <nav>

     <Link to="/">Home</Link>
     {` `}
     <Link to="/pricing">Pricing</Link>

   </nav>
 );
}

export default function App() {
 return (
   <div>
     <Nav />

     <Routes>
       <Route path="/" element={<Home />} />
       <Route path="/pricing" element={<Pricing />} />
       <Route path="/dashboard" element={
         <PrivateRoute >
           <Dashboard />
         </PrivateRoute>
       } />
       <Route path="/settings" element={
         <PrivateRoute isAuth={false}>
           < Settings />
         </PrivateRoute>

       } />
       <Route path="/login" element={<Login />} />
     </Routes>
   </div>
 );
}
```

### Ces ressources peuvent vous aider

Itinéraires protégés

[https://ui.dev/react-router-protected-routes-authentication/](https://ui.dev/react-router-protected-routes-authentication/)
