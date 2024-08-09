# Chapitre : ROUTES IMBRIQUEES AVEC SORTIE

# Routes imbriquées avec sortie

L'élément `<Outlet>` est utilisé comme espace réservé. Dans ce cas, un `<Outlet>` permet au composant Users de restituer ses itinéraires enfants. Ainsi, l'élément `<Outlet>` restituera soit un élément `<Profile>` soit un élément `<Account>` en fonction de l'emplacement actuel.
Voyons le même exemple que précédemment avec un point de vente :

```
import { Link, Outlet, Route, Routes } from 'react-router-dom';
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
     <div>
       {/*
       This outlet will serve as a placeholder
       until the nested component will be rendered
        */}
       <Outlet />
     </div>
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
         <Route path="user" element={<User />}>
           <Route path="profile" element={<Profile />} />
           <Route path="account" element={<Account />} />
         </Route>
       </Routes>
     </>
   </div>
 );
}

export default App;
```

### Ces ressources peuvent vous aider

Routage imbriqué

[https://www.youtube.com/watch?v=PWi9V9d_Jsc](https://www.youtube.com/watch?v=PWi9V9d_Jsc)
