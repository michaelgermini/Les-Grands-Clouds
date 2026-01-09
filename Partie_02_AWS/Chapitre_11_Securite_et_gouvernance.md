# Chapitre 11 — Sécurité et gouvernance (IAM, Organizations)

## Introduction

La sécurité est la priorité #0 ("Job Zero") chez AWS. Contrairement à la croyance populaire, le cloud n'est pas automatiquement sécurisé : c'est un modèle de **responsabilité partagée**. Ce chapitre explore les outils fondamentaux pour sécuriser et gouverner votre environnement AWS.

---

## 1. Le Modèle de Responsabilité Partagée

| Responsabilité AWS | Votre Responsabilité |
|-------------------|---------------------|
| Sécurité physique des datacenters | Configuration des Security Groups |
| Hardware, réseau | Gestion des accès IAM |
| Hyperviseur | Chiffrement de vos données |
| Services managés (patching RDS) | Patching de vos EC2 |

> [!IMPORTANT]
> AWS sécurise le cloud. Vous sécurisez ce que vous METTEZ dans le cloud.

---

## 2. AWS IAM (Identity and Access Management)

### Les briques fondamentales

| Concept | Description |
|---------|-------------|
| **User** | Identité humaine avec credentials |
| **Group** | Collection d'users (ex: "Developers") |
| **Role** | Identité assumable (services, cross-account) |
| **Policy** | Document JSON définissant les permissions |

### Exemple de Policy IAM

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "s3:GetObject",
        "s3:PutObject"
      ],
      "Resource": "arn:aws:s3:::mon-bucket/*"
    },
    {
      "Effect": "Deny",
      "Action": "s3:DeleteObject",
      "Resource": "*"
    }
  ]
}
```

### Principe du Moindre Privilège

> [!CAUTION]
> Ne donnez JAMAIS `AdministratorAccess` sauf nécessité absolue. Accordez uniquement les permissions requises pour la tâche.

### IAM Roles pour les services

```
EC2 Instance --> IAM Role --> S3 Access
```

Les Roles permettent aux services AWS d'accéder à d'autres services sans stocker de credentials.

---

## 3. AWS Organizations

### Gestion multi-comptes

| Concept | Description |
|---------|-------------|
| **Organization** | Conteneur racine |
| **OU (Organizational Unit)** | Dossier de comptes |
| **Account** | Compte AWS isolé |
| **SCP (Service Control Policy)** | Garde-fous au niveau org |

### Architecture typique

```
Organization Root
├── Management Account
├── OU: Production
│   ├── Prod-App1
│   └── Prod-App2
├── OU: Development
│   ├── Dev-Team1
│   └── Dev-Team2
└── OU: Security
    ├── Log Archive
    └── Security Tooling
```

### Service Control Policies (SCP)

Les SCPs définissent les permissions MAXIMALES pour une OU ou un compte.

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Deny",
      "Action": "ec2:RunInstances",
      "Resource": "*",
      "Condition": {
        "StringNotEquals": {
          "aws:RequestedRegion": ["eu-west-1", "eu-west-3"]
        }
      }
    }
  ]
}
```
*Cette SCP interdit de lancer des instances hors d'Europe.*

---

## 4. Audit et Traçabilité

### AWS CloudTrail
L'audit log de toutes les actions API.

| Aspect | Détail |
|--------|--------|
| **Quoi** | Chaque appel API AWS |
| **Qui** | User/Role qui a fait l'action |
| **Quand** | Timestamp précis |
| **Où** | Région, IP source |

### AWS Config
L'historique de la configuration de vos ressources.

- "À quoi ressemblait mon Security Group hier à 14h ?"
- "Qui a modifié cette règle ?"
- Règles de conformité automatiques

### Amazon GuardDuty
Détection de menaces intelligente (ML-based) :
- Accès depuis des IPs malveillantes
- Comportements anormaux
- Compromission de credentials

---

## 5. Chiffrement

### Chiffrement au repos

| Service | Chiffrement par défaut |
|---------|----------------------|
| S3 | SSE-S3 (AES-256) |
| EBS | Optionnel (recommandé) |
| RDS | Optionnel (recommandé) |

### AWS KMS (Key Management Service)
Gestion centralisée des clés de chiffrement.

| Type de clé | Gestion |
|-------------|---------|
| **AWS Managed** | AWS gère tout |
| **Customer Managed** | Vous contrôlez la rotation |
| **Customer Provided** | Vous apportez vos clés |

---

## 6. Checklist Sécurité AWS

- [ ] MFA activé sur le compte root et tous les admins
- [ ] Pas de credentials dans le code (utiliser Roles)
- [ ] Least privilege sur toutes les policies
- [ ] CloudTrail activé dans toutes les régions
- [ ] GuardDuty activé
- [ ] Security Groups : principe de deny par défaut
- [ ] Chiffrement activé sur S3, EBS, RDS
- [ ] Rotation automatique des secrets (Secrets Manager)

---

## Ce qu'il faut retenir

> La sécurité AWS est un **process continu**, pas un état final.

| Outil | Fonction |
|-------|----------|
| **IAM** | Qui peut faire quoi |
| **Organizations** | Gouvernance multi-comptes |
| **CloudTrail** | Audit log |
| **GuardDuty** | Détection de menaces |
| **KMS** | Chiffrement |

> [!TIP]
> Utilisez AWS Security Hub pour avoir une vue consolidée de votre posture de sécurité.
