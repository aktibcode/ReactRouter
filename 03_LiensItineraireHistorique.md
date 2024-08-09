# Chapitre : LIENS ET ITINERAIRES HISTORIQUES


# History

**history ***est une bibliothèque JavaScript qui vous permet de gérer facilement l'historique des sessions dans n'importe quel environnement JavaScript. History fournit une API minimale qui vous permet de gérer la pile d'historique, de naviguer, de confirmer la navigation et de conserver l'état entre les sessions. — [Documentation de formation React](https://github.com/ReactTraining/history)*

Chaque composant de routeur crée un objet d'historique qui conserve la trace des emplacements actuels ( `history.location`) et des emplacements précédents dans une pile. Lorsque l'emplacement actuel change, la vue est réaffichée et vous obtenez une idée de la navigation et de l'interaction. Comment l'emplacement actuel change-t-il ? L'objet d'historique dispose de méthodes telles que `history.push()`et `history.replace()`pour s'en occuper. `history.push()`est invoqué lorsque vous cliquez sur un `<Link>`composant et `history.replace()`est appelé lorsque vous utilisez `<Redirect>`. D'autres méthodes, telles que `history.goBack()`et `history.goForward()`, sont utilisées pour naviguer dans la pile d'historique en revenant en arrière ou en avant d'une page.

# Links et Routes

• Le `<Route>`composant est le composant le plus important dans React router. Il restitue une partie de l'interface utilisateur si l'emplacement actuel correspond au chemin de la route. Idéalement, un `<Route>`composant doit avoir un prop nommé `path`et si le nom du chemin correspond à l'emplacement actuel, il est restitué.

• Le `<Link>`composant, quant à lui, est utilisé pour naviguer entre les pages. Il est comparable à l'élément d'ancrage HTML. Cependant, l'utilisation de liens d'ancrage entraînerait une actualisation du navigateur, ce que nous ne voulons pas. Nous pouvons donc l'utiliser `<Link>`pour naviguer vers une URL particulière et faire en sorte que la vue soit réaffichée sans actualisation du navigateur.

History

[Ouvrir le lien](https://reactrouter.com/web/api/history)

Route

[Open link](https://reactrouter.com/web/api/Route)
