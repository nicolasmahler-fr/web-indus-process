.PHONY: deployenv

ssh=user@domaine.ext
path=~/public_html/monsite.fr/www/
themedir=nomdutheme
gitaccount=https://nicolasmahler-fr:GITHUBTOKEN@github.com/nicolasmahler-fr/
gitrepo=nom-du-repo-github
localdomain=http://monsite.test
domain=https://monsite.fr
localdumppath=/var/vhosts/monsite.test/db/

help: ## Affiche cette aide
	@grep -E '^[a-zA-Z_-]+:.*?## .*$$' $(MAKEFILE_LIST) | sort | awk 'BEGIN {FS = ":.*?## "}; {printf "\033[36m%-30s\033[0m %s\n", $$1, $$2}'
	
deploy: ## Déploiement initial de l'APP (git clone du repo) + envoi du fichier .env sur le serveur (sans le versionner)
	ssh $(ssh) "cd $(path); git clone $(gitaccount)$(gitrepo).git .; composer install --no-dev --optimize-autoloader"
	rsync -av .env.prod $(ssh):$(path)
	ssh $(ssh) "cd $(path); mv .env.prod .env"
