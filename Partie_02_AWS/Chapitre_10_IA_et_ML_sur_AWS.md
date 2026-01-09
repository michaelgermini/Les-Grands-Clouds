# Chapitre 10 — IA et ML sur AWS (SageMaker, Bedrock)

## Introduction

AWS propose l'écosystème ML le plus complet du marché, des APIs prêtes à l'emploi aux plateformes d'entraînement avancées. Avec Bedrock, AWS rattrape son retard sur l'IA générative en proposant un accès multi-modèles.

---

## 1. L'écosystème IA/ML AWS

| Niveau | Service | Public cible |
|--------|---------|--------------|
| **APIs IA** | Rekognition, Comprehend, Polly | Développeurs |
| **ML Plateforme** | SageMaker | Data Scientists |
| **GenAI** | Bedrock, Amazon Q | Développeurs |
| **Infrastructure** | EC2 GPU, Inferentia | ML Engineers |

---

## 2. Amazon SageMaker

### La plateforme ML complète

| Composant | Fonction |
|-----------|----------|
| **Studio** | IDE intégré pour ML |
| **Data Wrangler** | Préparation de données |
| **Feature Store** | Stockage de features |
| **Training** | Entraînement distribué |
| **Pipelines** | CI/CD pour ML |
| **Endpoints** | Déploiement de modèles |
| **Model Monitor** | Détection du drift |

### Exemple d'entraînement

```python
from sagemaker.estimator import Estimator

estimator = Estimator(
    image_uri='pytorch-training:2.0-gpu',
    instance_type='ml.p3.2xlarge',
    instance_count=2,
    hyperparameters={'epochs': 10}
)
estimator.fit({'train': 's3://bucket/train/'})
predictor = estimator.deploy(instance_type='ml.m5.xlarge')
```

---

## 3. Amazon Bedrock (GenAI)

### Modèles disponibles

| Fournisseur | Modèle | Spécialité |
|-------------|--------|------------|
| **Anthropic** | Claude 3 | Raisonnement |
| **Meta** | Llama 3 | Open source |
| **Mistral** | Mixtral | Efficacité |
| **Amazon** | Titan | General purpose |

### Exemple d'appel Claude

```python
import boto3, json

bedrock = boto3.client('bedrock-runtime')
response = bedrock.invoke_model(
    modelId='anthropic.claude-3-sonnet',
    body=json.dumps({
        "messages": [{"role": "user", "content": "Explique le cloud"}]
    })
)
```

### Knowledge Bases pour RAG
Connectez vos documents S3 aux LLMs pour des réponses contextualisées.

---

## 4. APIs IA prêtes à l'emploi

| Service | Fonction |
|---------|----------|
| **Rekognition** | Vision (visages, objets) |
| **Textract** | OCR intelligent |
| **Comprehend** | NLP (sentiment, entités) |
| **Polly** | Text-to-Speech |
| **Transcribe** | Speech-to-Text |
| **Translate** | Traduction 75+ langues |

---

## Ce qu'il faut retenir

> AWS offre le **choix** multi-modèles via Bedrock, contrairement à l'exclusivité Azure/OpenAI.

| Besoin | Service |
|--------|---------|
| Vision, NLP rapide | APIs IA |
| ML personnalisé | SageMaker |
| GenAI / LLMs | Bedrock |
