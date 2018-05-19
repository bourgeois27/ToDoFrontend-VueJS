# laboratoire5

> Laboratoire 5 pour le cours de GLO-3102

## But : 
Se familiariser avec le framework **VueJS** en réalisant une application MVC basique.

## Travail :
Réaliser la même application qu'au laboratoire \#4 mais cette fois-ci en utilisant le framework VueJS au lieu du JavaScript Vanille.

## Consignes :
* Il doit s’agir de la même application qu’au laboratoire 4,
utilisant la même API... mais refaite en VueJS.
* Réutiliser tout le style fait au laboratoire précédent.
* API disponible [ici](https://glo3102lab4.herokuapp.com/)

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report
```

For a detailed explanation on how things work, check out the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).

## Documentation de l'API :

#### <code>GET</code> /:userId/tasks

Permet de retourner toutes les tâches actuelles.

###### Entrée

>Aucune entrée nécessaire

**Paramètres obligatoires**

`userId` est le paramètre de l'id associé à l'utilisateur.

###### Sortie
Retourne la liste de toutes les tâches à faire
```JSON
{
    "tasks": [
        {
            "id": "352e1ee0-49dd-48da-99e0-1ea3cffb1ee3",
            "name": "grab a couple of beers"
        },
        {
            "id": "e1760f91-8329-4387-91b0-5acb0ff99906",
            "name": "drink said beers"
        },
        {
            "id": "8574da1e-f83f-4101-af6d-34d2f8a7318e",
            "name": "take a huge shit"
        }
    ]
}
```

#### <code>POST</code> /:userId/tasks

Permet de créer une nouvelle tâche.

###### Entrée

>Le `content-type` doit être `application/json`

```JSON
{
	"name": "Something"
}
```

**Paramètres obligatoires**

`userId` est le paramètre de l'id associé à l'utilisateur.

###### Sortie
Retourne la tâche avec son `id` et son `name`
```JSON
{
    "id": "8d5fad38-e2d6-41f8-9662-44427a3086e1",
    "name": "Something"
}
```

#### <code>PUT</code> /:userId/tasks/:taskId

Permet de modifier la tâche associée à l'id. (Remplace les valeurs de la tâche par la nouvelle passée dans la requête)

###### Entrée

>Le `content-type` doit être `application/json`

```JSON
{
	"name": "Something else"
}
```

**Paramètres obligatoires**

`userId` est le paramètre de l'id associé à l'utilisateur.

`taskId` est le paramètre de l'id associé à la tâche à modifier.

###### Sortie
Retourne la tâche avec son `id` et son nouveau `name`.
```JSON
{
    "id": "8d5fad38-e2d6-41f8-9662-44427a3086e1",
    "name": "Something else"
}
```

#### <code>DELETE</code> /:userId/tasks/:taskId

Permet de supprimer la tâche associée à l'id.

###### Entrée

>Aucune entrée nécessaire

**Paramètres obligatoires**

`userId` est le paramètre de l'id associé à l'utilisateur.

`taskId` est le paramètre de l'id associé à la tâche à modifier.


###### Sortie
>Aucun retour de la part du serveur
