
## Tickets de caisse

Un client va nous envoyer ses tickets de caisse.

Ils sont envoyés en http, sur un webhook `/ticket` de notre serveur, avec un appel par ticket.

Le payload est constitué d'un en-tête avec un enregistrement par ligne, suivi d'un saut de ligne, suivi des produits au format csv :

```
Order: 123456
VAT: 3.10
Total: 16.90

product,product_id,price
Formule(s) midi,aZde,14.90
Café,IZ8z,2
```

Nous voulons stocker ces tickets dans une base postgresql, et constituer une base de produits à partir des produits contenus dans les tickets.

**Contraintes :**

 - les tickets arriveront avec une volumétrie très importante, potentiellement en burst
 - nous ne sommes pas sûrs de la qualité des données des tickets reçus, ni que le format est respecté (mais la plupart des tickets seront au même format que l'exemple)
 - nous ne voulons perdre aucun ticket qui nous est envoyé sur le webhook

**Exercice :**

- Ecrire un service qui gère ce qui est indiqué ci-dessus
- Décrire (brièvement) les choix et les compromis qui ont été faits en écrivant le service (sous forme de commentaires ou de README)

**Consignes :**

 - il faut utiliser (node.js, typescript ou Go) et (postgresql ou Mongo)
 - il est possible d'utiliser n'importe quoi d'autre qui serait utile
 - il n'est pas nécessaire de faire des tests unitaires
 - il n'est pas nécessaire de gérer l'authentification, les droits, les utilisateurs

**Conseils :**

- Ce que nous évaluerons est :
    - La conception, l'architecture et le modèle de données de la solution correspondent aux contraintes indiquées.
    - La qualité du code (lisibilité, maintenabilité, structure, etc.)
- Ce n'est pas la peine de passer du temps sur ce qui n'est pas lié au point ci-dessus (tests unitaires, etc.)
- Il y a de nombreuses bonnes réponses à l'exercice, nous ne cherchons pas une solution en particulier, à partir du moment où la solution proposée répond aux contraintes
- Ne pas hésiter à décrire (brièvement) les choix faits
- L'exercice ne doit pas prendre trop de temps à être fait. Si la solution devient compliquée ou trop longue à coder, il faut essayer de faire plus simple (tout en respectant les contraintes)
