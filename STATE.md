# État du projet - Journal des sessions

## Session actuelle

**Date** : 2026-01-29

### Phase 2 : ORL - Bilan d'extension

### Travail effectué
- [x] **Revue bibliographique ORL** : `knowledge/orl_pet_ct_contrast_review.md`
- [x] **Protocole acquisition ORL** : `knowledge/protocole_acquisition_orl.md`

### Recherches effectuées
- Guidelines EHNS-ESMO-ESTRO 2020 (SCC oral/larynx/oropharynx/hypopharynx)
- Guidelines ESMO nasopharynx 2021, glandes salivaires 2022, sinonasal 2025
- Recommandations NCCN Head and Neck 2025
- Études comparatives contrast-enhanced vs non-enhanced PET/CT

### Découvertes clés

**Recommandations guidelines :**
- Aucune guideline majeure ne recommande explicitement le contrast-enhanced PET/CT
- Utilisation du PCI laissée à l'appréciation des équipes

**Études en faveur du PCI :**
- **PMID 20652890** : "We strongly suggest performing a contrast-enhanced PET/CT" (ganglions kystiques HPV+)
- **PMID 26122372** : CT injecté plus précis pour l'extension extranodale (92% vs 74% spécificité)
- **PMID 25892275** : PET/CECT outil le plus fiable pour surveillance post-op cavité buccale

**Indications retenues :**
- Carcinome oropharyngé HPV+ (ganglions kystiques) : **fortement recommandé**
- Suspicion d'ENE : **recommandé**
- Stades III-IV sans IRM programmée : **à considérer**

### Fichiers créés
- `src/1769697071_head_neck_PET_CT_contrast_staging.jsonl` (79 articles)
- `src/1769697XXX_head_neck_EANM_ESMO_meta_guidelines.jsonl` (87 articles)
- `src/1769697XXX_contrast_enhanced_PET_CT_head_neck.jsonl` (50 articles)
- `knowledge/orl_pet_ct_contrast_review.md`
- `knowledge/protocole_acquisition_orl.md`

### Prochaines étapes
- [ ] Validation protocole ORL par le chef de service
- [ ] Formation équipe sur spécificités ORL (ganglions kystiques, ENE)
- [ ] Mise en place pilote

---

## Historique

### 2026-01-29 - Session 4 : Phase 2 ORL
- **Objectif** : PCI sur TEP CT pour bilan d'extension cancers ORL
- Revue systématique de la littérature (216 articles analysés)
- Identification des études clés sur contrast-enhanced PET/CT en ORL
- **Création revue bibliographique** : `knowledge/orl_pet_ct_contrast_review.md`
- **Création protocole ORL** : `knowledge/protocole_acquisition_orl.md`
- Conclusion : PCI recommandé surtout pour oropharynx HPV+ et suspicion ENE

### 2026-01-28 - Session 3 : Protocole Gynéco Complet

### 2026-01-28 - Session 3 : Protocole d'Acquisition Complet
- **Création protocole complet** : `knowledge/protocole_acquisition_gyneco.md`
- Document structuré en 3 sections métier : Manipulateur, Physicien Médical, Médecin
- Inclut chronologie détaillée, arbres décisionnels, fiches synthèses
- Toutes les sources citées avec PMID et références ESUR/EANM v3.0
- Protocole prêt pour validation et mise en œuvre

### 2026-01-28 - Session 2 : Guidelines TEP FDG Gynécologie
- Recherche ciblée : protocole de réalisation (furosémide, contraste iodé)
- Récupération et analyse de 6 articles clés (guidelines EANM/SNMMI + études protocole)
- **Création synthèse complète** : `knowledge/gyneco_guidelines.md`
- Points clés : protocole furosémide 20-40 mg IV + sonde, PCI phase porto-veineuse compatible
- Fichiers: `src/1769597216_gyneco_fdg_pet_guidelines_protocols.jsonl`

### 2026-01-28 - Session 1 : Setup + Synthèse EANM v3.0
- Objectif défini : injection PCI sur TEP CT FDG
- Indications cibles : gynéco (phase 1), ORL (phase 2)
- pm-tools installé, recherches sauvegardées en JSONL dans src/
- **Synthèse EANM v3.0 complète** : changements majeurs identifiés (metformine, SGLT2, contraste oral, seuils rénaux)
- Référence ESUR intégrée pour gestion contraste
- Fichiers: `knowledge/iv_recommendations_eanm.md` (v3.0), fichiers JSONL recherches PubMed
