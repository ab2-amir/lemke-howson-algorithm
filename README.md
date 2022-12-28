# Rapport TP Théorie des jeux Algorithme Lemke-Howson<br>
## Introduction<br>
L'algorithme de Lemke-Howson pour les jeux à deux matrices fournit à la fois une
preuve élémentaire de l'existence de points d'équilibre et une méthode de calcul
efficace pour trouver au moins un point d'équilibre (Equilibre de NASH)<br>
## Implémentation de l’algorithme LEMKE-HOWSON<br>
## Pseudo Algorithme:<br>
Entrée : Un jeu bimatrix non-dégénéré (A, B).<br>
Sortie : Un équilibre de Nash du jeu.<br>
1. Choisir k ∈ P ∪ Q<br>
2. Commencer par (x, y) = ((0, 0), (0, 0)) / x ∈ P et y ∈ Q. Supprimer l'étiquette k de
(x, y))<br>
3. Soit (x, y) le sommet courant. Soit l l'étiquette ramassée en supprimant
l'étiquette k. Si l = k, on termine et (x, y) est un équilibre de Nash du jeu. Si l ≠ k,
supprimer l dans l'autre polytope et répétez cette étape.<br>
## Code et explication:<br>
## Fonction drop() :<br>
La fonction drop() permet de supprimer le label donnée en entrée et met à
jour l’état actuel (state)<br>

<picture>
 <source media="(prefers-color-scheme: dark)" srcset="https://github.com/ab2-amir/lemke-howson-algorithm/blob/main/screenshots/drop.png">
 <img alt="YOUR-ALT-TEXT" src="https://github.com/ab2-amir/lemke-howson-algorithm/blob/main/screenshots/drop.png">
</picture><br>

## Fonction pickup():<br>
La fonction pickup() permet de prendre un label qui est en commun entre les
deux polytopes P et Q de l’état actuel (state) et qui va être supprimer avec la
fonction drop() par la suite.<br>

<picture>
 <source media="(prefers-color-scheme: dark)" srcset="https://github.com/ab2-amir/lemke-howson-algorithm/blob/main/screenshots/pickup.png">
 <img alt="YOUR-ALT-TEXT" src="https://github.com/ab2-amir/lemke-howson-algorithm/blob/main/screenshots/pickup.png">
</picture><br>

## Fonction get_state_tuple():<br>
La fonction get_state_tuple() renvoie les labels associer à chaque sommet de
l’état actuel (state).<br>

<picture>
 <source media="(prefers-color-scheme: dark)" srcset="https://github.com/ab2-amir/lemke-howson-algorithm/blob/main/screenshots/get%20state.png">
 <img alt="YOUR-ALT-TEXT" src="https://github.com/ab2-amir/lemke-howson-algorithm/blob/main/screenshots/get%20state.png">
</picture><br>

## Fonction get_Enash():<br>
Après l’obtention des paire de sommets entièrement étiquetés on fait appel à
get_Enash() qui renvoie les coordonnées de ces sommets avec normalisation<br>

<picture>
 <source media="(prefers-color-scheme: dark)" srcset="https://github.com/ab2-amir/lemke-howson-algorithm/blob/main/screenshots/nash.png">
 <img alt="YOUR-ALT-TEXT" src="https://github.com/ab2-amir/lemke-howson-algorithm/blob/main/screenshots/nash.png">
</picture><br>

## Main du programme :<br>
On a A et B deux matrices de gains:<br>
A = (3 1 1 3)<br> B = (1 3 3 1)<br>
P et Q deux polytopes :<br>
P = {x ∈ 𝑅𝑚 / x ≥ 0, xB ≤ 1}<br>
Q = {y ∈ 𝑅𝑚 / y ≥ 0, Ay ≤ 1}<br>
Ce qui donne pour P:<br>
X1 ≥ 0<br>
X2 ≥ 0<br>
X1 + 3x2 ≤ 1<br>
3x1 + x2 ≤ 1<br>
=> V = {(0, 0), (0, 1/3), (1/3, 0), (1/4, 1/4)}<br>
On fait de même pour Q :<br>
=> V = {(0, 0), (1/3, 0), (0, 1/3), (1/4, 1/4)}<br>
On illustre tout ça avec le code suivant :<br>

<picture>
 <source media="(prefers-color-scheme: dark)" srcset="https://github.com/ab2-amir/lemke-howson-algorithm/blob/main/screenshots/polytopes.png">
 <img alt="YOUR-ALT-TEXT" src="https://github.com/ab2-amir/lemke-howson-algorithm/blob/main/screenshots/polytopes.png">
</picture><br>

<picture>
 <source media="(prefers-color-scheme: dark)" srcset="https://github.com/ab2-amir/lemke-howson-algorithm/blob/main/screenshots/p.png">
 <img alt="YOUR-ALT-TEXT" src="https://github.com/ab2-amir/lemke-howson-algorithm/blob/main/screenshots/p.png">
</picture><br>

<picture>
 <source media="(prefers-color-scheme: dark)" srcset="https://github.com/ab2-amir/lemke-howson-algorithm/blob/main/screenshots/q.png">
 <img alt="YOUR-ALT-TEXT" src="https://github.com/ab2-amir/lemke-howson-algorithm/blob/main/screenshots/q.png">
</picture><br>

<picture>
 <source media="(prefers-color-scheme: dark)" srcset="https://github.com/ab2-amir/lemke-howson-algorithm/blob/main/screenshots/main.png">
 <img alt="YOUR-ALT-TEXT" src="https://github.com/ab2-amir/lemke-howson-algorithm/blob/main/screenshots/main.png">
</picture><br>

## Output:<br>

<picture>
 <source media="(prefers-color-scheme: dark)" srcset="https://github.com/ab2-amir/lemke-howson-algorithm/blob/main/screenshots/output.png">
 <img alt="YOUR-ALT-TEXT" src="https://github.com/ab2-amir/lemke-howson-algorithm/blob/main/screenshots/output.png">
</picture><br>

## Vérification avec lemke_howson_enumiration() :<br>
C’est une fonction prédéfinie qui permet de calculé tous les équilibres de NASH
pour toutes les labels de départ possibles<br>

<picture>
 <source media="(prefers-color-scheme: dark)" srcset="https://github.com/ab2-amir/lemke-howson-algorithm/blob/main/screenshots/veref.png">
 <img alt="YOUR-ALT-TEXT" src="https://github.com/ab2-amir/lemke-howson-algorithm/blob/main/screenshots/veref.png">
</picture><br>

On constate que c’est les mêmes résultats obtenus précédemment.
