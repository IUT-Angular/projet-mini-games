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

### Page d'accueil

### Page classement

La page classement permettra à l'utilisateur de consulter le classement :
 - des joueurs en fonction de leur nombre de points
 - des joueurs en fonction du nombre de jour (série) qu'ils ont joué

Chaque classement devra être paginé.

### Page Sudoku

## Bonus

1. Fournir un `.dockerfile` permettant de lancer l'application via Docker

## Ressources 

1. API pour récupérer les classements : https://664ba07f35bbda10987d9f99.mockapi.io/api/users
2. API pour récupérer le profil d'un utilisateur : https://664ba07f35bbda10987d9f99.mockapi.io/api/users/{user-id}
3. Collection Postman avec toutes les routes APIs utilisées : https://www.postman.com/apside-clermont/iut/collection/4163533-68aa265a-23b3-484a-b900-f255c298b847/?action=share&creator=4163533

NB : le champ `streak` correspond au nombre de jours d'affilé où le joueur a fini.