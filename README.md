# Formation PLB « Deep Learning avec PyTorch » (DLPT)

Matériel de formation en 2 jours : plan, présentations, démonstrations et TP. Les consignes de production sont dans `AGENTS.MD`. Les éléments retirés lors du passage de 3 à 2 jours (03/10/2026) sont dans `archive/`.

## Environnement

Versions alignées sur le runtime Google Colab : Python 3.12, torch 2.11.0, torchvision 0.26.0 (runtime GPU A100, build CUDA 12.8).

```bash
uv sync --extra cpu      # poste sans GPU NVIDIA (dont macOS)
uv sync --extra cu128    # poste avec GPU NVIDIA, CUDA 12.8 (comme Colab)
```

### Fichiers requirements

- `requirements.txt` : l'environnement complet, figé par `uv.lock` (variante GPU CUDA 12.8), pour reproduire le projet hors uv : `uv pip install -r requirements.txt`. Il se régénère avec la commande indiquée en tête du fichier.
- `requirements-colab.txt` : les seules bibliothèques utilisées par les notebooks, aux versions du runtime Colab. Dans Colab : `%pip install uv` puis `!uv pip install --system -r requirements-colab.txt` ; les paquets déjà présents ne sont pas réinstallés. Il ne contient ni Jupyter ni ipykernel, pour ne pas toucher au noyau de Colab. Chaque notebook commence par une cellule « Installation » qui écrit ce fichier puis l'installe ainsi, dans Colab seulement.

## Présentations

Les fichiers `slides/jour1.pptx` (modules 1 à 5) et `slides/jour2.pptx` (modules 6 à 10) sont générés à partir du template PLB par les scripts de `slides/build/`. Le fond (marine ou blanc) et le logo PLB sont posés à la construction par `slides/build/deck.py` :

```bash
uv run --extra cpu python slides/build/build.py jour1 jour2            # génère les .pptx
uv run --extra cpu python slides/build/check_snippets.py jour1 jour2   # exécute le code des slides
uv run python slides/build/index_slides.py                 # met à jour l'index de plan/couverture.md
uv run --extra cpu python slides/build/sans_speech.py      # copies sans speech dans slides/without/
```

La génération s'arrête si un titre dépasse une ligne, si un bloc de code dépasse 15 lignes ou si sa police descend sous 15 pt.

## Démos et TP

Les notebooks de `demos/` et `tps/` sont générés par les scripts de `notebooks/build/` (`jour1.py` : démos 1 à 5 et TP1-TP2 ; `jour2.py` : démos 6-7 du jour 1, démos 1-2 du jour 2 et TP3 à TP5 ; `jour3.py` : démos 3 à 6 du jour 2 et TP6 à TP8), puis exécutés en local pour enregistrer leurs sorties. Les démos utilisent Fashion-MNIST (torchvision) ; les TP utilisent des jeux publics (contrats freMTPL2 pour le TP1, CIFAR-10 pour les TP2 à TP5, TP7 et TP8, accidents ONISR pour le TP6), chargés par les fonctions de `notebooks/build/donnees.py`, recopiées dans chaque notebook.py`, et chaque notebook les recopie dans sa cellule de préparation pour tourner seul dans Colab. Licences et détails : `plan/couverture.md`.

```bash
uv run python notebooks/build/jour1.py                                          # génère les notebooks du jour 1
uv run python notebooks/build/run.py demos/jour1/*.ipynb tps/jour1/*/*_corrige.ipynb   # test local, sans modifier les notebooks
uv run python notebooks/build/check.py demos/jour1/*.ipynb tps/jour1/*/*.ipynb tps/jour1/*/enonce.md   # structure, erreurs, emojis, sources, valeurs citées
```

Circuit d'exécution : les notebooks sont testés en local, puis exécutés par le formateur dans Colab sur GPU A100 ; ce sont ces sorties qui sont enregistrées. Régénérer un notebook conserve les sorties des cellules de code inchangées, et `run.py` n'écrit les sorties locales qu'avec `--enregistrer`. Les commentaires des résultats (`notebooks/build/textes_*.py`) sont ensuite relus d'après les sorties A100 ; `check.py` signale tout nombre cité absent de la sortie commentée. Les versions stagiaires ne sont pas exécutées.
