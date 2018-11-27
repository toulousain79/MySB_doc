# FAQ

Administrateur

### Système

#### Problème de droits sur des fichiers ou dossiers

Vous ne pouvez plus exécuter les commandes MySB\_\*\*\* ?  
Ou vous avez des problèmes d'accès à certains services ?

Lancez ces commandes suivantes, cela restaurera tous les droits où il faut.

`source /opt/MySB/inc/vars  
gfnManageDirAndFiles 'global'`

### Réseau

#### L'adresse IP d'un utilisateur a été bannis par Fail2Ban, par utilisation répété d'un mauvais mot de passe.

Il est nécessaire de restaurer les règles de sécurité par défaut. De cette manière, les bannissements seront purgés.

`MySB_SecurityRules create`

### Web

#### Je souhaite ajouter un site perso

Techniquement c'est possible, je détaillerai plus tard comment procéder.

## Utilisateurs

### Réseau

#### Vôtre adresse IP a changé et vous n'êtes plus autorisé à vous connecter.

Dans chacun des mails envoyés par MySB, vous disposez d'un lien permettant de forcer l'ajout d'une nouvelle adresse IP.  
Vous devrez vous identifier pour pouvoir en ajouter une nouvelle.

![](../.gitbook/assets/mail_force_ip.jpg)

L'URL permettant d'ajouter de nouvelles adresses autorisées est formatée ainsi:

[**https://**demo-mysb.dyndns.org:8189**/ForceAddress?page=ManageAddresses**](https://demo-mysb.dyndns.org:8189/ForceAddress?page=ManageAddresses)\*\*\*\*

{% hint style="warning" %}
_**Note**: Faites bien attention d'activer vôtre nouvelle adresse avant d'enregistrer vos modifications._
{% endhint %}

![](../.gitbook/assets/force_ip_add.jpg)

