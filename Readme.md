import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Chargement des données
df = pd.read_csv("votre_fichier_de_données.csv")  # adapter si le dataset est déjà chargé

# Statistiques descriptives
print(df.describe())

# Distribution des métiers
plt.figure(figsize=(10,6))
sns.countplot(data=df, x='metier', order=df['metier'].value_counts().index)
plt.xticks(rotation=45)
plt.title("Répartition des métiers")
plt.show()

# Histogramme du salaire
plt.figure(figsize=(10,6))
sns.histplot(data=df, x='salaire', bins=30, kde=True)
plt.title("Distribution des salaires")
plt.show()

# Boxplot des expériences par métier
plt.figure(figsize=(12,6))
sns.boxplot(x='metier', y='experience', data=df)
plt.xticks(rotation=45)
plt.title("Expérience par métier")
plt.show()

# Heatmap des corrélations
plt.figure(figsize=(8,6))
sns.heatmap(df.corr(), annot=True, cmap="coolwarm", fmt=".2f")
plt.title("Carte des corrélations")
plt.show()

# Scatter plot salaire vs expérience
plt.figure(figsize=(10,6))
sns.scatterplot(x='experience', y='salaire', hue='metier', data=df)
plt.title("Salaire vs Expérience")
plt.show()

