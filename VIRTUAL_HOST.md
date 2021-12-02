## Méthode d'utilisation d'un hôte virtuel
Il est préférable de développer ses différents projets dans des répertoires indépendants les uns des autres.

Pour ce faire je vais implémenter un hôte virtuel avec Apache.

Mon répertoire de travail est normalement htdocs.

Je crée  pour l'exemple un projet dans htdocs(essai_virtual/public/index.html).

Je vais donc créer un serveur nommé  "virtual.local" et quand je taperais http://virtual.local/ c'est le dossier "htdocs/essai_virtual/public/index.html" qui sera le document racine du projet.

Si je tape à nouveau http://localhost/ je retournerais à la racine initiale du serveur soit directement dans "htdocs" et j'y verrais le dossier essai_virtual.


* Procédure détaillée:
	* On ajoute le domaine virtuel voulu dans le fichier "hosts" de windows(sur mon pc il est ici => "C:\Windows\System32\drivers\etc\hosts")
	* J'ajoute 127.0.0.1 virtual.local à la fin de ce dernier(pour modifier ce fichier ouvrez le avec le bloc-notes en administrateur).
	* Dans httpd.conf je modifie:
		* Décommenter la ligne LoadModule rewrite_module modules/mod_rewrite.so
		* Dans le paramètre du DocumentRoot il faut modifier ".....AllowOverride None...." en "AllowOverride All".
	* Maintenant nous allons indiquer le serveur virtuel dans httpd.conf(il faut déclarer le local host également afin de ne pas le perdre !).
		* En fin de fichier j'ajoute 2 hôtes virtuels:
		
	* Pour localhost
			
			#####
				
			## localhost
					
			#####   
				
			<VirtualHost localhost>
				
			DocumentRoot "${SRVROOT}/htdocs" 
				
			ServerName localhost  
				
			</VirtualHost> 
			
				
	* Pour virtual.local
				
			#####
				
			## virtual.local 
				
			#####    
				
			<VirtualHost virtual.local>   
				
    			DocumentRoot "${SRVROOT}/htdocs/essai_virtual/public/"  
			
    			ServerName virtual.local
			
			</VirtualHost>
				
	* On démarre le serveur(.\httpd.exe --console)
			* Si on saisit http://localhost/ on arrive bien dans htdocs
			* Si on saisit http://virtual.local/ on arrive bien dans essai_virtual/public


# Déplacement des directives dans httpd-vhosts.conf

* Procédure détaillée:
	* On décommente la ligne #Include conf/extra/httpd-vhosts.conf
	* On déplace les hôtes virtuels à la fin de httpd-vhosts.conf(on commente les hôtes d'exemple)
	* On démarre le serveur(.\httpd.exe --console)
		* Si on saisit http://localhost/ on arrive bien dans htdocs
		* Si on saisit http://virtual.local/ on arrive bien dans essai_virtual/public
	* On ajoute également les fichiers de log en modifiant légèrement les directives comme suit
		* On ajoute dans chacun des Virtual Host(XXXX sera ici remplacé par localhost et virtual):
			
			 	ErrorLog "logs/XXXX-error.log"
				
			 	CustomLog "logs/XXXX-access.log" common

		

## Liens utiles
[Virtual Hosting via httpd.conf et hosts](https://www.commentcamarche.net/faq/10240-configurer-apache-et-windows-pour-creer-un-hote-virtuel)

[Virtual Hosting via httpd-vhosts.conf et hosts](https://blog.pascal-martin.fr/public/zfstde-fr/zfbook.creating.a.local.domain.using.apache.virtual.hosts.html)
