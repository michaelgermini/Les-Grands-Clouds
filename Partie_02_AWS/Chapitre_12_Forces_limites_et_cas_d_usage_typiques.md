# Chapitre 12 — Forces, limites et cas d'usage typiques

## Introduction

Après avoir exploré les services AWS en détail, prenons du recul. Quand choisir AWS ? Quelles sont ses véritables forces et ses limites honnêtes ? Ce chapitre vous donne une vision pragmatique pour guider vos décisions.

---

## 1. Les Forces d'AWS

### Force #1 : Maturité et Profondeur

| Métrique | AWS |
|----------|-----|
| **Lancement** | 2006 (7 ans d'avance sur Azure) |
| **Services** | 200+ |
| **Régions** | 33+ |
| **Documentation** | La plus complète |

> "Nobody gets fired for choosing AWS" (version cloud du "Nobody gets fired for choosing IBM")

### Force #2 : L'écosystème

- **Communauté** : Le plus grand nombre de développeurs formés
- **Partenaires** : Milliers de partenaires certifiés
- **Marketplace** : Des milliers de solutions tierces
- **Formations** : Certifications reconnues mondialement

### Force #3 : L'innovation continue

AWS lance ~100 nouveaux services/features par an lors du re:Invent.

### Force #4 : Flexibilité de pricing

| Option | Économie |
|--------|----------|
| Reserved Instances | Jusqu'à 72% |
| Spot Instances | Jusqu'à 90% |
| Savings Plans | Jusqu'à 72% |

---

## 2. Les Limites d'AWS

### Limite #1 : Complexité

> [!WARNING]
> 200+ services = courbe d'apprentissage massive.

La console AWS peut être overwhelming pour les nouveaux utilisateurs. Il faut du temps pour maîtriser même les services de base.

### Limite #2 : Coûts cachés

| Piège fréquent | Coût caché |
|----------------|------------|
| NAT Gateway | ~$45/mois par gateway |
| Egress (sortie de données) | $0.09/Go |
| Cross-AZ traffic | $0.01/Go |
| EBS non supprimés | Facturation continue |
| Elastic IPs non attachées | $0.005/heure |

### Limite #3 : Support

| Niveau | Coût | Temps de réponse |
|--------|------|------------------|
| Basic | Gratuit | Forums uniquement |
| Developer | $29/mois | 12h business |
| Business | 10% de la facture | 1h (urgent) |
| Enterprise | 15%+ | 15 min (critique) |

### Limite #4 : Verrouillage (Lock-in)

Plus vous utilisez les services natifs AWS (Lambda, DynamoDB), plus la migration vers un autre cloud est complexe.

---

## 3. Cas d'usage typiques

### Cas #1 : Startups

| Avantage | Détail |
|----------|--------|
| **AWS Activate** | Crédits gratuits jusqu'à $100K |
| **Pay-as-you-go** | Pas de CAPEX initial |
| **Scale infini** | Accompagne la croissance |

### Cas #2 : Migration Enterprise (Lift & Shift)

| Outil | Fonction |
|-------|----------|
| **AWS MGN** | Migration de VMs |
| **AWS DMS** | Migration de bases de données |
| **AWS Application Discovery** | Inventaire on-prem |

### Cas #3 : Applications Serverless

Architecture event-driven avec :
- API Gateway + Lambda + DynamoDB
- Coût quasi-nul au repos
- Scale automatique

### Cas #4 : Big Data et Analytics

| Service | Fonction |
|---------|----------|
| S3 | Data Lake storage |
| Glue | ETL |
| Athena | Query SQL sur S3 |
| Redshift | Data Warehouse |
| EMR | Spark/Hadoop managé |

### Cas #5 : Machine Learning

Pipeline complet avec SageMaker, de la préparation des données au déploiement en production.

---

## 4. Quand NE PAS choisir AWS

| Situation | Alternative suggérée |
|-----------|---------------------|
| Entreprise 100% Microsoft (AD, Office, .NET) | **Azure** |
| Besoin impératif de GPT-4 | **Azure OpenAI** |
| Analytics/BigQuery natif | **GCP** |
| Budget très limité, équipe sans expertise | **Solutions SaaS** |

---

## 5. Comparaison synthétique avec Azure et GCP

| Critère | AWS | Azure | GCP |
|---------|-----|-------|-----|
| **Maturité** | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐ |
| **Enterprise** | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ |
| **Data/ML** | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| **Serverless** | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ |
| **Kubernetes** | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| **Hybride** | ⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ |

---

## 6. Checklist avant de choisir AWS

- [ ] Mon équipe a-t-elle les compétences ou peut-elle se former ?
- [ ] Ai-je estimé les coûts réels (y compris egress, NAT) ?
- [ ] Ai-je vérifié que tous les services nécessaires sont disponibles dans ma région ?
- [ ] Ai-je un plan pour éviter le vendor lock-in excessif ?
- [ ] Ai-je budgété le support Enterprise si critique ?

---

## Ce qu'il faut retenir

> AWS est le **choix par défaut** pour la plupart des projets cloud. Sa maturité, son écosystème et sa flexibilité en font le leader incontesté.

**Mais** ne choisissez pas AWS par défaut si :
- Votre ADN est Microsoft → Azure
- Votre priorité est la Data/IA → GCP peut être meilleur
- Vous voulez GPT-4 → Azure OpenAI

> [!TIP]
> Le meilleur cloud est celui que votre équipe maîtrise. L'expertise compte plus que les features.
