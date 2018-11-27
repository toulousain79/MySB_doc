# L'envoie de mails

C'est un sujet récurrent pour beaucoup d'entre vous. Beaucoup me dise qu'ils ne reçoivent pas de mail à la fin de l'installation.

Il peut y avoir beaucoup de raisons à cela.  
Les plus courantes rencontrées sont les suivantes:

## Utilisation de la configuration LOCAL

Dans ce cas, c'est vôtre serveur qui enverra tous les mails directement vers vôtre adresse e-mail. Cependant, dans une majorité de cas, les mails seront probablement identifiés comme SPAM.  
Beaucoup d'entre vous laissez le nom d'hôte par défaut attribué par l'hébergeur.  
Et ceci peu poser problème.  
Pensez à vérifier vôtre dossier SPAM dans vôtre boîte mail.

## Utilisation de la configuration GMAIL, YAHOO, ...

Dans cette situation, ce n'est pas compliqué. A chaque fois il s'agit d'une erreur de saisie identifiant/mot de passe...  
Veillez donc à bien saisir vos identifiants 🧐   
Vous pouvez modifier vos identifiants via le portail MySB dans le menu **Admin** &gt; **SMTP**.  
Pour mémo, l'adresse du portail sera formée comme suit:

{% hint style="info" %}
**https**://server.domain.com:**8189**/
{% endhint %}

Sinon, il s'agit d'un problème de sécurité car votre serveur n'a pas les droits de se connecter à votre compte de messagerie pour déléguer l'envoie de mail. Cela arrive régulièrement avec Gmail par exemple, qui limite l'envoie de mail qu'à certaines plate-formes.

Si à la fin de l'installation vous n'avez reçu de mail de confirmation, c'est qu'il est toujours bloqué en file d'attente sur votre serveur. Pour vérifier cela, connectez-vous à votre serveur en ROOT et exécutez la commande suivante:

```text
mailq
```

Si un ou plusieurs mails sont bloqués, vous verrez une liste de ce type:

![Liste de mails bloqu&#xE9;s et en attente](../.gitbook/assets/mailq.jpg)

Ici, nous voyons que l'erreur est **SASL authentication failed**.

Si votre mot de passe est pourtant correct, vous devez alors autoriser les applications moins sécurisées à pouvoir se connecter _\(cf._ [_Pré-requis_](https://mysb.gitbook.io/doc/~/edit/drafts/-LS9xi-gc9Grq6Zkdqn7/v/v5.3_fr/installation/pre-requis#mails)_\)_.

## Autres cas

Dans d'autres situations, c'est qu'il y a eu un problème lors de l'installation... 😏 

