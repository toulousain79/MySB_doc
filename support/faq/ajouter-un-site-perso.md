# Ajouter un site perso

Il est possible d'héberger un site perso avec MySB, cependant, la gestion restera manuelle.  
Les ports 80 et 443 pourront être utilisés.

## Créer une entrée dans NginX

```bash
vi /etc/nginx/sites-available/mon_site

#### Mon site (HTTPs)
server {
        listen 443 default_server ssl http2;
        server_name "mon_site.mon_domaine.org";
        index index.php;
        charset utf-8;

        include snippets/letsencrypt_mon_site.mon_domaine.org.conf;

        access_log /var/log/nginx/mon_site-access.log anonymized;
        error_log /var/log/nginx/mon_site-error.log error;

        root /var/www/html;

        include /etc/nginx/conf.d/static_files;
        include /etc/nginx/conf.d/global_deny_access;
        location ~ \.php$ {
                include /etc/nginx/conf.d/php-ssl;
        }
}

#### Mon site (HTTP)
server {
        listen 80 default_server http2;
        server_name "mon_site.mon_domaine.org";
        index index.php;
        charset utf-8;

        access_log /var/log/nginx/mon_site-access.log anonymized;
        error_log /var/log/nginx/mon_site-error.log error;

        root /var/www/html;

        include /etc/nginx/conf.d/static_files;
        include /etc/nginx/conf.d/global_deny_access;
        location ~ \.php$ {
                include /etc/nginx/conf.d/php;
        }
}
```

{% hint style="info" %}
Les fichiers de votre site internet devront se trouver dans le dossier _**/var/www/html**_.
{% endhint %}

## Activer le nouveau site avec Nginx

```bash
[[ ! -L /etc/nginx/sites-enabled/mon_site ]] && ln -s /etc/nginx/sites-available/mon_site /etc/nginx/sites-enabled/mon_site
service nginx restart
```

## Ajouter un FQDN pour Let's Encrypt

```bash
echo "mon_site.mon_domaine.org" >> /opt/MySB/ssl/letsencrypt_domains
/bin/bash /opt/MySB/install/LetsEncrypt renew
```

{% hint style="warning" %}
Pensez à supprimer les FQDN qui ne sont plus valides dans le fichier _**/opt/MySB/ssl/letsencrypt\_domains**_ !
{% endhint %}

