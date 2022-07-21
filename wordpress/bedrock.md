# Industrialisation de site Wordpress avec Bedrock

## 01. Setup le projet en local
- Créér une base de données dans phpmaydmin (http://localhost/phpmyadmin)
- [Configurer un domaine local (virtual host)](../vhost.md) 

## 02. Télécharger Bedrock

Aller dans le dossier d'installation :  

    cd /var/vhost/monsite.test/web

Installer Bedrock (*directement dans le dossier*)

    composer create-project roots/bedrock ./

**RAPPEL : Attention configuration du vhost, le site doit pointer sur le dossier web!!**

## 03. Configurer le projet

*Suivre les instructions dans le fichier **.env*** :
* Accès DB
* Environnement et url du site
* Salage des variables globales

## 04. Lancer l'install de Wordpress

Dans le navigateur :  
http://monsite.test