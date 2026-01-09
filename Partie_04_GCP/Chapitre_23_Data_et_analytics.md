# Chapitre 23 — Data & analytics (BigQuery, Dataflow)

## Introduction

Si la Data est votre priorité, GCP est souvent le choix n°1. **BigQuery** a révolutionné le Data Warehousing en étant le premier entrepôt serverless capable de requêter des pétaoctets en secondes.

---

## 1. BigQuery : Le Data Warehouse Serverless

### Caractéristiques uniques

| Aspect | Valeur |
|--------|--------|
| **Architecture** | Serverless (pas de cluster à gérer) |
| **Stockage** | Séparé du compute |
| **Performance** | Pétaoctets en secondes |
| **Format** | Columnar (Capacitor) |
| **Pricing** | À la requête ou flat-rate |

### Différence avec les DW traditionnels

| DW Classique | BigQuery |
|--------------|----------|
| Provisionner un cluster | Rien à provisionner |
| Scaling manuel | Auto-scaling automatique |
| Payer 24/7 | Payer à l'usage |
| Tuning nécessaire | Optimisé automatiquement |

### Exemple de requête

```sql
-- Requête sur 1 To de données en quelques secondes
SELECT
    country,
    COUNT(*) as total_users,
    AVG(session_duration) as avg_duration
FROM `project.dataset.user_sessions`
WHERE date BETWEEN '2024-01-01' AND '2024-12-31'
GROUP BY country
ORDER BY total_users DESC
LIMIT 100;
```

### Modèles de tarification

| Modèle | Description | Meilleur pour |
|--------|-------------|---------------|
| **On-demand** | $6.25/To analysé | Workloads variables |
| **Flat-rate** | Slots réservés | Usage prévisible élevé |
| **Editions** | Standard/Enterprise/Enterprise+ | Fonctionnalités avancées |

### BigQuery ML

Entraînez des modèles ML directement en SQL !

```sql
CREATE OR REPLACE MODEL `project.dataset.churn_model`
OPTIONS(model_type='logistic_reg') AS
SELECT
    * EXCEPT(churned),
    churned AS label
FROM `project.dataset.customers`;

-- Prédiction
SELECT * FROM ML.PREDICT(MODEL `project.dataset.churn_model`,
    (SELECT * FROM `project.dataset.new_customers`));
```

---

## 2. Dataflow (Apache Beam)

### Traitement Stream et Batch unifié

| Caractéristique | Détail |
|-----------------|--------|
| **Modèle** | Apache Beam (portable) |
| **Mode** | Batch et Stream unifiés |
| **Scaling** | Autoscaling dynamique |
| **Exactly-once** | Garantie de traitement |

### Cas d'usage

| Use Case | Description |
|----------|-------------|
| ETL temps réel | Ingestion IoT, logs |
| Streaming analytics | Détection de fraude |
| Data enrichment | Jointure avec reference data |

### Exemple Python (Apache Beam)

```python
import apache_beam as beam

with beam.Pipeline() as pipeline:
    (pipeline
     | 'Read' >> beam.io.ReadFromPubSub(topic='projects/p/topics/events')
     | 'Parse' >> beam.Map(parse_json)
     | 'Window' >> beam.WindowInto(beam.window.FixedWindows(60))
     | 'Count' >> beam.combiners.Count.PerKey()
     | 'Write' >> beam.io.WriteToBigQuery('project:dataset.counts'))
```

---

## 3. Autres services Data

| Service | Fonction |
|---------|----------|
| **Cloud Storage** | Data Lake (équivalent S3) |
| **Pub/Sub** | Messaging temps réel |
| **Dataproc** | Spark/Hadoop managé |
| **Cloud Composer** | Airflow managé (orchestration) |
| **Data Fusion** | ETL visuel (CDAP) |
| **Dataplex** | Data Governance/Catalog |

---

## 4. Architecture Data Lake moderne

```
Sources                  Ingestion          Stockage           Analytics
────────                 ─────────          ────────           ─────────
Apps    ───┐
IoT     ───┼──► Pub/Sub ──► Dataflow ──► Cloud Storage ──► BigQuery
Logs    ───┤                    │              │              │
Bases   ───┘                    │              ▼              ▼
                                └────────► BigQuery ────► Looker/BI
```

---

## 5. Looker

### BI moderne par Google

| Aspect | Détail |
|--------|--------|
| **Modélisation** | LookML (semantic layer) |
| **Intégration** | Native BigQuery |
| **Embedded** | Intégrable dans vos apps |

---

## Ce qu'il faut retenir

> **BigQuery** est probablement le meilleur service d'analytics cloud pour le rapport qualité/simplicité/performance.

| Besoin | Service GCP |
|--------|-------------|
| Data Warehouse | BigQuery |
| ETL temps réel | Dataflow |
| Messaging | Pub/Sub |
| Spark managé | Dataproc |
| BI | Looker |

> [!TIP]
> Si vous faites du Big Data, évaluez sérieusement GCP. BigQuery seul justifie souvent le choix.
