# TP4 : Dataset, DataLoader et entraînement d'un CNN

**Durée** : 50 min. **Module** : préparer ses données (Dataset et DataLoader), jour 2.

## Objectif

Partir des photos CIFAR-10 rangées en fichiers PNG, avec leurs classes dans un fichier CSV, écrire votre
propre Dataset, le servir par minibatchs avec des DataLoader, puis définir un CNN et l'entraîner. Ce
pipeline sert de point de départ au TP5.

## Prérequis

- Démo 1 du jour 2 (Dataset et DataLoader) ; corrigé du TP3 (le même CNN).
- Notebook : `tp4_dataset_entrainement.ipynb`, à ouvrir dans Google Colab avec un runtime GPU.

## Étapes

0. Exécuter la préparation et l'exploration fournies, puis répondre aux questions.
1. Compléter `ImagesCifar` : `__len__`, et la lecture de l'image dans `__getitem__`.
2. Créer les trois DataLoader.
3. Compléter `CNNCifar` : le troisième bloc, le classifieur et `forward`.
4. Entraîner 10 époques avec Adam (lr=1e-3), fonctions d'entraînement fournies ; les courbes sont écrites
   pour TensorBoard.
5. Lire les courbes d'entraînement et de validation dans TensorBoard (cellule fournie).
6. Mesurer le modèle une seule fois sur le jeu de test.

## Critères de réussite

- Étape 1 : 5000 exemples d'entraînement, et une image de forme `(3, 32, 32)`.
- Étape 2 : un paquet d'images de forme `(64, 3, 32, 32)`.
- Étape 3 : la sortie du modèle sur un paquet a la forme `(64, 10)`.
- Étape 4 : l'accuracy de validation dépasse 35 %.

Ces critères sont vérifiés par des `assert` dans le notebook.

## Données

CIFAR-10 (Krizhevsky, Nair et Hinton, 2009), fourni par torchvision : photos couleur de 32 x 32 pixels en
10 classes. Le site du jeu ne donne pas de licence ; il demande de citer le rapport *Learning Multiple
Layers of Features from Tiny Images* (Krizhevsky, 2009). Les TP utilisent les mêmes tirages : 5000 images
d'entraînement, 1000 de validation et 1000 de test. Ici, les images sont rangées dans `cifar10_fichiers/images/`, avec un fichier
CSV par partie.

## Bonus

- B1. Comparer le temps de lecture d'une époque avec `num_workers=0` et `num_workers=2`.
- B2. Compter les paquets d'une époque avec et sans `drop_last=True`.

## Corrigé

`tp4_dataset_entrainement_corrige.ipynb`, à ouvrir après avoir terminé.
