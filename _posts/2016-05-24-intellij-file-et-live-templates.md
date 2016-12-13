---
layout: post
title:  "Intellij : File et live templates"
date:   2016-03-28 13:29:08 +0100
categories: tools
---
Petite note sur l'utilisation des templates dans Intellij, WebStorm, PHPStorm...

## Templates de fichiers

Les variables de templates ${NOM_VARIABLE} ( ou $NOM_VARIABLE )permettent de définir des placeholders "dynamiques", que l'on pourra renseigner au moment de la création du fichier.

### Syntaxe variables

```
class ${NOM_VARIABLE}{
$END$
}
```

### Variables pré-définies

- ${NAME}
- ${PACKAGE_NAME}
- ... cf [doc](https://www.jetbrains.com/help/idea/2016.1/file-template-variables.html)

Les valeurs des variables de _file templates_ sont saisies via la popup de création du fichier.

Une option permet d'activer les live templates au sein du file templates, de manière à éditer les variables injectées "dans leur contexte".

Dans cet exemple, on définit un placeholder pour inclure une doc pour la classe crée, il sera bien plus pratique de le remplir dans l'éditeur, plutôt que dans une popup.

```
/**
* #[[ DOC ]]#
*/
class ${FILENAME}{
$END$
}
```

## Live templates

Les live templates permettent d'insérer des fragments de codes paramètrables à l'aide de raccourci textuel. Par exemple un raccourci _lg_ qui afficherait automatiquement _console.log("")_ et qui placerait le curseur entre les guillemets après insertion.

```
console.log("$NOM_VARIABLES$");
```

Intellij intégre deux variables prédéfinies :
- $END$ : permet d'indiquer où le curseur doit être placé après insertion du template et saisies de ses variables.
-

Il est également possible de définir ses propres variables, renseignées dans la continuité de l'insertion du live template.

```
console.log('$NOM_VARIABLES$');
$END$
```
### Injecter un live template autour d'une sélection
Ce template permet d'injecter une boucle for...of autour de la sélection active.
```
for( let p of $SELECTION$ ){
  $END$
}
```

### utilisation des fonctions de live templates

Il est possible d'utiliser quelques fonctions dans les _live templates_ :
- capitalize()
- arrayVariable()
- camelCase()
- capitalize()
- clipboard()
- ... cf [doc](https://www.jetbrains.com/help/idea/2016.1/live-template-variables.html)
