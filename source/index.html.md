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

time curl -X POST -H "Content-Type: application/json" -H \
"X-Access-Token":"1234567890" -d \
'{"email":"test@epitech.eu", "password":"123456", "username":"Unicorn"}' \
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

time curl -X GET -H "Content-Type: application/json" -H \
"X-Access-Token":"1234567890" -d \
'{"login": "unicorn"}' \
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
'{"email": "lysa.lewitanski@yahoo.fr", "password":"test"}' \
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
access_token | im8Md1lnVxhGGhgsjsHrksF5ByU
Message | You are connected

<aside class="success">
Lorsque la connexion à l'application est réussie, le code de retour (status_code) est le 200.
</aside>

## Déconnexion de l'application

Si vous avez le besoin de vous déconnecter de l'application, utilisez la requête suivante.

<aside class="notice">
La requête est en <code>DELETE</code>
</aside>

```shell

time curl -X DELETE -H "Content-Type: application/json" -H \
"X-Access-Token":"1234567890" \
https://api.offroute.fr/Users/Logout

```

### Requête HTTP :

`DELETE https://api.offroute.fr/Users/Logout`

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

time curl -X GET -H "Content-Type: application/json" -H \
"X-Access-Token: 8iVdv2PCvWbJJNp" \
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
username | Shaun
birthdate | Fri, 06 Jul 2018 00:00:00 GMT
password | poli45\
firstname | Arthur
lastname | Lefèvre
email | shone.witze@gmail.com
id_user | 142

<aside class="success">
Lorsque la requête à fonctionné et que vous avez pu récupéré les informations, le code de retour (status_code) est le 200.
</aside>

## Modification de vos informations personnelles

Afin de modifier, certaines ou la totalité de vos informations personnelles, lancez la requête suivante.

<aside class="notice">
La requête est en <code>PUT</code>
</aside>

```shell

time curl -X PUT -H "Content-Type: application/json" -H \
"X-Access-Token: 8iVdv2PCvWbJJNp" -d \
'{"Username":"Wonderful_unicorn"}' \
https://api.offroute.fr/Users/setUserModification

```

### Requête HTTP :

`PUT https://api.offroute.fr/Users/setUserModification`

### Arguments attendus :

Afin de lancer la requête, vous n'aurez besoin que de connaître les arguments que vous souhaitez modifier. Arguments se trouvant dans la liste suivante.

Arguments | Exemple de clés
--------- | -------
username | Shaun The Sheep
password | Wrath56/
firstname | Emmanuel
lastname | Decronumbourg
birthdate | Fri, 06 Jul 2018 00:00:00 GMT
age | 21
email | shone.witze@gmail.com
user_id | 142

Il n'est pas nécessaire de rajouter en argument, des informations que vous en souhaitez pas modifier.

### Retour :

Lorsque la requête a été correctement exécuté, l'API vous renverra les informations personnelles qui ont été modifié.

Ainsi, un retour depuis l'API pourrait être sous la forme :

Paramètres | Valeur
--------- | -------
status_code | 200
login | Shaun The Sheep
age | 21
firstname | Emmanuel
email | shone.witze@gmail.com

<aside class="success">
Lorsque les informations ont été correctement modifié, le code de retour (status_code) est le 200.
</aside>

## Changement du mot de passe

Afin de changer le mot de passe, il vous faut passer par cette requête.

<aside class="notice">
La requête est en <code>PUT</code>
</aside>

```shell

time curl -X PUT -H "Content-Type: application/json" -H \
"X-Access-Token: 8iVdv2PCvWbJJNp" -d \
'{"password":"123456", "new_password":"Secret_unicorn"}' \
https://api.offroute.fr/Users/updateUserPassword

```

### Requête HTTP :

`PUT https://api.offroute.fr/Users/updateUserPassword`

### Arguments attendus :

Afin de lancer la requête, vous n'aurez besoin de connaître qu'un seul argument : Le <code>token</code>, il vous suffira de suivre cet argument de l'ancien mot de passe, puis du nouveau.

### Retour :

Lorsque la requête a été correctement exécuté, l'API vous enverra un message pour vous prévenir du changement.

Un retour depuis l'API peut être, par exemple :

Paramètres | Valeur
--------- | -------
status_code | 200
Message | Your password has been changed

<aside class="success">
Lorsque le mot de passe est changé avec succès, le code de retour (status_code) est le 200.
</aside>

## Récupération du mot de passe

Afin de récupérer le mot de passe, en cas de perte, il vous faut passer par cette requête.

<aside class="notice">
La requête est en <code>PUT</code>
</aside>

```shell

time curl -X PUT -H "Content-Type: application/json" -d \
'{"email":"shone.witze@gmail.com"}' \
https://api.offroute.fr/Users/getUserPassword

```

### Requête HTTP :

`PUT https://api.offroute.fr/Users/getUserPassword`

### Arguments attendus :

Afin de lancer la requête, vous n'aurez besoin que de renseigner votre adresse mail, afin que le mot de passe soit modifié, puis vous soit envoyé par mail.

### Retour :

Lorsque la requête a été correctement exécuté, l'API vous préviendra de l'envoi du mail.

Un retour depuis l'API peut être, par exemple :

Paramètres | Valeur
--------- | -------
status_code | 200
Message | Your password has been changed. An email has been sent to you

<aside class="success">
Lorsque les informations ont été correctement modifié, le code de retour (status_code) est le 200.
</aside>


## Suppression du compte

Si un compte doit être supprimé, il faut passer par cette requête.

<aside class="notice">
La requête est en <code>DELETE</code>
</aside>

```shell

time curl -X GET -H "Content-Type: application/json" -H \
"X-Access-Token":"1234567890" -d \
'{"email":"lisa.lewitanski@yahoo.fr", "password":"Secret_unicorn"}'
https://api.offroute.fr/Users/deleteUser

```

### Requête HTTP :

`DELETE https://api.offroute.fr/Users/deleteUser`


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
