# Projet mini-games

## Consignes générales

L'application devra être ergonomique et intuitive.

La bibliothèque MatAngular devra être utilisée pour la mise en place des composants standards.

## Description fonctionnelle des pages

### Page de connexion

- La page de connexion est composé d'un champ 'login' ainsi que d'un champ 'mot de passe'.
- Les 2 champs sont obligatoires et tant qu'ils ne sont pas renseigné le bouton de validation du formulaire doit être non cliquable.
- Pour valider la connexion d'un utilisateur, le login et le mot de passe doivent être identiques.
- Si un utilisateur a déjà été identifié (mettre en place une mécanique de LocalStorage pour garder la session de l'utilisateur) alors on le redirigera directement sur la page d'accueil.

### Template des pages

- Sur toute les pages, on retrouvera une `navbar` qui sera composée d'un menu burger qui affichera la liste des jeux disponibles sur la plateforme (pour le moment seul le SUDOKU est cliquable le reste est désactivé)
- La `navbar` affichera aussi le pseudo du joueur connecté. Au clic sur le pseudo du joueur alors on est déconnecté.
- On retrouvera un lien vers la page d'accueil et un autre lien vers la page des classements.

### Page d'accueil

- La page d'accueil affichera en titre la date du jour
- On retrouvera la série du joueur courant sur les 7 derniers jours (un tick vert lorsque le joueur a joué, une croix rouge lorsque le joueur n'a pas réalisé de partie)
  - la série sera issue de la propriété `streaks` d'un user
  - si la propriété est vide on considère que le joueur n'a pas joué
  - sinon la propriété streak sera composée des 7 derniers jours

### Page classement

La page classement permettra à l'utilisateur de consulter le classement :
 - des joueurs en fonction de leur nombre de points
 - des joueurs en fonction du nombre de jour (série) qu'ils ont joué

Chaque classement devra être paginé.

### Page Sudoku

1. L'API permettant de récupérer une partie de Sudoku est accessible ici : https://sudoku-game-and-api.netlify.app/api/sudoku
2. Voici la description de la réponse reçu (ce qui n'est pas décrit ici n'est pas à exploiter) : 
 - le champ `data` contient la solution de la grille
 - le champ `easy` contient les positions de départ de la grille. Les 0 représentent des cases vides.
3. Vous devrez gérer les erreurs provenant de l'API.
   En cas d'indisponibilité de celle-ci, vous trouverez ci-dessous un exemple de partie par défaut :

```
{
  "data": [
  	[6,4,3,5,1,2,7,9,8],
  	[7,8,1,9,3,6,4,2,5],
  	[2,5,9,7,8,4,6,1,3],
  	[4,9,5,2,6,3,8,7,1],
  	[3,7,8,1,5,9,2,6,4],
  	[1,2,6,8,4,7,3,5,9],
  	[8,3,7,6,9,1,5,4,2],
  	[9,6,4,3,2,5,1,8,7],
  	[5,1,2,4,7,8,9,3,6]
  ],  
  "easy": [
  	[0,4,3,0,0,2,7,9,0],
  	[7,8,1,0,3,6,4,2,5],
  	[2,0,9,0,8,0,6,0,3],
  	[4,0,5,2,0,3,8,7,1],
  	[0,0,8,0,5,0,2,6,4],
  	[0,2,6,8,0,0,3,0,9],
  	[8,3,7,0,9,0,5,4,2],
  	[9,6,0,0,2,0,1,8,7],
  	[5,1,2,4,7,8,9,0,6]
  ],  
  "medium": [
  	[6,4,0,0,1,2,7,9,0],
  	[0,0,0,0,0,6,0,2,0],
  	[2,0,9,0,0,4,0,0,0],
  	[0,0,5,2,6,0,0,7,1],
  	[3,7,0,0,0,0,0,0,0],
  	[0,2,6,8,0,0,3,0,9],
  	[8,0,0,6,9,1,0,0,0],
  	[9,6,4,0,2,0,1,0,0],
  	[5,1,2,0,0,0,0,0,6]
  ],  
  "hard": [
  	[0,0,0,0,0,0,0,0,0],
  	[0,0,0,9,0,0,0,2,5],
  	[0,0,0,7,0,4,0,0,0],
  	[4,9,0,0,6,0,0,0,0],
  	[0,7,0,0,0,0,0,6,0],
  	[0,0,0,0,0,7,0,0,0],
  	[0,0,7,0,0,0,5,4,2],
  	[9,0,0,0,2,0,0,0,0],
  	[0,0,0,0,7,8,0,0,0]
  ]
}

```
   
4. Sur la page, un utilisateur aura la possibilité de : 
 - remplir le sudoku
 - effectuer une validation de sa grille (ce qui augmentera le nombre d'indices utilisés par le joueur). Le nombre d'indices sera affiché sous le bouton `Vérifier`
 - soumettre sa grille. A la soumission, un check sera effectué. En cas de check réussie, alors la grille sera validée avec 0 indice, sinon il n'y aura pas de soumission et le nombre d'indices sera incrémenté.
5. La validation d'une partie se fera sur l'URL suivante : https://664ba07f35bbda10987d9f99.mockapi.io/api/game et devra respecter la nomenclature suivante :
 - `date` : la date de la partie
 - `playerName` : le pseudo du joueur
 - `clues` : le nombre d'indices utilisés par le joueur

NB : A chaque appel, une nouvelle partie vous sera proposée. Afin de pouvoir tenter la même partie, vous pouvez sauvegarder la partie reçu dans le LocalStorage
NB : Chaque tableau du tableau de données représente une ligne dans la grille sudoku

## Bonus

1. Fournir un `.dockerfile` permettant de lancer l'application via Docker
2. Pouvoir rejouer la même partie sur une même journée
3. Pouvoir choisir la difficulté de la partie

## Ressources 

1. API pour récupérer les classements : https://664ba07f35bbda10987d9f99.mockapi.io/api/users
2. API pour récupérer le profil d'un utilisateur : https://664ba07f35bbda10987d9f99.mockapi.io/api/users/{user-id}
3. API pour récupérer une partie de Sudoku : https://sudoku-game-and-api.netlify.app/api/sudoku
3. Collection Postman avec toutes les routes APIs utilisées : https://www.postman.com/apside-clermont/iut/collection/4163533-68aa265a-23b3-484a-b900-f255c298b847/?action=share&creator=4163533

NB : le champ `streak` correspond au nombre de jours d'affilé où le joueur a fini.

NB : le champ `streaks` est un tableau composé des éléments suivants : 
- day : string qui correspond à l'initial du jour
- isPlayed : bool qui correspond au fait que le joueur est joué ou non

NB : une fois connecté, vous pouvez définir l'utilisateur connecté comme celui ayant l'ID 1.
