# Chapitre 26 — Forces, limites et cas d'usage typiques

## Introduction

GCP est le 3ème hyperscaler mais brille dans des domaines spécifiques. Ce chapitre dresse un bilan objectif pour guider vos décisions.

---

## 1. Les Forces de GCP

### Force #1 : Data et Analytics

| Service | Avantage |
|---------|----------|
| **BigQuery** | Meilleur DW serverless |
| **Dataflow** | Stream+Batch unifié |
| **Looker** | BI moderne |

### Force #2 : Kubernetes

| Aspect | GCP Leader |
|--------|------------|
| **Inventeur** | Google a créé K8s |
| **GKE** | Référence mondiale |
| **Autopilot** | K8s vraiment serverless |
| **Anthos** | Multi-cloud K8s |

### Force #3 : IA et ML

| Innovation | Description |
|------------|-------------|
| **TPU** | Chips IA propriétaires |
| **TensorFlow** | Framework dominant |
| **Gemini** | LLM compétitif |
| **Vertex AI** | Plateforme ML unifiée |

### Force #4 : Expérience développeur

| Produit | Appréciation |
|---------|--------------|
| **Cloud Run** | Serverless adoré |
| **gcloud CLI** | CLI intuitive |
| **Documentation** | Claire et moderne |
| **Pricing** | Souvent plus simple |

### Force #5 : Réseau

| Caractéristique | Unique |
|-----------------|--------|
| **VPC Global** | Simplification massive |
| **Backbone** | Réseau Google mondial |
| **Premium Tier** | Performance garantie |

---

## 2. Les Limites de GCP

### Limite #1 : Part de marché

| Cloud | Part |
|-------|------|
| AWS | 32% |
| Azure | 23% |
| **GCP** | **11%** |

**Conséquence :** Moins de talents disponibles sur le marché.

### Limite #2 : Enterprise

| Aspect | Perception |
|--------|------------|
| **Support** | Historiquement moins "customer obsessed" |
| **Commercial** | Moins d'account managers |
| **Écosystème partenaires** | Plus petit |

### Limite #3 : Fermeture de services

> [!WARNING]
> Google a une réputation de fermer des services (Google Reader, Stadia...). Même si GCP est différent, la perception persiste.

### Limite #4 : Intégration Enterprise

| Besoin | GCP vs Concurrents |
|--------|-------------------|
| Active Directory | Moins intégré qu'Azure |
| SAP | Moins certifié qu'Azure |
| Migration legacy | Moins d'outils qu'AWS |

---

## 3. Cas d'usage typiques

### Cas #1 : Startups tech / SaaS

| Avantage | Détail |
|----------|--------|
| BigQuery gratuit | 1 To/mois |
| Cloud Run | Scale to zero |
| Pricing simple | Pas de surprises |

### Cas #2 : Data-intensive applications

- Data Lakes
- Analytics à grande échelle
- ML pipelines

### Cas #3 : Applications cloud-native

- Microservices sur GKE
- Serverless sur Cloud Run
- Event-driven sur Cloud Functions

### Cas #4 : Multi-cloud Kubernetes

Anthos permet de gérer des clusters K8s sur GCP, AWS, Azure et on-prem avec les mêmes outils.

---

## 4. Quand NE PAS choisir GCP

| Situation | Alternative |
|-----------|-------------|
| Entreprise Microsoft-centric | Azure |
| Besoin GPT-4 exclusif | Azure OpenAI |
| Migration lift & shift massive | AWS |
| Écosystème partenaires critique | AWS |

---

## 5. Comparaison synthétique

| Critère | GCP | AWS | Azure |
|---------|-----|-----|-------|
| **Data/Analytics** | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ |
| **Kubernetes** | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ |
| **ML/AI** | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ |
| **Serverless** | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ |
| **Enterprise** | ⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| **Maturité** | ⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ |

---

## 6. Checklist avant de choisir GCP

- [ ] La Data/Analytics est-elle ma priorité ?
- [ ] Mon équipe a-t-elle une culture DevOps/Kubernetes ?
- [ ] Ai-je besoin de BigQuery ou équivalent ?
- [ ] Suis-je prêt à former mon équipe sur un cloud moins répandu ?
- [ ] Le support enterprise est-il critique ?

**Si 3+ oui aux 4 premières → GCP mérite une évaluation sérieuse.**

---

## Ce qu'il faut retenir

> GCP est le cloud des **ingénieurs, des data teams et des startups tech**. Si BigQuery, GKE ou Cloud Run correspondent à vos besoins, c'est souvent le meilleur choix.

| Profil | Recommandation |
|--------|----------------|
| Data team | ✅ GCP (BigQuery) |
| Startup cloud-native | ✅ GCP (Cloud Run) |
| Enterprise traditionnelle | ⚠️ Évaluer Azure/AWS |
| Migration legacy | ⚠️ AWS souvent meilleur |
