# Chapitre 29 — IA & ML : plateformes ou briques ?

## Introduction

L'approche de l'IA diffère fondamentalement entre les hyperscalers. Certains vous donnent des **plateformes** pour construire, d'autres des **briques** prêtes à l'emploi. Comprendre cette distinction guide vos choix.

---

## 1. Les deux philosophies

### Philosophie "Plateforme"
> "Voici les outils, construisez votre IA"

- Cible : Data Scientists, ML Engineers
- Flexibilité maximale
- Courbe d'apprentissage élevée

### Philosophie "Briques"
> "Voici l'IA prête, consommez-la"

- Cible : Développeurs d'applications
- Rapidité de mise en œuvre
- Moins de personnalisation

---

## 2. Positionnement des hyperscalers

| Cloud | Approche dominante | Service phare |
|-------|-------------------|---------------|
| **AWS** | Plateforme + Multi-modèles | SageMaker + Bedrock |
| **Azure** | Briques (OpenAI) | Azure OpenAI Service |
| **GCP** | Plateforme + Google AI | Vertex AI + Gemini |

---

## 3. Comparaison des plateformes ML

| Aspect | SageMaker (AWS) | Azure ML | Vertex AI (GCP) |
|--------|-----------------|----------|-----------------|
| **Notebooks** | Studio | Workbench | Workbench |
| **AutoML** | Autopilot | AutoML | AutoML |
| **Pipelines** | Pipelines | Pipelines | Pipelines (Kubeflow) |
| **Déploiement** | Endpoints | Endpoints | Endpoints |
| **MLOps** | ⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ |

---

## 4. Comparaison GenAI

| Aspect | AWS Bedrock | Azure OpenAI | GCP Vertex AI |
|--------|-------------|--------------|---------------|
| **Modèle star** | Claude (Anthropic) | GPT-4 | Gemini |
| **Approche** | Multi-fournisseurs | Exclusivité OpenAI | Google natif |
| **Modèles** | Claude, Llama, Mistral, Titan | GPT-4, GPT-3.5, DALL-E | Gemini, PaLM, Imagen |

### Avantages de chaque approche

| Bedrock (AWS) | Azure OpenAI | Vertex AI (GCP) |
|---------------|--------------|-----------------|
| Choix de modèles | Meilleur LLM actuel | Contexte 1M tokens |
| Pas de lock-in modèle | SLA enterprise | Intégration BigQuery |
| Flexibilité | Écosystème Microsoft | TPU pour training |

---

## 5. APIs IA comparées

| Fonction | AWS | Azure | GCP |
|----------|-----|-------|-----|
| **Vision** | Rekognition | Vision AI | Vision AI |
| **Speech-to-Text** | Transcribe | Speech Services | Speech-to-Text |
| **Text-to-Speech** | Polly | Speech Services | Text-to-Speech |
| **NLP** | Comprehend | Language Services | Natural Language |
| **Traduction** | Translate | Translator | Translation |
| **OCR** | Textract | Document Intelligence | Document AI |

---

## 6. Tendance : La convergence

### AWS et GCP adoptent l'approche "Briques"
- **Bedrock** = AWS adopte les LLMs as-a-service
- **Model Garden** = GCP propose des modèles pré-packagés

### Azure maintient son avance GenAI
- Partenariat exclusif OpenAI
- Copilot dans tout l'écosystème

---

## 7. Guide de décision

| Besoin | Recommandation |
|--------|----------------|
| GPT-4 en production enterprise | **Azure OpenAI** |
| Choix de modèles, pas de lock-in | **AWS Bedrock** |
| Intégration data (BigQuery) | **GCP Vertex AI** |
| ML custom, équipe Data Science | Les 3 sont comparables |
| AutoML simple | **GCP** ou Azure |
| Training avec TPU | **GCP** |

---

## Ce qu'il faut retenir

> La plupart des entreprises veulent **consommer** l'IA, pas la **construire**. Les briques (Azure OpenAI, Bedrock) gagnent du terrain.

| Profil | Recommandation |
|--------|----------------|
| Développeur app + IA | Azure OpenAI ou Bedrock |
| Data Scientist | SageMaker, Azure ML, ou Vertex AI |
| Startup IA-native | GCP (coûts TPU) |
