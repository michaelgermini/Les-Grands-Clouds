# Chapitre 21 — Architecture GCP et réseau global

## Introduction

L'architecture réseau de Google est unique parmi les hyperscalers. Le concept de **VPC Global** simplifie drastiquement les architectures mondiales.

---

## 1. Infrastructure mondiale

| Métrique GCP (2024) | Valeur |
|---------------------|--------|
| **Régions** | 40+ |
| **Zones** | 121+ |
| **Points de présence** | 187+ |
| **Pays câblés** | 200+ |

---

## 2. Le VPC Global

### Différence fondamentale

| AWS/Azure | GCP |
|-----------|-----|
| VPC = Régional | **VPC = Global** |
| Subnets dans une région | Subnets dans une région, VPC global |
| Peering pour connecter régions | Tout est déjà connecté |

### Exemple pratique

```
GCP VPC "production"
├── Subnet us-central1 (10.0.0.0/24)
├── Subnet europe-west1 (10.0.1.0/24)
└── Subnet asia-east1 (10.0.2.0/24)

→ Les VMs des 3 subnets se parlent en IP privée nativement
```

### Avantages

| Avantage | Description |
|----------|-------------|
| **Simplicité** | Pas de VPC peering à configurer |
| **Latence** | Réseau privé Google |
| **Sécurité** | Règles firewall globales |

---

## 3. Régions et Zones

### Structure

```
Région (us-central1)
├── Zone a (datacenter)
├── Zone b (datacenter)
├── Zone c (datacenter)
└── Zone f (datacenter)
```

### Régions européennes

| Région | Localisation |
|--------|--------------|
| europe-west1 | Belgique |
| europe-west2 | Londres |
| europe-west3 | Francfort |
| europe-west4 | Pays-Bas |
| europe-west9 | **Paris** |
| europe-north1 | Finlande |

---

## 4. Le réseau privé Google

### Backbone mondial

Google possède l'un des plus grands réseaux privés :
- Câbles sous-marins (Grace Hopper, Dunant, Curie...)
- Interconnexions privées avec ~90% du trafic internet mondial

### Premium vs Standard Tier

| Tier | Routing | Latence | Coût |
|------|---------|---------|------|
| **Premium** | Via réseau Google | Optimale | +++ |
| **Standard** | Via Internet public | Variable | + |

---

## 5. Load Balancing Global

### Un seul load balancer pour le monde

```
Utilisateur Tokyo → Anycast IP → Edge POP Tokyo
Utilisateur Paris → Anycast IP → Edge POP Paris
                         ↓
              Backend le plus proche
```

| Type | Use Case |
|------|----------|
| **HTTP(S) LB** | Applications web |
| **TCP/SSL Proxy** | Autres protocoles |
| **Network LB** | UDP, préservation IP |

---

## 6. Cloud Interconnect

### Connexion dédiée au réseau Google

| Option | Bande passante |
|--------|----------------|
| Dedicated Interconnect | 10-200 Gbps |
| Partner Interconnect | 50 Mbps - 50 Gbps |

---

## Ce qu'il faut retenir

> Le **VPC Global** de GCP est un game-changer pour les architectures mondiales. Ce qui nécessite du peering complexe sur AWS prend 5 minutes sur GCP.

| Concept | Particularité GCP |
|---------|------------------|
| VPC | Global par défaut |
| Load Balancer | Anycast mondial |
| Réseau | Backbone privé Google |
| Simplicité | Moins de configuration |
