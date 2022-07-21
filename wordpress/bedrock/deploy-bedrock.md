# Déploiement initial de Bedrock (Prod ou staging)

## 01. Préparation du projet en local

Versionner le site (à la racine du projet)

    git init

*Remarque: bedrock est livré avec un fichier .gitignore préconfiguré*

Envoyer les fichiers sur Github

    git push

Création d'un fichier bash pour automatiser certaines tâches :

(*Attention: suivant la config de Vscode le fichier peut poser problème, dans ce cas écrire le fichier dans l'éditeur de texte par défaut de l'OS*)

Penser à modifier les variables (l.3 à l.10)  

Nom du fichier : [Makefile](Makefile)

**!!! ATTENTION A BIEN AJOUTER LE FICHIER MAKEFILE DANS LE FICHIER .GITIGNORE !!!**

## 02. Configuration de l'environnement de prod / staging

*****************
***__(Procédure sur un serveur mutualisé 02Switch)__***
*****************
Connexion à CPanel :

https://bastet.o2switch.net:2083/

* Installer le domaine / sous-domaine (**NE PAS FAIRE POINTER LE SITE SUR LE DOSSIER WEB DE BEDROCK POUR LE MOMENT** (=> sinon problème pour cloner le dépot github))
* Activer certificat SSL Let's Encrypt (optionnel)
* Créer une base de données MySql
* Créer un utilisateur associé à la BDD et accorder les droits

## 03. Installation du site sur le serveur de prod / staging

*(Prérequis: installer composer sur l'hébergement : https://faq.o2switch.fr/hebergement-mutualise/installation-composer-o2switch)*

    composer install --no-dev --optimize-autoloader

Utiliser la commande de déploiement ([voir Makefile](Makefile))

    make deploy

  *Concrètement, commande permet de **se connecter en SSH à l'hébergement**, **cloner le repo github dans le dossier d'installation** et **installer les dépendances via composer (sans le dev)***

## 04. Modification du dossier d'installation du site.

Maintenant que les fichiers sont bien sur le serveur, on se connecte à CPanel et on modifie le chemin d'installation du domaine (en ajoutant le dossier web à la suite).

Exemple, si on avait : **public_html/monsite.fr/www** on passe à : **public_html/monsite.fr/www/web**

## 05. Installation wordpress du site en prod/staging

Dans le navigateur :  
http://monsite.test

Suivre la procédure d'installation (compte admin).
