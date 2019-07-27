# Migrer son serveur

Vous souhaitez migrer vers un nouveau serveur et importer toutes vos données ?

La procédure se déroule en 2 étapes minimum.  
Si le volume est important, cela permettra de gagner du temps lors de la dernière synchronisation et de limiter ainsi le temps de la coupure _\(pouvant se compter en heures...\)_. Il est nécessaire de lancer une première synchronisation _\(before\)_.  
Puis une seconde synchronisation quand vous aurez déterminé le bon moment pour basculer vers le nouveau serveur.

Suivez les étapes suivantes:

## 1/5 - Installer MySB sur le nouveau serveur

1. laissez le FQDN par défaut, ou saisissez-en un temporaire _\(FQDN valide bien entendu...\)_
2. l'utilisateur principal doit être le même que sur l'ancien serveur _\(le mot de passe importe peu\)_

## 2/5 - Vérifier la connexion vers le nouveau serveur

```bash
bash /opt/MySB/upgrade/Migration.bsh check
```

Pour que le résultat soit positif, vous devrez ajouter les adresses IP des 2 serveurs, respectivement, dans les adresses autorisées via le portail.

Idem, le script vous indiquera quoi faire pour effectuer l'échange de la clé SSH pour que l'ancien serveur accède sans mot de passe au nouveau serveur.

## 3/5 - Lancer une première synchronisation

Sur l'ancien serveur, connectez-vous en ROOT et exécutez la commande suivante pour lancer une première synchronisation: 

```bash
bash /opt/MySB/upgrade/Migration.bsh before
```

{% hint style="info" %}
Vous pouvez relancer cette commande autant que nécessaire. Surtout s'il se passe plusieurs jours entre la première synchronisation et la suivante.
{% endhint %}

{% hint style="info" %}
Vous pouvez lancer cette première synchronisation en tâche de fond à l'aide de screen.

```bash
screen -dmS MySB_Migration /bin/bash /opt/MySB/upgrade/Migration.bsh before ip_nouveau_serveur port_ssh CRON
```

Le paramètre **CRON** permettant d'écrire le déroulement dans le fichier **logs/Migrate.bsh.log**.
{% endhint %}

## 4/5 - Mise en maintenance de l'ancien serveur

Afin de bloquer l'accès à l'ancien serveur pour tous les utilisateurs, il faut passer l'ancien serveur en mode maintenance. Ainsi, plus aucune modification ne sera faite sur le système de fichiers.

```bash
bash /opt/MySB/upgrade/Migration.bsh lock_old
```

## 5/5 - Lancer la dernière synchronisation

Sur l'ancien serveur, connectez-vous en ROOT et exécutez la commande suivante pour lancer la dernière synchronisation: 

```bash
bash /opt/MySB/upgrade/Migration.bsh after
```

{% hint style="info" %}
Cette étape forcera l'ancien serveur en mode maintenance. Les services seront donc non disponibles.
{% endhint %}

## Réutiliser l'ancien nom d'hôte _\(optionnel\)_

Dans le cas où le FQDN de l'ancien serveur pointe sur un domaine dont vous avez la main, vous pouvez attribuer l'ancien FQDN à vôtre nouveau serveur.

Ceci est intéressant si vous _\(et vos utilisateurs\)_ avez des favoris enregistrés, ou utilisez NextCloud par exemple.  
Déplacer le FQDN de l'ancien vers le nouveau serveur vous évitera de modifier ce FQDN partout...

{% hint style="warning" %}
Ceci est à faire uniquement lorsque le transfert sera effectif et quand vous aurez choisit le moment pour basculer définitivement de serveur.
{% endhint %}

{% hint style="danger" %}
**Il est impératif que l'ancien FQDN pointe sur la nouvelle adresse IP !**
{% endhint %}

Connectez-vous en **ROOT** sur le nouveau serveur, et exécutez les commandes suivantes:

Vérifiez que le'ancien FQDN point bien sur la nouvelle adresse IP:

```bash
grep 'Address: ' <<<"$(demo-mysb.dyndns.org)"
Address: ma_nouvelle_IP
```

Quand c'est validé, alors on peut renommer le nouveau serveur:

```bash
. /opt/MySB/inc/vars
. /opt/MySB/inc/funcs_by_script/funcs_Upgrade
gfnChangeFQDN "fqdn_de_l_ancien_serveur"
```

