# Chapitre 1 — Qu'est-ce qu'un hyperscaler ?

## Introduction

Avant de plonger dans les détails techniques d'AWS, Azure ou GCP, il est essentiel de comprendre ce qui les rend uniques. Ces entreprises ne sont pas de simples hébergeurs. Elles opèrent à une échelle que la plupart des organisations ne peuvent même pas imaginer. Ce chapitre pose les fondations conceptuelles pour tout le reste du livre.

---

## Définition

Un **hyperscaler** est un fournisseur de cloud capable d'opérer à une échelle massive et élastique, offrant des ressources informatiques à la demande à des millions de clients simultanément.

Le terme "hyper" fait référence à la capacité de croître de manière **hyperbolique** : passer de 10 serveurs à 10 000 en quelques minutes, sans intervention humaine.

---

## Les 4 piliers d'un hyperscaler

### 1. Déploiement massif d'infrastructure
Un hyperscaler est capable de :
- Déployer des **millions de serveurs** à travers le monde.
- Construire ses propres datacenters sur mesure (pas de location chez des tiers).
- Concevoir parfois son propre matériel (chips, switches réseau).

> [!NOTE]
> Google, par exemple, conçoit ses propres serveurs, switches réseau, et même ses processeurs IA (TPU).

### 2. Couverture géographique mondiale
- Opérer des **dizaines de régions** sur tous les continents.
- Offrir une latence faible à n'importe quel utilisateur dans le monde.
- Respecter les contraintes de **souveraineté des données** locales.

### 3. Catalogue de services
- Fournir des **centaines, voire des milliers de services managés** : calcul, stockage, bases de données, IA, IoT, sécurité...
- Chaque service est une API que vous pouvez orchestrer par programmation.

### 4. Élasticité en temps réel
- **Absorber une charge mondiale** lors d'événements massifs (Black Friday, élections, événements sportifs).
- Facturer à la seconde ou à l'octet, permettant un modèle économique OPEX.

---

## Les trois hyperscalers dominants

| Fournisseur | Fondation Cloud | Part de marché (2024) | ADN |
| :--- | :--- | :--- | :--- |
| **Amazon Web Services (AWS)** | 2006 | ~32% | E-commerce, pragmatisme |
| **Microsoft Azure** | 2010 | ~23% | Entreprise, hybride |
| **Google Cloud Platform (GCP)** | 2008 | ~11% | Data, IA, ingénierie |

### Pourquoi seulement 3 ?
La barrière à l'entrée est colossale :
- Investissement de **dizaines de milliards de dollars** par an en datacenters.
- Économies d'échelle impossibles à répliquer pour des acteurs plus petits.
- Effet réseau : plus il y a de clients, plus il y a de services, plus il y a de clients.

> [!IMPORTANT]
> Alibaba Cloud et Oracle Cloud sont parfois mentionnés, mais leur portée reste régionale ou de niche comparée aux "Big 3".

---

## Ce qu'il faut retenir

> Un hyperscaler n'est pas un hébergeur classique qui a grandi. C'est une **infrastructure planétaire** conçue dès le départ pour l'échelle, l'automatisation et l'innovation continue.

Comprendre les hyperscalers, c'est comprendre les forces économiques et techniques qui façonnent le numérique mondial.
