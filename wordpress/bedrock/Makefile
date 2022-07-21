.PHONY: help deployprod deploystaging deployenvprod deployenvstaging

ssh=user@domaine.ext
pathprod=~/public_html/monsite.fr/www/
pathstaging=~/public_html/monsite.fr/staging/
themedir=nomdutheme
gitaccount=https://nicolasmahler-fr:GITHUBTOKEN@github.com/nicolasmahler-fr/
gitrepo=nom-du-repo-github
localdomain=http://monsite.test
domain=https://monsite.fr
localdumppath=/var/vhosts/monsite.test/db/

help: ## Affiche cette aide
	@grep -E '^[a-zA-Z_-]+:.*?## .*$$' $(MAKEFILE_LIST) | sort | awk 'BEGIN {FS = ":.*?## "}; {printf "\033[36m%-30s\033[0m %s\n", $$1, $$2}'
	
deployprod: ## Déploiement initial de l'APP (git clone du repo) + envoi du fichier .env sur le serveur de PROD (sans le versionner)
	ssh $(ssh) "cd $(pathprod); git clone $(gitaccount)$(gitrepo).git .; composer install --no-dev --optimize-autoloader"
	rsync -av .env.prod $(ssh):$(path)
	ssh $(ssh) "cd $(pathprod); mv .env.prod .env"
	
deploystaging: ## Déploiement initial de l'APP (git clone du repo) + envoi du fichier .env sur le serveur de STAGING (sans le versionner)
	ssh $(ssh) "cd $(pathstaging); git clone $(gitaccount)$(gitrepo).git .; composer install --no-dev --optimize-autoloader"
	rsync -av .env.staging $(ssh):$(path)
	ssh $(ssh) "cd $(pathstaging); mv .env.staging .env"
	
deployenvprod: ## Déploi le fichier .env en prod
	rsync -av .env.prod $(ssh):$(path)
	ssh $(ssh) "cd $(pathprod); mv .env.prod .env"
	
deployenvstaging: ## Déploi le fichier .env en staging
	rsync -av .env.staging $(ssh):$(path)
	ssh $(ssh) "cd $(pathstaging); mv .env.staging .env"
