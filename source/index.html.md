---
title: API Offroute

language_tabs: # must be one of https://git.io/vQNgJ
  - JSON

toc_footers:
  - <a href='http://offroute.fr'>Venez nous découvrir sur le site de l'API</a>

includes:
  - errors

search: true
---

# Introduction

Bienvenue sur la documentation de l'application Offroute.

Une solution de de navigation inertielle pour Smartphone qui vous facilitera les déplacements dans les zones sans couvertures réseau.

<aside class="notice">
Toutes les requêtes doivent obligatoirement contenir dans leur header un <code>Content-Type : application/json</code>
</aside>

# Création d'un compte, Authentification et Connexion

## Création d'un compte Utilisateur

La requête suivante permet de créer un compte sur notre application.


<aside class="notice">
La requête est en <code>POST</code>
</aside>

> Un exemple de requête dans un shell serait :

```shell

time curl -X POST -H "Content-Type: application/json" -d \
'{"password":"123456", "email":"test@epitech.eu", "login":"unicorn", "access_token":"1234567890"}' \
https://api.offroute.fr/Users/CreateUser

```

### Arguments attendus :

La liste suivante recense tout les arguments acceptés et pouvant être utilisés, lors de l'utilisation de cette commande.

Arguments | Exemple
--------- | -------
login | Shaun
password | poli45\
firstname | Arthur
lastname | Lefèvre
age | 21
email | shone.witze@gmail.com


### Requête HTTP :

`POST https://api.offroute.fr/Users/CreateUser`


### Retour :

Un retour depuis l'API serait, par exemple, sous la forme :

Paramètres | Valeur
--------- | -------
status_code | 201
Id | 142
Message | User created

<aside class="success">
Lorsque la création d'un compte est réussie, le code de retour (status_code) est le 201
</aside>


## Connaître la validité d'un compte utilisateur

Afin de savoir si votre compte est toujours valide, utilisez la requête suivante :

<aside class="notice">
La requête est en <code>GET</code>
</aside>


```shell

time curl -X GET -H "Content-Type: application/json" -d \
'{"login": "unicorn", "token":"im8Md1lnVxhGGhgsjsHrksF5ByU"}' \
https://api.offroute.fr/Users/ValidAccount

```

### Requête HTTP :

`GET https://api.offroute.fr/Users/ValidAccount`

### Arguments attendus :

Cette requête n'attend que deux arguments : le <code>login</code> et le <code>token</code>.

### Retour :

Un retour depuis l'API serait, par exemple, sous la forme :

Paramètres | Valeur
--------- | -------
status_code | 200
Message | This account is valid

<aside class="success">
Lorsque la création d'un compte est réussie, le code de retour (status_code) est le 200.
</aside>


## Connexion à l'application

Afin de correctement se connecter à notre application, il est nécessaire que le compte soit créé et qu'il soit toujours valide.

<aside class="notice">
La requète est en <code>POST</code>
</aside>

```shell

time curl -X POST -H "Content-Type: application/json" -d \
'{"login": "unicorn", "password":"123456"}' \
https://api.offroute.fr/Users/Login

```

### Requête HTTP :

`POST https://api.offroute.fr/Users/Login`

### Arguments attendus :

Cette requête n'attend que deux arguments : votre <code>login</code> et votre <code>password</code>.

### Retour :

Un retour depuis l'API serait, par exemple, sous la forme :

Paramètres | Valeur
--------- | -------
status_code | 200
login | im8Md1lnVxhGGhgsjsHrksF5ByU
Message | You are logged in

<aside class="success">
Lorsque la connexion à l'application est réussie, le code de retour (status_code) est le 200.
</aside>

## Déconnexion de l'application

Si vous avez le besoin de vous déconnecter de l'application, utilisez la requête suivante.

<aside class="notice">
La requête est en <code>POST</code>
</aside>

```shell

time curl -X POST -H "Content-Type: application/json" -d \
'{"token":"im8Md1lnVxhGGhgsjsHrksF5ByU"}' \
https://api.offroute.fr/Users/Logout

```

### Requête HTTP :

`POST https://api.offroute.fr/Users/Logout`

### Arguments attendus :

Afin de lancer la requête, vous n'aurez besoin de connaître qu'un seul argument : Le <code>token</code>

### Retour :

Un retour depuis l'API serait, par exemple, sous la forme :

Paramètres | Valeur
--------- | -------
status_code | 200
Message | You are disconnected

<aside class="success">
Lorsque vous avez réussi à vous déconnecter de l'API, le code de retour (status_code) est le 200.
</aside>


# Modification du compte

## Affichage de vos informations personnelles

Afin de récupérer correctement toutes les informations de votre compte, lancez la requête suivante.

<aside class="notice">
La requête est en <code>GET</code>
</aside>

```shell

time curl -X GET -H "Content-Type: application/json" -d \
'{"token":"im8Md1lnVxhGGhgsjsHrksF5ByU"}' \
https://api.offroute.fr/Users/getUserInformation

```

### Requête HTTP :

`GET https://api.offroute.fr/Users/getUserInformation`


### Arguments attendus :

Afin de lancer la requête, vous n'aurez besoin de connaître qu'un seul argument : Le <code>token</code>

### Retour :

Un retour depuis l'API serait, par exemple, sous la forme :

Paramètres | Valeur
--------- | -------
status_code | 200
login | Shaun
age | 21
password | poli45\
firstname | Arthur
lastname | Lefèvre
email | shone.witze@gmail.com
Id | 142

<aside class="success">
Lorsque la requête à fonctionné et que vous avez pu récupéré les informations, le code de retour (status_code) est le 200.
</aside>

## Modification de vos informations personnelles

Afin de modifier, certaines ou la totalité de vos informations personnelles, lancez la requête suivante.

<aside class="notice">
La requête est en <code>POST</code>
</aside>

```shell

time curl -X POST -H "Content-Type: application/json" -d \
'{"token":"im8Md1lnVxhGGhgsjsHrksF5ByU", "login":"wonderful_unicorn", "age":"24"}' \
https://api.offroute.fr/Users/setUserInformation

```

### Requête HTTP :

`POST https://api.offroute.fr/Users/setUserInformation`

### Arguments attendus :

Afin de lancer la requête, vous n'aurez besoin de connaître qu'un seul argument : Le <code>token</code>, suivi des arguments et des clés que vous souhaitez modifier parmi la liste suivante :

Arguments | Exemple de clés
--------- | -------
login | Shaun The Sheep
password | Wrath56/
firstname | Emmanuel
lastname | Decronumbourg
age | 21
email | shone.witze@gmail.com
Id | 142

Il n'est pas nécessaire de rajouter en argument, des informations que vous en souhaitez pas modifier.

### Retour :

Lorsque la requête a été correctement exécuté, l'API vous renverra une liste récapitulant toutes vos informations personnelles.

Ainsi, un retour depuis l'API pourrait être sous la forme :

Paramètres | Valeur
--------- | -------
status_code | 200
login | Shaun The Sheep
age | 21
password | Wrath56/
firstname | Emmanuel
lastname | Decronumbourg
email | shone.witze@gmail.com
Id | 142

<aside class="success">
Lorsque les informations ont été correctement modifié, le code de retour (status_code) est le 200.
</aside>

## Changement du mot de passe

Afin de changer le mot de passe, il vous faut passer par cette requête.

<aside class="notice">
La requête est en <code>POST</code>
</aside>

```shell

time curl -X POST -H "Content-Type: application/json" -d \
'{"token":"im8Md1lnVxhGGhgsjsHrksF5ByU", "new_password":"secret_unicorn"}' \
https://api.offroute.fr/Users/updateUserPassword

```

### Requête HTTP :

`POST https://api.offroute.fr/Users/updateUserPassword`

### Arguments attendus :

Afin de lancer la requête, vous n'aurez besoin de connaître qu'un seul argument : Le <code>token</code>, il vous suffira de suivre cet argument du nouveau mot de passe.

### Retour :

Lorsque la requête a été correctement exécuté, l'API vous renverra le mot de passe modifié.

Un retour depuis l'API peut être, par exemple :

Paramètres | Valeur
--------- | -------
status_code | 200
password | secret_unicorn
Message | Your password has been changed

<aside class="success">
Lorsque le mot de passe est changé avec succès, le code de retour (status_code) est le 200.
</aside>

## Récupération du mot de passe

Afin de récupérer le mot de passe, en cas de perte, il vous faut passer par cette requête.

<aside class="notice">
La requête est en <code>GET</code>
</aside>

```shell

time curl -X GET -H "Content-Type: application/json" -d \
'{"email":"shone.witze@gmail.com", "username":"Shaun The Sheep"}' \
https://api.offroute.fr/Users/getUserPassword

```

### Requête HTTP :

`GET https://api.offroute.fr/Users/getUserPassword`

### Arguments attendus :

Afin de lancer la requête, vous n'aurez besoin de connaître qu'un seul argument : le <code>token</code>. Il vous suffira de faire suivre cet argument par le nouveau mot de passe.

### Retour :

Lorsque la requête a été correctement exécuté, l'API vous renverra le mot de passe modifié.

Un retour depuis l'API peut être, par exemple :

Paramètres | Valeur
--------- | -------
status_code | 200
password | secret_unicorn
Message | Your password has been changed

<aside class="success">
Lorsque les informations ont été correctement modifié, le code de retour (status_code) est le 200.
</aside>


## Suppression du compte

Si un compte doit être supprimé, il faut passer par cette requête.

<aside class="notice">
La requête est en <code>POST</code>
</aside>

```shell

time curl -X GET -H "Content-Type: application/json" -d \
'{"token":"im8Md1lnVxhGGhgsjsHrksF5ByU"}' \
https://api.offroute.fr/Users/deleteUser

```

### Arguments attendus :

Afin de lancer la requête, vous n'aurez besoin de connaître qu'un seul argument : Le <code>token</code>.


### Retour :

Lorsque la requête a été correctement exécuté, l'API vous indiquera le suppression du compte.

Paramètres | Valeur
--------- | -------
status_code | 200
Message | Your account has been deleted

<aside class="success">
Lorsque le compte a été supprimé avec succès, le code de retour (status_code) est le 200.
</aside>
