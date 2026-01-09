# Chapitre 18 — Identité et sécurité (Entra ID, Defender)

## Introduction

L'identité est au cœur de la stratégie Microsoft. **Entra ID** (ex-Azure AD) est le service d'identité le plus utilisé au monde, gérant l'accès à Azure, Microsoft 365 et des milliers d'applications SaaS.

---

## 1. Microsoft Entra ID

### Le Directory mondial

| Métrique | Valeur |
|----------|--------|
| **Utilisateurs gérés** | 1+ milliard |
| **Connexions/jour** | 50+ milliards |
| **Applications SSO** | 3000+ intégrées |

### Fonctionnalités clés

| Fonctionnalité | Description |
|----------------|-------------|
| **SSO** | Single Sign-On pour toutes les apps |
| **MFA** | Authentification multi-facteurs |
| **Conditional Access** | Règles d'accès contextuelles |
| **B2B** | Collaboration avec partenaires externes |
| **B2C** | Identité pour vos clients |

### Architecture hybride

```
Active Directory On-Prem
         │
         │ Entra ID Connect (sync)
         ▼
    Entra ID Cloud
         │
    ┌────┴────┬────────┬────────┐
    │         │        │        │
  Azure    M365    SaaS    Vos Apps
```

---

## 2. Conditional Access

### Le moteur de règles de sécurité

```
IF [Utilisateur dans groupe "Direction"]
AND [Appareil non géré]
AND [Localisation hors France]
THEN [Bloquer l'accès]
ELSE [OK avec MFA]
```

### Signaux évalués

| Signal | Exemple |
|--------|---------|
| **User/Group** | Administrateurs, Direction |
| **Location** | Pays, IP connues |
| **Device** | Compliant, Azure AD joined |
| **Application** | SharePoint, Azure Portal |
| **Risk** | Détection de compromission |

### Exemple de policy

| Condition | Valeur |
|-----------|--------|
| Users | Tous |
| Apps | Azure Portal |
| Conditions | Hors réseau corporate |
| Access | Autoriser avec MFA |

---

## 3. Microsoft Defender for Cloud

### CSPM + Threat Detection

| Composant | Fonction |
|-----------|----------|
| **Secure Score** | Score de posture (0-100%) |
| **Recommendations** | Actions à mener |
| **Workload Protection** | Protection runtime (VMs, containers) |
| **Multi-cloud** | Étend à AWS et GCP |

### Secure Score

```
┌─────────────────────────────────────────┐
│ Votre Secure Score : 67/100             │
├─────────────────────────────────────────┤
│ ⚠ Activer MFA sur tous les admins (-5) │
│ ⚠ Chiffrer les VMs (-3)                │
│ ⚠ Configurer les alertes (-2)          │
└─────────────────────────────────────────┘
```

### Defender pour différents workloads

| Plan | Protection |
|------|------------|
| Defender for Servers | VMs, anti-malware |
| Defender for Containers | AKS, registries |
| Defender for SQL | Bases de données |
| Defender for Storage | Données sensibles |
| Defender for App Service | Applications web |

---

## 4. Azure Key Vault

### Gestion des secrets centralisée

| Type de secret | Exemple |
|----------------|---------|
| **Secrets** | Mots de passe, connection strings |
| **Keys** | Clés de chiffrement |
| **Certificates** | Certificats SSL/TLS |

### Intégration avec les services

```python
from azure.identity import DefaultAzureCredential
from azure.keyvault.secrets import SecretClient

credential = DefaultAzureCredential()
client = SecretClient(vault_url="https://myvault.vault.azure.net/", credential=credential)

secret = client.get_secret("database-password")
password = secret.value
```

---

## 5. Microsoft Sentinel

### SIEM/SOAR cloud-native

| Composant | Fonction |
|-----------|----------|
| **Collect** | Logs de partout (Azure, M365, on-prem) |
| **Detect** | Règles analytics, ML |
| **Investigate** | Workbooks, hunting queries |
| **Respond** | Playbooks d'automatisation (Logic Apps) |

### Sources de données

- Azure Activity Logs
- Microsoft 365 audit logs
- Azure AD sign-in logs
- Firewall logs
- Threat Intelligence feeds

---

## 6. Checklist Sécurité Azure

- [ ] Entra ID : MFA activé pour tous les admins
- [ ] Conditional Access : Policies de base en place
- [ ] Defender for Cloud : Activé, score > 70%
- [ ] Key Vault : Pas de secrets dans le code
- [ ] Azure Policy : Guardrails de conformité
- [ ] Locks : Ressources critiques protégées
- [ ] Sentinel : Si budget et maturité suffisants

---

## Ce qu'il faut retenir

> **Entra ID** est le centre de gravité de la sécurité Microsoft. Toute stratégie Azure commence par l'identité.

| Besoin | Service |
|--------|---------|
| Identité | Entra ID |
| Accès conditionnel | Conditional Access |
| Posture sécurité | Defender for Cloud |
| Secrets | Key Vault |
| SIEM | Sentinel |

> [!TIP]
> Activez **Security Defaults** dans Entra ID si vous débutez. C'est une baseline gratuite qui couvre 80% des besoins.
