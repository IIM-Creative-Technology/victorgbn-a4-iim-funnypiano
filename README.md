# iim-a4-funny-piano-project
Projet développé dans le cadre d'un cours de DevOps en Master à l'IIM. 

## Installation du projet
```
npm install
```

### Compiler pour développement
```
npm run serve
```

### Corriger les fichiers
```
npm run lint
```

## Mise en production en CI/CD

J'ai utilisé Github Actions et Huroku pour la mise en ligne automatique du projet.

- Lien vers le [site en prod](https://iim-a4-funny-piano-project.herokuapp.com/) (branche `main`)
- Liens vers le [site en pré-prod](https://iim-a4-funny-piano-dev.herokuapp.com/) (branche `develop`)

Via Github Actions, j'ai créé deux Workflows qui ont pour but de mettre en ligne chacune de mes deux branches de développement :
- la branche `main` en production 
- la branche `develop`en pré-production

Pour cela, j'ai créé deux fichiers : 
- `deploy-develop.yml`
- `deplay-main/yml`

Les deux fichiers sont liés à leur répertoire Heroku respectif. 

Les Workflows sont découpés en trois étapes : 
- Lint
- Build
- Deploy

Dès lors qu'un `git push` est effectué sur la branche `develop`, le Workflow `deploy develop` se lance. La mise en production est validée une fois que les trois étapes du Workflow sont réalisées avec succès. 

Dès lors qu'un `git push` ou qu'un `merge` est effectué sur la branche `main`, le Workflow `deploy main` se lance. La mise en production est validée une fois que les trois étapes du Workflow sont réalisées avec succès. 
