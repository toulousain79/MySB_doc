# Pré-requis

## Matériel

Je sais que l'idée de prendre le serveur le moins cher possible compte. Il n'y a pas vraiment de configuration matériel à proprement parlé. C'est à vous de déterminer ce qu'il vous faut.

Cependant, il y a tout de même quelques bases à respecter si possible. Dans tous les cas, l'installation sera possible, ainsi que l'utilisation. Mais vous pourriez rencontrer quelques désagréments lors l’utilisation de Plex par exemple. Ou alors une installation relativement longue.

Le **processeur**, autant que faire ce peu, évitez les processeurs **Atom**.  
C'est vrai, c'est moi cher, mais aussi beaucoup moins rapide, surtout si vous faites du multi-utilisateurs et du Plex.

La **mémoire**, 4 Go ça peut le faire, **8 Go** étant un minimum selon moi, surtout si vous faites du multi-utilisateurs. L'installation sera impossible si vous avez moins de 2 Go, mais pas recommandé.

Le **système**, Debian 9 _\(Strectch\)_ avec le _**noyau par défaut**_ de Debian, un accès **ROOT** et rien d'autre.

L' **espace disque**, ben là, je dois dire que je m'en fout un peu, c'est vôtre problème 😉   
Cela dit, un minimum vital de **4 Go** pour permettre l’installation de MySB.  
Il est possible de prendre des serveurs dédiés avec 2 disques pour faire du RAID0.  
Pour un serveur de 2 disques de 3 To, un RAID0 vous donnera 6 To. Mais en faisant cela, je vise plutôt l'accès disque _\(lecture + écriture\)_ qui sera doublé. Le RAID0 peut-être dangereux, car si un disque lâche, on perd toutes les données...  
Je me dis que ces serveurs se trouvent dans des sales blanches, protégés comme il le faut _\(normalement\),_ en tout cas mieux qu'à la maison. C'est également un choix que de choisir des disques **Entreprise** lors de l'acquisition d'un serveur, étant plus fiables. Et je dois dire que les données stockées ne sont pas vitales...

La **bande passante**, le minimum étant une connexion de 100 Mbits.  
On peut trouver des connexions à 250 Mbits et même 1 Gbits. Ça dépendra de vos moyens, mais surtout de vôtre usage. Car si vous avez 5 utilisateurs ou plus en concurrence sur Plex, et bien il faut que le serveur puisse fournir un flux correct pour tout le monde.

**Une configuration intéressante**:

* **Processeur:** Intel i7
* **Mémoire:** 16 Go
* **Disques:** 2x3 To en RAID0 _\(disques Enterprise\)_
* **Réseau:** 1 Gbits
* **Utilisateurs:** 7 _\(ex: 3 normaux avec rTorrent + 4 Plex uniquement en partageant la bibliothèque\)_
* **Prix:** ~31 € / mois \(soit 4,47€ / utilisateur\)

## Mails

Si vous souhaitez utiliser un relais de messagerie pour déléguer l'envoie de vos mails, pensez à autoriser des applications externes à se connecter à votre compte de messagerie.

### Gmail

Dans les paramètres de Gmail, activez l'option **Paramètre "Autoriser les applications moins sécurisées"** disponible sur [cette page](https://myaccount.google.com/security#connectedapps).

{% hint style="warning" %}
_**NOTE**: Faites attention d'être connecté avec le bon compte..._
{% endhint %}

Pour Gmail, il est également probable d'utiliser le lien ci-dessous pour autoriser vôtre serveur à se connecter à vôtre compte mail.  
Pour se faire, suivez les étapes suivantes jsute avant l'installation de MySB:

1. Ouvrez ce lien: [https://www.google.com/accounts/DisplayUnlockCaptcha](https://www.google.com/accounts/DisplayUnlockCaptcha)
2. Identifiez-vous avec le compte mail que vous souhaitez utiliser

