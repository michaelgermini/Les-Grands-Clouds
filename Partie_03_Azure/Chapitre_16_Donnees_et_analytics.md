# Chapitre 16 — Données et analytics (SQL Azure, Synapse)

## Introduction

Microsoft vient du monde de la donnée d'entreprise avec SQL Server et Excel. Azure hérite de cet ADN avec une suite complète pour le stockage, le traitement et l'analyse des données.

---

## 1. Panorama des services Data Azure

| Service | Type | Use Case |
|---------|------|----------|
| **Azure SQL Database** | SQL PaaS | Applications OLTP |
| **Azure SQL Managed Instance** | SQL quasi-IaaS | Migration lift & shift |
| **Cosmos DB** | NoSQL multi-modèle | Global, basse latence |
| **Azure Synapse** | Data Warehouse | Analytics à grande échelle |
| **Azure Data Factory** | ETL/ELT | Orchestration de données |
| **Azure Databricks** | Spark managé | Data Engineering, ML |

---

## 2. Azure SQL Database

### SQL Server en mode PaaS

| Aspect | Détail |
|--------|--------|
| **Moteur** | SQL Server |
| **Compatibilité** | Presque 100% avec SQL Server |
| **Scaling** | DTU ou vCore |
| **HA** | Multi-AZ automatique |
| **Backups** | Automatiques (7-35 jours) |

### Modèles de tarification

| Modèle | Description |
|--------|-------------|
| **DTU** | Bundles simplifiés (CPU+IO+Mémoire) |
| **vCore** | Contrôle granulaire des ressources |
| **Serverless** | Pause automatique si inactif |
| **Hyperscale** | Jusqu'à 100 To, scaling instantané |

### Exemple de connexion

```csharp
using Microsoft.Data.SqlClient;

var connectionString = "Server=myserver.database.windows.net;Database=mydb;...";
using var connection = new SqlConnection(connectionString);
await connection.OpenAsync();

var command = new SqlCommand("SELECT * FROM Users", connection);
var reader = await command.ExecuteReaderAsync();
```

---

## 3. Azure Cosmos DB

### Base NoSQL distribuée globalement

| Caractéristique | Valeur |
|-----------------|--------|
| **Latence** | < 10ms (P99) en lecture/écriture |
| **Distribution** | Multi-région active-active |
| **Modèles** | Document, Key-Value, Graph, Column |
| **Consistance** | 5 niveaux configurables |

### APIs supportées

| API | Compatibilité |
|-----|---------------|
| **NoSQL (natif)** | API Cosmos native |
| **MongoDB** | Applications MongoDB existantes |
| **Cassandra** | Applications Cassandra |
| **Gremlin** | Graphes |
| **Table** | Azure Table Storage |

---

## 4. Azure Synapse Analytics

### La plateforme analytics unifiée

```
┌─────────────────────────────────────────────────────┐
│                  Azure Synapse                       │
├─────────────────┬────────────────┬──────────────────┤
│ SQL Pool        │ Spark Pool     │ Data Explorer    │
│ (Data Warehouse)│ (Big Data)     │ (Time Series)    │
├─────────────────┴────────────────┴──────────────────┤
│              Synapse Studio (Interface unifiée)      │
├─────────────────────────────────────────────────────┤
│              Data Lake Storage Gen2                  │
└─────────────────────────────────────────────────────┘
```

### Capacités

| Composant | Fonction |
|-----------|----------|
| **Dedicated SQL Pool** | Data Warehouse MPP |
| **Serverless SQL Pool** | Query on-demand sur Data Lake |
| **Spark Pool** | Traitement Big Data |
| **Pipelines** | Orchestration ETL (Data Factory intégré) |

### Exemple : Query sur Data Lake

```sql
-- Requête SQL sur fichiers Parquet dans le Data Lake
SELECT 
    Year, 
    COUNT(*) as TotalSales
FROM OPENROWSET(
    BULK 'https://datalake.blob.core.windows.net/sales/*.parquet',
    FORMAT = 'PARQUET'
) AS sales
GROUP BY Year
ORDER BY Year;
```

---

## 5. Microsoft Fabric

### La nouvelle plateforme SaaS Data

Fabric unifie tous les services data dans une expérience "Office-like" :
- Data Factory
- Data Engineering (Spark)
- Data Warehouse
- Data Science
- Real-Time Analytics
- Power BI

| Avantage | Description |
|----------|-------------|
| **OneLake** | Un seul Data Lake pour tout |
| **Simplicité** | Interface unifiée |
| **Licence** | Capacity-based (comme Power BI Premium) |

---

## 6. Azure Data Factory

### Orchestration ETL/ELT

| Composant | Fonction |
|-----------|----------|
| **Pipelines** | Workflows d'intégration |
| **Datasets** | Définition des sources/destinations |
| **Activities** | Transformations, copies, scripts |
| **Triggers** | Planification, événements |

### Connecteurs

90+ connecteurs : SQL Server, Oracle, SAP, Salesforce, REST APIs...

---

## 7. Arbre de décision Data

```
Besoin Data
    │
    ├── Application transactionnelle SQL? → Azure SQL Database
    │
    ├── Migration SQL Server? → SQL Managed Instance
    │
    ├── NoSQL global, basse latence? → Cosmos DB
    │
    ├── Analytics à grande échelle?
    │   ├── Entreprise traditionnelle → Synapse
    │   └── Modern Data Stack → Databricks ou Fabric
    │
    └── ETL/Orchestration? → Data Factory
```

---

## Ce qu'il faut retenir

> L'écosystème Data Azure est **le plus naturel pour les entreprises SQL Server existantes**.

| Besoin | Service |
|--------|---------|
| SQL transactionnel | Azure SQL Database |
| NoSQL distribué | Cosmos DB |
| Data Warehouse | Synapse ou Fabric |
| ETL | Data Factory |
| Analytics self-service | Power BI |
