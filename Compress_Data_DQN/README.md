# DQN-Based File Compression Agent (V1)

## Description

Ce projet implémente un **agent d’apprentissage par renforcement basé sur DQN** (Deep Q-Network) pour optimiser la **compression de fichiers binaires**. L’agent apprend à choisir des actions qui améliorent la compression tout en assurant une reconstruction sans perte.  

Le système est conçu pour être extensible : plusieurs méthodes de compression peuvent être ajoutées à la classe `Compressor`. La version actuelle utilise `zlib`.

## Fonctionnalités

- **Compression sans perte** : vérification par checksum SHA-256 pour garantir l’intégrité des fichiers.
- **Agent DQN** : réseau de neurones simple (3 couches) pour prendre des décisions sur les actions de compression.
- **Apprentissage adaptatif** : l’agent apprend en explorant différentes stratégies de compression et en mémorisant ses expériences.
- **Gestion des fichiers** : exploration automatique des fichiers dans un répertoire `Data` et sauvegarde des meilleures compressions dans `Result`.
- **Extensible** : possibilité d’ajouter de nouvelles méthodes de compression et d’adapter les actions de l’agent.
