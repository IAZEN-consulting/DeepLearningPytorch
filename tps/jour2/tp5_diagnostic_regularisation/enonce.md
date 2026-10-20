# TP5 : diagnostiquer, régulariser, choisir l'optimiseur

**Durée** : 45 min. **Module** : M6 (régularisation, batch normalization, diagnostic).

## Objectif

Repartir du pipeline du TP4, provoquer un surapprentissage avec un CNN volontairement sur-paramétré, le
diagnostiquer à partir des courbes, appliquer les remèdes un par un en mesurant l'effet de chacun sur
l'écart entre entraînement et validation, puis comparer les optimiseurs et un scheduler.

## Prérequis

- Démo 2 du jour 2 (dropout, batch norm, schedulers, clipping) et corrigé du TP4.
- Notebook : `tp5_diagnostic_regularisation.ipynb`, à ouvrir dans Google Colab avec un runtime GPU.

## Étapes

0. Exécuter les cellules fournies : le Dataset du TP4, l'entraînement réduit à 400 images, les fonctions
   d'entraînement, `fit` avec TensorBoard.
1. Lire `GrosCNN(batchnorm, dropout)` (fournie) et l'entraîner 20 époques, sans option ni augmentation.
2. Diagnostiquer : époque du minimum de la loss de validation, comportement ensuite.
3. Régulariser, un remède à la fois : dropout, puis batch norm, puis augmentation plus forte.
4. Comparer Adam, SGD avec momentum, AdamW, et AdamW avec un scheduler `CosineAnnealingLR`.
5. Faire le bilan.

## Critères de réussite

- Étape 1 : la sortie de `nouveau_cnn()` sur un paquet de 2 images a la forme `(2, 10)` (vérifié par un
  `assert`).
- Étape 2 : le diagnostic cite l'époque du minimum de la loss de validation et ce qui suit.
- Étapes 3 à 5 : l'écart d'accuracy est relevé après chaque remède et pour chaque optimiseur, et le bilan
  s'appuie sur ces valeurs.

## Données

CIFAR-10 (Krizhevsky, Nair et Hinton, 2009), fourni par torchvision : photos couleur de 32 x 32 pixels en
10 classes. Le site du jeu ne donne pas de licence ; il demande de citer le rapport *Learning Multiple
Layers of Features from Tiny Images* (Krizhevsky, 2009). Les TP utilisent les mêmes tirages : 5000 images
d'entraînement, 1000 de validation et 1000 de test. Ici, les images sont rangées dans `cifar10_fichiers/images/`, avec un fichier
CSV par partie.

## Bonus

- B1. Garder et recharger les poids de la meilleure époque.

## Corrigé

`tp5_diagnostic_regularisation_corrige.ipynb`, à ouvrir après avoir terminé.
