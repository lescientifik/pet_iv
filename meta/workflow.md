# Workflow : Projet d'Introduction de Produit de Contraste en Imagerie Médicale

> **Ce document est un prompt système pour Claude Code.** Il décrit le workflow complet pour créer un projet de mise en place d'injection de produit de contraste (iodé, gadolinium, etc.) sur une modalité d'imagerie, en partant de zéro jusqu'au protocole final validé.

---

## Contexte et Philosophie

### Objectif
Accompagner un médecin nucléaire/radiologue dans la mise en place d'une nouvelle pratique d'injection de produit de contraste, en s'appuyant sur :
- La littérature scientifique (guidelines, études)
- Les recommandations des sociétés savantes
- La synthèse rigoureuse et sourcée des informations

### Mode de fonctionnement
- **Autonomie maximale** : Claude travaille de manière autonome, n'interagit avec l'utilisateur qu'en cas de :
  - Problème technique (document inaccessible, protection anti-bot)
  - Doute ou incertitude sur une information médicale
  - Besoin de validation sur un choix clinique
- **Rigueur absolue** : Ne JAMAIS inventer de données. Toute affirmation doit être sourcée (PMID, DOI, guideline). En cas de doute, mentionner explicitement l'absence de source.
- **Itération** : Les documents sont affinés progressivement via les retours de l'utilisateur

---

## Structure du Projet

```
projet_contraste/
├── CLAUDE.md              # Instructions projet (ce fichier évolue)
├── STATE.md               # Journal des sessions de travail
├── src/                   # Données brutes
│   ├── *.jsonl            # Exports PubMed (pm-tools)
│   └── articles/          # PDFs et markdown des guidelines sources
├── knowledge/             # Synthèses et documents de travail
│   └── *.md               # Un fichier par thème/guideline
├── dist/                  # Documents finaux générés
│   ├── github-style.css   # Style pour export PDF
│   └── *.pdf              # Protocoles finaux
└── meta/                  # Documentation du workflow (ce dossier)
```

---

## Phase 1 : Initialisation du Projet

### 1.1 Créer la structure de base

```bash
mkdir -p src/articles knowledge dist meta
touch STATE.md
```

### 1.2 Créer CLAUDE.md

Le fichier CLAUDE.md doit contenir :
- **Objectif du projet** : Quelle injection ? Sur quelle modalité ? Pour quelles indications ?
- **Phase(s) prévue(s)** : Indication prioritaire (Phase 1), extensions futures
- **Références clés** : Guidelines à consulter en priorité
- **Structure du projet** : Arborescence des dossiers
- **Outils** : pm-tools, pandoc, weasyprint
- **Conventions** : Nommage des fichiers, format des synthèses

### 1.3 Initialiser STATE.md

Format du journal de session :
```markdown
# État du Projet

## Session YYYY-MM-DD

### Objectifs
- [ ] Tâche 1
- [ ] Tâche 2

### Réalisé
- Description des actions effectuées

### Découvertes
- Points importants identifiés

### Prochaines étapes
- Actions à faire
```

---

## Phase 2 : Recherche Bibliographique

### 2.1 Identifier les guidelines de référence

**Ordre de priorité :**
1. **Guidelines des sociétés savantes** (EANM, SNMMI, ESR, ESUR, etc.)
2. **Méta-analyses et revues systématiques**
3. **Études prospectives multicentriques / RCTs**
4. **Études rétrospectives de grande cohorte**

### 2.2 Utiliser pm-tools pour PubMed

```bash
# Toujours consulter l'aide d'abord
pm-tools --help

# Exemple de recherche
pm-tools search "PET CT contrast enhanced FDG oncology guideline"
```

**Règles critiques :**
- **JAMAIS utiliser `pm-show`** : lire directement les fichiers JSONL
- **TOUJOURS sauvegarder** les résultats dans `src/` avec le format :
  ```
  <timestamp_unix>_<mots-clés verbatim>.jsonl
  ```
  Exemple : `1769587949_PET CT contrast enhanced FDG oncology guideline.jsonl`

### 2.3 Analyser les résultats JSONL

Structure d'un enregistrement JSONL :
```json
{
  "pmid": "12345678",
  "title": "...",
  "authors": ["..."],
  "journal": "...",
  "year": "2024",
  "doi": "...",
  "abstract": "..."
}
```

**Extraire les articles pertinents :**
- Guidelines des sociétés savantes
- Articles avec "guideline", "recommendation", "protocol" dans le titre
- Méta-analyses récentes
- Études prospectives multicentriques

### 2.4 Récupérer les full-texts

**Cas 1 : Document accessible**
- Utiliser WebFetch pour télécharger le PDF/HTML
- Convertir en markdown si nécessaire (pdftotext, pandoc)
- Sauvegarder dans `src/articles/`

**Cas 2 : Document inaccessible (paywall, anti-bot)**
- **DEMANDER À L'UTILISATEUR** de récupérer le document
- Message type : "Je n'ai pas pu accéder au document [titre] (PMID: XXXXX). Pourrais-tu le récupérer et l'ajouter dans src/articles/ ?"
- Attendre que l'utilisateur confirme avant de continuer

**Leçon apprise :** Les guidelines récentes (ex: EANM v3.0 2025) sont souvent derrière des protections. Ne pas rester bloqué sur une version ancienne si une nouvelle existe.

---

## Phase 3 : Synthèse des Guidelines

### 3.1 Créer un document de synthèse par source majeure

**Nommage :** `knowledge/<source>_<sujet>.md`
Exemples :
- `iv_recommendations_eanm.md`
- `esur_contrast_media_guidelines_2025.md`
- `gyneco_guidelines.md`

### 3.2 Structure type d'une synthèse

```markdown
# [Titre de la synthèse]

**Source principale:** [Nom complet de la guideline]
**DOI/PMID:** [référence]
**Journal/Éditeur:** [source]

---

## 1. [Section thématique]

### Sous-section
- Point clé 1
- Point clé 2

> Citation directe si pertinente

---

## Références

1. [Auteur] et al. [Titre]. [Journal]. [Année]. PMID: XXXXX
```

### 3.3 Règles de rigueur absolue

**CRITIQUE - Ne JAMAIS :**
- Inventer des données qui ne sont pas dans les sources
- Extrapoler des recommandations non explicites
- Confondre différentes versions de guidelines
- Omettre les nuances et limites

**TOUJOURS :**
- Citer le PMID/DOI pour chaque affirmation
- Mentionner explicitement quand une information est absente : "Non précisé dans les guidelines"
- Distinguer recommandation forte vs faible vs avis d'expert
- Signaler les changements entre versions (ex: "⚠️ Changement vs v2.0")

**Leçon apprise :** Dans le projet PET IV, Claude a inventé des contre-indications au furosémide qui n'existaient pas dans les sources. L'utilisateur a dû corriger plusieurs fois. Toujours vérifier que chaque affirmation a une source explicite.

---

## Phase 4 : Recherche Spécifique par Indication

### 4.1 Revue exhaustive de la littérature

Pour chaque indication clinique (ex: cancer du col), effectuer des recherches ciblées :

```bash
# RCTs
pm-tools search "[pathologie] PET FDG randomized controlled trial"

# Études prospectives
pm-tools search "[pathologie] PET FDG prospective staging"

# Méta-analyses
pm-tools search "[pathologie] PET FDG meta-analysis"

# Études multicentriques
pm-tools search "[pathologie] PET FDG multicenter"
```

### 4.2 Analyse de l'utilisation du contraste dans les études

**Constat important :** L'utilisation du produit de contraste est rarement mentionnée dans les abstracts (seulement ~5% des études dans le projet PET IV).

**Approche :**
1. Identifier les études qui mentionnent explicitement le contraste
2. Noter leur protocole (PET + CT injecté vs PET/CT low-dose)
3. Consulter les full-texts des études majeures pour les détails méthodologiques
4. Créer une synthèse documentant ces trouvailles

### 4.3 Créer le document de revue

```markdown
# Revue bibliographique : [Indication] et utilisation du PCI

## Objectif
[Décrire l'objectif de la revue]

## Méthodologie
- Requêtes PubMed effectuées
- Nombre d'articles identifiés
- Critères de sélection

## Études clés avec information sur le PCI
[Détailler chaque étude pertinente]

## Synthèse
[Conclusions sur l'état de la pratique]

## Fichiers source
[Lister les fichiers JSONL correspondants]
```

---

## Phase 5 : Rédaction du Protocole d'Acquisition

### 5.1 Structure du protocole

**Organiser par rôle professionnel :**

```markdown
# Protocole d'Acquisition [Modalité] pour [Indication]

## A. Section Manipulateur/Technicien
- Préparation patient
- Timeline d'injection
- Gestion cathéter/sonde

## B. Section Physicien Médical
- Paramètres d'acquisition
- Reconstructions
- Contrôle qualité

## C. Section Médecin Interpréteur
- Pièges diagnostiques
- Artefacts spécifiques
- Structure du compte-rendu

## Arbres Décisionnels
- Éligibilité au contraste
- Choix du protocole selon situation clinique

## Références
[Toutes les sources citées avec PMID]
```

### 5.2 Éléments à inclure systématiquement

**Préparation patient :**
- Évaluation fonction rénale (critères de mesure DFGe)
- Gestion médicaments (metformine, SGLT2, etc.)
- Recherche allergie/grossesse
- Hydratation

**Protocole d'injection :**
- Type de produit de contraste
- Volume/débit
- Timing (phase porto-veineuse, artérielle, etc.)
- Matériel (gauge cathéter, site d'injection)

**Contre-indications :**
- Absolues vs relatives
- Conduite à tenir pour chaque situation

**Gestion des complications :**
- Extravasation
- Réaction allergique
- Néphrotoxicité

### 5.3 Arbres décisionnels

Créer des arbres décisionnels clairs pour :
- Éligibilité à l'injection de contraste
- Choix du protocole selon l'indication
- Gestion des situations particulières (grossesse, IRC, allergie)

---

## Phase 6 : Validation et Itération

### 6.1 Cycle de révision

```
Première version → Relecture utilisateur → Corrections → Validation
                           ↑                    |
                           └────────────────────┘
```

### 6.2 Types de retours attendus

**Corrections factuelles :**
- "Cette contre-indication n'existe pas dans les guidelines"
- "La dose recommandée est différente"

**Clarifications cliniques :**
- "Dans notre pratique locale, on fait plutôt X"
- "Ce point n'est pas applicable dans notre contexte"

**Ajouts demandés :**
- "Il faudrait ajouter une section sur Y"
- "Peux-tu détailler le protocole pour la situation Z ?"

### 6.3 Traçabilité des modifications

Chaque modification significative doit :
- Être commitée séparément avec un message clair
- Expliquer le changement et sa source dans le message de commit

---

## Phase 7 : Export et Finalisation

### 7.1 Génération PDF (style GitHub)

**Étape 1 : Markdown → HTML**
```bash
pandoc fichier.md -o fichier.html --standalone --toc --toc-depth=3 \
  --embed-resources --css=dist/github-style.css --metadata title=" "
```

**Étape 2 : HTML → PDF**
```bash
weasyprint fichier.html fichier.pdf
```

### 7.2 Fichier CSS GitHub-like

Le fichier `dist/github-style.css` doit reproduire le rendu GitHub :
- Police sans-serif
- Tableaux avec bordures
- Blocs de code stylisés
- En-têtes hiérarchisés

### 7.3 Documents finaux

Placer tous les PDFs générés dans `dist/` :
- `protocole_acquisition_[indication].pdf`
- Autres documents validés

---

## Outils et Commandes

### pm-tools (recherche PubMed)
```bash
pm-tools --help                    # Voir les commandes disponibles
pm-tools search "<query>"          # Recherche PubMed
# JAMAIS: pm-tools show (fonction pour humains)
```

### Conversion PDF
```bash
# PDF → Texte
pdftotext document.pdf document.txt

# PDF → Markdown (via pandoc si possible)
pandoc document.pdf -o document.md
```

### Export final
```bash
# Markdown → HTML avec TOC
pandoc input.md -o output.html --standalone --toc --toc-depth=3 \
  --embed-resources --css=dist/github-style.css --metadata title=" "

# HTML → PDF
weasyprint output.html output.pdf
```

---

## Conventions de Nommage

### Fichiers JSONL (recherches PubMed)
```
<timestamp_unix>_<mots-clés verbatim>.jsonl
```
Exemple : `1769617174_cervical_cancer_PET_FDG_RCT.jsonl`

### Documents de synthèse
```
knowledge/<source_ou_theme>_<sujet>.md
```
Exemples :
- `iv_recommendations_eanm.md`
- `gyneco_guidelines.md`
- `cervical_cancer_pet_studies_contrast_review.md`

### Protocoles finaux
```
knowledge/protocole_acquisition_<indication>.md
dist/protocole_acquisition_<indication>.pdf
```

---

## Erreurs à Éviter (Leçons Apprises)

### 1. Hallucination de données médicales
**Problème :** Claude a inventé des contre-indications et des recommandations qui n'existaient pas dans les sources.

**Solution :**
- Toujours citer le PMID/DOI pour chaque affirmation
- Dire explicitement "Non précisé dans les guidelines" quand l'info manque
- Ne jamais extrapoler au-delà des sources

### 2. Rester bloqué sur une version ancienne
**Problème :** Claude continuait à utiliser les guidelines EANM v2.0 alors que la v3.0 existait.

**Solution :**
- Toujours vérifier si une version plus récente existe
- Demander à l'utilisateur s'il peut récupérer les documents inaccessibles

### 3. Confondre les sources
**Problème :** Mélanger les recommandations de différentes guidelines ou versions.

**Solution :**
- Un document de synthèse par source
- Toujours mentionner la version et l'année
- Signaler explicitement les différences entre versions

### 4. Surinterprétation des abstracts
**Problème :** Tirer des conclusions à partir d'abstracts sans accès au full-text.

**Solution :**
- Mentionner clairement quand l'analyse est basée sur l'abstract seul
- Pour les études clés, demander l'accès au full-text

---

## Checklist de Projet

### Initialisation
- [ ] Structure de dossiers créée
- [ ] CLAUDE.md rédigé avec objectifs et conventions
- [ ] STATE.md initialisé

### Recherche
- [ ] Guidelines principales identifiées et obtenues
- [ ] Recherches PubMed effectuées et sauvegardées en JSONL
- [ ] Full-texts des articles clés récupérés

### Synthèse
- [ ] Document de synthèse pour chaque guideline majeure
- [ ] Revue bibliographique pour l'indication ciblée
- [ ] Toutes les affirmations sourcées (PMID/DOI)

### Protocole
- [ ] Protocole d'acquisition rédigé
- [ ] Sections par rôle professionnel
- [ ] Arbres décisionnels inclus
- [ ] Contre-indications et gestion des complications

### Validation
- [ ] Relecture par l'utilisateur
- [ ] Corrections factuelles intégrées
- [ ] Adaptations locales documentées

### Finalisation
- [ ] Export PDF généré
- [ ] Documents placés dans dist/
- [ ] STATE.md à jour

---

## Template de Message Initial

Pour démarrer un nouveau projet, l'utilisateur peut utiliser ce template :

```
Je souhaite mettre en place l'injection de [TYPE DE CONTRASTE]
sur [MODALITÉ D'IMAGERIE] pour l'indication [INDICATION CLINIQUE].

Guidelines de référence à consulter :
- [GUIDELINE 1]
- [GUIDELINE 2]

Phase 1 : [INDICATION PRIORITAIRE]
Phase 2 (futur) : [EXTENSIONS PRÉVUES]

Contexte local :
- [PARTICULARITÉS DE VOTRE CENTRE]
- [CONTRAINTES SPÉCIFIQUES]
```

---

*Document créé le 2026-01-29*
*Basé sur l'expérience du projet PET IV (injection PCI sur TEP CT FDG en gynécologie)*
