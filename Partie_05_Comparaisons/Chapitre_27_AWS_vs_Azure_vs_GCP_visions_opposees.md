# Chapitre 27 — AWS vs Azure vs GCP : visions opposées (Synthèse)

## Introduction

Chaque hyperscaler a une vision et un ADN différents. Ce n'est pas une question de "meilleur" mais de **meilleur pour votre contexte**. Ce chapitre synthétise les différences fondamentales.

---

## 1. Les origines qui façonnent les visions

| Cloud | Origine | Vision |
|-------|---------|--------|
| **AWS** | E-commerce Amazon | Pragmatisme, self-service, APIs |
| **Azure** | Enterprise Microsoft | Extension du datacenter, hybride |
| **GCP** | Ingénierie Google | Data-first, innovation technique |

---

## 2. Tableau comparatif global

| Critère | AWS | Azure | GCP |
|---------|-----|-------|-----|
| **Lancement** | 2006 | 2010 | 2008 |
| **Part de marché** | ~32% | ~23% | ~11% |
| **Forces** | Maturité, étendue | Enterprise, hybride, GPT-4 | Data, K8s, innovation |
| **Public cible** | Tous | Entreprises MS | Data/Dev teams |
| **Nombre de services** | 200+ | 200+ | 100+ |
| **Régions** | 33+ | 60+ | 40+ |

---

## 3. Comparaison par domaine

### Compute

| Service | AWS | Azure | GCP |
|---------|-----|-------|-----|
| VMs | EC2 ⭐⭐⭐⭐⭐ | VMs ⭐⭐⭐⭐ | GCE ⭐⭐⭐⭐ |
| Kubernetes | EKS ⭐⭐⭐⭐ | AKS ⭐⭐⭐⭐ | GKE ⭐⭐⭐⭐⭐ |
| Serverless | Lambda ⭐⭐⭐⭐⭐ | Functions ⭐⭐⭐⭐ | Cloud Run ⭐⭐⭐⭐⭐ |

### Data

| Service | AWS | Azure | GCP |
|---------|-----|-------|-----|
| Object Storage | S3 ⭐⭐⭐⭐⭐ | Blob ⭐⭐⭐⭐ | GCS ⭐⭐⭐⭐ |
| Data Warehouse | Redshift ⭐⭐⭐⭐ | Synapse ⭐⭐⭐⭐ | BigQuery ⭐⭐⭐⭐⭐ |
| NoSQL | DynamoDB ⭐⭐⭐⭐⭐ | Cosmos DB ⭐⭐⭐⭐⭐ | Bigtable ⭐⭐⭐⭐ |

### IA/ML

| Aspect | AWS | Azure | GCP |
|--------|-----|-------|-----|
| Plateforme | SageMaker ⭐⭐⭐⭐ | Azure ML ⭐⭐⭐⭐ | Vertex AI ⭐⭐⭐⭐ |
| GenAI | Bedrock (multi) | OpenAI (GPT-4) ⭐⭐⭐⭐⭐ | Gemini ⭐⭐⭐⭐ |
| Hardware | Inferentia | NVIDIA | TPU ⭐⭐⭐⭐⭐ |

### Sécurité & Identité

| Aspect | AWS | Azure | GCP |
|--------|-----|-------|-----|
| IAM | IAM ⭐⭐⭐⭐⭐ | Entra ID ⭐⭐⭐⭐⭐ | Cloud IAM ⭐⭐⭐⭐ |
| Hybride | Outposts ⭐⭐⭐ | Arc/Stack ⭐⭐⭐⭐⭐ | Anthos ⭐⭐⭐⭐ |
| Zero Trust | ⭐⭐⭐ | ⭐⭐⭐⭐ | BeyondCorp ⭐⭐⭐⭐⭐ |

---

## 4. Profils types et recommandations

| Profil d'entreprise | Recommandation |
|---------------------|----------------|
| Startup tech, pas de legacy | **GCP** ou AWS |
| Entreprise Microsoft (AD, Office) | **Azure** |
| Migration massive legacy | **AWS** |
| Data/Analytics prioritaire | **GCP** |
| Besoin GPT-4 en production | **Azure** |
| Multi-cloud stratégique | **AWS** (plus de services) |

---

## 5. Le vrai facteur de décision

> [!IMPORTANT]
> Le meilleur cloud est celui que **votre équipe maîtrise**. L'expertise compte plus que les features.

### Facteurs souvent sous-estimés

| Facteur | Impact réel |
|---------|-------------|
| **Compétences existantes** | Courbe d'apprentissage |
| **Recrutement** | Disponibilité des talents |
| **Partenaires/Intégrateurs** | Support externe |
| **Contrats existants** | Négociation commerciale |

---

## 6. La tendance : Convergence

Les trois clouds convergent :
- **AWS** ajoute du PaaS (App Runner = Cloud Run-like)
- **Azure** améliore son expérience développeur
- **GCP** renforce son enterprise sales

---

## Ce qu'il faut retenir

> Maîtriser le cloud aujourd'hui, ce n'est pas **choisir un fournisseur**. C'est comprendre leurs logiques profondes et savoir architecturer au-dessus d'eux.

**Le vrai pouvoir est au niveau de l'architecture, pas du logo.**

| Résumé rapide | AWS | Azure | GCP |
|---------------|-----|-------|-----|
| **En un mot** | Maturité | Enterprise | Innovation |
| **Slogan** | "Le plus complet" | "L'extension de votre IT" | "Built by engineers" |
