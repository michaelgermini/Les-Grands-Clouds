# Chapitre 14 — Architecture Azure et régions

## Introduction

Microsoft possède plus de régions cloud que n'importe quel autre fournisseur. Cette couverture géographique massive est un avantage stratégique pour la conformité et la latence. Ce chapitre explore l'architecture mondiale d'Azure.

---

## 1. Vue d'ensemble

| Métrique Azure (2024) | Valeur |
|----------------------|--------|
| **Régions** | 60+ |
| **Pays** | 140+ |
| **Datacenters** | 200+ |
| **Edge sites** | 190+ |

### Comparaison couverture géographique

| Cloud | Régions |
|-------|---------|
| Azure | 60+ |
| AWS | 33+ |
| GCP | 40+ |

Azure est présent dans des pays où les autres ne sont pas (Afrique du Sud, Moyen-Orient, etc.).

---

## 2. Concept de Région Azure

### Définition
Une région Azure est un ensemble de datacenters déployés dans une zone géographique définie.

### Régions françaises et européennes

| Région | Localisation | Code |
|--------|--------------|------|
| **France Central** | Paris | francecentral |
| **France South** | Marseille | francesouth |
| **West Europe** | Pays-Bas | westeurope |
| **North Europe** | Irlande | northeurope |
| **Germany West Central** | Francfort | germanywestcentral |

---

## 3. Region Pairs (Paires de régions)

### Concept unique à Azure
Chaque région Azure est jumelée avec une autre région dans la même géographie.

| Région primaire | Région paire |
|-----------------|--------------|
| France Central | France South |
| West Europe | North Europe |
| East US | West US |

### Avantages du pairing

| Avantage | Description |
|----------|-------------|
| **Mises à jour** | Jamais simultanées sur les deux régions |
| **DR par défaut** | GRS réplique vers la paire |
| **Récupération** | Priorité de restauration en cas de panne |

---

## 4. Zones de Disponibilité (Availability Zones)

### Architecture

```
┌─────────────── Région France Central ───────────────┐
│                                                      │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐          │
│  │  Zone 1  │  │  Zone 2  │  │  Zone 3  │          │
│  │    DC    │  │    DC    │  │    DC    │          │
│  └──────────┘  └──────────┘  └──────────┘          │
│       │              │              │               │
│       └──────────────┼──────────────┘               │
│                      │                              │
│              Réseau < 2ms                           │
└─────────────────────────────────────────────────────┘
```

### Caractéristiques

| Aspect | Détail |
|--------|--------|
| **Distance** | Physiquement séparées (km) |
| **Alimentation** | Indépendante |
| **Réseau** | Fibre dédiée < 2ms |
| **SLA** | 99.99% en Multi-Zone |

> [!NOTE]
> Historiquement, certaines régions Azure n'avaient pas d'AZs. Microsoft les ajoute progressivement.

---

## 5. Availability Sets (Ensembles de disponibilité)

Pour les régions sans AZs, les **Availability Sets** répartissent les VMs sur différents racks.

| Concept | Description |
|---------|-------------|
| **Fault Domain** | Rack physique (alimentation, réseau) |
| **Update Domain** | Groupe de MAJ simultanées |

---

## 6. Réseau Microsoft Global

### Le backbone Azure
Microsoft possède l'un des plus grands réseaux privés du monde.

| Composant | Description |
|-----------|-------------|
| Câbles sous-marins | Propriété Microsoft |
| Points de peering | 190+ sites |
| Latence | Optimisée via anycast |

### ExpressRoute
Connexion privée dédiée entre votre datacenter et Azure (pas par Internet).

| Option | Bande passante |
|--------|---------------|
| ExpressRoute Direct | Jusqu'à 100 Gbps |
| ExpressRoute standard | 50 Mbps - 10 Gbps |

---

## 7. Services par région

> [!WARNING]
> Tous les services Azure ne sont pas disponibles dans toutes les régions. Vérifiez toujours avant de déployer.

Utilisez [Azure Products by Region](https://azure.microsoft.com/regions/services/) pour vérifier.

---

## Ce qu'il faut retenir

> La couverture géographique Azure est son **avantage compétitif** pour les entreprises mondiales et les exigences de souveraineté.

| Concept | Usage |
|---------|-------|
| **Région** | Choix basé sur latence/conformité |
| **Region Pair** | DR automatique |
| **Availability Zone** | Haute dispo intra-région |
| **ExpressRoute** | Connexion privée entreprise |
