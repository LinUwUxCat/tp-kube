# Captures d'écran
<img width="1160" height="184" alt="image" src="https://github.com/user-attachments/assets/03f3148f-0d2f-4dde-a30e-6bc6d4a39128" />
<img width="1588" height="367" alt="image" src="https://github.com/user-attachments/assets/1355505a-d0ab-4bfb-8ebc-ae0b517b4622" />


# Réponses
## Optimisations dans le Dockerfile : 
- Utiliser node:20-alpine permet de réduire considérablement la taille du conteneur
- On copie uniquement les fichiers nécéssaires dans le conteneur
- Optimisation manquante : il faudrait pouvoir faire un build au lieu de copier les node_modules

## À quoi sert imagePullSecrets et comment vous l’avez configuré
imagePullSecrets est un secret permettant de pull l'image si elle est privée sur docker hub. Dans notre cas elle est set a "regcred", qui est le nom du secret configuré en ligne de commande.
