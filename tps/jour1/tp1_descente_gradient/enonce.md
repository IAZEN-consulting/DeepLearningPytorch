# TP1 : descente de gradient à la main sur des contrats d'assurance auto

**Durée** : 35 min. **Module** : M2 (tenseurs, opérations, autograd).

## Objectif

Refaire à la main ce que font `nn.Linear` et l'optimiseur de la démo 1 : un modèle linéaire qui prédit
le coefficient de bonus-malus d'un contrat d'assurance auto à partir de l'âge du conducteur, de l'âge du
véhicule et du nombre de sinistres. Observer ce qui se passe quand on oublie de remettre les gradients à
zéro, puis corriger la boucle et comparer à la solution exacte.

## Prérequis

- Démo 1 (le premier neurone), démo 2 (tenseurs) et démo 3 (autograd, accumulation, `no_grad`).
- Notebook : `tp1_descente_gradient.ipynb`, à ouvrir dans Google Colab (le GPU n'est pas nécessaire).

## Étapes

0. Exécuter la préparation et l'exploration fournies ; répondre aux questions.
1. Écrire le modèle `x @ w + b` et l'erreur quadratique moyenne (une ligne chacun).
2. Appeler `backward()` deux fois sans remise à zéro, et observer le gradient.
3. Exécuter la boucle fournie sans remise à zéro, et expliquer la courbe d'erreur.
4. Compléter la boucle corrigée : remise à zéro des gradients, mise à jour des poids.
5. Comparer vos poids à la solution exacte (cellule fournie).

## Critères de réussite

- Étape 1 : une prédiction par contrat, forme `(5000,)`.
- Étape 4 : l'erreur finale est au moins dix fois plus petite que l'erreur de départ.
- Étape 5 : vos poids coïncident avec la solution exacte à 0.01 près.

Chaque critère est vérifié par un `assert` dans le notebook.

## Données

freMTPL2freq : contrats d'assurance responsabilité civile automobile en France, publiés sur OpenML sous
licence CC0.

## Bonus

- B1. Refaire l'entraînement avec `torch.optim.SGD`.
- B2. Essayer un learning rate trop grand, puis trop petit.

## Corrigé

`tp1_descente_gradient_corrige.ipynb`, à ouvrir après avoir terminé.
