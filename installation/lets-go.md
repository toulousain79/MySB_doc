# Let's go !

## Lancement de l'installation

Connectez-vous en SSH à vôtre serveur avec le compte **ROOT**.  
Puis lancez la commande suivante pour récupérer le script d'installation.

`wget --no-check-certificate -N` [`https://raw.githubusercontent.com/toulousain79/MySB/v5.3/install/MySB_Install.bsh`](https://raw.githubusercontent.com/toulousain79/MySB/MySB_Version/install/MySB_Install.bsh)\`\`

Ensuite, exécutez-le.

`bash MySB_Install.bsh`

Selon la localisation du serveur, une langue par défaut sera chargée, soit le français, soit l'anglais.  
Si vous voulez forcer la langue, il suffit de le préciser en argument.

**Pour l'anglais:**

`bash MySB_Install.bsh en`

**Pour le français:**

`bash MySB_Install.bsh fr` 

![](../.gitbook/assets/install_download_script.jpg)

## Sommaire de l'installation

### Choix du répertoire d'installation

A ce stade, les pré-requis de base sont vérifiés, et les étapes du déroulement de l'installation affichées.

Répondez à la question **Êtes-vous prêt à installer MySB** ? En tapant **oui** ou **o**.

Ensuite, vous pouvez valider le répertoire d'installation par défaut en tapant sur **Entrée**.  
Ou saisissez un autre emplacement si vous savez ce que vous faites. Le répertoire doit être absolut, c'est à dire qu'il doit commencer par / en préfixe du chemin. Et ne doit pas contenir de **/** à la fin.

![](../.gitbook/assets/install_start.jpg)

### Préparatifs

Les préparatifs commencent.  
Nous mettons d'abord à jour les listes sources de Debian.

![](../.gitbook/assets/install_maj_sources.jpg)

Puis l'installation de certains paquets nécessaires au reste des opérations.

![](../.gitbook/assets/install_install_packages.jpg)

Ensuite, nous téléchargeons le contenu de MySB versionné sur GitHub, à destination du répertoire d'installation choisi, normalement vers **/opt/MySB**. Ces fichiers sont le socle de fonctionnement de MySB.  
Puis, la création de certains répertoires utiles au fonctionnement.  
Et enfin, la création et la population des bases de données MySQL et SQLite.

![](../.gitbook/assets/install_github_mysql.jpg)

