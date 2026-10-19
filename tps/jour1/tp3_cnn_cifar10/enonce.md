# TP3 : un CNN pour classer les images CIFAR-10

**Durée** : 50 min. **Module** : M5 (réseaux convolutifs).

## Objectif

Classer les images CIFAR-10 du TP2 (10 classes) avec un réseau convolutif, et mesurer le gain par rapport
au MLP du TP2, sur les mêmes images.

## Prérequis

- Démos 6 (convolution, pooling, feature maps) et 7 (transforms, Dataset, DataLoader) du jour 1.
- Notebook : `tp3_cnn_cifar10.ipynb`, à ouvrir dans Google Colab avec un runtime GPU.

## Étapes

0. Exécuter la préparation et l'exploration fournies.
1. Écrire `train_tf` (miroir horizontal et décalage aléatoires, conversion), les trois `ImageFolder` et les
   trois DataLoader.
2. Écrire `CNNCifar` : trois blocs Conv2d + ReLU + MaxPool2d (16, 32, 64 canaux), puis le classifieur.
3. Entraîner 10 époques avec Adam (lr=1e-3), fonctions d'entraînement fournies.
4. Afficher les feature maps de la première couche pour une image d'avion et une image de chat.
5. Comparer le CNN au MLP du TP2 sur la même validation (cellules fournies).

## Critères de réussite

- Étape 1 : 10 classes, `class_to_idx["automobile"] == 0`, et un batch de forme `(32, 3, 32, 32)`.
- Étape 2 : la sortie du modèle sur un batch a la forme `(32, 10)`.
- Étape 3 : l'accuracy de validation dépasse 35 %.

Ces critères sont vérifiés par des `assert` dans le notebook.

## Données

CIFAR-10 (Krizhevsky, Nair et Hinton, 2009), fourni par torchvision : photos couleur de 32 x 32 pixels en
10 classes. Le site du jeu ne donne pas de licence ; il demande de citer le rapport *Learning Multiple
Layers of Features from Tiny Images* (Krizhevsky, 2009). Les TP utilisent les mêmes tirages : 5000 images
d'entraînement, 1000 de validation et 1000 de test.

## Bonus

- B1. Matrice de confusion du CNN sur la validation.
- B2. Même entraînement sans augmentation.

## Corrigé

`tp3_cnn_cifar10_corrige.ipynb`, à ouvrir après avoir terminé.
