# TP6 : fine-tuning de ResNet50 et comparaison MLP / CNN / ResNet

**Durée** : 60 min. **Module** : M7 (transfer learning et fine-tuning).

## Objectif

Améliorer la classification des images CIFAR-10 avec un ResNet50 pré-entraîné sur ImageNet, en deux phases
(tête seule, puis dégel des deux derniers blocs avec un learning rate différentiel), comparer les trois
modèles du parcours (MLP, CNN, ResNet) sur le même jeu de test, et sauvegarder le meilleur avec ses
métadonnées.

## Prérequis

- Démo 3 du jour 2 (feature extraction, fine-tuning, learning rate différentiel) ; corrigés des TP2 et TP3.
- Notebook : `tp6_fine_tuning.ipynb`, à ouvrir dans Google Colab avec un runtime GPU (indispensable).

## Étapes

0. Exécuter les cellules fournies : données agrandies en 224 x 224 pour le ResNet, DataLoader, fonctions
   d'entraînement.
1. Phase 1 : `resnet50` pré-entraîné, backbone gelé, `fc` à 10 sorties, 5 époques (Adam, lr=1e-3).
2. Phase 2 : dégel de `layer3` et `layer4` (lr=1e-4) et de `fc` (lr=1e-3), 5 époques.
3. Compléter `metriques(model, loader)` : precision, recall et F1 par classe (matrice de confusion fournie).
4. Comparer MLP, CNN et ResNet sur le même jeu de test (cellules fournies).
5. Sauvegarder le ResNet (`state_dict` et métadonnées) dans `cifar_best.pt`, puis le recharger.

## Critères de réussite

- Étape 1 : exactement 20490 paramètres entraînables (2048 x 10 + 10).
- Étape 3 : dix valeurs de F1, chacune entre 0 et 1.
- Étape 5 : le modèle rechargé retrouve la même accuracy de test.

Ces critères sont vérifiés par des `assert` dans le notebook.

## Données

CIFAR-10 (Krizhevsky, Nair et Hinton, 2009), fourni par torchvision : photos couleur de 32 x 32 pixels en
10 classes. Le site du jeu ne donne pas de licence ; il demande de citer le rapport *Learning Multiple
Layers of Features from Tiny Images* (Krizhevsky, 2009). Les TP utilisent les mêmes tirages : 5000 images
d'entraînement, 1000 de validation et 1000 de test.

## Bonus

- B1. Même feature extraction avec EfficientNet-B0.

## Corrigé

`tp6_fine_tuning_corrige.ipynb`, à ouvrir après avoir terminé.
