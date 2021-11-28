## Méthode
Au vu de la taille du dossier MySQL un .gitigore est ajouté pour éviter de le transférer.

La version de MySql utilisée est mysql-5.7.35-winx64.zip

Les fichiers modifiés sont eux dans le dépot(mysqlTransfert) il suffira de les remplacer dans web_server(l'organisation du dossier reprends leur emplacement réel).

On décompresse l'archive téléchargée.

On renomme le répertoire extrait en mysql(il peut être placé ensuite où on le souhaite).

Dans mon cas je le place dans web_server(avec un .gitignore qui contient mysql/).

On crée le fichier de configuration my.ini dans mysql

	* on y ajoute les lignes suivantes:
		* [mysqld]
		* basedir=C:/Web_Server/web_server/mysql
		* datadir=C:/Web_Server/web_server/mysql/data






## Liens utiles
[Installation de MySQL](https://www.youtube.com/watch?v=0vS3fOkAbPs)