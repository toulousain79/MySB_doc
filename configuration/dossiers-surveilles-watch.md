# Dossiers surveillés \(watch\)

Pour ceux qui ne connaissent pas, le dossier **watch** est géré par rTorrent.  
Ce dossier est surveillé continuellement par rTorrent pour vérifier la présence de nouveaux fichiers .torrent.  
Chaque fichier .torrent ajouté ici, est alors aspiré par rTorrent pour lancer automatiquement le téléchargement de celui-ci.

Dans MySB, cela va un plus loin grâce aux catégories que l'on ajoute via le portail.

On va reprendre les exemples donnés dans le chapitre [Labels & Synchros](https://mysb.gitbook.io/doc/v/v5.3_fr/configuration/labels-and-synchros).  
Nous avons ajouté 4 catégories:

1. Animation
2. Applications
3. Films HD
4. Films mHD

Chacune de ces catégories sont maintenant présentes dans différents endroit de vôtre serveur, dont le dossier **watch**. Pour pouvoir envoyer vos fichier .torrent dans l'une de ces catégories du dossier **watch**, plusieurs moyen sont possibles:

* FTPs/sFTP
* Samba _\(via OpenVPN\)_
* NextCloud

<table>
  <thead>
    <tr>
      <th style="text-align:left">FTPs/sFTP</th>
      <th style="text-align:left">Samba (via OpenVPN)</th>
      <th style="text-align:left">Nextcloud</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">
        <p></p>
        <p>
          <img src="../.gitbook/assets/watch_ftps.jpg" alt/>
        </p>
      </td>
      <td style="text-align:left">
        <p></p>
        <p>
          <img src="../.gitbook/assets/watch_samba.jpg" alt/>
        </p>
      </td>
      <td style="text-align:left">
        <p></p>
        <p>
          <img src="../.gitbook/assets/watch_nextcloud.jpg" alt/>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><a href="https://mysb.gitbook.io/doc/v/v5.3_fr/configuration/ftps-sftp">Acc&#xE8;s FTPs/sFTP</a>
      </td>
      <td style="text-align:left"><a href="https://mysb.gitbook.io/doc/v/v5.3_fr/configuration/openvpn">Acc&#xE8;s OpenVPN</a>
      </td>
      <td style="text-align:left"><a href="https://mysb.gitbook.io/doc/v/v5.3_fr/configuration/nextcloud">Acc&#xE8;s NextCloud</a>
      </td>
    </tr>
  </tbody>
</table>

