# Rapport d'absentéisme — mini app

Lancer localement une petite application Flask qui permet de téléverser le fichier Excel et de télécharger le rapport CSV pour le mois détecté.

Pré-requis

- Python 3.8+
- installer les dépendances:

```bash
pip install -r requirements.txt
```

Lancer l'app

```bash
python app.py
```

Ouvrir http://127.0.0.1:5000 et téléverser le fichier `FICHIER DE SUIVI PERM ET ABS 2026.xlsx`.

Sortie

- Un fichier CSV nommé `report_<SHEET>.csv` sera proposé au téléchargement contenant pour chaque travailleur : nom, fonction, présence, absence, congé payé, permission, arrêt maladie, taux d'absentéisme (%) calculé comme :

```
taux = (absence + arrêt_maladie) / (presence + absence + congé_payé + arrêt_maladie + permission) * 100
```

Remarques

- Le parser tente d'identifier automatiquement la feuille du mois (feuilles nommées `JANVIER`, `FEVRIER`, …). Si la feuille mensuelle n'est pas détectable, il bascule sur la feuille `DECOMPTE` ou la première feuille.
- Les en-têtes fusionnées ou formats complexes peuvent nécessiter un pré-traitement. Si vous voulez, j'adapte le parser à la structure exacte du fichier.
