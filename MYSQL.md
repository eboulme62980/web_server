## Méthode
Au vu de la taille du dossier MySQL un .gitigore est ajouté pour éviter de le transférer.

La version de MySql utilisée est mysql-8.0.27-winx64.zip

Les fichiers modifiés sont eux dans le dépot(PourDeplacementMysql) il suffira de les remplacer dans web_server(l'organisation du dossier reprends leur emplacement réel).

On décompresse l'archive téléchargée.

On renomme le répertoire extrait en mysql(il peut être placé ensuite où on le souhaite).

Dans mon cas je le place dans web_server(avec un .gitignore qui contient mysql/).

On crée le fichier de configuration my.ini dans mysql

	* on y ajoute les lignes suivantes:
		* [mysqld]
		* basedir=C:/Web_Server/web_server/mysql
		* datadir=C:/Web_Server/web_server/mysql/data

Pour initialiser le dossier data on ouvre un shell sur mysql/bin en administrateur
	* on execute .\mysqld.exe --defaults-file=c:\Web_Server\web_server\mysql\my.ini --initialize
	* le dossier data a été créé dans le dossier mysql

* On va ensuite enlever le mot de passe par défaut pour root créé lors de l'initialisation du dossier data
	* On démarre le serveur mysql en mode console avec .\mysqld.exe --console (devra resté ouvert pour que le serveur demeure actif)
	* Le mot de passe est stocké dans mysql/data/{nom_du_pc}.err(ouvrez le avec le bloc-notes).
	* Recherchez dans ce fichier A temporary password is generated for root@localhost: 
	* le mot de passe est après root@localhost:
	* On ouvre un autre terminal qui va permettre la connexion à MySQL 
	* On copie le mot de passe temporaire et on exécute .\mysql.exe -u root -p
	* Pour le password on colle celui qui a été copié
	* Nous sommes maintenant connecté au serveur MySQL
	* Rien n'est vraiment possible tant que le mot de passe par défaut n'as pas été changé.
	* On change le password pour root en éxécutant  ALTER user 'root'@'localhost' identified by '';
	* ATTENTION Ce n'est pas sécurisé d'utiliser root pour un site en production et encore moins sans mot de passe!!!!!
	* On quitte MySQL en éxécutant exit
	* On se connecte à nouveau en tant que root mais sans mot de passe en éxécutant .\mysql.exe -u root
	* Vérifions l'aacès complet en éxécutant SHOW DATABASES;
	* Le serveur est donc fonctionnel
	* Pour le quitter proprement on éxécute exit
	* Ensuite on éxécute .\mysqladmin.exe -u root shutdown(Vous verrez le serveur s'arrêter dans l'autre terminal lancé au début  par .\mysqld.exe --console).

## Liens utiles
[Installation de MySQL](https://www.youtube.com/watch?v=0vS3fOkAbPs)
