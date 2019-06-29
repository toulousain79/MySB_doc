# Accueil

MySB _\(My SeedBox\)_ est un projet permettant l'installation d'une SeedBox sécurisée multi-utilisateurs pour un serveur dédié sous Debian 9 _\(Stretch\),_ et pourrait être renommé MySSB, My Secured SeedBox.

Tout l'intérêt de MySB réside dans la sécurité via la gestion de listes de blocage d'IP avec PeerGuardian _\(ou rTorrent\)_ pour les requêtes entrantes, ainsi que la sécurisation des requêtes DNS grâce à DNScrypt-proxy pour les requêtes sortantes.

Les connections SSL sont priorisées par rTorrent.

La gestion des torrents est également simplifiée grâce à NextCloud et au portail MySB pour la synchronisation distante des données par Rsync ou FTPs, la gestion des labels pour rTorrent, ainsi que le filtrage de tous les fichiers .torrent ajoutés.

Une question simple, savez-vous qui se connecte à votre serveur ?

