## Méthode
Apache ne fournissant pas de  Binaire depuis son site on va le télécharger sur [Apache Lounge](https://www.apachelounge.com/download/)

Dans mon cas dans la partie Apache 2.4 binaries VS16, je choisi la version 64 Bits => Apache 2.4.51 Win64.

Il est à noter que pour fonctionner Apache à besoin de Visual C++ Redistributable Packages.

La dernière version étant rétro-compatible vous la trouverez [ici](https://aka.ms/vs/17/release/VC_redist.x64.exe)

Après installation du package Microsoft je peux extraire Apache de son archive.

Vous copiez l'intégralité du dossier Apache 24 dans votre dossier web_server sur C:.

* Maintenant il faut configurer Apache
	* On ouvre le fichier httpd.conf situé dans le répertoire conf.
		* Pour modifier la racine du serveur en ligne 37, on remplace Define SRVROOT "c:/Apache24" en Define SRVROOT "c:/Web_Server/web_server/Apache24".
		* En ligne 60 Listen 80 correspond au port d'écoute du serveur Apache.
		* De la ligne 74 à 185 se trouvent les modules d'Apache.
		* Dans notre cas on enlève le # en début de ligne 162 afin d'avoir le module rewrite activé ce qui donne LoadModule rewrite_module modules/mod_rewrite.so
		* En ligne 218 on peut configurer le mail de l'administrateur si on le souhaite en modifiant ServerAdmin admin@example.com.
		* Pour le serveur name en ligne on remplace #ServerName www.example.com:80 par ServerName localhost
		* Le répertoire du serveur(htdocs) où seront les fichiers est définit en ligne 251 et 252.
		* Pour démarrer le serveur Apache il faut éxécuter ".\httpd.exe" dans une ligne de commande ouverte dans le dossier bin(dans mon cas Windows Power Shell en mode administrateur).
		* Ne pas refermer cette fenêtre sinon le serveur Apache sera stoppé!
		* On vérifie le fonctionnement du serveur Apache en ouvrant localhost dans son navigateur et si tout est OK on a le message "Apache est fonctionnel" qui correspond à index.html situé dans le répertoire htdocs.


## Liens utiles
[Installation du serveur Apache](https://www.youtube.com/watch?v=79XwZrJdzho&t=11s)
