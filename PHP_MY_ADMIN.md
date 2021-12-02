## Installation PhpMyAdmin

Je vais dans mon cas ignorer le dossier htdocs/phpmymadmin dans git avec un.gitignore (il vous faudra donc télécharger phpMyAdmin par vous même)
* Installation détaillée
	* On récupère l'archive de [phpMyAdmin](https://www.phpmyadmin.net/downloads/) (dans mon cas la version phpMyAdmin-5.1.1-all-languages.zip)
		* On extrait l'archive récupérée
		* On renomme le dossier obtenu en phpmyadmin
		* On coupe/colle ce dossier dans le répertoire htdocs
	* Dans le dossier de phpmyadmin
		* On fait une copie de config.sample.inc.php
		* On la renomme config.inc.php 
	* On va utiliser les cookies et pour ce faire on va devoir créer un mot de passe pour $cfg['blowfish_secret'] = ''
		* On utilise un site en ligne afin de générer ce mot de passe
		* On le colle entre les ''
	* Dans la section Server parameters
		* On modifie $cfg['Servers'][$i]['AllowNoPassword'] = false; à $cfg['Servers'][$i]['AllowNoPassword']= true; car le mot de passe de root a été supprimmé précédemment.
		* On définit la langue de phpMyAdmin en ajoutant $cfg['DefaultLang'] = 'fr'; sous les $cfg déjà présents.
		* On définit le serveur par défaut en ajoutant $cfg['ServerDefault'] = 1; sous les $cfg déjà présents. 
		* On peut également nommer le serveur en ajoutant $cfg['Servers'][$i]['verbose'] = 'web_server';
		* On définit l'utilisateur en ajoutant $cfg['Servers'][$i]['user'] = 'root';
		* On définit le mot de passe $cfg['Servers'][$i]['password'] = '';
	* On va modifier php.ini situé dans le dossier apache(ainsi que celui dans le dossier php)
		* On décommente la ligne qui contient ;extension=mysqli
	* On démarre les serveurs d'Apache et de MySQL
	* On accède bien à phpMyAdmin en saisissant localhost/phpmyadmin
	* Une fois connecté on crée automatiquement la base phpmyadmin(voir lien erreur en bas de première page)

## Liens utiles
[Installation de Php My Admin](https://www.youtube.com/watch?v=S0mR_Gl7Rg4)
