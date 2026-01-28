# État du projet - Journal des sessions

## Session actuelle

**Date** : 2026-01-28

### Travail effectué
- [x] Installation pm-tools (GitHub lescientifik/pm-tools)
- [x] Recherche PubMed: "EANM FDG PET oncology guideline" → 25 articles
- [x] Recherche PubMed: "PET CT contrast enhanced FDG oncology guideline" → 17 articles
- [x] Extraction EANM Guidelines v2.0 (PMID 25452219, PMC4315529)
- [x] Synthèse complète: `knowledge/iv_recommendations_eanm.md`

### Découvertes clés
- **Strategy 2a recommandée** pour quantification: CT bas dose (correction atténuation) + CT injecté séparé
- **Impact SUV <10%** si contraste utilisé pour correction atténuation
- **Phase d'équilibre/veineuse** obligatoire, éviter phase artérielle
- **Metformine**: arrêt au moment de l'examen + 48h après
- **Bénéfice maximal contraste**: tête/cou + abdomen/pelvis (localisation anatomique)

### Prochaines étapes
- [ ] Recherche spécifique gynécologie: ovarian cancer, cervical cancer, endometrial
- [ ] Identifier études comparatives PET CT injecté vs non-injecté en onco-gynéco
- [ ] Synthèse protocole pratique pour mise en place

---

## Historique

### 2026-01-28 - Session 1 : Setup + Synthèse EANM v2.0
- Objectif défini : injection PCI sur TEP CT FDG
- Indications cibles : gynéco (phase 1), ORL (phase 2)
- pm-tools installé, recherches sauvegardées en JSONL dans src/
- **Synthèse EANM v2.0 complète** : 4 stratégies d'acquisition, recommandations quantification, protocoles injection
- Fichiers créés: `src/1769587861_EANM FDG PET oncology guideline.jsonl`, `src/1769587949_PET CT contrast enhanced FDG oncology guideline.jsonl`
