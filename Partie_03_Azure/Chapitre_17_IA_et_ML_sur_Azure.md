# Chapitre 17 — IA et ML sur Azure (Azure ML, OpenAI)

## Introduction

Le partenariat exclusif entre Microsoft et OpenAI fait d'Azure le cloud de référence pour l'IA générative. Mais Azure propose également une plateforme ML complète pour les cas d'usage classiques.

---

## 1. Azure OpenAI Service

### L'accès exclusif à GPT-4

| Modèle | Disponibilité |
|--------|---------------|
| GPT-4 Turbo | ✅ Azure (exclusif) |
| GPT-4 Vision | ✅ Azure (exclusif) |
| GPT-3.5 Turbo | ✅ Azure |
| DALL-E 3 | ✅ Azure |
| Whisper | ✅ Azure |

### Pourquoi Azure OpenAI vs OpenAI direct ?

| Critère | OpenAI API | Azure OpenAI |
|---------|------------|--------------|
| **SLA** | Aucun | 99.9% entreprise |
| **Conformité** | Limitée | SOC2, HIPAA, RGPD |
| **Données** | Peuvent servir à l'entraînement | **Non utilisées** |
| **Réseau** | Internet | VNet privé possible |
| **Région** | US | Multi-région |

### Exemple d'appel

```python
from openai import AzureOpenAI

client = AzureOpenAI(
    api_key="your-key",
    api_version="2024-02-15-preview",
    azure_endpoint="https://your-resource.openai.azure.com/"
)

response = client.chat.completions.create(
    model="gpt-4",  # Nom du déploiement
    messages=[
        {"role": "user", "content": "Explique le cloud en 3 phrases."}
    ]
)
print(response.choices[0].message.content)
```

---

## 2. Azure AI Services

### APIs cognitives prêtes à l'emploi

| Service | Fonction |
|---------|----------|
| **Vision** | Analyse d'images, OCR |
| **Speech** | Speech-to-Text, Text-to-Speech |
| **Language** | NLP, traduction, QnA |
| **Document Intelligence** | Extraction de documents |
| **Content Safety** | Modération de contenu |

---

## 3. Azure Machine Learning

### Plateforme MLOps complète

| Composant | Fonction |
|-----------|----------|
| **Designer** | ML visuel (drag & drop) |
| **AutoML** | Entraînement automatisé |
| **Notebooks** | Jupyter intégré |
| **Compute** | Clusters GPU managés |
| **Pipelines** | CI/CD pour ML |
| **Model Registry** | Versioning des modèles |
| **Endpoints** | Déploiement managé |

### Exemple : AutoML

```python
from azure.ai.ml import automl

classification_job = automl.classification(
    compute="gpu-cluster",
    experiment_name="customer-churn",
    training_data=train_dataset,
    target_column_name="Churned",
    primary_metric="AUC_weighted",
    n_cross_validations=5
)

ml_client.jobs.create_or_update(classification_job)
```

---

## 4. Azure AI Search (ex-Cognitive Search)

### Recherche vectorielle pour RAG

```
Documents → Embeddings → Index Vector → Recherche → LLM → Réponse
```

| Fonctionnalité | Description |
|----------------|-------------|
| **Indexation** | Fichiers, SQL, Cosmos DB |
| **Vector Search** | Recherche sémantique |
| **Hybrid Search** | Keyword + Vector |
| **Intégration OpenAI** | RAG native |

---

## 5. Microsoft Copilot : L'IA partout

### Copilot dans l'écosystème Microsoft

| Produit | Copilot intégré |
|---------|-----------------|
| **Microsoft 365** | Word, Excel, PowerPoint, Outlook |
| **GitHub** | GitHub Copilot (code) |
| **Power Platform** | Copilot Studio (chatbots) |
| **Dynamics 365** | Sales, Service, Finance |
| **Azure** | Azure Copilot (assistance admin) |

---

## 6. Comparaison avec AWS et GCP

| Aspect | Azure | AWS | GCP |
|--------|-------|-----|-----|
| **GenAI Star** | GPT-4 | Claude | Gemini |
| **Exclusivité** | OpenAI | Multi-modèles | Google |
| **ML Platform** | Azure ML | SageMaker | Vertex AI |
| **Intégration** | Office/Dynamics | Services AWS | BigQuery |

---

## Ce qu'il faut retenir

> Azure est le **seul cloud avec accès natif à GPT-4**. C'est son avantage compétitif majeur en 2024.

| Besoin | Service Azure |
|--------|---------------|
| Chatbot GPT-4 | Azure OpenAI |
| Vision, Speech, NLP | Azure AI Services |
| ML personnalisé | Azure Machine Learning |
| RAG enterprise | Azure AI Search |

> [!TIP]
> Pour la plupart des cas GenAI en entreprise, Azure OpenAI + AI Search est la combinaison gagnante.
