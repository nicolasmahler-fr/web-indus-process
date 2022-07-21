# Déploiement initial de Bedrock (Prod ou staging)

## 01. Préparation du projet en local

Versionner le site (à la racine du projet)

    git init

*Remarque: bedrock est livré avec un fichier .gitignore préconfiguré*

Envoyer les fichiers sur Github

    git push


## 02. Configuration de l'environnement de prod / staging

*****************
***__(Procédure sur un serveur mutualisé 02Switch)__***
*****************
Connexion à CPanel :

https://bastet.o2switch.net:2083/

* Installer le domaine / sous-domaine 
* Activer certificat SSL Let's Encrypt (optionnel)
* Créer une base de domaine
* Créer un utilisateur associé à la BDD et accorder les droits

## 03. Installation du site sur le serveur de prod / staging

Connexion SSH à l'hébergement

    ssh login@domaine.ext  -p 22

Aller dans le dossier d'installation du site (exemple):

    cd public_html/monsite.fr/www

Pull le dossier github directement dans le dossier (sans créer de sous-dossier, d'où le point à la fin de la commande)

    git clone https://github.com/nicolasmahler-fr/monsite.git .

Installation des dépendances via composer

*(Prérequis: installer composer sur l'hébergement : https://faq.o2switch.fr/hebergement-mutualise/installation-composer-o2switch)*

    composer install

## 04. Création et push du fichier .env

## 05. Installation wordpress du site en prod/staging

Dans le navigateur :  
http://monsite.test

Suivre la procédure d'installation (compte admin).