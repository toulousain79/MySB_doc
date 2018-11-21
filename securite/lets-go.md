---
description: Lancement de l'installation
---

# Let's go !

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

