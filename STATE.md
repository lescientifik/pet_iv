# État du projet - Journal des sessions

## Session actuelle

**Date** : 2026-01-28

### Travail effectué
- [x] Installation pm-tools (GitHub lescientifik/pm-tools)
- [x] Recherche PubMed: "EANM FDG PET oncology guideline" → 25 articles
- [x] Recherche PubMed: "PET CT contrast enhanced FDG oncology guideline" → 17 articles
- [x] Extraction EANM Guidelines v2.0 (PMID 25452219, PMC4315529)
- [x] **MISE À JOUR v3.0** (DOI: 10.1016/j.eanmj.2025.100006) - extraction complète
- [x] Synthèse mise à jour: `knowledge/iv_recommendations_eanm.md`

### Découvertes clés v3.0 (changements vs v2.0)
- ⚠️ **Metformine**: NE PLUS arrêter si DFGe >30 (suivre ESUR)
- ⚠️ **SGLT2 inhibiteurs** (nouveau): omission 48h si préoccupation
- ⚠️ **Contraste oral**: eau/water-based préférés (moins artefacts)
- ⚠️ **Seuil néphrotoxicité**: DFGe <30 (vs <60 avant)
- **Phase porto-veineuse** pour injection IV
- **Double reconstruction AC/NAC** pour identifier artefacts
- **Systèmes modernes**: suivre procédure EARL

### Prochaines étapes
- [ ] Recherche spécifique gynécologie: ovarian cancer, cervical cancer, endometrial
- [ ] Identifier études comparatives PET CT injecté vs non-injecté en onco-gynéco
- [ ] Synthèse protocole pratique pour mise en place

---

## Historique

### 2026-01-28 - Session 1 : Setup + Synthèse EANM v3.0
- Objectif défini : injection PCI sur TEP CT FDG
- Indications cibles : gynéco (phase 1), ORL (phase 2)
- pm-tools installé, recherches sauvegardées en JSONL dans src/
- **Synthèse EANM v3.0 complète** : changements majeurs identifiés (metformine, SGLT2, contraste oral, seuils rénaux)
- Référence ESUR intégrée pour gestion contraste
- Fichiers: `knowledge/iv_recommendations_eanm.md` (v3.0), fichiers JSONL recherches PubMed
