# Avertissements

## Connaissance de Linux

**TOUS** vos noms d'utilisateur et votre mot de passe doivent être écrits sans espace.

**NE PAS** modifier n'importe quoi dans votre serveur, si vous avez un doute posez votre question avant.

**NE PAS** essayer de reconfigurer les paquets en utilisant d'autres tutoriels ou vous-même. Cela pourrait poser des problèmes quand vous mettrez à jour MySB. Ou même générer un dysfonctionnement de MySB.

**POUR METTRE A JOUR** votre système, utilisez la commande **MySB\_UpgradeSystem**. Cette commande est comparable, en partie, à apt-get update + apt-get upgrade.

## Serveurs OVH \(OVH, KimSufi, SoYouStart\)

* Utilisez le noyau de distribution par défaut. Dans votre interface de gestion OVH, lorsque vous démarrez le processus d'installation, choisissez Installation personnalisée et Utilisation du noyau de la distribution.
* Vous pouvez monitorer votre serveur. Il faut simplement le spécifier lors de l'installation de MySB. MAIS, il faut désactiver ce service dans l'interface OVH avant l'installation de MySB. Si vous autorisez la surveillance avec MySB, les adresses IP de votre fournisseur seront ajoutées à la liste blanche globale \(PeerGuardian, Fail2Ban, IPTables\) et ces adresses ne seront pas filtrées.
* Si vous laissez active la surveillance de votre serveur dans l'interface OVH, ET que vous ne l'avez pas activé pendant l'installation de MySB, votre serveur pourrait être redémarré en mode secours par le personnel OVH... Si vous souhaitez utiliser le service de monitoring , alors vous devez d'abord le désactiver AVANT de démarrer l'installation de MySB. Vous pourrez le réactiver APRÈS la FIN de l'installation. Vous pouvez également désactiver le Real Time Monitoring \(RTM\), lire cette page. [Real Time Monitoring \(RTM\)](http://www.torrent-invites.com/showthread.php?t=39022)

