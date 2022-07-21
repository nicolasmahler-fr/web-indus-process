# Créer un domaine local (Ubuntu + Apache)


## 1. Ajouter le domaine
    sudo gedit /etc/hosts

Renseigner : 

    127.0.0.1  monsite.test www.monsite.test
    

## 2. Tester la config

    ping monsite.test

## 3. Créer les dossiers

    cd /var/vhosts/     

Dossiers :

    monsite.test
        -/db
        -/logs
        -/web

## 4. Créer le fichier de configuration

    sudo gedit /etc/apache2/sites-available/wpstarter.test.conf

Contenu du fichier 

    <VirtualHost *:80>
            #nom de domaine
        ServerName wpstarter.test 
            #on accepte aussi le www
        ServerAlias www.wpstarter.test 
            #logs d'erreur
        ErrorLog /var/vhosts/wpstarter.test/logs/error.log 
            #logs de connexion
        CustomLog /var/vhosts/wpstarter.test/logs/access.log common
            #Définition de la racine des sources php
        DocumentRoot "/var/vhosts/wpstarter.test/web/"
        <directory /var/vhosts/wpstarter.test/web/>
            Options -Indexes +FollowSymLinks +MultiViews
            AllowOverride All
            Require all granted
        </Directory>
    </VirtualHost>

**DANS LE CAS DE BEDROCK, il faut ajouter un dossier!**

    <VirtualHost *:80>
            #nom de domaine
        ServerName wpstarter.test 
            #on accepte aussi le www
        ServerAlias www.wpstarter.test 
            #logs d'erreur
        ErrorLog /var/vhosts/wpstarter.test/logs/error.log 
            #logs de connexion
        CustomLog /var/vhosts/wpstarter.test/logs/access.log common
            #Définition de la racine des sources php
        DocumentRoot "/var/vhosts/wpstarter.test/web/web"
        <directory /var/vhosts/wpstarter.test/web/web>
            Options -Indexes +FollowSymLinks +MultiViews
            AllowOverride All
            Require all granted
        </Directory>
    </VirtualHost>

## 05 Activer le vhost et restart Apache

    sudo a2ensite wpstarter.test.conf
    sudo systemctl reload apache2