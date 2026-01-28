# État du projet - Journal des sessions

## Session actuelle

**Date** : 2026-01-28

### Travail effectué
- [x] Recherche PubMed spécifique gynécologie (4 requêtes)
- [x] Récupération 6 articles clés (PMIDs: 33275178, 34215923, 25345433, 28287942, 14736836, 27775939)
- [x] **Synthèse complète**: `knowledge/gyneco_guidelines.md`

### Découvertes clés - Protocole gynéco

#### Furosémide (EANM/SNMMI guideline col utérin PMID 33275178)
- **Posologie**: 20-40 mg IV (0.5 mg/kg)
- **Timing**: Après injection FDG
- **Hydratation**: ~1 L perfusion IV NaCl 0.9%
- **Sonde urinaire**: OUI - Foley AVANT injection FDG, drainage par gravité

#### Produit de contraste iodé
- **N'affecte PAS l'interprétation visuelle** du PET (confirmé par littérature)
- **Phase porto-veineuse** (~50-70 sec)
- **Bénéfice majeur** : localisation anatomique pelvis (vaisseaux, ganglions iliaques)
- **Contraste oral**: eau/agents hydrosolubles préférés (moins d'artefacts CT-AC)

#### Alternative "patient-friendly" (sans sonde)
- Hydratation orale modérée + diurétique dose faible tardif
- Acquisition retardée si nécessaire
- Efficace pour bladder cancer (100% visualisation dans étude PMID 25345433)

### Prochaines étapes
- [ ] Rédaction protocole opérationnel pour le service
- [ ] Formation équipe sur gestion vésicale
- [ ] Check-list patient pré-examen

---

## Historique

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
