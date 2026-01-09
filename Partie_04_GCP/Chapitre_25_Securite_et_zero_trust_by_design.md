# Chapitre 25 — Sécurité et zero-trust by design

## Introduction

Google a inventé le concept **BeyondCorp** qui a popularisé le Zero Trust. Sur GCP, la sécurité n'est pas une option à activer : elle est intégrée par défaut.

---

## 1. Le modèle Zero Trust

### Principe fondateur

> "Ne faites confiance à aucun réseau, même le réseau interne."

### Différence avec le modèle classique

| Modèle Périmétrique | Modèle Zero Trust |
|---------------------|-------------------|
| Firewall = frontière de confiance | Pas de frontière de confiance |
| Interne = sûr | Tout doit être vérifié |
| VPN pour l'extérieur | Identité + contexte partout |

### BeyondCorp Enterprise

| Composant | Fonction |
|-----------|----------|
| **Identity-Aware Proxy** | Accès basé sur identité |
| **Context-Aware Access** | Vérification continue |
| **Device Trust** | État de l'appareil |

---

## 2. Chiffrement par défaut

### Chiffrement au repos

| Aspect | GCP |
|--------|-----|
| **Par défaut** | Tout est chiffré (AES-256) |
| **Impossible à désactiver** | Sécurité garantie |
| **CMEK** | Clés gérées par vous (optionnel) |
| **CSEK** | Vos propres clés (optionnel) |

### Chiffrement en transit

| Niveau | Protection |
|--------|------------|
| **Externe** | TLS obligatoire |
| **Interne** | ALTS (Application Layer Transport Security) |
| **Entre datacenters** | Chiffré automatiquement |

---

## 3. IAM GCP

### Modèle de permissions

```
Who (Principal)
    │
    ├── User (compte Google)
    ├── Service Account (identité machine)
    └── Group
          │
          ▼
    Role (Collection de permissions)
          │
          ▼
    Resource (projet, bucket, VM...)
```

### Types de rôles

| Type | Exemple |
|------|---------|
| **Basic** | Owner, Editor, Viewer (déconseillés) |
| **Predefined** | roles/storage.objectViewer |
| **Custom** | Créés par vous |

### Exemple de binding

```bash
gcloud projects add-iam-policy-binding my-project \
    --member="user:alice@example.com" \
    --role="roles/bigquery.dataViewer"
```

---

## 4. Organisation et hiérarchie

```
Organization (example.com)
├── Folder: Production
│   ├── Project: prod-app1
│   └── Project: prod-app2
├── Folder: Development
│   └── Project: dev-sandbox
└── Folder: Shared Services
    └── Project: logging
```

### Organization Policies

Contraintes au niveau organisation :

| Policy | Effet |
|--------|-------|
| `constraints/compute.vmExternalIpAccess` | Interdire IPs publiques |
| `constraints/gcp.resourceLocations` | Limiter les régions |
| `constraints/iam.allowedPolicyMemberDomains` | Limiter les domaines |

---

## 5. Security Command Center

### Vue consolidée de la sécurité

| Fonctionnalité | Description |
|----------------|-------------|
| **Asset Discovery** | Inventaire automatique |
| **Vulnerability Scanner** | Détection de failles |
| **Threat Detection** | Menaces en temps réel |
| **Compliance** | CIS benchmarks |

---

## 6. VPC Service Controls

### Périmètre de sécurité pour les données

Empêche l'exfiltration de données même si un attaquant a des credentials valides.

```
┌─────────────────────────────────────┐
│       VPC Service Controls          │
│  ┌─────────────────────────────┐   │
│  │     Périmètre sécurisé      │   │
│  │                             │   │
│  │  BigQuery ◄──► Cloud Storage│   │
│  │                             │   │
│  └─────────────────────────────┘   │
│         ↑                          │
│    Accès autorisé uniquement       │
└─────────────────────────────────────┘
```

---

## 7. Checklist Sécurité GCP

- [ ] Organisation créée et hiérarchie définie
- [ ] Org Policies de base activées
- [ ] Service Accounts avec permissions minimales
- [ ] VPC Service Controls pour données sensibles
- [ ] Security Command Center activé
- [ ] Cloud Audit Logs centralisés
- [ ] MFA sur tous les comptes admin

---

## Ce qu'il faut retenir

> Sur GCP, la sécurité est **by design**. Le chiffrement est obligatoire, pas optionnel.

| Concept | Service GCP |
|---------|-------------|
| Identité | Cloud Identity, IAM |
| Zero Trust | BeyondCorp Enterprise |
| Chiffrement clés | Cloud KMS |
| Posture | Security Command Center |
| Data protection | VPC Service Controls |
