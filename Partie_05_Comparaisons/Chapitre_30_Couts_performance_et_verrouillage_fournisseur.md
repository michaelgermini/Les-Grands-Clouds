# Chapitre 30 — Coûts, performance et verrouillage fournisseur

## Introduction

"Quel cloud est le moins cher ?" est la mauvaise question. La bonne question est : "Quel cloud est le plus rentable pour **mon** use case ?" Ce chapitre démystifie les coûts et le lock-in.

---

## 1. Le mythe du "moins cher"

### Pourquoi la comparaison est difficile

| Raison | Exemple |
|--------|---------|
| **Tarification différente** | AWS par heure, GCP par seconde |
| **Remises différentes** | RI vs CUD vs Savings Plans |
| **Services différents** | Lambda vs Cloud Run = pas comparable |
| **Trafic réseau** | Egress fees varient énormément |

### Benchmarks généraux (approximatifs)

| Service | Le moins cher (souvent) |
|---------|------------------------|
| Compute (VMs) | GCP |
| Stockage objet | AWS ou Azure |
| Data Warehouse | GCP (BigQuery) |
| Egress | GCP |
| Spot/Preemptible | AWS |

---

## 2. Les pièges de coûts par cloud

### AWS

| Piège | Coût caché |
|-------|------------|
| NAT Gateway | ~$45/mois par gateway |
| Egress | $0.09/Go |
| EBS non supprimés | Facturation continue |
| Cross-AZ traffic | $0.01/Go |

### Azure

| Piège | Coût caché |
|-------|------------|
| Bandwidth | Variable selon régions |
| Disques Premium | Plus cher qu'AWS |
| Log Analytics | Peut exploser |

### GCP

| Piège | Coût caché |
|-------|------------|
| Premium Network Tier | Par défaut, plus cher |
| Sustained discounts | Moins prévisible que RIs |
| Support | Payant dès le début |

---

## 3. Stratégies d'optimisation

### Committed Use (toutes plateformes)

| Type | Cloud | Économie |
|------|-------|----------|
| Reserved Instances | AWS | 30-72% |
| Savings Plans | AWS | 30-72% |
| Reserved VMs | Azure | 30-72% |
| Committed Use Discounts | GCP | 30-57% |

### Spot/Preemptible

| Cloud | Nom | Économie |
|-------|-----|----------|
| AWS | Spot Instances | Jusqu'à 90% |
| Azure | Spot VMs | Jusqu'à 90% |
| GCP | Spot VMs | Jusqu'à 91% |

### Autres optimisations

| Stratégie | Impact |
|-----------|--------|
| Right-sizing | 20-40% |
| Arrêt dev/test la nuit | 65% |
| Serverless | Variable (peut être + ou -) |
| Graviton/ARM (AWS) | 20-40% |

---

## 4. Le Vendor Lock-in

### Types de verrouillage

| Type | Exemple | Gravité |
|------|---------|---------|
| **API Lock-in** | Lambda, DynamoDB | Moyen |
| **Data Lock-in** | Egress fees | **Élevé** |
| **Skills Lock-in** | Équipe formée sur 1 cloud | Moyen |

### Coût réel de la migration

| Volume de données | Coût egress (AWS) |
|-------------------|-------------------|
| 1 To | ~$90 |
| 100 To | ~$9,000 |
| 1 Po | ~$90,000 |

### Stratégies anti-lock-in

| Stratégie | Efficacité | Coût |
|-----------|------------|------|
| Kubernetes partout | Moyenne | Élevé |
| Formats ouverts (Parquet) | **Élevée** | Faible |
| Abstraction Terraform | Moyenne | Moyen |
| Multi-cloud | Faible | **Très élevé** |

---

## 5. Conseil pragmatique

> [!IMPORTANT]
> **Acceptez le lock-in API** (vous gagnez en productivité).
> **Évitez le lock-in Data** (formats ouverts, réplication).

### Matrice de décision

| Aspect | Accepter le lock-in | Éviter le lock-in |
|--------|---------------------|-------------------|
| APIs/Functions | ✅ Oui | Trop coûteux |
| Données | 🔶 Partiellement | Formats ouverts |
| Kubernetes | ✅ Oui (portable) | Non nécessaire |
| IA/ML | 🔶 Modèles standards | Éviter modèles propriétaires |

---

## 6. Outils FinOps

| Outil | Type |
|-------|------|
| AWS Cost Explorer | Natif AWS |
| Azure Cost Management | Natif Azure |
| GCP Cost Management | Natif GCP |
| **CloudHealth** | Multi-cloud |
| **Spot.io** | Optimisation Spot |
| **Kubecost** | Coûts Kubernetes |

---

## Ce qu'il faut retenir

> Il n'y a pas de cloud "moins cher". Il y a le cloud le **plus rentable pour votre workload**.

| Principe | Application |
|----------|-------------|
| Benchmark votre workload | Pas de généralisation |
| Budgétez les coûts cachés | Egress, NAT, support |
| Utilisez les commitments | 30-70% d'économie |
| Formats ouverts | Protection contre le lock-in data |
