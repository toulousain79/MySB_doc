# Labels & Synchros

## Intérêts des labels

Les labels _\(ou catégories\)_ permettent d'organiser vos téléchargements par catégories pour rTorrent et ruTorrent. Des classements par type de fichier ou type de films par exemple.  
Cela créera des dossiers aux noms de vos labels dans différents endroits de vôtre SeedBox:

* /home/user/rtorrent/**complete**/ Emplacement définitif de vos fichiers terminés;
* /home/user/rtorrent/**torrents**/ Emplacement de "sauvegarde" de vos fichiers .torrent envoyés dans les dossiers "watch";
* /home/user/rtorrent/**watch**/ Emplacement surveillé par rTorrent pour "aspirer" vos .torrent et lancer vos téléchargements automatiquement.

Un dossier sera également créé si vous utilisez la synchronisation de vos fichiers vers l'emplacement distant.

Tous les utilisateurs disposant d'un compte **normal** peut gérer des labels.

Le fonctionnement est simple. En prenant en exemple une catégorie nommée **Films\_HD**, on obtiendra l'arborescence suivante:

* /home/user/rtorrent/**complete**/**Films\_HD**/
* /home/user/rtorrent/**torrents**/**Films\_HD**/
* /home/user/rtorrent/**watch**/**Films\_HD**/

1. On envoie un fichier .torrent dans le dossier /home/user/rtorrent/**watch/Films\_HD**/;
2. Le téléchargement se lance, et le fichier téléchargé se retrouve dans /home/user/rtorrent/**complete/Films\_HD**/;
3. Le fichier .torrent envoyé dans /home/user/rtorrent/watch/Films\_HD/ et ensuite déplacé dans /home/user/rtorrent/**torrents/Films\_HD**/.

Si jamais un mode de synchronisation est affecté à cette catégorie, alors le fichier téléchargé sera envoyé vers la destination de vôtre choix. Soit immédiatement une fois le fichier téléchargé, soit de manière programmée à une heure que vous aurez déterminée.

Il est possible de choisir le type de synchronisation à affecter à une catégorie.

* Ignore les scripts _\(Pas de synchro\)_
* Synchronisation programmée
* Synchronisation directe

Un autre intérêt de ces catégories est l'organisation de vos bibliothèques dans Plex si jamais vous décidez de l'utiliser. En gros, une catégorie créée ici correspondra à une bibliothèque dans Plex.

## Gestion des téléchargements terminés

Rendez-vous dans vôtre menu utilisateur.

![](../.gitbook/assets/menu_user_labels.jpg)

Vous pouvez ajouter jusqu'à 5 catégories à la fois en cliquant sur **Ajouter une catégorie**.  
Donnez un nom à toutes vos catégories et sélectionnez un type de synchronisation à chacune d'elles. Pour le nommage, les accents et les espaces sont autorisés lors de la saisie. Mais au final, l'accentuation sera supprimée et les espace remplacés par des des **tirais bas** _\(\_\)_.

Une fois vos catégories ajoutées, cliquez sur **Sauvegarder les modifications**.

![](../.gitbook/assets/labels_add.jpg)

Si vous avez sélectionné **Synchronisation programmée** ou **Synchronisation directe** pour l'une ou plusieurs de vos catégories, de nouvelles options s'afficheront.

1. Crontab / Scripts à utiliser
2. Informations de connexion pour les synchronisations distantes _\(directes et programmées\)_

![](../.gitbook/assets/lables_more.jpg)

### Crontab / Scripts à utiliser

Ici, on sélectionne les scripts à utiliser pour vos synchronisations. Un script différent peut être utiliser pour les synchronisations programmées et directes.  
Un script est déjà proposé remplissant déjà les besoins principaux. Toutefois, vous avez la possibilité d'ajouter tous les scripts que vous désirez dans le dossier **/home/user/scripts/** 🙂 

Le script par défaut est **synchro.sh**.  
Pour l'exemple, j'ai ajouté le script **mon\_script\_perso.sh**.

![](../.gitbook/assets/synchro_scripts.jpg)

Dans l'exemple, les synchronisations programmées seront lancées tous les jours à **0h30** et utiliseront le script **synchro.sh**. Une fois la planification et le script choisit, cliquez sur **Ajouter**.

Pour les synchronisations programmées, il est possible d'affecter autant de programmation qu'il y aura de script.

Comme nous avons ajouté un second script, nous avons pu ajouter une première programmation. Et nous pouvons en ajouter une seconde, en utilisant le second script.



