# FAQ

## Installation

### Lors de l'installation je bloque sur le nom d'hôte FQDN

Si la question demandant vôtre FQDN se répète, c'est probablement que le nom d'hôte que vous souhaitez utiliser ne correspond pas à l'adresse IP publique de vôtre serveur.

Pour vérifier cela, utilisez la commande **nslookup fqdn\_de\_mon\_serveur**:

```bash
root@mysb~ # nslookup www.google.fr
Server:         127.0.0.1
Address:        127.0.0.1#53

Non-authoritative answer:
Name:   www.google.fr
Address: 216.58.210.35
```

Ici, on voit que le FQDN **www.google.fr** pointe vers l'IP **216.58.210.35**.  
Où www.google.fr serait le nom de vôtre serveur, et 216.58.210.35, son adresse IP.

Si jamais vous obtenez un résultat comme celui ci-dessous, ou que l'adresse IP affichée n'est pas celle de vôtre serveur, alors vous avez loupez quelque chose...

```bash
root@mysb~ # nslookup monserveur.mondomaine.com
Server:         127.0.0.1
Address:        127.0.0.1#53

** server can't find monserveur.mondomaine.com: NXDOMAIN
```

## Administrateur

### Système

#### Problème de droits sur des fichiers ou dossiers

Vous ne pouvez plus exécuter les commandes MySB\_\*\*\* ?  
Ou vous avez des problèmes d'accès à certains services ?

Lancez les commandes suivantes, cela restaurera tous les droits où il faut.

```bash
. /opt/MySB/inc/vars
gfnManageDirAndFiles 'global'
```

#### Changer le nom de vôtre serveur

```bash
. /opt/MySB/inc/vars
. /opt/MySB/inc/funcs_by_script/funcs_Upgrade
gfnChangeFQDN
```

### Migrer son serveur

Vous souhaitez migrer vers un nouveau serveur et importer toutes vos données ?

La procédure se déroule en 2 étapes minimum.  
Si le volume est important, cela permettra de gagner du temps lors de la dernière synchronisation et de limiter ainsi le temps de la coupure _\(pouvant se compter en heures...\)_. Il est nécessaire de lancer une première synchronisation _\(before\)_.  
Puis une seconde synchronisation quand vous aurez déterminé le bon moment pour basculer vers le nouveau serveur.

Suivez les étapes suivantes:

#### Installer MySB sur le nouveau serveur

1. laissez le FQDN par défaut, ou saisissez-en un temporaire _\(FQDN valide bien entendu...\)_
2. l'utilisateur principal doit être le même que sur l'ancien serveur _\(le mot de passe importe peu\)_

#### Vérifier la connexion vers le nouveau serveur

```bash
bash /opt/MySB/upgrade/Migrate.bsh check
```

Pour que le résultat soit positif, vous devrez ajouter les adresses IP des 2 serveurs, respectivement, dans les adresses autorisées via le portail.

Idem, le script vous indiquera quoi faire pour effectuer l'échange de la clé SSH pour que l'ancien serveur accède sans mot de passe au nouveau serveur.

#### Lancer une première synchronisation

Sur l'ancien serveur, connectez-vous en ROOT et exécutez la commande suivante pour lancer une première synchronisation: 

```bash
bash /opt/MySB/upgrade/Migrate.bsh before
```

{% hint style="info" %}
Vous pouvez relancer cette commande autant que nécessaire. Surtout s'il se passe plusieurs jours entre la première synchronisation et la suivante.
{% endhint %}

{% hint style="info" %}
Vous pouvez lancer cette première synchronisation en tâche de fond à l'aide de screen.

```bash
screen -dmS MySB_Migrate /bin/bash /opt/MySB/upgrade/Migrate.bsh before ip_nouveau_serveur port_ssh CRON
```

Le paramètre **CRON** permettant d'écrire le déroulement dans le fichier **logs/Migrate.bsh.log**.
{% endhint %}

#### Lancer la dernière synchronisation

Sur l'ancien serveur, connectez-vous en ROOT et exécutez la commande suivante pour lancer une première synchronisation: 

```bash
bash /opt/MySB/upgrade/Migrate.bsh after
```

{% hint style="info" %}
Cette étape laissera l'ancien serveur en mode maintenance. Les services seront donc non disponibles.
{% endhint %}

### Renommer le nouveau serveur _\(optionnel\)_

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

```bash
. /opt/MySB/inc/vars
. /opt/MySB/inc/funcs_by_script/funcs_Upgrade
gfnChangeFQDN "fqdn_de_l_ancien_serveur"
```

### Les 5% de blocs réservés

Par défaut, 5% des blocs du système de fichiers sont réservés et ne peuvent être écrits. Ils sont réservés en "secours" et utilisables uniquement par root.  
Si le système de fichier est grand _\(ex: 1To\)_ ça fait quand même 50Go, surtout si on stocke des données c'est pas utile.  
Mettre à 0% c'est pas l'idéal, mais on peut mettre cette valeur à 1% par exemple.

#### Obtention des infos actuelles

```bash
dumpe2fs -h /dev/sda1 | grep -i 'block count'

dumpe2fs 1.43.4 (31-Jan-2017)
Block count:              5016832
Reserved block count:     250841
```

#### Calcul du pourcentage actuel utilisé

_Nombre de blocs réservés / Nombre de blocs \* 100 = Pourcentage réservé_

**Ex**: 250841 / 5016832 \* 100 = 4,9999880402612644792570291371128 _**\(~5%\)**_

#### Changer le pourcentage de bloc réservé à 1%

```bash
tune2fs -m 1 /dev/sda1
```

#### Vérification

```bash
dumpe2fs -h /dev/sda1 | grep -i 'block count'

dumpe2fs 1.43.4 (31-Jan-2017)
Block count:              5016832
Reserved block count:     50168
```

_Nombre de blocs réservés / Nombre de blocs \* 100 = Pourcentage réservé_

**Ex**: 50168 / 5016832 \* 100 = 0,99999362147267438893708220646017 _**\(~1%\)**_

Pour résumer, il suffit d'utiliser la commande _tune2fs -m **X** /dev/**partition**_, où **X** correspond au pourcentage désiré.

{% hint style="danger" %}
**NE PAS mettre à 0% cet espace réservé !**
{% endhint %}

### Réseau

#### L'adresse IP d'un utilisateur a été bannis par Fail2Ban, par utilisation répétée d'un mauvais mot de passe

Il est nécessaire de restaurer les règles de sécurité par défaut. De cette manière, les bannissements seront purgés.

```bash
MySB_SecurityRules create
```

### Web

#### Je souhaite ajouter un site perso

Il est possible d'héberger un site perso avec MySB, cependant, la gestion restera manuelle. Les ports 80 et 443 pourront être utilisés.

#### Créer une entrée dans NginX

```bash
vi /etc/nginx/sites-available/mon_site

#### Mon site (HTTPs)
server {
        listen 443 default_server ssl http2;
        server_name "mon_site.mon_domaine.org";
        index index.php;
        charset utf-8;

        include snippets/letsencrypt_mon_site.mon_domaine.org.conf;

        access_log /var/log/nginx/mon_site-access.log anonymized;
        error_log /var/log/nginx/mon_site-error.log error;

        root /var/www/html;

        include /etc/nginx/conf.d/static_files;
        include /etc/nginx/conf.d/global_deny_access;
        location ~ \.php$ {
                include /etc/nginx/conf.d/php-ssl;
        }
}

#### Mon site (HTTP)
server {
        listen 80 default_server http2;
        server_name "mon_site.mon_domaine.org";
        index index.php;
        charset utf-8;

        access_log /var/log/nginx/mon_site-access.log anonymized;
        error_log /var/log/nginx/mon_site-error.log error;

        root /var/www/html;

        include /etc/nginx/conf.d/static_files;
        include /etc/nginx/conf.d/global_deny_access;
        location ~ \.php$ {
                include /etc/nginx/conf.d/php;
        }
}
```

{% hint style="info" %}
Les fichiers de votre site internet devront se trouver dans le dossier _**/var/www/html**_.
{% endhint %}

#### Activer le nouveau site avec Nginx

```bash
[[ ! -L /etc/nginx/sites-enabled/mon_site ]] && ln -s /etc/nginx/sites-available/mon_site /etc/nginx/sites-enabled/mon_site
service nginx restart
```

#### Ajouter un FQDN pour Let's Encrypt

```bash
echo "mon_site.mon_domaine.org" >> /opt/MySB/ssl/letsencrypt_domains
/bin/bash /opt/MySB/install/LetsEncrypt renew
```

{% hint style="warning" %}
Pensez à supprimer les FQDN qui ne sont plus valides dans le fichier _**/opt/MySB/ssl/letsencrypt\_domains**_ !
{% endhint %}

## Utilisateurs

### Réseau

#### Vôtre adresse IP a changé et vous n'êtes plus autorisé à vous connecter.

Dans chacun des mails envoyés par MySB _\(contenant MySB dans l'objet...\)_, vous disposez d'un lien permettant de forcer l'ajout d'une nouvelle adresse IP.  
Vous devrez vous identifier pour pouvoir en ajouter une nouvelle.

![](../.gitbook/assets/mail_force_ip.jpg)

L'URL permettant d'ajouter de nouvelles adresses autorisées est formatée ainsi:

[**https://**demo-mysb.dyndns.org:8189**/ForceAddress?page=ManageAddresses**](https://demo-mysb.dyndns.org:8189/ForceAddress?page=ManageAddresses)\*\*\*\*

{% hint style="warning" %}
_**Note**: Faites bien attention d'activer vôtre nouvelle adresse avant d'enregistrer vos modifications._
{% endhint %}

![](../.gitbook/assets/force_ip_add.jpg)

