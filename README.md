# hugo-workers

Cette démo utilise Cloudflare et Github Action pour déployer votre blog de manière simplifié sur les infrastructures de Cloudflare.

Ce projet a été réalisé pour supporter ma session sur [Cloudflare TV](https://cloudflare.tv/event/7whW44ANFW9dTakUb3nRtA).

Suite a la publication du [boutton déployer](https://developers.cloudflare.com/workers/platform/deploy-button), des modifications ont été apportées afin de vous permettre de deployer ce projet rapidement sur votre compte Cloudflare (cf. section [déploiement](#déplopiement))

## Objectifs

* Simplifier le déploiement et le maintient de votre blog
* Bénéficier des solutions de sécurité et de performance de Cloudflare
* Fournir un squelette d'implementation permettant une reproduction simplifiée 

## Pré-requis

* Un compte et un domaine sur Cloudflare, documentation [ici](https://support.cloudflare.com/hc/fr-fr/articles/201720164-Cr%C3%A9er-un-compte-Cloudflare-et-ajouter-un-site-web)
* Un souscription à [Workers Unlimited](https://workers.cloudflare.com/#plans)
* Un compte Github

## Composantes du projet

Ce projet s'appuie sur:
* **Github Action** : la méthode d'integration Continue mise en place par Github. Le fichier de configuration est [main.yml](https://github.com/vences/hugo-workers/blob/master/.github/workflows/main.yml)
* **Wrangler** : l'outil d’orchestration de Cloudflare Workers. Le fichier de configuration est [wrangler.toml](https://github.com/vences/hugo-workers/blob/master/wrangler.toml)
* **Hugo** : framework permettant la génération de site web. Le fichier de configuration est [config.toml](https://github.com/vences/hugo-workers/blob/master/config.toml)

## Déploiement

Si vous souhaiter deployer simplement ce projet vous pouvez utiliser le boutton suivant: [![Deploy to Cloudflare Workers](https://deploy.workers.cloudflare.com/button?paid=true)](https://deploy.workers.cloudflare.com/?url=https://github.com/vences/hugo-workers&paid=true)

Les modifications suivantes ont été apportées afin d'intégrer le support du boutton :
* Suppression de `account_id` dans `wrangler.toml`
* Modification du workflow Github Actions `.github/workflows/main.yml` avec:
  * Ajout de `wrangler-actions` avec un secret `CF_ACCOUNT_ID`
  * Ajout de `repository_dispatch:` 

Vous devez également changer la `route` et `zone_id` dans le fichier `wrangler.toml` pour que le deploiement soit un succes sur votre compte.

## Pour aller plus loin

Voici les documentaions sur lesquelles je me suis reposée:
* [Worker site](https://developers.cloudflare.com/workers/sites/)
* [Hugo](https://gohugo.io/getting-started/quick-start/)
* [Github Actions](https://help.github.com/en/actions)

La demo est visible sur https://mon-blog.vence.tech/ 

Un article a été ajouté à la suite de la session Cloudflare TV afin de répondre à la question sur l'implementation de Workers KV.

Vous pouvez visionner plus de contenue sur [Cloudflare TV](https://cloudflare.tv/live)
