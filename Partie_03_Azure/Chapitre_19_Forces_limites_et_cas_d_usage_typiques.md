# Chapitre 19 — Forces, limites et cas d'usage typiques

## Introduction

Après avoir exploré les services Azure, faisons le bilan. Quand Azure est-il le meilleur choix ? Quelles sont ses vraies limites ? Ce chapitre vous aide à décider objectivement.

---

## 1. Les Forces d'Azure

### Force #1 : L'écosystème Microsoft

| Technologie | Intégration Azure |
|-------------|-------------------|
| Windows Server | Azure VMs natives |
| SQL Server | Azure SQL + Hybrid Benefit |
| Active Directory | Entra ID sync |
| .NET | App Service, Azure Functions |
| Office 365 | Même Tenant, même facturation |
| Power BI | Intégration Synapse |

### Force #2 : L'IA Générative (GPT-4)

Azure est le **seul cloud** avec accès natif à :
- GPT-4 / GPT-4 Turbo
- GPT-4 Vision
- DALL-E 3
- Whisper

### Force #3 : L'hybride

| Solution | Fonction |
|----------|----------|
| Azure Arc | Gérer n'importe quel serveur |
| Azure Stack Hub | Azure dans votre datacenter |
| Azure Stack HCI | Hyperconvergé Azure |
| ExpressRoute | Connexion dédiée |

### Force #4 : Enterprise-ready

- Négociation commerciale groupée (EA)
- Intégration SAP certifiée
- Régions gouvernementales et souveraines
- Support enterprise mature

---

## 2. Les Limites d'Azure

### Limite #1 : Fiabilité historique

> [!WARNING]
> Azure a connu plus de pannes globales qu'AWS. Notamment sur Entra ID qui peut impacter tout l'écosystème Microsoft.

### Limite #2 : Expérience développeur

| Aspect | Perception |
|--------|------------|
| Portal | Plus GUI que CLI |
| Documentation | Parfois moins claire qu'AWS |
| Naming | Renommages fréquents (Azure AD → Entra ID) |
| Consistance | Services avec des UX différentes |

### Limite #3 : Parts de marché cloud

| Cloud | Part de marché IaaS |
|-------|---------------------|
| AWS | ~32% |
| Azure | ~23% |
| GCP | ~11% |

Moins de parts de marché = moins de talents disponibles sur le marché.

---

## 3. Cas d'usage typiques

### Cas #1 : Digitalisation des grandes entreprises

Si l'entreprise utilise déjà :
- Windows Server
- Active Directory
- SQL Server
- Office 365
- .NET

→ **Azure est le choix naturel**.

### Cas #2 : Applications nécessitant GPT-4

Pour les projets d'IA générative d'entreprise avec exigences de conformité, Azure OpenAI est unique.

### Cas #3 : SAP sur le cloud

Azure a une relation privilégiée avec SAP et des certifications spécifiques.

### Cas #4 : Hybride on-prem + cloud

Azure Arc permet de gérer des VMs on-prem, sur AWS, ou n'importe où avec les mêmes outils qu'Azure.

---

## 4. Quand NE PAS choisir Azure

| Situation | Alternative |
|-----------|-------------|
| Startup tech pure, pas de legacy Microsoft | AWS |
| Focus Big Data / Analytics | GCP (BigQuery) |
| Équipe Linux-first, Kubernetes-native | GCP ou AWS |
| Multi-cloud stratégique | AWS (plus de services) |

---

## 5. Comparaison synthétique

| Critère | Azure | AWS | GCP |
|---------|-------|-----|-----|
| **Enterprise Microsoft** | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐ |
| **IA Générative** | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ |
| **Hybride** | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐ |
| **Maturité** | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ |
| **Data/Analytics** | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| **Fiabilité** | ⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ |

---

## 6. Checklist avant de choisir Azure

- [ ] Mon entreprise utilise-t-elle déjà Microsoft 365 / Active Directory ?
- [ ] Ai-je des licences Windows/SQL Server réutilisables (Hybrid Benefit) ?
- [ ] Ai-je besoin de GPT-4 en production avec conformité ?
- [ ] Mon application est-elle .NET ?
- [ ] Ai-je besoin d'une solution hybride mature ?

**Si 3+ oui → Azure est le bon choix.**

---

## Ce qu'il faut retenir

> Azure est le meilleur choix pour les **entreprises Microsoft** et les projets **IA générative**. Ce n'est pas forcément le meilleur choix pour tout le monde.

| Profil | Recommandation |
|--------|----------------|
| Entreprise Microsoft existante | ✅ Azure |
| Projet GPT-4 entreprise | ✅ Azure |
| Startup tech sans legacy | ⚠️ Évaluer AWS |
| Data/Analytics prioritaire | ⚠️ Évaluer GCP |

> [!TIP]
> Le plus grand avantage d'Azure n'est pas technique, c'est **l'accord commercial unifié** avec Microsoft couvrant cloud + productivité + ERP.
