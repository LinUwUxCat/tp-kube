# Captures d'écran

# Réponses
## Optimisations dans le Dockerfile : 
- Utiliser node:20-alpine permet de réduire considérablement la taille du conteneur
- On copie uniquement les fichiers nécéssaires dans le conteneur
- Optimisation manquante : il faudrait pouvoir faire un build au lieu de copier les node_modules

## À quoi sert imagePullSecrets et comment vous l’avez configuré
imagePullSecrets est un secret permettant de pull l'image si elle est privée sur docker hub. Dans notre cas elle est set a "regcred", qui est le nom du secret configuré en ligne de commande.