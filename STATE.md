# État du projet - Journal des sessions

## Session actuelle

**Date** : 2026-01-28

### Travail effectué
- [x] **Protocole complet rédigé** : `knowledge/protocole_acquisition_gyneco.md`

### Contenu du protocole

#### Section Manipulateur
- Checklist pré-examen complète (éligibilité PCI, grossesse, glycémie, eGFR)
- Chronologie détaillée d'injection (FDG, furosémide, PCI)
- Protocole furosémide avec sonde Foley
- Gestion incidents (extravasation, réaction allergique)
- Fiche synthèse opérationnelle

#### Section Physicien Médical
- Paramètres d'acquisition TEP (activité, temps/lit, champ)
- Paramètres CT diagnostique injecté
- Reconstructions obligatoires (AC + NAC)
- Documentation dose
- Fiche synthèse

#### Section Médecin Interprétant
- Pièges et faux positifs/négatifs (PMID 28287942)
- Interprétation par localisation (col, ovaire, endomètre, vulve)
- Artefacts liés au contraste et conduite à tenir
- Structure compte-rendu recommandée

#### Annexes
- Arbres décisionnels (éligibilité PCI, choix protocole vésical)
- Toutes les sources citées avec PMID

### Prochaines étapes
- [x] ~~Rédaction protocole opérationnel pour le service~~
- [ ] Formation équipe sur gestion vésicale
- [ ] Check-list patient pré-examen (intégrée dans le protocole)
- [ ] Validation par le chef de service
- [ ] Mise en place pilote

---

## Historique

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
