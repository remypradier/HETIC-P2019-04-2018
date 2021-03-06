# Les expressions

En JavaScript, une expression est tout ce qui peut renvoyer un résultat : 
- un calcul
- une fonction exécutée
- une comparaison ou une ternaire
- une valeur

## Exemples

```javascript
1 + 1 - (5 + 2);
// renvoie -> -5
5 > 2;
// renvoie -> true
doThis();
// renvoie -> ce que "return" la fonction (si on l'avait créée)
var isEqual = ('5' === 5 ? true : false);
// renvoie -> false
var hello = function () { };
// renvoie -> une fonction
```

Toutes les expressions peuvent être stockées dans des variables car, elles renvoient un résultat vers la gauche.
Les fonctions peuvent aussi être des expressions quand elles sont stockées ou mises entre parenthèses.
Tout ce qui est entre parenthèses est considéré comme une expression et est évalué en premier comme en mathématiques.


## Expressions booléennes

On peut user de cette notion avec les opérateurs booléens.

### Les règles

Dans une suite de booléens séparés par des `||` (OU logique), l'expression s'arrête à la première valeur **truthy** ou la dernière des valeurs **falsy** si elles sont toutes **falsy**.

```javascript
var result = null || "1" || false || 5 || 0;
// result vaut : "1" : car c'est la première valeur truthy rencontrée

var result = "" || 0 || null;
// result vaut : null : car c'est la dernière valeur testée et donc renvoyée même si elle est fausse
```

Dans une suite de booléens séparés par des `&&` (ET logique), l'expression s'arrête à la dernière valeur **truthy** ou la première des valeurs **falsy** s'il y en a au moins une **falsy**.

```javascript
var result = null && "1" && false && 5 && 0;
// result vaut : null : car c'est la première valeur falsy rencontrée

var result = "1" && "Ariel" && 5;
// result vaut : 5 : car c'est la dernière valeur testée et donc 
// renvoyée vu que toutes les valeurs sont truthy
```

Ces expressions sont très pratiques pour donner une valeur par défaut par exemple.
```javascript
function hello(name, greeting) {
    greeting = greeting || 'Bonjour';

    return greeting + ', ' + name;
}

// "greeting" vaut "bonjour" s'il n'est pas passé car, ne pas le passer
// rend greeting "undefined" et donc l'expression "undefined || 'Bonjour'" 
// suit la règle des OU.
```

```javascript
function hello(doAltert) {
    var message = 'Salut salut !';

    doAltert && alert(message);

    return message;
}

// si doAltert vaut "true" ou quelque chose de truthy
// l'expression "doAltert && alert(message)" donnera "true && alert(message)"
// et donc fera un alert car il testera la 2ème valeur.
```

Pour connaître les valeurs falsy et truthy
https://www.sitepoint.com/javascript-truthy-falsy/
