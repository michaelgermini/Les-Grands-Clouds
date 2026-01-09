# Chapitre 22 — Compute cloud-native (GCE, GKE, Cloud Run)

## Introduction

GCP brille par ses services de compute cloud-native. De la VM classique au serverless conteneurisé, ce chapitre explore les options.

---

## 1. GCE (Compute Engine)

### VMs sur Google Cloud

| Caractéristique | Détail |
|-----------------|--------|
| **Types de machines** | Prédéfinies ou custom |
| **Live Migration** | Maintenance sans reboot |
| **Preemptible/Spot** | Jusqu'à -91% |
| **OS** | Linux, Windows |

### Live Migration

> [!NOTE]
> GCP peut migrer vos VMs d'un hôte à un autre **sans interruption** lors des maintenances. C'est unique à cette échelle.

### Familles de machines

| Famille | Optimisation |
|---------|-------------|
| E2 | Coût optimisé |
| N2 | Général |
| C2 | Compute intensif |
| M2 | Mémoire (jusqu'à 12 To RAM) |
| A2/A3 | GPU (A100, H100) |

---

## 2. GKE (Google Kubernetes Engine)

### Le "Gold Standard" de Kubernetes

| Avantage | Description |
|----------|-------------|
| **Versions** | Premières disponibilités des nouvelles versions K8s |
| **Autopilot** | Mode serverless (Google gère les nodes) |
| **Security** | Shielded nodes, Binary Authorization |
| **Networking** | CNI avancé, Anthos Service Mesh |

### GKE Standard vs Autopilot

| Aspect | Standard | Autopilot |
|--------|----------|-----------|
| Gestion nodes | Vous | Google |
| Facturation | Par node | Par pod |
| Flexibilité | Totale | Encadrée |
| Recommandé pour | Experts K8s | Développeurs |

### Exemple : Créer un cluster GKE Autopilot

```bash
gcloud container clusters create-auto my-cluster \
    --region=europe-west1 \
    --project=my-project
```

---

## 3. Cloud Run

### Le joyau de GCP

Cloud Run est la façon la plus simple de déployer un conteneur en production.

```
Vous : "Voici mon conteneur Docker"
Cloud Run : "Voici votre URL HTTPS, auto-scaled, pay-per-request"
```

### Caractéristiques

| Aspect | Valeur |
|--------|--------|
| **Cold start** | Secondes (vs minutes pour VMs) |
| **Scaling** | 0 à 1000+ instances |
| **Facturation** | À la requête (100ms) |
| **Concurrency** | Jusqu'à 1000 requêtes/instance |

### Exemple de déploiement

```bash
# Build et push l'image
gcloud builds submit --tag gcr.io/PROJECT_ID/my-app

# Déployer sur Cloud Run
gcloud run deploy my-service \
    --image gcr.io/PROJECT_ID/my-app \
    --platform managed \
    --region europe-west1 \
    --allow-unauthenticated
```

### Cloud Run vs Lambda

| Critère | Cloud Run | Lambda |
|---------|-----------|--------|
| **Format** | Conteneur | Function |
| **Durée max** | 60 min | 15 min |
| **Concurrency** | Multi-request | 1 request/instance |
| **Portabilité** | Standard Docker | Propriétaire |

---

## 4. Cloud Functions

### Functions-as-a-Service

| Génération | Caractéristique |
|------------|-----------------|
| Gen 1 | Classique, HTTP/Events |
| Gen 2 | Basé sur Cloud Run, plus puissant |

### Triggers supportés

- HTTP
- Cloud Storage (upload/delete)
- Pub/Sub
- Firestore
- Cloud Scheduler

---

## 5. Arbre de décision Compute GCP

```
Nouvelle Workload
    │
    ├── VM classique/Legacy? → Compute Engine
    │
    ├── Kubernetes requis?
    │   ├── Équipe DevOps → GKE Standard
    │   └── Développeurs → GKE Autopilot
    │
    ├── Conteneur simple? → Cloud Run ⭐
    │
    └── Event-driven simple? → Cloud Functions
```

---

## Ce qu'il faut retenir

> **Cloud Run** est probablement le meilleur service serverless du marché. Commencez par là.

| Service | Quand l'utiliser |
|---------|------------------|
| Compute Engine | Legacy, HPC, contrôle total |
| GKE | Microservices K8s complexes |
| Cloud Run | Conteneurs simples (recommandé) |
| Cloud Functions | Events ponctuels |
