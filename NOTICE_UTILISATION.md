## Mode d'emploi du serveur

	* Procédure d'utilisation
		* On démarre Apache(1 terminal actif)
		* On démarre MySql(2 terminaux actifs)
		* On code dans la joie et la bonne humeur
		* On arrête Mysql(à partir de la fenêtre où nous nous sommes connectés au serveur)
		* On arrête Apache


* Pour démarrer Apache:
	* Ouvrir un terminal en administrateur dans le dossier bin d'Apache 24.
	* y éxécuter la commande .\httpd.exe.
	* Fermer le terminal pour arrêter le serveur Apache.

* Pour démarrer PHP:
	* PHP démarre automatiquement(est appelé par Apache lorsque ce dernier rencontre des fichiers portant l'extension .php)

* Pour démarrer MySQL:
	* Ouvrir un terminal en administrateur mysql/bin.
	* Y éxécuter la commande .\mysqld.exe --console(toujours laisser cette fenêtre active tant que l'on utilise MySQL).
	* Ouvrir un deuxième terminal dans mysql/bin.
	* Se connecter au serveur MySQL en éxécutant .\mysql.exe -u root
	* Pour quitter proprement dans le deuxième terminal éxécuter les instructons suivantes:
		* exit
		* .\mysqladmin.exe -u root shutdown


