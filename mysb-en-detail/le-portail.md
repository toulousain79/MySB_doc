# Le portail

Le portail est basé sur [Wolf](https://github.com/wolfcms/wolfcms), un [CMS](https://fr.wikipedia.org/wiki/Syst%C3%A8me_de_gestion_de_contenu) léger utilisant une base de données SQLite, et utilisant un [template](https://www.css3templates.co.uk/) adapté pour le besoin de MySB.

L'URL d'accès au portail est formatée comme suit:

{% hint style="info" %}
https://monserver.domain.com:**8189**/
{% endhint %}

Tous les utilisateurs n'auront pas accès aux même menus.  
Le portail a été scindé 3 groupes:

1. Utilisateur principal _\(administrateur\)_
2. Utilisateurs standards _\(session rTorrent\)_
3. Utilisateurs Plex

## Utilisateurs Plex

Les utilisateurs Plex disposent d'un accès très limité au portail.

### Menu Services

* NetData

### Menu Utilisateur

* Informations du compte _\(affichage minimum\)_
* Options MySB
  * choix de la langue du portail
* Modification du mot de passe
* Gestion des adresses
* Modification de l'adresse e-mail
* Information de location
  * Trésorerie
  * Statut des périodes

## Utilisateurs standards _\(session rTorrent\)_

Les utilisateurs standards disposent d'un accès plus complet au portail.

### Menu Services

* ruTorrent
* NextCloud
* NetData
* Seedbox-Manager
* Cakebox-Light

### Menu Utilisateur

* Informations du compte
* Gestion des adresses
* Modification de l'adresse e-mail
* Modification du mot de passe
* OpenVPN
* Options MySB
  * choix de la langue du portail
  * redémarrer rTorrent
  * notification email
* Labels & Synchros
* Information de location
  * Trésorerie
  * Statut des périodes

### Menu Trackers

* Liste des trackers _\(lecture seule\)_

### Menu Listes noires

* PeerGuardian _\(lecture seule\)_
* rTorrent _\(lecture seule\)_

## Utilisateur principal _\(administrateur\)_

L'utilisateurs _standards_ disposent d'un accès plus complet au portail.

### Menu Services

* ruTorrent
* Tautulli
* NextCloud
* NetData
* Seedbox-Manager
* Cakebox-Light
* Shell In a Box

### Menu Utilisateur

* Informations du compte
* Gestion des adresses
* Modification de l'adresse e-mail
* Modification du mot de passe
* OpenVPN
* Options MySB
  * choix de la langue du portail
  * redémarrer rTorrent
  * notification email
* Labels & Synchros

### Menu Trackers

* Liste des trackers
* Mes trackers

### Menu Listes noires

* PeerGuardian
* rTorrent

### Menu Location _\(si activée\)_

* Gestion locative
* Options de location
* Paiements

### Menu Admin

* Utilisateurs
* SMTP
* Options système
* Plex.tv
* Logs
* DNScrypt-proxy
* Webmin

