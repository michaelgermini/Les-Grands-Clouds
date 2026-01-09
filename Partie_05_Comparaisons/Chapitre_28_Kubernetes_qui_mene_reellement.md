# Chapitre 28 — Kubernetes : qui mène réellement ?

## Introduction

Kubernetes est devenu le standard de facto pour l'orchestration de conteneurs. Les trois hyperscalers proposent des services managés, mais avec des différences significatives.

---

## 1. Rappel : Qu'est-ce que Kubernetes ?

### Origine
- Créé par **Google** en 2014 (basé sur Borg, leur système interne)
- Open-source via la **CNCF** (Cloud Native Computing Foundation)
- Devient le standard de l'industrie

### Fonction
Orchestrer des **conteneurs** à grande échelle :
- Déploiement automatisé
- Scaling horizontal
- Self-healing
- Service discovery

---

## 2. Comparaison des services managés

| Aspect | GKE (Google) | EKS (AWS) | AKS (Azure) |
|--------|--------------|-----------|-------------|
| **Lancement** | 2015 | 2018 | 2018 |
| **Control plane** | Gratuit | $73/mois | Gratuit |
| **Version K8s** | +rapide | Standard | Standard |
| **Expérience** | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ |

---

## 3. GKE (Google Kubernetes Engine)

### Le Gold Standard

| Avantage | Détail |
|----------|--------|
| **Le créateur** | Google a inventé K8s |
| **Versions** | Accès anticipé aux nouvelles versions |
| **Autopilot** | Mode serverless (pas de nodes à gérer) |
| **Security** | Shielded nodes, Binary Authorization |

### GKE Autopilot vs Standard

| Aspect | Standard | Autopilot |
|--------|----------|-----------|
| Gestion nodes | Vous | Google |
| Facturation | Par node | Par pod |
| Recommandé | Experts K8s | Développeurs |

---

## 4. EKS (Amazon Elastic Kubernetes Service)

### Le pragmatique

| Avantage | Détail |
|----------|--------|
| **Intégration AWS** | ALB, IAM, VPC natifs |
| **Fargate** | Pods serverless |
| **Écosystème** | Le plus large |
| **Add-ons** | Marketplace riche |

### Particularités EKS

| Aspect | Détail |
|--------|--------|
| **IRSA** | IAM Roles for Service Accounts |
| **Karpenter** | Autoscaler nouvelle génération |
| **EKS Anywhere** | K8s on-prem avec EKS |

---

## 5. AKS (Azure Kubernetes Service)

### L'accessible

| Avantage | Détail |
|----------|--------|
| **Intégration AD** | RBAC via Entra ID |
| **Dev Tools** | VS Code, Bridge to K8s |
| **Azure Arc** | Multi-cloud K8s |
| **GitOps** | Flux intégré |

### Particularités AKS

| Aspect | Détail |
|--------|--------|
| **Control plane** | Gratuit |
| **Windows containers** | Support natif |
| **Azure Policy** | Gouvernance intégrée |

---

## 6. Anthos vs EKS Anywhere vs Azure Arc

### Solutions multi-cloud / hybride

| Solution | Éditeur | Force |
|----------|---------|-------|
| **Anthos** | Google | Le plus mature |
| **EKS Anywhere** | AWS | Intégration AWS |
| **Azure Arc** | Microsoft | Intégration Azure |

---

## 7. Verdict par cas d'usage

| Situation | Recommandation |
|-----------|----------------|
| Expertise K8s avancée | **GKE** |
| Déjà sur AWS, intégration | **EKS** |
| Entreprise Microsoft | **AKS** |
| Multi-cloud K8s | **Anthos** ou AKS+Arc |
| Débutant K8s | **GKE Autopilot** |

---

## 8. Le futur : Au-delà de Kubernetes

### Tendances

| Tendance | Description |
|----------|-------------|
| **Serverless K8s** | Autopilot, Fargate |
| **GitOps** | ArgoCD, Flux |
| **Service Mesh** | Istio, Envoy |
| **eBPF** | Cilium pour réseau/sécurité |

---

## Ce qu'il faut retenir

> **GKE reste la référence technique**, mais EKS et AKS ont rattrapé leur retard. Le choix dépend plus de votre écosystème cloud que de K8s lui-même.

| Critère | Leader |
|---------|--------|
| Innovation K8s | GKE |
| Écosystème | EKS |
| Enterprise | AKS |
| Multi-cloud | Anthos |

> [!TIP]
> Si Kubernetes est nouveau pour vous, **GKE Autopilot** est le meilleur point de départ.
