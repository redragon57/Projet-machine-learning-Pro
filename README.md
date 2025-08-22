# Projet-machine-learning-Pro

Ce dépôt GitHub a pour objectif de servir de **vitrine** à différents projets en **Machine Learning**, illustrant l’ensemble des compétences techniques et analytiques développées dans ce domaine.  
Chaque projet met en avant une approche méthodologique rigoureuse et une application concrète des algorithmes d’apprentissage automatique.

---

## Projets

### [1. DeepWeather](DeepWeather/)

**DeepWeather** est un projet de prédiction météorologique utilisant des modèles de Machine Learning et de Deep Learning.  
L’objectif est double :  
- Développer un système capable de **prédire les variables météorologiques** (température, précipitations, pression, etc.) à partir de données historiques et satellitaires.  
- Réaliser une **analyse comparative statistique** entre les résultats obtenus et ceux des **modèles météorologiques existants** (réanalyses, modèles physiques, modèles hybrides).

#### Installation et exécution

*Section à compléter* :  
Les instructions détaillant la configuration de l’environnement, l’installation des dépendances et l’exécution du programme seront ajoutées ici.  

Exemple (placeholders) :  
```bash
# Cloner le dépôt
git clone git@github.com:redragon57/Projet-machine-learning-Pro.git
cd Projet-machine-learning-Pro/DeepWeather

# Créer l'environnement virtuel
python -m venv venv
source venv/bin/activate  # Linux / macOS
venv\Scripts\activate     # Windows

# Installer les dépendances
pip install -r requirements.txt
```

### [CycleGAN & Adaptive CycleGAN (AC-GAN) for Photo-to-Anime Translation](Gen_Anime_Image/)

#### Description
Ce projet implémente un **CycleGAN classique** et une version expérimentale **Adaptive CycleGAN (AC-GAN)** pour la traduction d'images de photos réelles vers un style anime. L'objectif est de générer des images stylisées réalistes tout en explorant des techniques d'entraînement progressif pour accélérer la convergence et optimiser les poids inutiles.

---

#### Fonctionnalités

##### 1. CycleGAN Standard
- **Architecture Générateurs** : ResNet-based, 9 blocs résiduels, instance normalization.
- **Architecture Discriminateurs** : N-layer PatchGAN.
- **Loss Function** : LSGAN + cycle-consistency + identité.
- **Training** :
  - Support GPU (`cuda`) et CPU.
  - Entraînement typique : 50 epochs, ~3h pour G=5.876 D=0.662.
  - Sauvegarde périodique des poids (`weights_G_epoch.pth`).
- **Inference** : Fonction `stylize_photo(img_tensor)` pour transformer une image photo en anime.

##### 2. Adaptive CycleGAN (AC-GAN)
- **Principe** :
  - Progression des couches : ajout de nouvelles couches pendant l'entraînement.
  - Gel adaptatif des poids peu influents pour accélérer la convergence.
  - Suivi EMA des gradients pour déterminer les poids à geler.
- **Architecture Progressive** :
  - `ProgressiveGen` et `ProgressiveDisc` : couches préallouées, nombre actif contrôlé dynamiquement.
  - Paramètres adaptatifs `START_LAYERS`, `ADD_EVERY_EPOCHS`, `MAX_LAYERS`.
- **Loss Function** : LSGAN + cycle-consistency + identité.
- **Training Utilities** :
  - Gestion des dataloaders pour photos et anime.
  - Entraînement par batch unique (BATCH_SIZE=1), images redimensionnées.
  - Checkpoints réguliers (`checkpoints_acgan/acgan_epochX.pth`).
- **Performance Observée** :
  - 7 epochs, 36 layers, Loss G=0.2470 D=0.2467 (~34 min sur GPU).
  
##### 3. V2 Optimisée
- **Generator/Discriminator** :
  - Active layers variables avec augmentation progressive.
  - Historique de poids pour gel adaptatif.
  - Gestion des gradients via masques pour les poids gelés.
- **Training Loop** :
  - Gestion complète de l’augmentation progressive, sauvegarde des checkpoints, mise à jour adaptative des gradients.
  - Fusion des datasets photo/anime pour simplification.
  - Transformations : resize, crop, normalize [-1,1].



### [DQN-Based File Compression Agent (V1)](Compress_Data_DQN/)

#### Description

Ce projet implémente un **agent d’apprentissage par renforcement basé sur DQN** (Deep Q-Network) pour optimiser la **compression de fichiers binaires**. L’agent apprend à choisir des actions qui améliorent la compression tout en assurant une reconstruction sans perte.  

Le système est conçu pour être extensible : plusieurs méthodes de compression peuvent être ajoutées à la classe `Compressor`. La version actuelle utilise `zlib`.

#### Fonctionnalités

- **Compression sans perte** : vérification par checksum SHA-256 pour garantir l’intégrité des fichiers.
- **Agent DQN** : réseau de neurones simple (3 couches) pour prendre des décisions sur les actions de compression.
- **Apprentissage adaptatif** : l’agent apprend en explorant différentes stratégies de compression et en mémorisant ses expériences.
- **Gestion des fichiers** : exploration automatique des fichiers dans un répertoire `Data` et sauvegarde des meilleures compressions dans `Result`.
- **Extensible** : possibilité d’ajouter de nouvelles méthodes de compression et d’adapter les actions de l’agent.



### [2. Revue exhaustive des méthodes de Machine Learning et d’Analyse de données *(en projet)*](All_ML_python/)

Un second dossier contiendra une **liste exhaustive et organisée** de toutes les méthodes de Machine Learning et d’Analyse de données, allant des algorithmes classiques aux modèles avancés, émergents et expérimentaux.  
Cette revue sera structurée en catégories, avec implémentations et comparaisons.

---

#### [Méthodes classiques de Machine Learning](All_ML_python/Methode_classique_ML/)
- Régressions : linéaire, logistique, ridge, lasso, elastic net  
- Méthodes bayésiennes : naïf bayes, régression bayésienne  
- k-Nearest Neighbors (k-NN)  
- Support Vector Machines (SVM, SVR)  
- Arbres de décision  
- Random Forests, Extremely Randomized Trees  
- Gradient Boosting (XGBoost, LightGBM, CatBoost)  

---

#### [Clustering et réduction de dimension](All_ML_python/Clustering_et_réduction_de_dimension/)
- k-Means, k-Medoids  
- DBSCAN, OPTICS  
- Gaussian Mixture Models (GMM)  
- Spectral Clustering  
- PCA, ICA, t-SNE, UMAP  
- Autoencoders  

---

#### [Réseaux de neurones et Deep Learning](All_ML_python/Réseaux_Neurones_et_DL/)
- Perceptron, MLP  
- CNN, ResNet, DenseNet, EfficientNet  
- RNN, LSTM, GRU  
- Transformers (BERT, GPT, Vision Transformers)  
- Autoencoders, Variational Autoencoders (VAE)  
- Generative Adversarial Networks (GAN, cGAN, StyleGAN, BigGAN, CycleGAN)  

---

#### [Apprentissage par renforcement](All_ML_python/Reinforcement_Learning_RL/)
- Q-Learning, SARSA  
- Deep Q-Networks (DQN, Double DQN, Dueling DQN)  
- Policy Gradient, Actor-Critic  
- A3C, PPO, TRPO, SAC, DDPG  
- Meta-RL et Multi-Agent RL  

---

#### [Apprentissage avancé et hybrides](All_ML_python/ML_Avancée/)
- Apprentissage semi-supervisé et auto-supervisé  
- Few-shot learning, Zero-shot learning  
- Meta-learning : MAML, Reptile, LEAP  
- Neural Architecture Search (NAS)  
- AutoML (y compris pour Feature Augmentation et FA mixtes/apprises)  
- Lifelong Learning / Continual Learning  
  - Elastic Weight Consolidation (EWC)  
  - GEM (Gradient Episodic Memory)  
  - AGEM (Average GEM)  
  - Progressive Neural Networks  
- Neuroevolution of Augmenting Topologies (NEAT)  
- Genetic Programming (GP)  
- Systèmes à plasticité structurelle (Structural Plasticity Learning)  
- Apprentissage fédéré et distribué  
- Hybridation neuro-symbolique  

---

#### [Analyse de données et modèles probabilistes](All_ML_python/Analyse_data_et_modèle_probabiliste/)
- Séries temporelles : ARIMA, SARIMA, Prophet, RNN/Transformers pour séries temporelles  
- Méthodes de causalité : Granger Causality, DoWhy, modèles structurels  
- Graph Mining et **Graph Neural Networks (GNN, GraphSAGE, GAT)**  
- Méthodes bayésiennes hiérarchiques et Approximate Bayesian Computation  
- Simulation et modélisation probabiliste : Monte Carlo, MCMC, Variational Inference  

---

#### [Méthodes émergentes et bio-inspirées](All_ML_python/New_Methode_experimental/)
- Spiking Neural Networks (SNN)  
- Liquid State Machines (LSM)  
- Reservoir Computing  
- Neural Turing Machines, Differentiable Neural Computers  
- Modèles neuromorphiques et architectures matérielles spécialisées  
- Réseaux inspirés de la biologie : Plasticité synaptique, Hebbian Learning, Oja’s Rule  
- Self-Organizing Maps (Kohonen)  
- Évolution darwinienne appliquée à l’apprentissage (Neuroevolution, Evolutionary Strategies)  

---

#### [Apprentissage quantique (Quantum Machine Learning - QML)](All_ML_python/Quantum_ML/)
- Quantum Support Vector Machines (QSVM)  
- Variational Quantum Circuits (VQC)  
- Quantum k-Means  
- Quantum Boltzmann Machines  
- Quantum Neural Networks (QNN)  
- Hybrid Classical-Quantum Models  
- Applications QML : optimisation combinatoire, simulation moléculaire, chimie quantique  
