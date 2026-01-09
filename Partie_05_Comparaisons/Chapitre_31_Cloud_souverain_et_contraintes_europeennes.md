# Chapitre 31 — Cloud souverain et contraintes européennes

## Introduction

L'Europe a une position unique vis-à-vis du cloud américain. Entre le RGPD, le CLOUD Act, et les exigences de souveraineté, les entreprises doivent naviguer dans un paysage complexe.

---

## 1. Le problème : CLOUD Act vs RGPD

### CLOUD Act (USA, 2018)

| Aspect | Implication |
|--------|-------------|
| **Portée** | Entreprises US partout dans le monde |
| **Accès** | Gouvernement US peut exiger les données |
| **Localisation** | Même si données hors USA |

### RGPD (Europe, 2018)

| Aspect | Implication |
|--------|-------------|
| **Protection** | Données personnelles des Européens |
| **Transfert** | Encadré vers pays tiers |
| **Conflit** | Contradiction directe avec CLOUD Act |

### Le dilemme

```
CLOUD Act : "Donnez-nous les données"
     ↓
Entreprise US (AWS, Azure, GCP)
     ↓
RGPD : "Vous ne pouvez pas les donner"
```

---

## 2. SecNumCloud : Le label français

### Définition
Label de l'ANSSI (Agence Nationale de la Sécurité des Systèmes d'Information) pour les clouds de confiance.

### Exigences principales

| Exigence | Détail |
|----------|--------|
| **Nationalité** | Opérateur européen |
| **Immunité** | Pas de soumission aux lois extra-UE |
| **Localisation** | Données en France |
| **Sécurité** | Normes strictes |

### Qui est SecNumCloud ?

| Fournisseur | Statut |
|-------------|--------|
| OVHcloud | ✅ Certifié |
| Outscale | ✅ Certifié |
| 3DS Outscale | ✅ Certifié |
| AWS, Azure, GCP | ❌ Pas directement (mais partenariats) |

---

## 3. Les solutions hybrides

### Bleu (Microsoft + Orange + Capgemini)

| Aspect | Détail |
|--------|--------|
| **Technologie** | Azure |
| **Opérateur** | Français (Orange/Capgemini) |
| **Immunité** | Coupure juridique avec Microsoft |
| **Disponibilité** | 2024+ |

### S3NS (Google + Thales)

| Aspect | Détail |
|--------|--------|
| **Technologie** | Google Cloud |
| **Opérateur** | Français (Thales) |
| **Immunité** | Coupure juridique avec Google |
| **Disponibilité** | 2024+ |

### Schema conceptuel

```
Technologie US (Azure/GCP)
         │
    Licence/Support
         ▼
Opérateur Français (Orange/Thales)
         │
    Opérations, clés, données
         ▼
Entreprise française cliente
```

---

## 4. GAIA-X

### L'initiative européenne

| Objectif | Détail |
|----------|--------|
| **Interopérabilité** | Standards communs |
| **Souveraineté** | Données en Europe |
| **Fédération** | Pas un cloud unique, des règles |

### État actuel
Adoption lente, mais les hyperscalers participent.

---

## 5. Qui doit se soucier du cloud souverain ?

| Secteur | Niveau d'exigence |
|---------|------------------|
| **Défense** | Obligatoire |
| **Santé (données sensibles)** | Fortement recommandé |
| **Finance** | Régulé |
| **Administration publique** | Obligatoire pour sensible |
| **Entreprise privée standard** | Évaluer le risque |

---

## 6. Coût de la souveraineté

| Aspect | Impact |
|--------|--------|
| **Prix** | +30-50% vs hyperscalers |
| **Innovation** | Retard sur les features |
| **Écosystème** | Plus petit |
| **Compétences** | Moins de talents formés |

---

## 7. Guide de décision

| Situation | Recommandation |
|-----------|----------------|
| Données non sensibles | Hyperscaler standard |
| Données personnelles UE | Hyperscaler + précautions RGPD |
| Données sensibles (santé, finance) | Évaluer Bleu/S3NS ou souverain |
| Défense, gouvernement critique | Cloud souverain (SecNumCloud) |

---

## Ce qu'il faut retenir

> La souveraineté cloud a un **coût**. Évaluez si votre cas d'usage le justifie.

| Principe | Application |
|----------|-------------|
| Classifier vos données | Pas tout n'est sensible |
| Évaluer Bleu/S3NS | Compromis intéressant |
| Suivre la régulation | Ça évolue vite |
| Localisation ≠ Souveraineté | La nationalité de l'opérateur compte |

> [!WARNING]
> Dire "mes données sont en Europe" ne suffit pas. C'est la **nationalité de l'opérateur** qui détermine l'immunité au CLOUD Act.
