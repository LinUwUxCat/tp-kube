# Poids
- Classic : 1.12GB
- Multistage : 202MB

# Pourquoi le multistage réduit le poids?
- On omet les dépendances dev (ici, eslint) donc moins de librairies sont téléchargées (2MB au lieu de 16)
- On utilise node dans sa version complète pour télécharger les dépendances et build mais on utilise node slim pour lancer l'application.

# Amélioration
- Possibilité d'utiliser une image de node encore plus petite (node:alpine)