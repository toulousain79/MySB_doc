# Restriction par adresse IP

Il est possible de restreindre l'accès à votre serveur en fonction de certaines adresse IP.
Il faut savoir que tous les services présents dans votre SeedBox ne seront pas soumis à cette restriction.

**Soumis à la restriction par adresse IP**

* accès SSH
* accès FTPs et sFTP
* accès au portail MySB
* OpenVPN
* services Web _\(sauf exception\)_:
  * ruTorrent
  * Cakebox
  * Seedbox-Manager
  * LoadAvg
  * Shell In a Box

**Non soumis à la restriction par adresse IP** _**\(mais filtré par Fail2Ban\)**_

* services Web**:**
  * Tautulli
  * Plex Media Server
  * NextCloud

Les adresses autorisées _\(IP ou FQDN\)_ devront être ajoutées [via le portail](https://mysb.gitbook.io/doc/v/v5.4_fr/configuration/ajout-de-vos-adresses).
Chaque utilisateur "normal" pourra ajouter ses adresses en toute autonomie.

Mais l'ensemble des adresses ajoutées sera inclus de manière globale, c'est à dire applicable pour tout le monde.
