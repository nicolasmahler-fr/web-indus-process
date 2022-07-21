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
	
deployenv: ## Déploie le fichier .env.prod sur le serveur distant et le renomme en .env
	rsync -av .env.prod $(ssh):$(path)
	ssh $(ssh) "cd $(path); mv .env.prod .env"
