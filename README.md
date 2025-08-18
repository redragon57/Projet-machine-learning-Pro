# Projet-machine-learning-Pro

Ce dépôt GitHub a pour objectif de servir de **vitrine** à différents projets en **Machine Learning**, illustrant l’ensemble des compétences techniques et analytiques développées dans ce domaine.  
Chaque projet met en avant une approche méthodologique rigoureuse et une application concrète des algorithmes d’apprentissage automatique.

---

## Projets

### 1. DeepWeather

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

### 2. Revue exhaustive des méthodes de Machine Learning et d’Analyse de données *(en projet)*

Un second dossier contiendra une **liste exhaustive et organisée** de toutes les méthodes de Machine Learning et d’Analyse de données, allant des algorithmes classiques aux modèles avancés, émergents et expérimentaux.  
Cette revue sera structurée en catégories, avec implémentations et comparaisons.

---

#### [Méthodes classiques de Machine Learning](All_ML_python/Methode_classique_ML/README.md)
- Régressions : linéaire, logistique, ridge, lasso, elastic net  
- Méthodes bayésiennes : naïf bayes, régression bayésienne  
- k-Nearest Neighbors (k-NN)  
- Support Vector Machines (SVM, SVR)  
- Arbres de décision  
- Random Forests, Extremely Randomized Trees  
- Gradient Boosting (XGBoost, LightGBM, CatBoost)  

---

#### [Clustering et réduction de dimension](All_ML_python/Clustering_et_réduction_de_dimension/README.md)
- k-Means, k-Medoids  
- DBSCAN, OPTICS  
- Gaussian Mixture Models (GMM)  
- Spectral Clustering  
- PCA, ICA, t-SNE, UMAP  
- Autoencoders  

---

#### [Réseaux de neurones et Deep Learning](All_ML_python/Réseaux_Neurones_et_DL/README.md)
- Perceptron, MLP  
- CNN, ResNet, DenseNet, EfficientNet  
- RNN, LSTM, GRU  
- Transformers (BERT, GPT, Vision Transformers)  
- Autoencoders, Variational Autoencoders (VAE)  
- Generative Adversarial Networks (GAN, cGAN, StyleGAN, BigGAN, CycleGAN)  

---

#### [Apprentissage par renforcement](All_ML_python/Reinforcement_Learning_RL/README.md)
- Q-Learning, SARSA  
- Deep Q-Networks (DQN, Double DQN, Dueling DQN)  
- Policy Gradient, Actor-Critic  
- A3C, PPO, TRPO, SAC, DDPG  
- Meta-RL et Multi-Agent RL  

---

#### [Apprentissage avancé et hybrides](All_ML_python/ML_Avancée/README.md)
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

#### [Analyse de données et modèles probabilistes](All_ML_python/Analyse_data_et_modèle_probabiliste/README.md)
- Séries temporelles : ARIMA, SARIMA, Prophet, RNN/Transformers pour séries temporelles  
- Méthodes de causalité : Granger Causality, DoWhy, modèles structurels  
- Graph Mining et **Graph Neural Networks (GNN, GraphSAGE, GAT)**  
- Méthodes bayésiennes hiérarchiques et Approximate Bayesian Computation  
- Simulation et modélisation probabiliste : Monte Carlo, MCMC, Variational Inference  

---

#### [Méthodes émergentes et bio-inspirées](All_ML_python/New_Methode_experimental/README.md)
- Spiking Neural Networks (SNN)  
- Liquid State Machines (LSM)  
- Reservoir Computing  
- Neural Turing Machines, Differentiable Neural Computers  
- Modèles neuromorphiques et architectures matérielles spécialisées  
- Réseaux inspirés de la biologie : Plasticité synaptique, Hebbian Learning, Oja’s Rule  
- Self-Organizing Maps (Kohonen)  
- Évolution darwinienne appliquée à l’apprentissage (Neuroevolution, Evolutionary Strategies)  

---

#### [Apprentissage quantique (Quantum Machine Learning - QML)](All_ML_python/Quantum_ML/README.md)
- Quantum Support Vector Machines (QSVM)  
- Variational Quantum Circuits (VQC)  
- Quantum k-Means  
- Quantum Boltzmann Machines  
- Quantum Neural Networks (QNN)  
- Hybrid Classical-Quantum Models  
- Applications QML : optimisation combinatoire, simulation moléculaire, chimie quantique  
