Shortener-URL-Redirect
======================

Script php permettant de raccourcir un lien. le lien raccourci redirigera automatiquement vers sa destination

A Propos :
======================
- Ce script php raccourcis simplement une URL donn� par un utilisateur pour lui fournir un lien redirigeant vers celle-ci.
- Le script verifie que l'utilisateur a rentr� une URL correcte via filter_var(FILTER_VALIDATE_URL), ce qui veut dire que l'url n'est pas visit�
- Fonctionne sans cookie, sans authentification, sans enrigistrement des donn�es de l'utilisateur(: pas d'ip sauvegard� par exemple),

Prerequi :
======================
- Avoir un domaine d�di� : pour ma part c'est pupu.eu
- Compatibilit� php sqlite3 (apt-get install php5-sqlite)
- configurer son VHost correctement (avec l'url rewriting configur�) voici un exemple de mon VHOST apache2 :
//short.conf

		<VirtualHost *:80>
        		ServerAdmin contact@purexo.eu
        		ServerName pupu.eu
        		ServerAlias pupu.eu
        		DocumentRoot /var/www/short
        		<Directory /var/www/short>
                		Options -Indexes +FollowSymLinks +MultiViews
                		AllowOverride All
                
                		RewriteEngine on
                
				RewriteCond %{REQUEST_URI} =/
				RewriteRule ^(.*) index.php [L]
                
				RewriteCond %{REQUEST_URI} !/index\.php
				RewriteRule ^(.*) index.php?a=$1 [L]
        		</Directory>
		</VirtualHost>

Instalation :
======================
1. editer dans index.php : $protocol $domaine pour correspondre � votre configuration
2. Enjoy
3. (le fichier sql ne sert plus a rien sauf a voir comment etait con�u la BDD sous mysql)

Utilisation :
======================
acceder � votre nom de domaine dans votre navigateur, enjoy.