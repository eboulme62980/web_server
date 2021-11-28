## Méthode
Ayant besoin de PHP 7.4 pour mon projet je choisis donc la version 7.4 en Thread Safe et je télécharge le .zip.

Je télécharge donc la version VC15 x64 Thread Safe (2021-Nov-16 20:36:58).

On décompresse l'archive obtenue.

On renomme le dossier obtenu en php7.4.26

On coupe/colle ce répertoire dans le dossier web_server.

* Maintenant il faut configurer PHP
	* On se rends dans le dossier php7.4.26
	* On crée une copie de php.ini-development
	* On la renomme php.ini
	* On coupe/colle ce répertoire dans Apache24.
	* Dans le dossier PHP on copie php7ts.dll et on le colle dans dans Apache24/bin
	* On ouvre maintenant httpd.conf dans Apache24/conf 
	* En fin de fichier on ajoute #PHP 7.4.26


## Liens utiles
[Installation du serveur Apache](https://www.youtube.com/watch?v=0vS3fOkAbPs)
