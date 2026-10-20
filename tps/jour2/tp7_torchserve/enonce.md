# TP7 : déployer le classifieur CIFAR-10

**Durée** : 45 min. **Module** : M10 (déploiement des modèles PyTorch).

## Objectif

Partir du ResNet50 sauvegardé au TP6, l'exporter en TorchScript et en ONNX, comparer la latence de
PyTorch et d'ONNX Runtime sur un lot de 100 images, puis le servir comme API REST avec TorchServe.

## Prérequis

- Démos 5 et 6 du jour 2 (sauvegarde, TorchScript, ONNX, TorchServe).
- Le fichier `cifar_best.pt` du TP6 ; s'il manque, une cellule fournie le recrée.
- Notebook : `tp7_torchserve.ipynb`, dans Google Colab avec un runtime GPU (pour recréer le checkpoint).

## Étapes

0. Charger les données et le checkpoint (cellules fournies).
1. Recharger le ResNet50 sur CPU à partir du `state_dict`.
2. L'exporter en TorchScript et vérifier les sorties.
3. L'exporter en ONNX, l'exécuter avec ONNX Runtime et vérifier les sorties.
4. Comparer les latences sur 100 images (cellules fournies).
5. Écrire le prétraitement et le post-traitement du handler.
6. Créer l'archive `cifar.mar`.
7. Démarrer TorchServe (cellules fournies).
8. Envoyer une image d'avion et une image de chat avec `curl`.
9. Récupérer et enregistrer la description OpenAPI du service.

## Critères de réussite

- Étape 2 : écart maximal inférieur à 1e-3 avec les sorties de PyTorch (`assert`).
- Étape 3 : écart maximal inférieur à 1e-2, et mêmes classes prédites que PyTorch (`assert`).
- Étape 8 : l'API renvoie un JSON avec la classe et la probabilité.
- Étape 9 : `api_cifar.json` contient la route `/predictions/{model_name}`.

## Données

CIFAR-10 (Krizhevsky, Nair et Hinton, 2009), fourni par torchvision : photos couleur de 32 x 32 pixels en
10 classes. Le site du jeu ne donne pas de licence ; il demande de citer le rapport *Learning Multiple
Layers of Features from Tiny Images* (Krizhevsky, 2009). Les TP utilisent les mêmes tirages : 5000 images
d'entraînement, 1000 de validation et 1000 de test.

## Bonus

- B1. L'accuracy à travers l'API sur 100 images de test.

## Corrigé

`tp7_torchserve_corrige.ipynb`, à ouvrir après avoir terminé.
