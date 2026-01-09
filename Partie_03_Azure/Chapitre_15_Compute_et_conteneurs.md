# Chapitre 15 — Compute et conteneurs (VMs, AKS)

## Introduction

Azure offre une gamme complète d'options de calcul, de la VM Windows classique au Kubernetes entièrement managé. Ce chapitre vous guide dans le choix du bon service.

---

## 1. Azure Virtual Machines

### Familles de VMs

| Série | Optimisation | Use Case |
|-------|-------------|----------|
| **B** | Burst | Dev/Test, petites apps |
| **D/Ds** | Général | Applications standard |
| **E** | Mémoire | Bases de données, SAP |
| **F** | Compute | Calcul intensif |
| **N** | GPU | ML, rendu graphique |
| **L** | Stockage | Big Data, NoSQL |

### Azure Hybrid Benefit

> [!TIP]
> Si vous avez des licences Windows Server ou SQL Server avec Software Assurance, réutilisez-les sur Azure pour économiser ~40%.

### Scale Sets
Groupes de VMs identiques avec auto-scaling automatique.

```
Load Balancer
     │
     ├── VM Instance 1
     ├── VM Instance 2
     ├── VM Instance 3
     └── ... (auto-scale)
```

---

## 2. Azure Kubernetes Service (AKS)

### Kubernetes managé par Azure

| Composant | Gestion |
|-----------|---------|
| Control Plane | **Azure** (gratuit) |
| Worker Nodes | **Vous** ou Azure (auto) |
| Networking | Intégré VNet Azure |
| Identité | Entra ID intégré |

### Avantages AKS

| Avantage | Description |
|----------|-------------|
| **Intégration AD** | RBAC via Entra ID |
| **Dev Tools** | VS Code, Bridge to K8s |
| **Scaling** | Cluster Autoscaler, KEDA |
| **Observabilité** | Azure Monitor, Container Insights |

### Exemple : Déploiement AKS

```bash
# Créer un cluster AKS
az aks create \
    --resource-group myResourceGroup \
    --name myAKSCluster \
    --node-count 3 \
    --enable-managed-identity \
    --generate-ssh-keys

# Connecter kubectl
az aks get-credentials --resource-group myResourceGroup --name myAKSCluster

# Déployer
kubectl apply -f deployment.yaml
```

---

## 3. Azure App Service

### Le PaaS pour applications web

| Aspect | Détail |
|--------|--------|
| **Langages** | .NET, Java, Node.js, Python, PHP |
| **Auto-scaling** | Intégré |
| **SSL** | Certificats gratuits |
| **Déploiement** | GitHub Actions, Azure DevOps |
| **Slots** | Blue/Green deployment natif |

### Quand utiliser App Service vs AKS

| Critère | App Service | AKS |
|---------|-------------|-----|
| **Simplicité** | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ |
| **Contrôle** | ⭐⭐⭐ | ⭐⭐⭐⭐⭐ |
| **Portabilité** | ⭐⭐ | ⭐⭐⭐⭐⭐ |
| **Équipe requise** | Dev | DevOps |

---

## 4. Azure Container Instances (ACI)

### Conteneurs serverless
Exécutez un conteneur sans gérer de serveur ou de cluster.

```bash
az container create \
    --resource-group myGroup \
    --name mycontainer \
    --image mcr.microsoft.com/azuredocs/aci-helloworld \
    --dns-name-label myapp \
    --ports 80
```

| Avantage | Limitation |
|----------|-----------|
| Démarrage rapide | Pas d'orchestration |
| Pas de gestion | Scaling manuel |
| Facturation à la seconde | Pas de volumes persistants avancés |

---

## 5. Azure Functions

### Serverless event-driven

| Trigger | Description |
|---------|-------------|
| HTTP | API REST |
| Timer | Cron jobs |
| Blob | Upload S3-like |
| Queue | Messages |
| Event Grid | Événements Azure |

### Exemple C#

```csharp
[FunctionName("HelloWorld")]
public static async Task<IActionResult> Run(
    [HttpTrigger(AuthorizationLevel.Function, "get")] HttpRequest req,
    ILogger log)
{
    log.LogInformation("C# HTTP trigger function processed a request.");
    return new OkObjectResult("Hello, Azure Functions!");
}
```

---

## 6. Arbre de décision

```
Nouvelle Workload
    │
    ├── VM Windows Legacy? → Azure VMs
    │
    ├── Web App simple? → App Service
    │
    ├── Conteneurs complexes?
    │   ├── Orchestration K8s → AKS
    │   └── Conteneur unique → ACI
    │
    └── Event-driven? → Azure Functions
```

---

## Ce qu'il faut retenir

> Pour les entreprises Microsoft, **App Service** est souvent le meilleur point de départ. AKS est pour les équipes DevOps matures.

| Service | Public |
|---------|--------|
| VMs | Migration, Legacy |
| App Service | Développeurs web |
| AKS | DevOps, Microservices |
| Functions | Event-driven, API |
