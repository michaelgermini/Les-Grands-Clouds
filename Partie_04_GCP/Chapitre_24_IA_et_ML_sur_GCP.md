# Chapitre 24 — IA et ML sur GCP (Vertex AI, TPU)

## Introduction

Google est une entreprise "AI First". Ses investissements en recherche IA (Google Brain, DeepMind) se traduisent dans GCP avec des outils uniques comme les **TPUs** et **Vertex AI**.

---

## 1. Vertex AI : La plateforme ML unifiée

### Composants

| Composant | Fonction |
|-----------|----------|
| **Workbench** | Notebooks Jupyter managés |
| **Training** | Entraînement distribué |
| **Pipelines** | MLOps (Kubeflow) |
| **Model Registry** | Versioning des modèles |
| **Endpoints** | Déploiement managé |
| **AutoML** | ML sans code |
| **Model Garden** | 100+ modèles pré-entraînés |

### AutoML : ML pour tous

Entraînez des modèles de haute qualité sans écrire de code :

| Type | Données d'entrée |
|------|------------------|
| AutoML Vision | Images |
| AutoML Text | Texte/Documents |
| AutoML Tabular | Données structurées |
| AutoML Video | Vidéos |

---

## 2. Gemini : Le LLM de Google

### Modèles disponibles

| Modèle | Caractéristique |
|--------|-----------------|
| **Gemini 1.5 Pro** | Contexte 1M tokens |
| **Gemini 1.5 Flash** | Rapide et économique |
| **Gemini Ultra** | Le plus capable |

### Exemple d'appel API

```python
import google.generativeai as genai

genai.configure(api_key="YOUR_API_KEY")
model = genai.GenerativeModel('gemini-1.5-pro')

response = model.generate_content("Explique le cloud computing")
print(response.text)
```

### Gemini vs GPT-4

| Aspect | Gemini | GPT-4 |
|--------|--------|-------|
| **Contexte** | 1M tokens | 128K tokens |
| **Multimodal** | Natif | Via Vision |
| **Cloud** | GCP | Azure |
| **Coût** | Compétitif | Plus cher |

---

## 3. TPU (Tensor Processing Units)

### Puces IA conçues par Google

| Version | Performance |
|---------|-------------|
| TPU v4 | Training large scale |
| TPU v5e | Inference optimisée |
| TPU v5p | Training/Inference premium |

### Avantages TPU vs GPU

| Aspect | TPU | GPU (NVIDIA) |
|--------|-----|--------------|
| **Optimisation** | TensorFlow/JAX natif | Universel |
| **Coût** | Souvent moins cher | Standard |
| **Disponibilité** | GCP only | Multi-cloud |

---

## 4. Model Garden

Bibliothèque de 100+ modèles déployables :

| Catégorie | Exemples |
|-----------|----------|
| **Foundation** | Gemini, PaLM, Llama |
| **Vision** | Imagen, Stable Diffusion |
| **Code** | Codey |
| **Embedding** | Text Embedding |

---

## 5. APIs IA prêtes à l'emploi

| Service | Fonction |
|---------|----------|
| **Vision AI** | Analyse d'images |
| **Video AI** | Analyse de vidéos |
| **Speech-to-Text** | Transcription |
| **Text-to-Speech** | Synthèse vocale |
| **Translation** | Traduction 100+ langues |
| **Natural Language** | NLP |
| **Document AI** | OCR intelligent |

---

## 6. Duet AI

### L'assistant IA de Google Cloud

| Intégration | Fonction |
|-------------|----------|
| Cloud Console | Aide à la configuration |
| BigQuery | Génération SQL |
| Cloud Code | Génération de code |
| Looker | Insights automatiques |

---

## Ce qu'il faut retenir

> GCP est le cloud où l'IA est **native**, pas un add-on. TPU + Vertex AI + Gemini forment un écosystème cohérent.

| Besoin | Service GCP |
|--------|-------------|
| ML plateforme | Vertex AI |
| LLM | Gemini |
| Training optimisé | TPU |
| ML no-code | AutoML |
| Vision, Speech... | APIs AI |

> [!TIP]
> Si vous utilisez TensorFlow ou JAX, les TPUs peuvent réduire vos coûts d'entraînement de 50%+.
