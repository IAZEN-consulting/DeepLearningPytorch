# TP2 : un réseau pour classer les images CIFAR-10

**Durée** : 55 min. **Modules** : M3 (nn.Module) et M4 (entraînement, losses, optimiseurs).

## Objectif

Classer des photos CIFAR-10 en 10 classes avec un réseau de neurones qui lit les pixels de l'image. Écrire
trois réseaux, les entraîner, et choisir le meilleur à partir des courbes et d'une référence simple.

## Prérequis

- Démo 4 (`nn.Module`, `nn.Sequential`) et démo 5 (DataLoader, boucle, validation, test).
- Notebook : `tp2_mlp_cifar10.ipynb`, à ouvrir dans Google Colab (runtime GPU conseillé).

## Étapes

0. Exécuter la préparation et l'exploration fournies ; répondre aux questions.
1. Calculer la référence : l'accuracy d'un modèle qui répond toujours la classe la plus fréquente.
2. Compléter la classe `Baseline` (une couche cachée de 128 neurones) et l'entraîner.
3. Écrire un réseau à deux couches cachées avec `BatchNorm1d`.
4. Écrire un réseau à trois couches cachées avec `Dropout`.
5. Comparer les courbes (cellules fournies) et choisir un réseau.
6. Mesurer le réseau choisi, une seule fois, sur le jeu de test.

## Critères de réussite

- Étape 2 : la baseline dépasse 25 % d'accuracy en validation (vérifié par un `assert`).
- Étape 5 : le choix est justifié par l'écart entre entraînement et validation, et par la référence.
- Étape 6 : le jeu de test n'est utilisé qu'une fois, après le choix.

## Données

CIFAR-10 (Krizhevsky, Nair et Hinton, 2009), fourni par torchvision : photos couleur de 32 x 32 pixels en
10 classes. Le site du jeu ne donne pas de licence ; il demande de citer le rapport *Learning Multiple
Layers of Features from Tiny Images* (Krizhevsky, 2009). Les TP utilisent les mêmes tirages : 5000 images
d'entraînement, 1000 de validation et 1000 de test.

## Bonus

- B1. Compter les paramètres de chaque réseau.
- B2. Entraîner la baseline 50 époques et observer l'erreur de validation.

## Corrigé

`tp2_mlp_cifar10_corrige.ipynb`, à ouvrir après avoir terminé.
