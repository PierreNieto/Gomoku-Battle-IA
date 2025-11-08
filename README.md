# Gomoku-Battle-IA
Gomoku Battle IA

Créer un jeu de type Gomoku où un joueur humain affronte une IA. L'IA utilise un algorithme
Minimax et un élagage Alpha-Bêta pour choisir ses coups.
Représentation et affichage de l'état du jeu (fonction afficher_planche)
• On a modélisée la grille par un dictionnaire pour économiser de la mémoire en stockant
uniquement les cases jouées.
• On afficher les cases vides avec des « . » les coups du joueur humain par « X » et ceux de
l'IA par « O ».
• On stock chaque coup joué dans un dictionnaire avec un tuple avec les coordonnées, et
1 ou 0 e fonction du joueur qui a joué (fonction jouer)
Minimax (fonction minmax)
L'algorithme explore toutes les possibilités jusqu'à une profondeur définie pour déterminer le
meilleur coup.
Choix des paramètres :
Profondeur = 3 :
Ce choix équilibre précision et performances. Une profondeur trop élevée augmenterait
considérablement le temps de calcul.
Une profondeur de 3 permet à l’IA d’anticiper à court terme tout en restant réactive pour
rpéondre en moins de cinq secondes
Évaluation des états :
Les alignements (lignes, colonnes, diagonales) sont évalués selon leur longueur : un alignement
de 3 pions a un poids plus élevé qu’un alignement de 2 pions, car il est plus menaçant.
Les alignements adverses sont pénalisés.
Alpha-Bêta (fonction alphabeta)
Amélioration de Minimax pour réduire le nombre de coups explorés :
Rôle d’Alpha-Bêta :
Alpha stocke la meilleure valeur trouvée pour le joueur maximisant.
Beta stocke la meilleure valeur pour le joueur minimisant.
Si une branche ne peut pas améliorer le score final (beta ≤ alpha), elle est abandonnée,
économisant ainsi du temps de calcul.
Impact sur les performance :
Réduit la complexité, permettant à l'IA de chercher plus loin en moins de temps.
Sans Alpha-Bêta, la profondeur aurait dû être réduite à 2 pour éviter des temps d’attente trop
longs. Avec cette optimisation, maintenir une profondeur de 3 permet de prévoir des coups à
court terme tout en gardant un temps en dessous de conq secondes
Verification victoire
Avec la fonction gagner, on parcourt les positions occupées par le joueur et on vérifie, pour
chaque direction, si cinq pions consécutifs appartiennent au même joueur. Cette méthode nous
permet de couvrir efficacement toutes les configurations gagnantes possibles sur la grille.
Voisins libres (fonction voisins_libre)
L’IA restreint l’exploration aux cases adjacentes aux pions déjà joués, car ces coups sont les
plus stratégiquement pertinents pour créer ou bloquer des alignements.
Cette limitation réduit drastiquement le nombre de coups évalués par Minimax et Alpha-Bêta en
ignorant les cases éloignées, qui ont peu d’impact sur l’état du jeu actuel.
Par exemple, sur une grille de 15x15, au lieu d’examiner potentiellement 225 positions, l’IA n’en
considère qu’une fraction (les cases autour des pions actifs), ce qui rend les calculs beaucoup
plus rapides tout en conservant une analyse pertinente.
Règles premier et deuxième tour
Nous avons ajouté deux fonctions premiertour, et secondtour pour appliquer les règles du
Gomoku, elles seront appelées plus tard dans la fonction main avec un compteur de tour pour
qu’elles s’appliquent au premier et au deuxième tour du joueur qui commence.
Conclusion
Nous avons conçu une IA capable de jouer au Gomoku en utilisant les algorithmes Minimax et
Alpha-Bêta pour prendre des décisions stratégiques. On a choisi une profondeur de 3 pour
équilibrer performance et rapidité. L’ajout des voisins libres nous a permis de concentrer les
calculs sur les coups les plus pertinents, améliorant ainsi l’efficacité globale.

