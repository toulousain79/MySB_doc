---
description: Commandes et scripts disponibles en console
---

# Console

## Introduction

Différentes commandes et scripts sont disponibles en console pour l'utilisateur principal.

Les commandes _\(ou binaires\)_, sont stockés dans le dossier /opt/MySB/**bin**/, et chargées dans l'environnement de l'utilisateur ROOT.  
Elles servent à l'exploitation continue du serveur et sont, pour certaines, utilisées par le portail pour interagir avec le système.

* MySB\_ChangeUserPassword
* MySB\_CreateUser
* MySB\_DeleteUser
* MySB\_GitHubRepoUpdate
* MySB\_SecurityRules
* MySB\_UpdateTools
* MySB\_UpgradeMe
* MySB\_UpgradeSystem

Les scripts, sont quant à eux, des outils complémentaires utilisés par les commandes précédentes.  
Ils sont stockés dans le dossier /opt/MySB/**scripts**/.

* ApplyConfig.bsh
* BlocklistsRTorrent.bsh
* DynamicAddressResolver.bsh
* GetTrackersCert.bsh
* LogServerAndQuota.bsh
* NextCloud.bsh
* OpenVPN-Bridge.bsh
* PaymentReminder.bsh
* PeerGuardian.bsh
* SendMails.bsh

## Les commandes MySB

### Gestion des utilisateurs

Bien qu'il soit possible de gérer les utilisateurs via le portail, les mêmes commandes sont accessibles en ligne de commande.

| Commandes | Description |
| :--- | :--- |
| MySB\_CreateUser | Permet d'ajouter un nouvel utilisateur |
| MySB\_ChangeUserPassword | Permet de modifier le mot de passe d'un utilisateur |
| MySB\_DeleteUser | Permet de supprimer un utilisateur |

### Gestion de la SeedBox

<table>
  <thead>
    <tr>
      <th style="text-align:left">Commandes</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">MySB_UpgradeSystem</td>
      <td style="text-align:left">
        <p>Permet de mettre à jour le système, les certificats et les modules Python,</p>
        <p>en <b>forçant </b>la <b>conservation </b>des fichiers de configuration.</p>
        <p>Cette commande est exécutée 1 fois <b>toutes les semaines</b> via une tâche</p>
        <p>programmée.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">MySB_GitHubRepoUpdate</td>
      <td style="text-align:left">
        <p>Permet de mettre à jour la version actuelle de MySB en utilisant un <b>git pull</b>.</p>
        <p>Cela permet l'application de petites corrections.
          <br />Cette commande est exécutée <b>tous les jours à 12h00</b>.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">MySB_SecurityRules</td>
      <td style="text-align:left">
        <p>Permet d'appliquer ou supprimer les règles de sécurité du système.
          <br
          /><b>Supprime </b>les règles: <code>MySB_SecurityRules </code><b><code>clean</code></b>
        </p>
        <p><b>Recrée</b> toutes les règles: <code>MySB_SecurityRules </code><b><code>create</code></b>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">MySB_UpgradeMe</td>
      <td style="text-align:left">
        <p>Permet de vérifier et/ou d'installer une nouvelle version majeure de MySB.</p>
        <p>Cette commande est exécutée <b>tous les 3 jours</b> à 04h00.</p>
        <p>Si une nouvelle version est détectée, un mail sera envoyé à l'admin</p>
        <p>qui devra lancer la commande manuellement pour procéder à la mise</p>
        <p>à jour.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">MySB_UpdateTools</td>
      <td style="text-align:left">
        <p>Permet de mettre à jour certains outils et services comme:</p>
        <ul>
          <li>PlexMedia et Tautulli</li>
          <li>Outils Docker</li>
          <li>Webmin</li>
          <li>Application de certains correctifs</li>
        </ul>
        <p>Cette commande est exécutée automatiquement à chaque fois que la</p>
        <p>commande <b>MySB_GitHubRepoUpdate</b> est exécutée, donc à minima</p>
        <p><b>tous les jours à 12h00</b>.</p>
      </td>
    </tr>
  </tbody>
</table>## Les scripts usuels

<table>
  <thead>
    <tr>
      <th style="text-align:left">Scripts</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">ApplyConfig.bsh</td>
      <td style="text-align:left">
        <p>Permet au portail d'interagir avec le serveur.</p>
        <p>Il est appelé chaque fois que l'on clique sur <b>Appliquer les modifications</b> dans
          le portail.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">BlocklistsRTorrent.bsh</td>
      <td style="text-align:left">
        <p>Permet la génération des listes noires <em>(listes de blocage)</em> qui
          seront utilisées par rTorrent en cas de besoin et copiées pour chaque utilisateur.
          Il se base sur les listes sélectionnées dans le portail <em>(<b>Listes noires</b> > <b>rTorrent</b>)</em>.</p>
        <p>Ce script est appelé par différentes commandes et est exécuté <b>2 fois par jour</b>.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">DynamicAddressResolver.bsh</td>
      <td style="text-align:left">
        <p>Permet l'actualisation des adresses IP dynamiques ajoutées par tous les
          utilisateurs.</p>
        <p>Il est exécuté <b>toutes les 5 minutes</b>.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">GetTrackersCert.bsh</td>
      <td style="text-align:left">
        <p>Permet de rafraîchir les adresses IP et les certificats SSL de tous les
          trackers activés dans le portail <em>(<b>Trackers </b>> <b>Liste des trackers</b>)</em>,
          de détecter et d'ajouter les trackers contenu dans les .torrent des utilisateurs.</p>
        <p>Il est appelé à chaque fois que cette liste est modifiée.</p>
        <p>Ce script est exécuté <b>1 fois par jour</b>.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">LogServerAndQuota.bsh</td>
      <td style="text-align:left">
        <p>Permet de convertir en HTML tous les logs d'exploitation de MySB, ainsi
          que certains journaux système pour les rendre accessibles dans le portail
          pour l'administrateur.</p>
        <p>Permet également de rafraîchir le quota pour tous les utilisateurs.</p>
        <p>Ce script est exécuté <b>toutes les heures</b>.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">NextCloud.bsh</td>
      <td style="text-align:left">
        <p>Permet d'actualiser les fichiers contenus dans /home de chaque utilisateur,
          accessibles via <b>MySB_Home</b> dans NextCloud.</p>
        <p>Ce script est exécuté <b>toutes les 5 minutes</b>.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">OpenVPN-Bridge.bsh</td>
      <td style="text-align:left">Ce script est <b>inutilisé</b>.</td>
    </tr>
    <tr>
      <td style="text-align:left">PaymentReminder.bsh</td>
      <td style="text-align:left">
        <p>Permet l'actualisation des trésoreries et du tarif par mois pour chaque
          utilisateur.</p>
        <p>Ce script est exécuté à chaque <b>ajout</b> ou <b>suppression</b> d'un utilisateur
          ET <b>tous les 1er du mois</b>.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">PeerGuardian.bsh</td>
      <td style="text-align:left">
        <p>Permet à la fois de mettre à jour les listes noires pour PeerGuardian
          ET de vérifier si le service fonctionne toujours. Si jamais PeerGuardian
          ne répond plus et qu'il ne peut pas être redémarré, c'est rTorrent qui
          est redémarré pour utiliser lui-même les listes noires jusqu'au prochain
          redémarrage de PeerGuardian.</p>
        <p>Ce script est exécuté <b>toutes les 5 minutes</b> avec le paramètre <b>check</b>,
          et <b>1 fois par jour</b> à <b>23h30</b> avec le paramètre <b>update</b>.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">SendMails.bsh</td>
      <td style="text-align:left">
        <p>Permet l'envoie des mails de location, de création et de suppression de
          comptes utilisateur. Ce script a été mis en place pour éviter l'envoie
          de mails en doublon.</p>
        <p>Ce script est exécuté <b>toutes les 5 minutes</b>.</p>
      </td>
    </tr>
  </tbody>
</table>