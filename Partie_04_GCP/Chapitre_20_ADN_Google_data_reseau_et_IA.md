# Chapitre 20 — ADN Google : data, réseau et IA

## Introduction

GCP n'est pas né comme un business cloud. C'est l'héritier direct de la technologie qui fait tourner Google Search, YouTube et Gmail. Cette origine façonne sa philosophie unique : **data-first**, **network-first**, **AI-first**.

---

## 1. L'héritage Google

### Services internes devenus publics

| Service interne | Produit GCP |
|-----------------|-------------|
| **Borg** (orchestration) | Kubernetes |
| **Colossus** (stockage) | Cloud Storage |
| **Dremel** (analytics) | BigQuery |
| **MapReduce** | Dataflow |
| **Spanner** (BD distribuée) | Cloud Spanner |

### L'échelle Google

| Métrique | Valeur |
|----------|--------|
| Recherches/jour | 8.5+ milliards |
| Vidéos YouTube/jour | 720,000 heures uploadées |
| Utilisateurs Gmail | 1.8+ milliard |

Les technologies GCP sont testées à cette échelle.

---

## 2. Les 4 piliers de l'ADN GCP

### Pilier 1 : Réseau Global Logiciel

GCP possède l'un des réseaux privés les plus avancés du monde.

| Caractéristique | Détail |
|-----------------|--------|
| **VPC Global** | Un VPC couvre le monde entier |
| **Bande passante** | >1 Pbps en interne |
| **Latence** | Prévisible et optimisée |
| **Câbles sous-marins** | Propriété Google |

**Différence clé avec AWS/Azure :**
```
AWS : VPC = Régional (Tokyo ≠ Paris)
GCP : VPC = Global (Tokyo = Paris sur le même réseau)
```

### Pilier 2 : Data-First

Google a révolutionné le traitement des données avec :
- MapReduce → Big Data
- Bigtable → NoSQL
- Dremel → Analytics interactive

**BigQuery** est la traduction cloud de cette expertise.

### Pilier 3 : Kubernetes Natif

Google a inventé Kubernetes en 2014 (projet Borg open-sourcé).

| Aspect | Avantage GCP |
|--------|--------------|
| **GKE** | Référence K8s mondiale |
| **Autopilot** | K8s serverless |
| **Anthos** | K8s partout (multi-cloud) |

### Pilier 4 : IA comme Fondation

| Innovation Google | Impact |
|-------------------|--------|
| **TensorFlow** | Framework ML dominant |
| **TPU** | Chips IA propriétaires |
| **Transformers** | Architecture derrière GPT |
| **Gemini** | LLM concurrent de GPT-4 |

---

## 3. Différences philosophiques

| Aspect | AWS | Azure | GCP |
|--------|-----|-------|-----|
| **Origine** | E-commerce | Enterprise IT | Ingénierie/Data |
| **Public** | Pragmatistes | Entreprises MS | Data Engineers |
| **Force** | Maturité | Hybride | Innovation |
| **Interface** | APIs partout | GUI friendly | CLI/API moderne |

---

## 4. L'écosystème GCP

```
┌────────────────────────────────────────────────┐
│              Google Cloud Platform              │
├────────────┬────────────┬────────────┬─────────┤
│  Compute   │   Data     │    AI      │ Network │
├────────────┼────────────┼────────────┼─────────┤
│ GCE        │ BigQuery   │ Vertex AI  │ VPC     │
│ GKE        │ Dataflow   │ Gemini     │ CDN     │
│ Cloud Run  │ Bigtable   │ Vision     │ LB      │
│ Functions  │ Spanner    │ Speech     │ Direct  │
└────────────┴────────────┴────────────┴─────────┘
```

---

## 5. Pourquoi choisir GCP

### Raison #1 : Big Data et Analytics
BigQuery est le **meilleur service d'analytics cloud** pour de nombreux experts.

### Raison #2 : Kubernetes
GKE reste la référence. Les nouvelles versions K8s arrivent en premier sur GKE.

### Raison #3 : ML/AI
TensorFlow + Vertex AI + TPUs = stack ML complète.

### Raison #4 : Simplicité développeur
Cloud Run, Cloud Functions : expérience développeur très appréciée.

---

## Ce qu'il faut retenir

> GCP est le cloud des **ingénieurs et des data teams**. Si la data et l'IA sont votre priorité, GCP mérite une évaluation sérieuse.

| Critère | GCP excelle |
|---------|-------------|
| Data Warehouse | BigQuery |
| Kubernetes | GKE |
| ML/AI | Vertex AI, TPU |
| Serverless moderne | Cloud Run |

> [!TIP]
> GCP est souvent sous-estimé en entreprise traditionnelle mais adoré par les startups tech et les data teams.
