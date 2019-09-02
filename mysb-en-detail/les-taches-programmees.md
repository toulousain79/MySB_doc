# Les tâches programmées

## Network Time Protocol \(NTP\)

[`0 0,6,12,18 * * *`](https://crontab.guru/#0_0,6,12,18_*_*_*)`/usr/sbin/ntpdate -u 0.fr.pool.ntp.org > /dev/null 2>&1`

Cette tâche permet de s'assurer que le serveur est toujours à l'heure.  
La synchronisation [NTP ](https://fr.wikipedia.org/wiki/Network_Time_Protocol)est trop souvent oubliée...

## GeoIP

[`48 2 9 * *`](https://crontab.guru/#48_2_9_*_*)`/usr/local/bin/geoipupdate > /dev/null 2>&1`

Fonctionnalité exploitée par PHP pour obtenir des informations de géolocalisation d'une adresse IP.  
L'horodatage d'exécution de cette tâche est calculée dynamiquement lors de l'installation de MySB.

## Rootkit Hunter \(RKHunter\)

 [**RKHunter**](https://fr.wikipedia.org/wiki/Rkhunter) ****est un programme Unix qui permet de détecter les rootkits, portes dérobées et exploits.

[`0 4 * * *`](https://crontab.guru/#0_4_*_*_*)`/usr/local/bin/rkhunter --cronjob --update --quiet > /dev/null 2>&1`

Cette tâche, exécutée **tous les jours** à **4h00**, permet de mettre à jour la base de données de l'outil et de lancer une vérification.

## **DNScrypt-proxy**

\*\*\*\*[`0 4 * * *`](https://crontab.guru/#0_4_*_*_*)_`service dnscrypt-proxy full-update > /dev/null 2>&1`_

Permet la mise à jour de la base de données de l'outil ainsi qu'une actualisation des résolveurs utilisés.  
Cette tâche est exécutée **tous les jours** à **4h00**.

[`*/5 * * * *`](https://crontab.guru/#*/5_*_*_*_*)`service dnscrypt-proxy cron-check > /dev/null 2>&1`

Si DNScrypt-proxy est activé, permet de redémarrer le service si celui-ci ne l'est pas.  
Cette tâche est exécutée **toutes les 5 minutes**.

## Plex Media Server & Tautulli

\_\_[_`*/5 * * * *`_](https://crontab.guru/#*/5_*_*_*_*)_`systemctl status plexmediaserver >/dev/null || systemctl restart plexmediaserver`_

[`*/5 * * * *`](https://crontab.guru/#*/5_*_*_*_*)`systemctl status tautulli >/dev/null || systemctl restart tautulli`

Toutes les 5 minutes, les services Plex Media Server et Tautulli sont vérifiés pour qu'ils soient bien démarrés.

## Sessions rTorrent

[_`*/5 * * * *`_](https://crontab.guru/#*/5_*_*_*_*)`/bin/bash /home/demo/.rTorrent_tasks.sh status`

**Toutes les 5 minutes**, toutes les sessions rTorrent de tous les utilisateurs sont vérifiées pour qu'elles soient bien démarrées.

## Système

[`0 12 * * *`](https://crontab.guru/#0_12_*_*_*)`/bin/bash /opt/MySB/bin/MySB_GitHubRepoUpdate CRON > /dev/null 2>&1`

[`0 2 * * */7`](https://crontab.guru/#0_2_*_*_*/7)`/bin/bash /opt/MySB/bin/MySB_UpgradeSystem CRON > /dev/null 2>&1`

[`0 4 */3 * *`](https://crontab.guru/#0_4_*/3_*_*)`/bin/bash /opt/MySB/bin/MySB_UpgradeMe CRON > /dev/null 2>&1`

[`0 1 * * */7`](https://crontab.guru/#0_1_*_*_*/7)`/bin/bash /opt/MySB/install/SourcesList CRON > /dev/null 2>&1`

[`0 2 * * */1`](https://crontab.guru/#0_2_*_*_*/1)`/bin/bash /opt/MySB/install/LetsEncrypt renew CRON > /dev/null 2>&1`

[`10 11,23 * * *`](https://crontab.guru/#10_11,23_*_*_*)`/bin/bash /opt/MySB/scripts/BlocklistsRTorrent.bsh CRON > /dev/null 2>&1`

[`5 0 */1 * *`](https://crontab.guru/#5_0_*/1_*_*)`/bin/bash /opt/MySB/scripts/PaymentReminder.bsh CRON > /dev/null 2>&1`

[`10 0 */1 * *`](https://crontab.guru/#10_0_*/1_*_*)`/bin/bash /opt/MySB/scripts/GetTrackersCert.bsh CRON > /dev/null 2>&1`

[`30 23 * * *`](https://crontab.guru/#30_23_*_*_*)`/bin/bash /opt/MySB/scripts/PeerGuardian.bsh update CRON > /dev/null 2>&1`

[`0 */1 * * *`](https://crontab.guru/#0_*/1_*_*_*)`/bin/bash /opt/MySB/scripts/LogServerAndQuota.bsh CRON > /dev/null 2>&1`

[`*/5 * * * *`](https://crontab.guru/#*/5_*_*_*_*)`/bin/bash /opt/MySB/scripts/NextCloud.bsh scan CRON > /dev/null 2>&`

[`*/5 * * * *`](https://crontab.guru/#*/5_*_*_*_*)`/bin/bash /opt/MySB/scripts/DynamicAddressResolver.bsh 95488 CRON > /dev/null 2>&1`

[`*/5 * * * *`](https://crontab.guru/#*/5_*_*_*_*)`/bin/bash /opt/MySB/scripts/SendMails.bsh CRON > /dev/null 2>&1`

[`*/5 * * * *`](https://crontab.guru/#*/5_*_*_*_*) `/bin/bash /opt/MySB/scripts/PeerGuardian.bsh check CRON > /dev/null 2>&1`

