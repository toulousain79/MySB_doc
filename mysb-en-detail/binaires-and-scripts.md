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
        <p>Permet de mettre &#xE0; jour le syst&#xE8;me, les certificats et les modules
          Python,</p>
        <p>en <b>for&#xE7;ant</b> la <b>conservation</b> des fichiers de configuration.</p>
        <p>Cette commande est ex&#xE9;cut&#xE9;e 1 fois <b>toutes les semaines</b> via
          une t&#xE2;che</p>
        <p>programm&#xE9;e.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">MySB_GitHubRepoUpdate</td>
      <td style="text-align:left">
        <p>Permet de mettre &#xE0; jour la version actuelle de MySB en utilisant
          un <b>git pull</b>.</p>
        <p>Cela permet l&apos;application de petites corrections.
          <br />Cette commande est ex&#xE9;cut&#xE9;e <b>tous les jours &#xE0; 12h00</b>.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">MySB_SecurityRules</td>
      <td style="text-align:left">
        <p>Permet d&apos;appliquer ou supprimer les r&#xE8;gles de s&#xE9;curit&#xE9;
          du syst&#xE8;me.
          <br /><b>Supprime</b> les r&#xE8;gles: <code>MySB_SecurityRules</code>  <b><code>clean</code></b>
        </p>
        <p><b>Recr&#xE9;e</b> toutes les r&#xE8;gles: <code>MySB_SecurityRules</code>  <b><code>create</code></b>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">MySB_UpgradeMe</td>
      <td style="text-align:left">
        <p>Permet de v&#xE9;rifier et/ou d&apos;installer une nouvelle version majeure
          de MySB.</p>
        <p>Cette commande est ex&#xE9;cut&#xE9;e <b>tous les 3 jours</b> &#xE0; 04h00.</p>
        <p>Si une nouvelle version est d&#xE9;tect&#xE9;e, un mail sera envoy&#xE9;
          &#xE0; l&apos;admin</p>
        <p>qui devra lancer la commande manuellement pour proc&#xE9;der &#xE0; la
          mise</p>
        <p>&#xE0; jour.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">MySB_UpdateTools</td>
      <td style="text-align:left">
        <p>Permet de mettre &#xE0; jour certains outils et services comme:</p>
        <ul>
          <li>PlexMedia et Tautulli</li>
          <li>Outils Docker</li>
          <li>Webmin</li>
          <li>Application de certains correctifs</li>
        </ul>
        <p>Cette commande est ex&#xE9;cut&#xE9;e automatiquement &#xE0; chaque fois
          que la</p>
        <p>commande <b>MySB_GitHubRepoUpdate</b> est ex&#xE9;cut&#xE9;e, donc &#xE0;
          minima</p>
        <p><b>tous les jours &#xE0; 12h00</b>.</p>
      </td>
    </tr>
  </tbody>
</table>

### Les scripts usuels

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
        <p>Permet au portail d&apos;interagir avec le serveur.</p>
        <p>Il est appel&#xE9; chaque fois que l&apos;on clique sur <b>Appliquer les modifications</b> dans
          le portail.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">BlocklistsRTorrent.bsh</td>
      <td style="text-align:left">
        <p>Permet la g&#xE9;n&#xE9;ration des listes noires <em>(listes de blocage)</em> qui
          seront utilis&#xE9;es par rTorrent en cas de besoin et copi&#xE9;es pour
          chaque utilisateur. Il se base sur les listes s&#xE9;lectionn&#xE9;es dans
          le portail <em>(<b>Listes noires</b> &gt; <b>rTorrent</b>)</em>.</p>
        <p>Ce script est appel&#xE9; par diff&#xE9;rentes commandes et est ex&#xE9;cut&#xE9; <b>2 fois par jour</b>.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">DynamicAddressResolver.bsh</td>
      <td style="text-align:left">
        <p>Permet l&apos;actualisation des adresses IP dynamiques ajout&#xE9;es par
          tous les utilisateurs.</p>
        <p>Il est ex&#xE9;cut&#xE9; <b>toutes les 5 minutes</b>.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">GetTrackersCert.bsh</td>
      <td style="text-align:left">
        <p>Permet de <b>rafra&#xEE;chir</b> les adresses IP et les <b>certificats SSL</b> de
          tous les trackers activ&#xE9;s dans le portail <em>(<b>Trackers</b> &gt; <b>Liste des trackers</b>)</em>,
          de <b>d&#xE9;tecter</b> et <b>d&apos;ajouter</b> les trackers contenu dans
          les .torrent des utilisateurs.</p>
        <p>Il est appel&#xE9; &#xE0; chaque fois que cette liste est modifi&#xE9;e.</p>
        <p>Ce script est ex&#xE9;cut&#xE9; <b>1 fois par jour</b>.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">LogServerAndQuota.bsh</td>
      <td style="text-align:left">
        <p>Permet de convertir en HTML tous les logs d&apos;exploitation de MySB,
          ainsi que certains journaux syst&#xE8;me pour les rendre accessibles dans
          le portail pour l&apos;administrateur.</p>
        <p>Permet &#xE9;galement de rafra&#xEE;chir le quota pour tous les utilisateurs.</p>
        <p>Ce script est ex&#xE9;cut&#xE9; <b>toutes les heures</b>.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">NextCloud.bsh</td>
      <td style="text-align:left">
        <p>Permet d&apos;actualiser les fichiers contenus dans /home de chaque utilisateur,
          accessibles via <b>MySB_Home</b> dans NextCloud.</p>
        <p>Ce script est ex&#xE9;cut&#xE9; <b>toutes les 5 minutes</b>.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">OpenVPN-Bridge.bsh</td>
      <td style="text-align:left">Ce script est <b>inutilis&#xE9;</b>.</td>
    </tr>
    <tr>
      <td style="text-align:left">PaymentReminder.bsh</td>
      <td style="text-align:left">
        <p>Permet l&apos;actualisation des tr&#xE9;soreries et du tarif par mois
          pour chaque utilisateur.</p>
        <p>Ce script est ex&#xE9;cut&#xE9; &#xE0; chaque <b>ajout</b> ou <b>suppression</b> d&apos;un
          utilisateur ET <b>tous les 1er du mois</b>.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">PeerGuardian.bsh</td>
      <td style="text-align:left">
        <p>Permet &#xE0; la fois de mettre &#xE0; jour les listes noires pour PeerGuardian
          ET de v&#xE9;rifier si le service fonctionne toujours. Si jamais PeerGuardian
          ne r&#xE9;pond plus et qu&apos;il ne peut pas &#xEA;tre red&#xE9;marr&#xE9;,
          c&apos;est rTorrent qui est red&#xE9;marr&#xE9; pour utiliser lui-m&#xEA;me
          les listes noires jusqu&apos;au prochain red&#xE9;marrage de PeerGuardian.</p>
        <p>Ce script est ex&#xE9;cut&#xE9; <b>toutes les 5 minutes</b> avec le param&#xE8;tre <b>check</b>,
          et <b>1 fois par jour</b> &#xE0; <b>23h30</b> avec le param&#xE8;tre <b>update</b>.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">SendMails.bsh</td>
      <td style="text-align:left">
        <p>Permet l&apos;envoie des mails de location, de cr&#xE9;ation et de suppression
          de comptes utilisateur. Ce script a &#xE9;t&#xE9; mis en place pour &#xE9;viter
          l&apos;envoie de mails en doublon.</p>
        <p>Ce script est ex&#xE9;cut&#xE9; <b>toutes les 5 minutes</b>.</p>
      </td>
    </tr>
  </tbody>
</table>

