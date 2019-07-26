# Contenu

* **rTorrent** _\(Rakshasa\) \(v0.9.7 avec SSL\)_
* **libTorrrent** _\(Rakshasa\) \(v0.13.7\)_
* **ruTorrent + plugins officiels**
* **NginX** _\(SSL, port spécifique et certaines personnalisations\)_
* **PHP7.1-FPM**
* **sFTP** _avec Chroot_
* **FTPs** _\(FTP via TLS\)_
* **Postfix** avec _\(ou sans\)_ authentication SMTP _\(Gmail, Free, Ovh, Yahoo and Zoho\)_
* **Seedbox-Manager** _\(optionnel\)_
* **LoadAvg** _\(analyse et surveillance du serveur\)_
* **NextCloud** _\(optionnel mais **recommandé**\)_
* **OpenVPN** _\(optionnel\); multi configuration TUN/TAP, avec ou sans redirection du traffic. Support de AES-NI._
* **CakeBox-Light** _\(optionnel\)_
* **PlexMedia Server** _\(optionnel, nécessite une configuration manuelle supplémentaire\)_
* **Tautulli** _\(si Plexmedia est installé\)_
* **Shell In A Box**
* **Webmin** _\(optionnel\)_
* **Partage Samba** pour chaque utilisateur _\(via l'accès VPN\)_
* **Partage NFS** pour chaque utilisateur _\(via l'accès VPN\)_
* **PeerGuardian** pour la gestion des listes de blocage _\(optionnel mais **recommandé**\)_
* **DNScrypt-proxy** avec Bind9 en tant que cache DNS _\(optionnel mais **recommandé**\)_
* **Let's Encrypt** _\(obtention d'un certificat signé gratuit pour l'accès au portail MySB et de tous les services Web\)_
* **Fail2ban** _\(optionnel mais **recommandé**\)_
* **RKHunter**
* **Portail MySB** \(_possibilité de gérer les trackers, les listes de blocages, les utilisateurs, rTorrent et plus encore\)_
* **Fonctions spéciales de MySB**
  * Récupération automatique des certificats SSL pour tous les trakers _\(si un certificat est disponible\)_
  * Bloquer toutes les possibilités d'utiliser les trackers listés qui n'ont pas été activés dans le portail MySB
  * Utilisation de listes de blocage _\(optionnel\) \(PeerGuardian ou rTorrent, si PeerGuardian n'a pas réussi à démarrer, rTorrent utilisera ses propres listes de blocage\)_
  * Service de surveillance disponible pour certains hébergeurs _\(OVH, Online, Digicube et Hetzner\)_
  * Accès restreint par IP pour tout accès au serveur _\(peut être désactivé\)_
  * Gestion de vos IP dynamiques pour la restriction par IP _\(DynDNS, No-IP, ...\)_
  * Sélection de la langue _\(anglais ou français\)_
  * Utilisation de scripts après un téléchargement terminé _\(Synchronisation directe ou programmée, via FTPs ou rsync\)_
  * Prioriser les connexions sécurisées via SSL pour rTorrent _\(dépend des trackers\)_
  * Création automatique de plusieurs dossiers 'Watch' pour rTorrent _\(Gestion via le portail MySB\)_
  * Accès aux dossiers 'Watch' via FTPs, sFTP, Samba _\(via OpenVPN\)_ ou NextCloud _\(interface web ou application cliente\)_
  * Chiffrement des requêtes DNS sortantes grâce à DNScrypt-proxy
  * Système de mise à jour de votre Seedbox
  * Gestion des connexions UDP
  * [Recyclage des téléchargements](../configuration/options-systemes.md#recyclage-des-telechargements)
    * Copie simple
    * Lien dur
  * [Gestion du type des trackers](../configuration/options-systemes.md#trackers-autorises)
    * Autorisation de tous les trackers _\(privés & publiques\)_
    * Autorisation des trackers privés uniquement
  * Filtrage des annonceurs dans un .torrent
    * Ajout automatique du tracker et de ces annonceurs dans le portail
    * Désactivation automatique des annonceurs en IPv6
    * Blocage manuel d'un tracker via le portail
    * [Blocage automatique des annonceurs présents dans une liste de blocage](../configuration/options-systemes.md#auto-blocks-annonceurs)

