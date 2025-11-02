# Serie1_Ouerghemmi_Marwen
Getting Started_1


Exercice 1 : Classement vecteurs de l'espace réciproque : Traitement et tri des vecteurs réciproques d'un réseau de Bravais cubique

1. Objectif
Ce programme permet de :
- Charger un fichier de vecteurs réciproques (Nx3) 
- Trier les vecteurs selon leur norme (distance à l'origine) avec insertion sort et bubble sort.
- Comparer les performances des algorithmes pour différentes tailles.
- Comparer le tri sur numpy arrays et sur listes Python.
- Visualiser les normes triées et sélectionner les vecteurs proches de l'origine.

2. Fichiers
- input_k_vectors.dat : fichier de vecteurs (x, y, z) 
   Si le fichier n'existe pas, il sera généré automatiquement ( pour éviter un problème ) 
- main.py : script principal contenant le code.


3. Fonctionnalités principales

- create_sample_data(filepath, n) : crée un fichier .dat de vecteurs aléatoires.
- load_data(filename) : charge les vecteurs depuis le fichier.
- insertion_ranking(data) : tri par insertion selon la norme.
- bubble_ranking(data) : tri à bulles selon la norme.
- compare_algorithms(data) : compare le temps d'exécution des deux algorithmes.
- compare_with_lists(data) : compare numpy arrays vs listes Python.
- plot_norms(data) : trace les normes triées et sélectionne les vecteurs avec |k| < R.

4. Résultats attendus ( voir les résultats lors de la compilation) 
Mes remarques : 
- L'insertion sort est généralement plus rapide que le bubble sort pour de grandes tailles.
- Les numpy arrays sont plus performants que les listes Python.
- Le tri permet de sélectionner facilement les vecteurs avec |k| < R tout en conservant la symétrie du réseau.
- Les graphiques montrent la croissance des normes et les performances des algorithmes.

5. 
Performance :
Les numpy arrays sont optimisés pour les calculs numériques avec des opérations vectorisées, tandis que les listes Python sont plus lentes pour de grandes données.

Observation :
Les tris insertion_ranking et bubble_ranking prennent plus de temps sur des listes Python que sur des numpy arrays, surtout pour des tailles supérieures à 1000 vecteurs.

Conclusion :
Les numpy arrays sont préférables pour traiter et trier de grands ensembles de vecteurs, tandis que les listes Python restent fonctionnelles mais moins efficaces.


6. Normes et sélection des vecteurs

Le tri des vecteurs montre des normes croissantes, ce qui permet de sélectionner facilement ceux avec |k| < R. La symétrie du réseau est conservée car on ne filtre que par distance.




Exercice 2 : Instabilité des fonctions de Bessel : 
: Étude numérique des fonctions de Bessel et stabilité des récurrences

1. Objectif

Notre exercice  vise à calculer les fonctions de Bessel Jn(x) et Yn(x) pour x=1 et n=0..20
en utilisant des récurrences vers le haut et vers le bas, comparer les erreurs
avec les valeurs exactes de scipy.special, et corriger les instabilités avec l'algorithme de Miller.

2. Fonctions principales

- rec_up(f0, f1, x, nmax) : récurrence vers le haut, initialisée avec f0=f(0), f1=f(1)
- rec_down(fNplus1, fN, x, nmax) : récurrence vers le bas, initialisée avec fN+1, fN
- miller_J(x, nmax, Nstart) : algorithme de Miller pour calculer Jn(x) stable vers le bas
- rel_error(calc, ref) : calcule l'erreur relative entre valeurs calculées et référence
- Utilisation de jv et yv (scipy.special) pour valeurs exactes de Jn et Yn

3. Étapes et résultats

1. Les fonctions rec_up et rec_down permettent de calculer Jn et Yn selon la récurrence 
   dans les deux sens.
2. Avec scipy.special, on calcule Jα(1) et Yα(1) pour α = 1..20 et on compare aux 
   récurrences.
3. L'erreur relative montre :
   - Pour Jn(x), la récurrence vers le haut est stable.
   - Pour Yn(x), la récurrence vers le bas est plus stable.
   - L’autre sens amplifie les erreurs numériques.
4. L’algorithme de Miller corrige l’instabilité de la récurrence vers le bas pour Jn,
   en descendant depuis un ordre élevé Nstart avec renormalisation périodique.
   Après renormalisation sur J0(x), les erreurs sont très faibles, garantissant
   stabilité et précision.

4. Instructions

1. Exécuter le script Python principal.
2. Observer les graphiques des erreurs relatives pour Jn et Yn.
3. Comparer les méthodes :
   - rec_up : stable pour Jn
   - rec_down : stable pour Yn
   - Miller : stable pour Jn dans le sens descendant

5. Conclusion
 La récurrence simple peut devenir instable selon la direction et le type de Bessel.
- L’algorithme de Miller est une méthode robuste pour corriger cette instabilité.
- Les graphiques permettent de visualiser directement l’amplification des erreurs et
  l’efficacité de la correction.

Références :
- scipy.special: jv, yv
- Numerical Recipes, chapitres 5 et 6



Exercice 3 : Représentation Graphique et Régression : 
Analyse de la position d'une mouche en fonction du temps

1. Objectif
Cet exercice  a pour but de :
- Charger les données expérimentales depuis un fichier HDF5 (data_ex3.h5).
- Effectuer une régression linéaire par la méthode des moindres carrés.
- Estimer la vitesse et la position initiale de la mouche.
- Visualiser les données et les erreurs résiduelles.

2. Fichiers

- data/data_ex3.h5 : fichier HDF5 contenant deux datasets 'x' (temps) et 'y' (position).
- main.py : script Python principal pour le traitement et l'affichage.


3. Fonctions principales
- my_lin_reg(x, y) :
    - Entrée : x et y (numpy array ou listes Python, ou tableau Nx2).
    - Calcule les coefficients a et b de la droite y = a*x + b.
    - Retourne également les erreurs résiduelles (y - (a*x+b)).

4. Étapes de traitement

a. Charger les données 'x' et 'y' depuis data_ex3.h5.
b. Appliquer la fonction my_lin_reg pour calculer a (vitesse) et b (position initiale).
c. Calculer l'erreur quadratique moyenne (RMSE) pour quantifier la précision de la régression.
d. Tracer deux sous-graphes :
   - Position vs temps avec la droite de régression.
   - Erreurs résiduelles en fonction du temps.

5. Résultats
- Coefficients estimés : a ≈ [valeur calculée] m/s, b ≈ [valeur calculée] m.
- RMSE faible indiquant une bonne approximation linéaire.
- Les erreurs résiduelles sont centrées autour de 0, sans tendance particulière.

6. Instructions  Importantes 
a- il faut placer le fichier data_ex3.h5 dans le dossier 'data'.
2. Exécuter le script Python principal.
3. Observer les graphiques générés :
   - Subplot 1 : Données expérimentales et droite de régression.
   - Subplot 2 : Courbe des erreurs résiduelles.
4. Ajuster les données si nécessaire pour d'autres expériences.

Références utilisés lors de mon travail 

- Numpy pour les calculs numériques.
- Matplotlib pour la visualisation graphique.
- H5py pour la lecture des fichiers HDF5.
"""










