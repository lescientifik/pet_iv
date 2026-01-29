# Projet PET IV - Injection de Produit de Contraste Iodé sur TEP CT FDG

## Objectif

Mise en place de l'injection de produit de contraste iodé (PCI) sur les examens TEP CT au FDG, en commençant par des indications ciblées.

## Indications ciblées

### Phase 1 : Gynécologie
- Indication prioritaire pour le déploiement initial

### Phase 2 (à venir) : ORL
- Extension potentielle dans un second temps

## Références

- **EANM Guidelines** : Nouvelles recommandations EANM sur le PET FDG en oncologie (publication récente)
  - Ces guidelines abordent notamment l'utilisation du produit de contraste iodé

## Structure du projet

```
pet_iv/
├── CLAUDE.md          # Documentation projet (ce fichier)
├── STATE.md           # Suivi des sessions de travail
├── src/               # Données brutes des recherches PubMed
│   └── *.jsonl        # Exports pm-tools (1 fichier par recherche)
├── knowledge/         # Découvertes et synthèses de la littérature
│   └── *.md           # Documents de recherche
└── dist/              # Documents générés (Word, PDF)
    └── *.docx         # Protocoles exportés
```

## Outils

- **pm-tools** : https://github.com/lescientifik/pm-tools
  - Outil pour effectuer les recherches PubMed
  - Utilisé pour la veille bibliographique
  - **Utiliser `pm-tools --help`** pour connaître les commandes disponibles
  - **JAMAIS utiliser `pm-show`** : c'est une fonction pour humains, lire directement les fichiers JSONL

- **pandoc** : Conversion Markdown → Word
  - Commande : `pandoc fichier.md -o fichier.docx --standalone --toc --toc-depth=3`
  - Options utilisées :
    - `--standalone` : Document complet avec métadonnées
    - `--toc` : Table des matières automatique
    - `--toc-depth=3` : Profondeur de la table des matières

## Workflow

1. Recherche PubMed via pm-tools
2. **Sauvegarder systématiquement** le résultat en JSONL dans `src/`
   - Nommage : `<timestamp>_<mots-clés verbatim>.jsonl`
   - Ex: `1706450400_PET CT contrast gynecology.jsonl`
   - Permet de tracer et revoir les recherches sans refaire d'appels API
3. Synthèse des découvertes dans `knowledge/`
4. Mise à jour de STATE.md à chaque session
