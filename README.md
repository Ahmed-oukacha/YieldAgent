# YieldAgent : Framework d'Agents Autonomes pour l'Évaluation d'Actifs en Temps Réel

** (Track 4 : IA en Trading et Investissement)**

---

## Le Problème : L'Évaluation Précise des Actifs est un Défi Complexe

Dans le monde du trading, la vitesse et la précision sont primordiales. Cependant, les modèles d'IA de premier plan (Frontier Models) peinent encore à évaluer correctement les actifs.

Lors de nos tests de performance sur data set de amazon , nous avons constaté que :
* **L'Expert Humain :** commet une erreur moyenne de 127 $.
* **Le Modèle GPT-4 :** commet une erreur moyenne de 76 $.
* **Le Machine Learning (ML) Traditionnel :** commet une erreur moyenne de 97 $.

Ces erreurs significatives représentent des opportunités manquées ou des risques élevés dans le domaine financier.

##  La Solution : YieldAgent - Un Framework d'Agents Autonomes

**YieldAgent** est un système hybride supérieur qui résout ce problème. Ce n'est pas seulement un "modèle", c'est un **Framework d'Agents Autonomes (Agentic Framework)** qui combine "l'expertise" et "la mémoire" pour prendre des décisions d'évaluation ultra-précises.

###  Performance Supérieure : Seulement 30 $ d'Erreur

En fusionnant un modèle de langage affiné (Fine-tuned LLM LLAMA 3 7b) avec une mémoire RAG, **YieldAgent** atteint une Erreur Absolue Moyenne (EAM) de seulement **30 $**.

Cette performance non seulement surpasse les modèles traditionnels et les experts humains, mais elle écrase également la performance de GPT-4 de plus de 38%.

---

## Architecture Technique

YieldAgent fonctionne comme un cerveau numérique coordonné. Le système est orchestré par un `PlanningAgent` (Agent Planificateur) qui gère une équipe d'agents spécialisés :

1.  **Le "Cerveau" (The Brain) - `EnsembleAgent` :**
    * Ce n'est pas un modèle unique. C'est un "agent d'ensemble" qui fait appel à notre **LLM affiné (Fine-tuned) propriétaire**.
    * Ce modèle expert est déployé en tant que service cloud (Serverless) sur la plateforme **Modal** pour une scalabilité infinie.

2.  **La "Mémoire" (The Memory) - RAG + ChromaDB :**
    * Avant que le "Cerveau" ne procède à l'évaluation, nous lui fournissons une "mémoire contextuelle".
    * Nous utilisons un pipeline **RAG (Génération Augmentée par Récupération)** qui interroge une base de données vectorielles (Vector Database) : **ChromaDB**.
    * Cette base contient les "embeddings" (plongements vectoriels) de milliers d'actifs historiques, donnant à notre modèle un contexte de marché instantané.

3.  **Les "Capteurs" et "Effecteurs" (Sensors & Actuators) :**
    * **`ScannerAgent` (Le Scanner) :** Surveille le marché en continu à la recherche de nouveaux actifs à évaluer.
    * **`MessagingAgent` (Le Messager) :** Lorsque le système identifie une opportunité "Alpha" (une décote importante), cet agent envoie un **signal d'exécution (Alerte)** automatisé (via Twilio).

## Tableau de Bord (Dashboard)

Nous avons construit une interface de démonstration interactive avec **Gradio** pour montrer le système en action.

* **Vue en direct des opportunités :** Un tableau à jour des actifs (opportunités) découverts.
* **Logs en temps réel :** Transparence totale sur ce que chaque agent "pense" en temps réel.
* **Visualisation du Cerveau :** Un graphique 3D Plotly affichant la mémoire vectorielle (t-SNE) du système pendant qu'il organise sa connaissance du marché.

 ---

## Technologies Utilisées

| Catégorie | Technologie |
| :--- | :--- |
| **Framework** | Python, Conception de Framework d'Agents |
| **Modèles IA** | Fine-tuned LLAMA 3 7B (LoRA), RAG (Génération Augmentée par Récupération) |
| **Cloud Computing** | Modal (Déploiement Serverless GPU) |
| **Base de Données** | ChromaDB (Base de Données Vectorielles) |
| **Interface** | (Dashboard Interactif) |
| **Notifications** | Twilio (Alertes SMS) |

---

## Comment l'exécuter

1.  **Installer les dépendances :**
    ```bash
    pip install -r requirements.txt
    ```

2.  **Préparer l'environnement :**
    * Créez un fichier `.env` et renseignez les variables requises (clés API Twilio, Modal).

3.  **Lancer ChromaDB :**
    * (Assurez-vous que ChromaDB est lancé et accessible, par exemple via Docker ou en tant que serveur).

4.  **Lancer l'interface Gradio :**
    ```bash
    python scr/price_is_right_final.py
    ```

5.  **Ouvrir le tableau de bord :**
    * Ouvrez votre navigateur à l'adresse `http://127.0.0.1:7860` pour voir **YieldAgent** en action.
