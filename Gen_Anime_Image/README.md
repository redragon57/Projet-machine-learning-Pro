# CycleGAN & Adaptive CycleGAN (AC-GAN) for Photo-to-Anime Translation

## Description
Ce projet implémente un **CycleGAN classique** et une version expérimentale **Adaptive CycleGAN (AC-GAN)** pour la traduction d'images de photos réelles vers un style anime. L'objectif est de générer des images stylisées réalistes tout en explorant des techniques d'entraînement progressif pour accélérer la convergence et optimiser les poids inutiles.

---

## Fonctionnalités

### 1. CycleGAN Standard
- **Architecture Générateurs** : ResNet-based, 9 blocs résiduels, instance normalization.
- **Architecture Discriminateurs** : N-layer PatchGAN.
- **Loss Function** : LSGAN + cycle-consistency + identité.
- **Training** :
  - Support GPU (`cuda`) et CPU.
  - Entraînement typique : 50 epochs, ~3h pour G=5.876 D=0.662.
  - Sauvegarde périodique des poids (`weights_G_epoch.pth`).
- **Inference** : Fonction `stylize_photo(img_tensor)` pour transformer une image photo en anime.

### 2. Adaptive CycleGAN (AC-GAN)
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
  
### 3. V2 Optimisée
- **Generator/Discriminator** :
  - Active layers variables avec augmentation progressive.
  - Historique de poids pour gel adaptatif.
  - Gestion des gradients via masques pour les poids gelés.
- **Training Loop** :
  - Gestion complète de l’augmentation progressive, sauvegarde des checkpoints, mise à jour adaptative des gradients.
  - Fusion des datasets photo/anime pour simplification.
  - Transformations : resize, crop, normalize [-1,1].

