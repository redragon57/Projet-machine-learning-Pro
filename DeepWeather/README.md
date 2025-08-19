# DeepWeather

**DeepWeather** est un projet de prédiction météorologique utilisant des modèles de Machine Learning et de Deep Learning.  
L’objectif est double :  
- Développer un système capable de **prédire les variables météorologiques** (température, précipitations, pression, etc.) à partir de données historiques et satellitaires.  
- Réaliser une **analyse comparative statistique** entre les résultats obtenus et ceux des **modèles météorologiques existants** (réanalyses, modèles physiques, modèles hybrides).

## Installation et exécution

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

## 1. Prétraitement des données

- Importation d’un dataset météorologique (weather_prediction_dataset.csv).
- Conversion des dates en format temporel exploitable.
- Extraction de variables temporelles (jour de l’année, sinus/cosinus pour la cyclicité).
- Création de features dérivées :
- Décalages (lags) de température moyenne (lag1, lag2, lag3, lag7).
- Moyennes glissantes (roll3, roll7).
- Nettoyage (dropna) et séparation en features X et cible y (prédiction de la température moyenne de Bâle à J+1).

## 2. Outils génériques

Classe WeatherDataset pour transformer le DataFrame en séquences temporelles exploitables par un LSTM.

Modèle LSTMForecast : LSTM multivarié avec couche fully connected finale.

Fonction dataframe_entropy(df) : calcule la taille brute du CSV et l’entropie moyenne par blocs de 128 octets (mesure de complexité structurelle).

## 3. Stratégies d’entraînement testées

- Model 1 : entraînement simple avec hyperparamètres fixes.
- Model 2 : ajout d’early stopping adaptatif basé sur une fenêtre de pertes et un gain minimal (eps_gain).
- Model 3 : paramétrage automatique du nombre de couches et de neurones via la taille du fichier et son entropie de Kolmogorov estimée.
- Model 4 : arrêt anticipé conditionné à une amélioration proportionnelle à la perte courante (10%).

## 4. Résultats expérimentaux

Données : taille CSV ≈ 2,73 Mo, entropie moyenne ≈ 3,19 bits/bloc, soit ≈ 0,40 bits/octet.
Corrélations obtenues (Pearson) entre prédictions et valeurs réelles :
- Model 1 : 0.8002
- Model 2 : 0.7448
- Model 3 : 0.8043
- Model 4 : 0.8345

## 5. Conclusion

Les quatre modèles sont fonctionnels et apprennent correctement, avec corrélation entre 0.74 et 0.83 sur les données de test.

L’approche 3 (entropie-guidée) obtient la meilleure corrélation (0.8345), montrant que l’intégration d’une mesure de complexité structurelle pour calibrer le réseau est viable.

Les mécanismes d’early stopping et de paramétrage automatique (taille du réseau, gain minimal) améliorent la stabilité et évitent le surapprentissage.