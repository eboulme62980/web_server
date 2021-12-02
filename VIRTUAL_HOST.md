## Méthode d'utilisation d'un hôte virtuel
Il est préférable de développer ses différents projets dans des répertoires indépendants les uns des autres.

Pour ce faire je vais implémenter un hote virtuel avec Apache.

Mon répertoire de travail est normalement htdocs.

Je crée un projet dans htdocs(essai_virtual/public/index.html).

Je vais donc créer un serveur nommé  "virtual.local" et quand je taperais http://virtual.local/ c'est le dossier "htdocs/essai_virtual/public/index.html" qui sera le document racine du projet.

Si je tape à nouveau http://localhost/ je retournerais à la racine initiale du serveur soit directement dans "htdocs".



* Procédure détaillée:
	* On ajoute le domaine virtuel voulu dans le fichier "hosts" de windows(sur mon pc il est ici => "C:\Windows\System32\drivers\etc\hosts")
	* J'ajoute 127.0.0.1 virtual.local à la fin de ce dernier(pour modifier ce fichier ouvrez le avec le bloc-notes en administrateur).
	* Dans httpd.conf je modifie:
		* Décommenter la ligne LoadModule rewrite_module modules/mod_rewrite.so
		* Dans le paramètre du DocumentRoot il faut modifier ".....AllowOverride None...." en "AllowOverride All".
	* 

## Liens utiles
[Virtual Hosting via httpd.conf et hosts](https://www.commentcamarche.net/faq/10240-configurer-apache-et-windows-pour-creer-un-hote-virtuel)

[Virtual Hosting via httpd-vhost.conf et hosts](https://blog.pascal-martin.fr/public/zfstde-fr/zfbook.creating.a.local.domain.using.apache.virtual.hosts.html)